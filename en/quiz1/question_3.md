
--- question ---

---
legend: Question 3 of 3
---

A tile is tagged with 'Safe'. What colour would the material of this tile be after a ball rolled over it?

![The Inspector window showing the script. with Unsafe Colour GlossRed, Start Colour GlossYellow, Safe Colour GlossGreen.](images/tag-question.png)

--- code ---
---
language: cs
filename: TileController.cs
line_numbers: false
line_number_start: 1
line_highlights: 
---

  void OnTriggerEnter(Collider other){
    if (gameObject.tag == "Safe")
    {
      rend.sharedMaterial = safeColour;
    }
    else if (gameObject.tag == "Tile")
    {
      rend.sharedMaterial = unsafeColour;
    }
  }

--- /code ---

--- choices ---

- ( ) GlossRed


  --- feedback ---

That's not correct. Which colour will be used when the tag is set to 'Safe'?

  --- /feedback ---

- ( ) GlossOrange


  --- feedback ---

  That's not correct. 'GlossOrange' is not used. 

  --- /feedback ---

- (x) GlossGreen


  --- feedback ---

  Correct. The tile would be set to 'GlossGreen' after the ball rolled over it, because it has the 'Safe' tag.

  --- /feedback ---

- ( ) GlossYellow


  --- feedback ---
  
  That's not correct. 'GlossYellow' is the start colour. The colour will change when the ball rolls over it.

  --- /feedback ---

--- /choices ---

--- /question ---
