# Linear Algebra

## Matrices

#### Definition of Matrices

- A Matrix is a representation of a system of linear equations.
  - ![$a_1x+b_1y=c_1$](https://render.githubusercontent.com/render/math?math=%24a_1x%2Bb_1y%3Dc_1%24) and ![$a_2x+b_2y=c_2$](https://render.githubusercontent.com/render/math?math=%24a_2x%2Bb_2y%3Dc_2%24) and be represented by a matrix as ![$\begin{bmatrix} a_1 & b_1 \ a_2 & b_2  \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24%5Cbegin%7Bbmatrix%7D%20a_1%20%26%20b_1%20%5C%5C%20a_2%20%26%20b_2%20%20%5Cend%7Bbmatrix%7D%24)
- Augmented Matrix includes dependent variables of a system of linear equations in the right most column, ![$\begin{bmatrix} a_1 & b_1 & c_1 \ a_2 & b_2 & c_2  \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24%5Cbegin%7Bbmatrix%7D%20a_1%20%26%20b_1%20%26%20c_1%20%5C%5C%20a_2%20%26%20b_2%20%26%20c_2%20%20%5Cend%7Bbmatrix%7D%24) or ![$\left[ \begin{array}{cc|r} a_1 & b_1 & c_1\ a_2 & b_2 & c_2 \end{array} \right]$](https://render.githubusercontent.com/render/math?math=%24%5Cleft%5B%20%5Cbegin%7Barray%7D%7Bcc%7Cr%7D%20a_1%20%26%20b_1%20%26%20c_1%5C%5C%20a_2%20%26%20b_2%20%26%20c_2%20%5Cend%7Barray%7D%20%5Cright%5D%24)
- The Size of A Matrix can be represented as `2 X 3`
  - First number represents the number of rows.(number of equations)
  - First number represents the number of columns.(number of variables)
- Square Matrix - is a matrix has the same number of rows and columns.
- The elements or entries of the matrix can be represented as ![$a_{ij}$](https://render.githubusercontent.com/render/math?math=%24a_%7Bij%7D%24) where `i` is its row number and `j` is its column number.
  - For example, ![$\begin{bmatrix} a_{11} & a_{12} & a_{13} \ a_{21} & a_{22} & a_{23} \ a_{31} & a_{32} & a_{33} \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24%5Cbegin%7Bbmatrix%7D%20a_%7B11%7D%20%26%20a_%7B12%7D%20%26%20a_%7B13%7D%20%5C%5C%20a_%7B21%7D%20%26%20a_%7B22%7D%20%26%20a_%7B23%7D%20%5C%5C%20a_%7B31%7D%20%26%20a_%7B32%7D%20%26%20a_%7B33%7D%20%5Cend%7Bbmatrix%7D%24)
- For Matrix `A` and `B`, `A = B` if they have the same dimension and all their elements are the same.
- When a matrix add a matrix, a Matrix minus a matrix and a matrix multiply or divide by a constant. These operations will take effect on each element of the matrix independently.
  - For example, `A + B` will get Matrix `C` which all of its element equals the sum of elements of `A` and `B` from the same location.
  - These three operations of matrix can be combined and calculated at the same time.
  - Addition and Subtraction only works for two matrix that has the same dimension.
  - The dimension of matrices will not be changed by these operation.
- When a matrix multiply by a matrix. If Matrix `A` has shape `M X N`, If Matrix `B` has shape `P X Q`
  - `N` must equal `P`.
  - The result will be matrix `C` with shape `M X Q`.
  - matrix `C` will have element ![$c_{mq} = $](https://render.githubusercontent.com/render/math?math=%24c_%7Bmq%7D%20%3D%20%24) equals the sum of elements from row `m` of Matrix A multiplies elements from row `q` of Matrix B. Ex, ![$c_{mq} = a_{m1}b_{1q}+a_{m2}b_{2q}+ \ldots $](https://render.githubusercontent.com/render/math?math=%24c_%7Bmq%7D%20%3D%20a_%7Bm1%7Db_%7B1q%7D%2Ba_%7Bm2%7Db_%7B2q%7D%2B%20%5Cldots%20%24)
- Identity Matrix ![$I_n$](https://render.githubusercontent.com/render/math?math=%24I_n%24) is a `n X n` square matrix has 1 aross diagonal and 0 for all other elements.
- ![$A^{-1}$](https://render.githubusercontent.com/render/math?math=%24A%5E%7B-1%7D%24) is the inverse of matrix `A` if ![$A^{-1}A=AA^{-1}=I$](https://render.githubusercontent.com/render/math?math=%24A%5E%7B-1%7DA%3DAA%5E%7B-1%7D%3DI%24)
  - Find the inverse of a 2 by 2 matrix
    - if ![$A = \begin{bmatrix} a & b \ c & d \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24A%20%3D%20%5Cbegin%7Bbmatrix%7D%20a%20%26%20b%20%5C%5C%20c%20%26%20d%20%5Cend%7Bbmatrix%7D%24) then ![$A^{-1} = \frac{1}{D} \begin{bmatrix} d & -b \ -c & a \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24A%5E%7B-1%7D%20%3D%20%5Cfrac%7B1%7D%7BD%7D%20%5Cbegin%7Bbmatrix%7D%20d%20%26%20-b%20%5C%5C%20-c%20%26%20a%20%5Cend%7Bbmatrix%7D%24) where `D` is the determinat of `A` ![$D = ad-bc$](https://render.githubusercontent.com/render/math?math=%24D%20%3D%20ad-bc%24)
  - Find the inverse of any matrices by using Gaussian Elimination
    - If ![$A=\begin{bmatrix} a & b \ c & d \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24A%3D%5Cbegin%7Bbmatrix%7D%20a%20%26%20b%20%5C%5C%20c%20%26%20d%20%5Cend%7Bbmatrix%7D%24)
    - Convert the matrix A on the left side to Identity matrix then the inverse matrix will be the matrix on the right side. ![$\left[ \begin{array}{cc|rr} a & b & 1 & 0 \ c & d & 0 & 1 \end{array} \right] \Rightarrow [I : | ; A^{-1}]$](https://render.githubusercontent.com/render/math?math=%24%5Cleft%5B%20%5Cbegin%7Barray%7D%7Bcc%7Crr%7D%20a%20%26%20b%20%26%201%20%26%200%20%5C%5C%20c%20%26%20d%20%26%200%20%26%201%20%5Cend%7Barray%7D%20%5Cright%5D%20%5CRightarrow%20%5BI%20%5C%3A%20%7C%20%5C%3B%20A%5E%7B-1%7D%5D%24)
- Matrix `A` divide by `B` equals to `A` times the inverse of `B`.
  - A system of linear equations can be represent by `AX = B` where `A` is a matrix of coefficient, `X` is a `n` by 1 matrix n variables, `C` equals a `n` by 1 matrix of the values of the dependent variables. Then `X` can be solved by using `B` times the inverse of `A`.
- The determinant of a matrix is a single value calculated from all elements of the matrix.
  - The determinant of a matrix `A` can be represented as `|A|` or `det(A)`
  - For a `2 X 2` matrix ![$A = \begin{bmatrix} a & b \ c & d \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24A%20%3D%20%5Cbegin%7Bbmatrix%7D%20a%20%26%20b%20%5C%5C%20c%20%26%20d%20%5Cend%7Bbmatrix%7D%24), the determinant equals to `ad - bc`.
  - For a `3 X 3` matrix to get the determinant, expand two more new column to the right, copy first column as the fourth column, copy the second column as the fifth column. and draw all the possible diagonal lines in two direction. Multiple all elements on one diagonal lines, add the sum of diagonal elements that goes from top-left to bottom right, substract the sum of diagonal elements that goes from top-right to bottom left.
    - Same idea for matrices with larger sizes.
  - coefficient + - + method

#### Gaussian Elimination

- Row Echelon Form - It has 1 across diagonal, all entries below 1 is 0.
  - In an augmented matrix, independent variables can be solved by subsitution.
- Reduced Echelon form - has 1 across diagonal, all other entries are 0.
  - In an augmented matrix, independent variables is solved and equals to corresponding entries in the right most coloumn.
- Method of Gaussian Elimination - Solve a system of linear equations by finding the Row Echelon Form or Reduced Echelon Form of an augmented matrix.
  - Steps for finding the Row Echelon Form
    - Divide the entire row by the first element to make the first element on first row 1.
    - Multiply first row and Substitute to the second row so the first element of the second row is 0.
    - repeat the step for the next row until the matrix is in the Row Echelon Form
  - Steps for finding the Reduced Echelon Form
    - find the Row Echelon Form first.
    - multiply and subsitute the last row into the second last row to make the last element of the second last row 0.
    - Transform the upper rows step by step until the matrix become Reduced Echelon Form.
  - ![$\left[ \begin{array}{ccc|r} 1 & 2 & 2 & 3 \ 0 & 1 & 1 & 2 \ 0 & 0 & 0 & 2 \end{array} \right]$](https://render.githubusercontent.com/render/math?math=%24%5Cleft%5B%20%5Cbegin%7Barray%7D%7Bccc%7Cr%7D%201%20%26%202%20%26%202%20%26%203%20%5C%5C%200%20%26%201%20%26%201%20%26%202%20%5C%5C%200%20%26%200%20%26%200%20%26%202%20%5Cend%7Barray%7D%20%5Cright%5D%24) this system of linear equations has no solution, because ![$0x+0y+0z \neq 2$](https://render.githubusercontent.com/render/math?math=%240x%2B0y%2B0z%20%5Cneq%202%24)
  - In Echelon Form if one row are all 0s, the equation has inifite solutions.

#### Cramer's Rule

- For a system of linear equations `D` is the determinant of the matrix of coefficient. ![$D_x$](https://render.githubusercontent.com/render/math?math=%24D_x%24) is the determinant of the matrix of coefficient which the column for coefficient of `x` is replaced by the dependent variable matrix. ![$D_y$](https://render.githubusercontent.com/render/math?math=%24D_x%24) is the determinant of the matrix of coefficient which the column for coefficient of `y` is replaced by the dependent variable matrix, and so on. Then ![$x= \frac{D_x}{D}, y= \frac{D_y}{D}, \ldots$](https://render.githubusercontent.com/render/math?math=%24x%3D%20%5Cfrac%7BD_x%7D%7BD%7D%2C%20y%3D%20%5Cfrac%7BD_y%7D%7BD%7D%2C%20%5Cldots%24)
