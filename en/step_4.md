## Create a safe route

<div style="display: flex; flex-wrap: wrap">
<div style="flex-basis: 200px; flex-grow: 1; margin-right: 15px;">
In this step you will create a safe route from the start to the end platform. Rolling over a safe tile will turn it green. 
</div>
<div>
<video width="640" height="360" controls preload="none" poster="images/safe-path-complete.png">
<source src="images/safe-path.mp4" type="video/mp4">
Your browser does not support WebM video, try FireFox or Chrome
</video>
</div>
</div>

### Use the Scene view to plan your path.

--- task ---

**Choose:** a 'safe' material to cover the safe tiles. We used 'Gloss green'.

**Design** a safe path. Drag the safe material to the safe tiles to see your route.

**Tip:** the safe path should make a route from the start platform to the end platform. The safe tiles need to form a connected path but you can have some safe tiles that are not on the correct path.  

![A screenshot showing a suggested safe path for your project. A green path leads the player from the start platform to the end platform.](images/safe-path.png)

--- /task ---

--- task ---

**Test:** Play your game. Notice that the safe tiles are not coloured in your safe material. This is because your TileController script sets the tile material.  

--- /task ---

--- task ---

In the Inspector, click on the tag dropdown and choose ‘Add Tag…’. Add a new Tag called "Safe".

**Tip:** It doesn't matter which objects you have selected when you create a new tag. 

--- /task ---

--- task ---

Go to the **Scene view** and select all the 'Safe' tiles. 

**Tip:** Hold down the <kbd>ctrl<kbd> / <kbd>cmd<kbd> key then click on the safe tiles in turn in the Scene view to highlight all the tiles in the path. 

Selected tiles are shown with an orange border:

![A screenshot showing the selected safe tiles.](images/safe-tiles-selected.png)

--- /task ---

--- task ---

Apply the 'Safe' tag to the safe tiles.

**Tip:** GameObjects can only have one tag so this will remove the 'Tile' tag from the safe tiles. 

--- /task ---

--- task ---

Edit the 'TileController' script to reveal the safe material when a player rolls across a safe tile: 

--- code ---
---
language: cs
filename: TileController.cs
line_numbers: true
line_number_start: 1
line_highlights: 6, 17-23
---
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class TileController : MonoBehaviour
{
    public Material startColour;
    public Material safeColour;
    Renderer rend;

    // Start is called before the first frame update
    void Start()
    {
        rend = GetComponent<Renderer>();
        rend.sharedMaterial = startColour;
    }

    void OnTriggerEnter(Collider other)
    {
        if (gameObject.tag == "Safe")
        {
           rend.sharedMaterial = safeColour;
       	}
	}
}


--- /code ---

--- /task ---

--- task ---

Save the script and return to the Unity Editor. 

In the Hierarchy window, select **all** the Floor cubes. 

Navigate to the materials folder.

Drag your 'safe' material to the 'Safe Colour' variable in the Inspector. 

![A screenshot showing the 'Safe Colour' applied to the 'Safe Colour' variable.](images/safe-colour-applied.png)

--- /task ---

--- task ---

With **all** of the floor tiles selected. Add a new BoxCollider component and **check** the 'Is Trigger' box.

Change the BoxCollider Size to X = `0.02`, Y = `0.01` and Z = `0.04` so that the ball is fully on top of the tile before the material is revealed. 

![A screenshot of the scene view showing the 'Is Trigger' BoxCollider boundaries do not cover the full tile.](images/box-collider.png) 

--- /task ---

--- task ---

**Test** your game by pressing play. You should be able to roll each player's ball across the tiles to reveal the safe path underneath. 

Exit play mode.

<video width="640" height="360" controls preload="none" poster="images/safe-path-complete.png">
<source src="images/safe-path.mp4" type="video/mp4">
Your browser does not support WebM video, try FireFox or Chrome
</video>

--- /task ---