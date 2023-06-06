# Unity

- Unity is a cross-platform game engine and can run in iOS, Android, Windows, Mac, Linux, PlayStation, etc

## Installation

1. Install Unity Hub for corresponding OS, then select supported editor version and add-ons for installation
2. Add the license in preference menu
   - personal or student license is free
3. Create or open a project in the `Projects` tab

## Settings

### Preferences

- External Tools - Set default script editor
- Physics Update Frequency - `100 Hz` by default
- Graphics Render Frequency - around `6 Hz`

### Project Manager

- It's under Edit menu
- Input manager defines user input
- Collision Matrix defines collision between layers

## Editor

### Interface

- The Scene window is where the objects and layouts are edited
  - Scene contains objects like camera and light
  - Center mode - it focuses on the center when multiple objects are selected
  - Pivot mode - each GameObject rotates around its own pivot point
  - Global mode - Use goal axis for all objects
  - Local mode - Use relative position from a selected object
- The Game window is the final presentation
  - It shows the view of the camera
  - It has an aspect ratio selector (e.g. 4:3, 16:9, 16:10 ...)
- Hierarchy window helps create and show all GameObject in a scene
  - Everthing in unity is a game object
  - `GameObject` is a collection of a transform and components
  - Objects can have a hierarchy relationship by dragging one of it under another, when parent object moves the child object will move with it
  - The transform parameters for child objects are the relative position to their parents
- Project window shows files in the project folder
  - `Assets` folder can commonly have:
    - `Materials` - it contains custom apperance of the game objects
    - `PhysMaterials` - it contains the physical properties of the game objects
    - `Prefabs` - it stores custom created parent game objects for future use
      - It's like create a custon class that can be inherited or overriden in future use
      - To create a Prefab, drag a GameObject from the Hierarchy and into the Project window
    - `Scripts` - it contains code that processes user inputs
    - `Textures` - image files to be applied as the skins of the objects
    - All asset files comes with a coreesponding `.meta` file in the same real file folder (including each directory itself), it is hidden from the Unity interface and it should be moved or managed together with the actual asset files
- Inspector window helps modify the object's attributes
- Console window shows console output from the scripts
- The play mode is the preview of the game
  - changes made in play mode won't be saved to the project
  - Step - this lets you step through your game one frame at a time

### Shortkeys

- Hold `ALT` and click the parent object in hierarchy window all child object will be expanded and displayed
- Scolling or sweeping two fingers forward/backward on touchpad to zoom
  - Optionally, hold `ALT`, then click and drag
- Hold scolling wheel or hold double clicking on touchpad to rotate view
- Transform Tools:
  - `Q` – Pan
  - `W` – Move
  - `E` – Rotate
  - `R` – Scale - 3-axis scaling
  - `T` – Rect Tool - Scale using a rect frame
  - `Y` - Unified Tool - Combination of above tools
- Select any GameObject in the Scene / Hierarchy and press `F` to zoom the scene view to the selected GameObject
  - Double clicking objects in Hierarchy window also works
- Select the Camera, and in the Scene view, press `CTRL+SHIFT+F` to Align the Camera to View
  - Or use two fingers to zoom on any window with trackpad
- Hover the mouse on any Window and press `SHIFT+SPACE` to Maximize / Minimize it
- Hold `CTRL` to Snap your GameObject to the grid
  - Snap Settings can be changed inside `Edit > Snap Settings...` to snap by `0.5`, `10`, or any other units
- Select the asset, and by Holding `V`, press and hold `LMB` on any Vertex. Then move the mouse to snap to another asset vertex
- Select object and press `CTRL+D` to duplicate it
  - Or select and press `CTRL`, then drag the selected object
- Press `CTRL+P` to Enter / Exit Play mode

### Inspector Components

- Inspector window contains a group of components for the selected game object
  - Script is also a component of an object
- Any configuration completed in the inspector window can be changed in the scripts as object properties
  - Utlizing the inspector panel instead of coding can speed up the workflow
- `Rigidbody` - It adds physics to an object
  - Constraints - It helps object freeze position/rotation in the x, y, or z axix
- `Renderer` - It affects how objects look
  - Materials are configured under this component
- `Layer` - in the top section, layer can be created and assigned to the object
  - When multiple objects are in the same layer, they are treated as one object when considering collision
  - After layer is defined, use layer mask instead of the individual objects in the script
  - Expose the `layerMask` from the script and attach one or more desired masks from Hierarchy window
  - In the scripts, layer is a number represented by its index in the layer section
- `Collider`
  - It can be a box, sphere, or mesh which depended on the object shape
  - `Is Trigger` - when checked, collision is registered but no physical interaction will be made
- `Audio Source`
  - It loads an audio clip file and make the object play sounds
