# Computer Graphics

## Introduction

- It is a sub-fields of computer science
- Computer Graphics studies methods for digitally synthesizing and manipulating visual content
  - This field has evolved to dealing with all kinds of sensory information
- Computer Vision deals with real life visual information and convert it into digital information
  - Dealing with the inverse problem of computer graphics
- 3D printing enables the digital information generated by computer graphics to become physical matters
- Prospective projection
  - 3D Objects that is further away from the camera will be smaller in the 2D projection
  - This can be proved by using `pinhole` cameara and similar triangles
- Display visual content on screen
  - Images are represented as a 2D grid of pixels
  - Each pixel is consisted of three color value R, G, B with stregth from 0 to 255
  - All combination of R, G, B values enable the pixels to display most of the colors
- Graphics problems are often break down into sampling and reconstruction:
  - sampling turns a continuous signal into digital information
  - reconstruction turns digital information into a continuous signal

## Computer Graphics Algorithms

### Digital 3D to Digital 2D

- Given that the camera is located at point `c = (x, y, z)`, the point `X = (X, Y, Z)` on any 3D object can be drawn on a 2D plane at point `P = (u, v)`, find the point `P`
  1. Substract `c` from `X` to get `(a, b, c)`, which is the 3D location of the point relative to the camera
  2. Divide `(a, b)` by `c` to get `(u, v)`

### Rasterization

- It is a method to display object on the screen, pixel by pixel
- It is the process of converting a continuous object to a discrete representation on a raster grid(pixel grid)
- Rasterization pipeline converts all primitives to triangles
  - it is the building bloack for graphics pipeline
- It considers each primitive(shapes like trangle) as a object for displaying
  - It is fast and a perfect match for 2D vector art, font and 3D preview
  - It is not good for photorealism
    - photorealism aims to display real life result
- The following line rasterization rules can be used:
  - Light up all pixels that are intersected by the line
  - Diamond rule - light up if line passes through associated diamond
    - associated diamond are created by connecting the midpoint of the four sides of the pixel square
    - used by modern GPUs
- The following ways can be used to iterate through pixels and determine whether it should be lit up based and the line rasteriztion rules
  - iterate through all pixels, `O(n^2)`
  - Incremental line rasterization - uses the endpoint and the slope to of the known line to find the pixels
- The following triangle rasterization rules can be used:
  - compute fraction of pixel area covered by triangle, then color pixel according to this fraction
    - not good when occlusion occurs
  - Use sample point to determine(e.g. use the center point of the pixel)
    - When the edge falls on the sample point specific rules are required to determine whether it is within the triangle
    - `OpenGL/Direct3D` considers that the sample falls within a triangle if the edge is a `top edge` or `left edge`
    - Aliasing occurs when undersampling high-frequency singals - the sample points will result in a completely different pattern than the original singal when details are lost in a certain large interval
      - As a result high frequencies signal are sampled as low frequencies
      - Nyquist-Shannon theorem - a band-limited signal(has no frequencies above some threhold) can be perfectly reconstructed if sampled with frequencies that equeals the threhold times two using a `sinc filter`
    - supersampling is using multiple points in a pixel to sample and use the fraction that the sample points are covered by the triangle to determent the brightness of the color
      - It is used to reduce aliasing
- The following ways can be used to iterate through pixels and determine whether it should be lit up based and the triangle rasteriztion rules
  - a sample point falls within a triangle if three half planes associated with the triangle edges all contain the point
  - iterata all point on screen
  - incremental traversal - iterate along the rows of the triangle and increment
    - improve memory performance
  - Parallel coverage test - test half planes for all sample points parallel
    - GPUs have special-purpose hardware for this task
  - Tiled triangle traversal - try large block first, ignore large empty area if it is not covered
    - divide the entire screen into for area, if exist, divide into four smaller area and then check further
  - A combination of above techniques are used in modern computer graphics processing

### Ray Tracing

- It is a method to display object on the screen, pixel by pixel
- It considers each pixel for displaying
- It is slow and good for photorealism

