# BTH010 FinalReview

## Unity 3D

## Data structures

### Array

### Linked Lists

### Queue

## Scripting

### Scripting language

## Game architecture

### Ad-Hoc

- An ad-hos architecture has no organization what so ever, classes are simply added when they are needed without looking at the big picture.
- Bad design, only acceptable for very small projects

### Modular

- Drawback: dependencies between modules are not controlled
- DAG Modular: dependencies under control

### Layered

- Similar to DAG architecture since no cycles is allowed in the corresponding graph
- a module is only allowed to access modules in the layer directly below.
- Internet protocol stack

### Initialization/Shutdown steps

Initialization steps <-- reverse --> Shutdown steps

### RAII

- Resource Acquisition Is Initialization
- when we create a game object, it is itself responsible for loading all resources it needs. Also shutdown itself.

### Fast Shutdown

- We can dedicate a large block of memory to the game world, and at shutdown just wipe the whole memory block.

### Main Game Loop

- Gather input -> run AI -> Run physics simulation -> Update game entities -> Render
- Each iteration fo this game loop is called a frame

### Simulation

- Subtasks

  - Run AI code so entities decide what to do (move, shoot, guard, ...) 
  - Run scripts that update states or trigger events           
  - Run physics simulation to make sure game objects move correctly in the game world
  - Update effects such as particle systems for explosions, fire or waterfalls
  - Run animations for characters
  - Update player position and animation based on player input
  - Update camera position
- Optimization
  - For large game world, only run simulation which are visible to player
  - Use a priority queue
### Collision

- Collision Handling
  - Detection
    - Optimization
      - Simplify collision volumes
      - Organizing entities in for example grids or BSP trees to reduce the number of entity pairs we need to calculate collisions for
- Response
  
- Overlap Testing

### Rendering

### The Five-Step Debugging Process

1. Reproduce the Problem Consistenty
2. Collect Clues
3. Pinpoint the Error
   - Propose a Hypothesis
   - Divide and Conquer
4. Repair the Problem
5. Test the Solution

### Summary

- Games are complex pieces of software.
- The choice of architecture has large influence on how flexible and dynamic the code structure is.
- The game loop is the heart of a game. Since it is run several times per second we need to optimize its execution.
- Game resources (assets) take up a large part of the memory usage, and reusing assets where possible is a good approach.
- Using pack files is a good approach to get more control over the file system.
- A structured approach to debugging will be a great aid in finding and correcting bugs in your game.

## Math

### The Dot Product

### The Cross Product 

### Matrix

## Rendering

- A large part of a game engine is rendering a three-dimensional scene onto a flat two-dimensional screen (of pixels).

### Buffers

#### Frame Buffer and Back Buffer

- What is frame buffer and back buffer?
  - The *frame buffer* is the location where what is shown on the actual screen is stored.
  - In many standard window-based computer applications the GUI contents are drawn directly on the frame buffer.（draw -> frame buffer -> screen）
  - In 3D games this is not feasible, since the user can see the frame being constructed (because it takes noticeable time to draw a frame).
  - Instead we construct the frame on a nonvisible area called the *back buffer*.
  - When the frame construction is finished, the back buffer is copied to the frame buffer (a very fast operation).（draw -> back buffer -> frame buffer -> screen）
- **What are pros of using back buffer?**
  - User cannot see the frame being constructed
  - Graphics card can manipulate instead of merely copying the back buffer to the frame buffer.
  - This allows the back buffer to have one fixed, often high, resolution frame and compress the frame to fit the screen resolution of the current hardware.

#### Depth Buffer

- The most common approach today is to use a second invisible buffer called the *depth buffer* (or *Z-buffer*, since the *z*-axis often represents the depth in a 3D scene).
- For each pixel that is written to the back buffer, a depth value for that pixel is written to the depth buffer.
- The values in the depth buffer indicate how far away pixels are, and when attempting to render a new object at the same position the depth of the new object is compared with the depth stored in the depth buffer.

#### Stencil Buffer

### Coordinate Spaces

#### World and Object space

- Global coordinate system
- Local coordinate system

#### Camera Space

- Frustum 

### Textures and Materials

#### Meshes & Materials

- A mesh is a collection of triangles forming an object.
- A material is a description of how to render the triangle.

#### Textures

- A texture is a surface holding the color value and possibly transparency for each pixel (called texel).
- Mipmap chains - a sequence of the same picture, but each is half the size in each dimension as the previous one

#### Shaders

- A shader is a small program running on the graphic hardware which determines the shape (vertex shader) and color (pixel shader) of a mesh.

#### Texture Filtering

- To smooth sharp edges in textures, filtering are usually applied when rendering a triangle.
- Three types of filtering:
  - Bilianear（双线性过滤）: the color of a pixel is an average of the color of the four closest pixels.
    - 选取texel和pixel大小最接近的一层mipmap做双线性过滤。
  - Trilinear （三线性过滤）: an extension of bilinear where we interpolate between two entries in a mipmap chain.
    - 选取texel和pixel大小最接近的两层mipmap分别做双线性过滤，再对两个结果做linear interpolate。
  - Anisotropic（各向异性过滤）: used when a texture is scaled differently in horizontal and vertical direction.

#### Lighting

- Bright directional lights
- Ambient light 

## Animation

### Bone-based animation

- Bones arranges in a tree hierarchy
- Root bone

### Kinematics

- The motion is forwarded down the tree hierarchy of bones
- This is called forward kinematics
- Inverse kinematics

### Extraction

#### Linear Motion Extraction

- Interpolate between first and last frame

#### Composite Motion Extraction

- Interpolate between each keyframe

#### Variable Delta Extraction

### Storage

#### Keyframes

- An optimization for storaging animations.

#### Interpolation

- Interpola&on between transla&on and scale is simple.

- We only need to linearly interpolate between two values:

#### Rotation

#### Rotation Interpolation

- Euler angles: suffer from the Gimbal Lock problem
- 3x3 rotation matrix: works better, but require 3 times as much memory
- Quaternions: the best option Q = ((x,y,z)sinθ/2, cosθ/2)

#### Bézier curve

- The only drawback is that we need to store two more points(T1 and T2)![Screen Shot 2021-01-17 at 2.21.53 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210628150914.png)

## Artificial Intelligence

### Game Agents

Sense -> Think -> Act

### Finite-State Machine(有限状态机)

- An FSM consists of stated, transitions between states, and conditions for a transition
- An agent can only be in one state at a time
- Each state has its own logic
- Execute logic of current state -> check for transition![Screen Shot 2021-01-17 at 2.25.53 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210628150918.png)

### Path Finding

#### DFS

#### Greedy Search

#### A-star

## Software Development

### Component Systems

- Adding or removing components does not require re-compilation of the code
- Help testing and debugging

### Data-Driven Composition

- The game entities are not defined in the code, but rather in separate data files.
- Loose coupling

### Development processes

### Waterfall model





