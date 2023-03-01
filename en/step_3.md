## Add the players

<div style="display: flex; flex-wrap: wrap">
<div style="flex-basis: 200px; flex-grow: 1; margin-right: 15px;">
In this step you will add two spheres with different materials for the two players and scripts to allow the players to be moved with different keys. When the first player reaches the end platform a particle effect will trigger.
</div>
<div>
![Step 3 output.](images/step-3-output){:width="300px"}
</div>
</div>

# Create the first player

--- task ---

Add a sphere and name it 'Player1'.

Choose a material for the player and drag it on to the sphere in the Scene view. 

Set the Transform Scale to 0.8, 0.8, 0.8. Position the sphere on the start platform, Transform Position: (-4.5, 1, -10).

![The Scene view showing a multicoloured ball on the start platform.](images/player1.png)

--- /task ---

--- task ---

Add a new script caller 'PlayerController' to the 'Player1' GameObject:

--- code ---
---
language: cs
filename: PlayerController.cs
line_numbers: true
line_number_start: 1
line_highlights: 
---

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    public Transform cameraTransform;
    public string forwardKey;
    public string leftKey;
    public string backwardKey;
    public string rightKey;
    private Rigidbody rb;
    
    // Start is called before the first frame update
    void Start()
    {
        rb = this.GetComponent<Rigidbody>();
        rb.transform.forward = cameraTransform.forward;
    }

    // FixedUpdate is called once per fixed frame-rate frame
    void FixedUpdate()
    {
        // Calculates cameraTransform.forward without the y value so the ball doesn't move up and down on the Y axis
        Vector3 forward = new Vector3(cameraTransform.forward.x, 0, cameraTransform.forward.z).normalized;
        Vector3 right = Quaternion.AngleAxis(90, Vector3.up) * forward;
        Vector3 left = -right;
        Vector3 backward = -forward;

        if (Input.GetKey(forwardKey))
        {
            rb.AddForce(forward * 10f);
        }

        if (Input.GetKey(rightKey))
        {
            rb.AddForce(right * 5f);
        }

        if (Input.GetKey(backwardKey))
        {
            rb.AddForce(backward * 2f);
        }

        if (Input.GetKey(leftKey))
        {
            rb.AddForce(left * 5f);
        }
    }
}


--- /code ---

--- /task ---

--- task ---

Drag the 'Main Camera' game object to the 'Camera Transform' variable in the inspector. 

Set the 'Forward Key', 'Left Key', 'Backward Key', and 'Right Key' to the lowercase letters that you want to use to control Player1. We used 'w', 'a', 's' and 'd'.

![The inspector for Player1 showing the PlayerController script with Camera Transform set to Main Camera and four key variables set to lowercase w, a, s and d.](images/player1.png)

**Tip:** The letters for the keys need to be in lower case. 

--- /task ---

--- task ---

**Test:** Play the game and check that you can control the sphere with the keys that you chose. 

Exit play mode. 

--- /task ---

### Add a second player

--- task ---

Duplicate Player1 to create a Player2 GameObject. 

Move Player2 to a different position on the start platform, Position: (4.5, 1 -10).

Drag a different material to Player2 in the scene view. 


![The Scene view showing two multicoloured balls on the start platform.](images/player2.png)

--- /task ---

--- task ---

**Test:** Play your game and use the keys you chose to move Player1. Player2 will also move! That's not what we want. 

Exit Play mode.

--- /task ---

--- task ---

Select the Player2 GameObject and find the 'PlayerController' GameObject in the inspector. 

Change the Player2 keys to use the arrow keys: `up`, `left`, `down`, and `right`. 

![The inspector for Player1 showing the PlayerController script with Camera Transform set to Main Camera and four key variables set to lowercase up, left, down and right.](images/player1.png)

--- /task ---

--- task ---

**Test:** Play your game and use the arrow keys to move Player2.

Exit Play mode.

--- /task ---

### Trigger a particle effect for the winner


--- task ---

Add the 'Player' tag to Player1 and Player2. 

--- /task ---

--- task ---


--- /task ---

--- task ---


--- /task ---

--- task ---


--- /task ---



--- task ---

**Test:** 

Exit Play mode.

--- /task ---