### Transformation

- It is a type of spatial tranformation
  - A function that assigns each point a new location
- Linear transformation is applied by linear map(function)
- A linear function maps lines to lines and preserves the origin
  - addition and scaling operation of a shape vector return the same results from the transformation when it is done together and separately
  - Otherwise its an affine transformation
- Linear transformation is simple and can be calculated by multipling the transformation matrix with the original matrix

#### Translation

- 2D Translation - $$\begin{bmatrix} p'_x \\ p'_y \end{bmatrix}=\begin{bmatrix} p_x + t_x \\ p_y + t_y \end{bmatrix}$$
  - Use Homogeneous Coordinates to represent the transformation with a matrix $$\begin{bmatrix} p'_x \\ p'_y \end{bmatrix}=\begin{bmatrix} 1&0&t_x \\ 0&1&t_y \end{bmatrix}\begin{bmatrix} p_x \\ p_y\\1 \end{bmatrix}=\begin{bmatrix} p_x + t_x \\ p_y + t_y \end{bmatrix}$$ or $$\begin{bmatrix} p'_x \\ p'_y\\1 \end{bmatrix}=\begin{bmatrix} 1&0&t_x \\ 0&1&t_y \\0&0&1\end{bmatrix}\begin{bmatrix} p_x \\ p_y\\1 \end{bmatrix}=\begin{bmatrix} p_x + t_x \\ p_y + t_y\\1 \end{bmatrix}$$ to make the transformation matrix `n+1` by `n+1`
- 3D Translation, $$\begin{bmatrix} 1&0&0&t_x \\ 0&1&0&t_y \\0&0&1&t_z\\0&0&0&1\end{bmatrix}$$

#### Rotation

- It preserves the origin and distances between points, orientation
- Rotation Matrices are Orthogonal - It yields an identity matrix when it multiply by the transpose of it itself, its transpose is the same as its inverse
- 2D Rotation
  - Clockwise rotation: $$\begin{bmatrix} p'_x \\ p'_y \end{bmatrix}=\begin{bmatrix} \cos{\theta}& \sin{\theta} \\ -\sin{\theta}&\cos{\theta} \end{bmatrix}\begin{bmatrix} p_x \\ p_y \end{bmatrix}$$
  - Counter-clockwise rotation: $$\begin{bmatrix} p'_x \\ p'_y \end{bmatrix}=\begin{bmatrix} \cos{\theta}& -\sin{\theta} \\ \sin{\theta}&\cos{\theta} \end{bmatrix}\begin{bmatrix} p_x \\ p_y \end{bmatrix}$$
- To rotate a 3D shape around x-axis multiple the vector representation of the shape by $$\begin{bmatrix} 1 & 0 & 0 \\ 0 & \cos{\theta} & -\sin{\theta} \\ 0 & \sin{\theta}&\cos{\theta} \end{bmatrix}$$, for y-axis multiply by $$\begin{bmatrix} \cos{\theta} & 0 & \sin{\theta} \\ 0 & 1 & 0 \\ -\sin{\theta} & 0 & \cos{\theta} \end{bmatrix}$$, for z-axis multiply by $$\begin{bmatrix} \cos{\theta} & -\sin{\theta} & 0 \\ \sin{\theta} & \cos{\theta} & 0 \\ 0 & 0 & 1 \end{bmatrix}$$
- The rotation transformation matrix `Q` that is used to multiple the origin shape vector has the propery that its transpose is its inverse, where $$Q^TQ=I$$
  - Any maitrx that satisfy this property describes a orthogonal transformation
  - When the determinant of `Q` is greater than `0`. it is a rotation
  - When the determinant of `Q` is smaller than `0`. it is a reflection(orientation not preserved)
- Any matrix multiply by the rotation transformation matrix `Q` and then multiply by $$Q^{-1}$$ or $$Q^T$$ will return the original matrix because of the above property
  - $$Q^T$$ can be used to revert the rotation transformation

#### Scaling

