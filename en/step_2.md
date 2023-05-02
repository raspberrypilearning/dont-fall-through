## Create the level

<div style="display: flex; flex-wrap: wrap">
<div style="flex-basis: 200px; flex-grow: 1; margin-right: 15px;">
In this step you will create the level for your game. 
</div>
<div>
![A screenshot of the Game view showing the created level with tiled floor, start and end platforms, and a coloured skybox.](images/created-level.png){:width="300px"}
</div>
</div>

### Create a project with the starter package

--- task ---

Launch the Unity Hub and open the project you created for [Disco dance floor](https://projects.raspberrypi.org/en/projects/disco-dance-floor/0){:target='_blank'}.

--- collapse ---

---
title: I haven't got my Disco dance floor project
---

If you are unable to open your project, launch the Unity Hub and click **Projects** then select **New project**:

![A screenshot of the black bar at the top of the Unity Hub with the 'New Project' button highlighted in red.](images/new-project.png)

From the list choose **All templates** then select **3D Core**:

![A screenshot of the left pane in the Unity Hub. The 3D core option is highlighted in red.](images/3D-core.png)

Edit the project settings to give your project a sensible name and save it to a sensible location. Then click **Create project**:

![A screenshot of the right pane in the Unity Hub. The filename and the 'Create Project' sections are highlighted in red.](images/create-project.png)

Your new project will open in the Unity Editor. It may take some time to load.

Download and unzip the [More Unity starter package](https://rpf.io/p/en/rainbow-run-go){:target="_blank"} to your computer. 

**Tip:** Choose a sensible location such as your Documents folder.

The Unity starter package for this More Unity path contains a number of **Assets** for you to use in your project.

To import them into your new project, click on the **Assets menu** and select **Import package > Custom Package…** then navigate to the downloaded Unity starter package.

--- /collapse ---

--- /task ---

--- task ---

In the **Project** panel right-click and select **Create --> Scene**.

![The right-click menu with Create and Scene highlighted](images/create-scene.png)

In the pop-up window, name your Scene `Don't fall through`:

A new file will appear in the Assets folder in the Project window:

![Project window with Don't fall through scene in the Assets folder.](images/dont-fall-through-scene.png)

Drag the new Scene into the 'Scenes' folder to organise your files.

--- /task ---

### Set up the level

--- task ---

In the Project window, click on **Parts**.

**Drag** the '8x8Floor' object to the Scene view: 

Your scene should look like this:

![The Scene View with a grey grid of 8*8 square tiles.](images/tiled-floor.png)

--- /task ---

--- task ---

In the Inspector window, change the Transform properties of the '8x8Floor' GameObject: Position X=`0`, Y=`0`, Z=`0`.

![The Inspector window with the Transform component of the 8x8Floor GameObject, with position values all set to 0](images/floor-position.png)

--- /task ---

### Set the camera view

--- task ---

Click on the **View tool** in the Scene view (the hand icon) and drag the view to one side of the floor looking down towards it. When you are happy, right-click on the Main Camera object in the Hierarchy window and select 'Align With View':

[[[unity-scene-navigation]]]

--- collapse ---
---
title: Alternatively, enter transform numbers to move the camera
---

Select the 'Main Camera' in the hierarchy window and change the position and rotate properties to match the following:

Position X=`0`, Y=`12`, Z=`-18` and Rotate X=`40`. 

Right-click on the 'Main Camera' and choose 'Align View to Selected' to match the scene view to the new camera position. 

--- /collapse ---

![A screenshot of the Scene view showing the tiled floor. The view is looking from above the floor and is looking down at a 35 degree angle.](images/camera-view.png)

--- /task ---

### Set up the tiles

--- task ---

In the Inspector, click on the tag dropdown and choose ‘Add Tag…’. Add a new Tag called "Tile".

**Tip:** It doesn't matter which objects you have selected when you create a new tag. 

![A screenshot of the inspector with tag dropdown and 'Add Tag' sub menu item highlighted.](images/tag-dropdown.png)

![A screenshot of the Tags and Layers window with The + icon highlightd and the word 'Title' typed in the 'New Tag Name' pr .](images/new-tag.png)

--- /task ---

--- task ---

Expand the Floor GameObject in the hierarchy and **select all** 64 cubes. 

In the Inspector, set the Tag to 'Tile'.

--- /task ---

This project will use physics so you need to set up the tiles. 

--- task ---

With all the Floor cubes selected:

+ Add a **Rigidbody** component with 'Use Gravity' **not checked** and 'Is Kinematic' **checked**. 
+ Add a **Box Collider** component. 

![Box Collider and Rigidbody components in the Inspector. Rigidbody has gravity check and kinematic unchecked.](images/cube-components.png)

--- collapse ---

---
title: What does isKinematic mean?
---

When you set a Rigidbody to be **Kinematic** it means that the object will be completely controlled through code. This means that the physics of the world from interactions like collisions and gravity will not effect the object. 

--- /collapse ---

--- /task ---

### Set the material with a script

The material for the tiles is set with code when the game starts. 

--- task ---

With all of the Floor cubes selected, add a script called `TileController`.

**Tip:** The new script will be added to all of the Floor cubes:

![The Inspector window with the 'TileController' script component.](images/tile-controller-script.png)

--- code ---
---
language: cs
filename: TileController.cs
line_numbers: true
line_number_start: 1
line_highlights: 
---

using System.Collections;
using System.Collections.Generic;
using UnityEngine;
public class TileController : MonoBehaviour
{
    public Material startColour;
    Renderer rend;
    
    // Start is called before the first frame update
    void Start()
    {
        rend = GetComponent<Renderer>();
        rend.sharedMaterial = startColour;
    }
}

--- /code ---

--- /task ---

--- task ---

**Choose:** a start material for the tiles from the 'Materials' folder. 

With all the Floor cubes selected, drag your chosen material to the 'Start Colour' variable of the 'TileController' script in the Inspector. 

We chose the 'GlossYellow' material:

![The TileController script in the Inspector with the start colour set to GlossYellow.](images/tile-start-colour.png)

--- /task ---

--- task ---

**Test:** Click 'Play'. Every tile should have the material you selected. 

![The scene view showing the GlossYellow colour applied to the tiles.](images/start-colour-test.png)

**Tip:** Make sure you exit the Game view and return to the Scene view before continuing. 

--- /task ---

### Add start and end platforms

--- task ---

Add a Cube GameObject for the start platform and position it at the end of the floor closest to the Main Camera. 

You can use the Move and Scale tools or set these settings in the Inspector: Position X = `0`, Y = `0`, Z = `-10` and Scale X = `18`, Y = `1`, Z = `2`.

![The Inspector for the start cube with Position 0,0,-10 and Scale 18,1,2.](images/start-settings.png)

--- /task ---

--- task ---

Rename the GameObject to `Start Platform`. 

--- /task ---

--- task ---

**Choose:** a material from the 'Materials' folder and drag it onto the start platform in the Scene view.

We used 'Gloss Blue'.

![The tiled floor with a blue start platform at the front.](images/start-platform.png)

--- /task ---

--- task ---

Duplicate the 'Start Platform' and position it at the end of the Floor furthest from the camera (Z=10).

Add a different material to the end platform. We used 'GlossOrange'.

![The tiled floor with an orange platform at the end.](images/end-platform.png)

--- /task ---

--- task ---

Rename the GameObject to `End Platform`. 

--- /task ---

### Add a coloured skybox

--- task ---

Create a new material called 'Skybox' in the 'Materials' folder, then go to the 'Inspector' window.

Change the 'Shader' to 'Skybox -> 6 Sided'.

**Choose:** Change the 'Tint Color' to a colour of your choice. Our example uses a dark blue colour.

Go to the Project window and drag the new skybox material onto the background of your scene. 

--- /task ---

--- task ---

**Test:** Click 'Play' to see your game with a coloured skybox. 

![A screenshot of the Game view showing the created level with tiled floor, start and end platforms, and a coloured skybox.](images/created-level.png)

--- /task ---