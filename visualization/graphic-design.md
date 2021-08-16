# Graphic Design

## Basic Concepts

### Raster and Vector image

- Raster images(bitmap images) - they are consisted of pixels in square shape. Common editor for this is Photoshop.
- Vector graphics - they are made up of shape elements that are defined by mathematical methods. It can be enlarged without losing quality. Editor used for vector graphics are Illustrator and Sketch.

### Color Mode

- RGB
  - Each pixel in RGB mode has 3 channel: Red Green Blue. Each has an 8-bit value from 0-255. 24 bit per pixel.
  - It is an additive color mode. 0,0,0 means no light from the display which means black.
  - It is used for digit display.
- CMYK
  - Each pixel in CMYK mode has 4 channel: cyan, magenta, yellow, key(black) from 0% to 100%
  - It is a subtractive color mode. 0%,0%,0%,0% means no ink is printed which is white. For any color a total percentage of 240% is recommended for good quality(avoid too much ink). sometimes all 4 have values for specific true black color.
  - It is used for printing design.
- Lab
  - Each pixel in Lab mode has 3 channel: Lightness component from 0-100, a component (green-red axis) and b component (blue-yellow axis) from -128 to +127.
  - It is a device-independent color model.
  - It focuses on the perceptive of human eye.
- Grayscale
  - Each pixel in Grayscale has 1-channel. from 0 black to 255 white in a 8-bit image.
  - Alpha channel uses grayscale mode to store layer mask.
- Bitmap
  - Each pixel is represented by either full black or pure white with 1-bit in size.
- Duotone
  - It like Grayscale with two specific color in two channel.
  - may have tritone, quadtone etc.

> Bit depth - the size of one pixel

### Image Resolution

- The number of pixels per inch(ppi)
- the maximum recognizable resolution for human eyes is around 300 ppi.
- Apple Retina display divide one pixel into four to increase display quality. It still take old resolution.

### Pantone color

- Pantone is company which makes fine printed colors template with specific code for each colors.
- It has coated and uncoated colors to give colors examples on coated and uncoated paper.
- It is used to calibrate colors on the display and colors on paper.

### Color Wheel

- It has three color type
- three primary colors: red yellow blue.
- three secondary made by two adjencent primary colours.
- tertiary color made by one primary add one secondary colors.
- green and red draw a line and divide the color into cold and ward color.
- Hue
  - Means color, represented by all the colours on the color wheel. from 0 degree (red) to 360(red),
- Saturation
  - from 100% on the color wheel to 0% towards the centre of the wheel which is created by add its complementary color(color on the opposite side of the wheel)
- Brightness(value)
  - It describe how dark the color is. lowest brightness is black
- Tint
  - add white to a color
- Shade
  - add black or its complementary color
- Tone
  - add grey

### Color Formula

- Monochromatic - Same H, Change S and B.
- Analogous - Use close color in the color wheel
- Complementary - Opposite ends of colours on the color wheel. or its monochromatic color
- Split Complementary - Choose the adjacent colours of one color plus its complimentary on the color wheel.
- Triadic - three colours from a perfect triangle on the wheel
  - This choice has more contrast.
- Tetradic - colors from a rectangle on the wheel.
  - works good if one color is chose as a dominant color.

### Image Format

- `png` format can contain transparent images.

### Topography

- serif font has more traditional stroke.
- sans-serif has no stroke. it is easy to read.
- display fonts: script blackletter. They are used to decorate title or graphics.
- limited to one or two fonts in one project, try vary size weight and style.
  try complementary styles of fonts
- Hierarchy - make important content to stand out.
- Leading - line spacing.
- Tracking - character spacing.
- Kerning - spacing for specific character.(spacing for ‘i’, ‘h’)
- Check fonts on google.com/fonts

## Editing Tools

### Photoshop

#### Tools

- Most tools can be understood according to its name, explore more.
- Some tools like healing brush and stamp tool need alt+click to set source pattern.
- Select Tool->Select object Automatically select objects.
- Background eraser Toll sample background color and remove
- Pen Tool Option dark make point command drag move point
- command click path confirm selection

#### Top Menu