- `Camera`
  - For camera object, it has a camera component that changes the game background
  - When the `Clear Flags` uses `skybox` for the camera, imported skybox asset can be loaded in `Windows` -> `Rendering` -> `Lighting` settings as a new skybox material in the `Environment` tab
- `Material`
  - `Albedo` takes the textures

### Scripts

- `C#` is the recommanded language
- The scripts are built with the help of [UnityEngine](https://docs.unity3d.com/ScriptReference/)
- `UnityEngine` contains the following classes/sub-namespaces
- Objects decleare as public or begin with `[SerializeField]` will be exposed in the inspector window
  - To establish a connection, drag object from Hierarchy window on to exposed component in the inspector window
- Some scripts require components. If the components aren’t found on the GameObject, they’ll be added automatically

#### [MonoBehaviour](https://docs.unity3d.com/ScriptReference/MonoBehaviour.html)

- It is the parent class for game object that contains the entire collection of features for a game object
- `Start()` it is called once before the first frame
- `Update()` is is called once per rendered frame
  - The execution frequency is depended on the frame rate
  - User input is checked here
- `FixedUpdate()` is is called once every physic update
  - All physic updates should be defined here
  - Since it's computed faster than the render rate, user input in this method might be missed. This won't happen when it's the other way around
- `OnCollisionEnter()` it is called when the object class is having an collision with other objects
- `OnCollisionExit()` it is called when the object class is no longer having an collision with other objects
- `onTriggerEnter(other)` it is called when the object has collision registered, other is the collider object that it collides with

#### [Vector3](https://docs.unity3d.com/ScriptReference/Vector3.html)

- Object `Vector3` has x, y, z value
  - `vector3 = new Vector3(x, y, z)`
  - `vector3.x` defines left and right
  - `vector3.y` defines up and down
  - `vector3.z` defines forward and backward

#### [Component](https://docs.unity3d.com/ScriptReference/Component.html)

- `component = GetCompoenet<Rigidbody>()` will return assiciated game object of the script
  - It is usually set in the `Start()` method
- `component.AddForce(Vector3.up * 10, ForceMode.VelocityChange)` add a force to the component
- property
  - `component.velocity` - A `Vector3` object that represents the velocity of the object
- `Destroy(component)` remove the object from the scene

#### [Input](https://docs.unity3d.com/ScriptReference/Input.html)

- It takes user input
- `Input.GetKeyDown(KeyCode.Space)` returns true when user presses the space key
- `Input.GetAxis(AxesString)` returns a float that reflects the key press
  - `AxesString` is from the Input Manager
  - Pressing one key will increase the value increase, pressing the other key will yield a negative value

#### [Physics](https://docs.unity3d.com/ScriptReference/Physics.html)

- It contains a collection of global physics properties and helper methods
- `Physics.OverlapSphere(position, radius, layerMask)` returns a list of collider objects

#### [Collider](https://docs.unity3d.com/ScriptReference/Collider.html)

- It describes collision
- `collider.gameObject` the colliding object

### Shaders

1. Create `Shaders` folder in the asset window
2. Create a new surface shader file
3. Use the following structure

   ```cpp
   Shader "Custom/ShaderName"{
       // Properties that are made available in the inspector with default value
       Properties{
           _Color ("Color Picker", Color) = (1,1,1,1)
           _EmissionColor("Emission Color Picker", Color) = (1,1,1,1)
           _MainTex("MainTexture" , 2D) = "white" {}
           _RefTex("Reflection Texture" , Cube) = "white" {}
       }

       // Shader Definition
       SubShader{
           CGPROGRAM
           #pragma surface surf Lambert
           // Required input for the shader
           struct Input {
               float2 uv_MainTex; // When prepended with uv, variable is auto generated for uv coordinates mapping of MainTex
               float3 worldRefl;
           };
           // Declare variables from shader properties
           float4 _Color;
           float4 _EmissionColor;
           sampler2D _MainTex;
           samplerCUBE _RefTex;
           // Functions that defines how the shader works
           void surf(Input IN, inout SurfaceOutput o) {
               o.Albedo =  tex2D(_MainTex, IN.uv_MainTex).rgb * _Color.rgb;
               o.Emission = texCUBE(_RefTex, IN.worldRefl).rgb;
           }
           ENDCG
       }
     FallBack "Diffuse"
   }
   ```

4. Assign the shader for the material to be used by a model

### Basic Workflow

1. Right click or click on the plus button in Hierarchy window to create new game objects
2. Create assets like materials in the Project window
3. Edit game objects, add components, attach scripts to objects with sence window and inspector window
   - Easiest way is to drag the asset onto the object from project window to scene window
   - The class name of the script must match the object name
   - Scripts are assigned by dragging code file from asset tab to the object in hierarchy
4. Create Refabs, arrange the scene
5. Run game, test, then debug