- It preserves the lines through the origin and direction of vectors
- 2D Scaling
  - Uniform scale $$\begin{bmatrix} p'_x \\ p'_y \end{bmatrix}=\begin{bmatrix} sp'_x \\ sp'_y \end{bmatrix}=\begin{bmatrix} s&0 \\ 0&s \end{bmatrix}\begin{bmatrix} p_x \\ p_y \end{bmatrix}$$
  - Non-uniform scale $$\begin{bmatrix} p'_x \\ p'_y \end{bmatrix}=\begin{bmatrix} s_xp'_x \\ s_yp'_y \end{bmatrix}=\begin{bmatrix} s_x&0 \\ 0&s_y \end{bmatrix}\begin{bmatrix} p_x \\ p_y \end{bmatrix}$$
- 3D Scaling in homogeneous coordinates, $$\begin{bmatrix} s_x&0&0&0 \\ 0&s_y&0&0\\0&0&s_z&0\\0&0&0&1 \end{bmatrix}$$
- Scaling a vector by `a` can be calculated as multiple the vector(a matrix with one column) by a diagonal matrix `D` of the same size with `a` along the diagonal
- When `a` is negative, each negative sign in the diagonal will reflect the shape once
  - for 2D, reflecting twice results in a 180 degree rotation transformation
  - for 3D, reflecting three times results in a reversed orientation, so it will be a reflection transformation
- Non-uniform scaling can happens along the axis(Axis-Aligned)
  - for calculation, replace all the `a` in the diagonal to `a`, `b`, `c` where they are the different scaling factors along three axes, corresponding to the axes of the vector on each row
- Non-uniform scaling along other axes can be calculated by rotate the object to the new axes, then apply the diagonal scaling, then rotate back to the original axes
  - The overall transformation can written as $$A=R^TDR$$ or $$A=RDR^T$$
  - the overall transformaiton is represented by a symmetric matrix
    - a symmetric matrix is a square matrix that is equal to its transpose
  - all symmetric matrics represent nonuniform scaling(Spectral Theorem)
  - If the semidefinite of the symmetric matrix is position, it means the scaling is positive

#### Shear

- A shear displaces each point `x` in a direction `u` according to its distance along a fixed vector `v`
- A shear transformation can be calculated by multiply the origin vector by matrix $$A_{u,v} = I+uv^T$$

#### Composite Transformations

- A combination transformation matrix of the above transformation can be achieved by multiply by related transformation matrix together
  - The transformation matrix on the right side is applied first
- All of the transformation matrix M works by multiplying it with the original matrix, transformed matrix `p'=Mp`
- Transformation matrix can be combined as `p' = RSTRSRST p = Mp`
  - The order matters
- In the combined the transformation matrix, the last row is for the homogeneous coordinates, the last column is for translation, the remaining submatrix on the top right is for the combined rotation and scale

#### Decompose Transformations

- A composite transformation can be decompose using the following methods
  - Polar Decomposition - It decomposes any composite transformation matrix A into an orthogonal matrix(rotation or reflection) and symmetric positive-semedefinete matrix
  - Spectral Decomposition - It decomposes the symmetric matrix into an orthogonal matrix,times a diagonal matrix, times the transpose of the first orthogonal matrix
  - Singular Value Decomposition - Polar Decomposition combines Spectral Decomposition
    - Every matrix has a Singular value decomposition

#### Projection

- Orthographic Projection - It doesn't have the sense of depth
  - $$\begin{bmatrix} \frac{2}{r-l}&0&0&\frac{-2l}{r-l}-1 \\ 0&\frac{2}{t-b}&0&\frac{-2b}{t-b}-1\\0&0&\frac{2}{f-n}&\frac{-2n}{f-n}-1\\0&0&0&1 \end{bmatrix}$$
- Perspective Projection - Objects that are further away will appear smaller
  - $$\begin{bmatrix} n&0&0&0 \\ 0&n&0&0\\0&0&n+f&-fn\\0&0&1&0 \end{bmatrix}$$