- Create new copy in a new layer of the selected area. `Right click selected area->Layer via Copy`
- Add image to exist project. `File->Place`
- `Edit->Fill->Content->Content Aware`, Use back ground pattern of the selected object to fill the selected area.
- `New Layer->Select->Color range->add adjustment layer` to change
  pick a range of color

#### Layer

- Order - Upper layer is shown first
- Blend mode - control how colours in the layers blends together. Good ones like multiply and overlay.
- adjustment layer links to one layer and adjust its color. Vibrance, Hue/Saturation etc.
- Mask - Layer mask link to one layer. for layer mask black area is removed, white area is shown.
- HSL - adjust the existing file color using Hue, saturation and Lamination.

#### Filter

- It is the final step, tune the image to be better.

#### 3D

- 3D object can be a postcard(plain) or extrusion to an object.
- 3D object can merge with a layer.
- 3D object needs to be rendered to get final result.

#### Plugins

- refers to the Adobe Exchange platform.

#### Shortcuts

- [ or ] change tool size.
- control + T transform
- control(command)+J copy layer
- Alt+Ctrl+Shift+E, Duplicate all existing layer
- ctrl+click on mask, show the grayscale image of the layer mask.
- Command +U HSB Panel

### Sketch

- It is a vector editing tool.
- It creates design for digital display.
- It is good for prototyping.

#### File management

- Auto-save all versions of the files.
- In order to use save as, hold option duplicate button will be changed to save as button.
- option+duplicate -> save as

#### Layouts

- Artboard
  - Each pages has an infinite large canvas with artboards.
  - Artboard is where the design is drawn on.
  - artboard can be moved by dragging its tittle.
  - when create artboard, choose a size on the right panel
- Toolbar
  - Tool bar is on the top.
  - It can be customized: right click -> select customized toolbar
  - Insert - All the graphic element is inserted from here.
- boolean operate
  - choose overlapping relationships for multiple shapes.
  - flatten button is used to confirm the relationships.
- Editing mode
  - Select shapes->Press return key -> editing mode
  - click on the line to create anchor point.
  - anchor point can be chose and deleted.
- Export->+ sign add 1X or 2X or 3X export
- Left panel
  - pages, symbol pages and its layers are listed in the left panel.
  - layers - upper layers is on top.
  - select two layers right click -> mask
  - for layers, the bottom can be a mask according to its shape.
    - slice tool - change the background size of the shapes for export. should be in the same group of the shapes
- right panel
  - properties are set in the right panel.
  - set artboard background.
  - alignment for all selected object
  - option key + alignment -> align selected object to the artboard.
  - fill a shape with an image using cut and paste into the fill thumbnail is an alternative for masking.
  - all other properties

#### Symbols

- Symbol is shared layers or group that can be reused.
- Symbol’s name indicates where to find it in the insert button.
- Symbols page in the left panel collect all the symbols.
- it can use right replace with function for symbol
- it can be in edit mode by double clicking.
- it can be overridden in the right panel.
- it can be nested.

#### Styles

- can be shared in the right panel
- changes can be updated by clicking the sync icon beside the share style menu.
- Same for text style

#### Shortcuts

- Option+drag duplicate
- shift+arrow move 10 pixel at a time
- select one object, option+mouse over see measurements.
- Option+Command+C/V -> Copy style
- Command+G -> Group Layers
- Command+R -> Rename layers ->tab-> rename the next layer
- Command+Arrow->transform the element in one direction
- Command+1 Zoom out to the artboard
- Command+2 Zoom in to a shape

#### Plugins

- Craft Plugins
  - Style Mangement
  - Auto generate content
  - Auto duplicate layout
  - Import/Export to Library
  - Upload to inVision Prototype account
  - 2X export density is for retina display.
- invision Webpage
- used to build dynamic prototype
- preview
- build links and transition
- comment
- inspect mode

## Online Tools and Resources

- convert png to base64 https://www.base64-image.de
- Copyright free Image on pixabay.com
- To make logos using logomakr.com
- More templates on tyler.com
- Android Mockup Design Tool `https://www.mockplus.com/blog/post/android-mockup`
