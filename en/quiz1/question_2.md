
--- question ---

---
legend: Question 2 of 3
---

A GameObject has this `Start` function:

--- code ---
---
language: cs
filename: TileController.cs
line_numbers: true
line_number_start: 1
line_highlights: 
---

    void Start()
    {
        rend = GetComponent<Renderer>();
        rend.sharedMaterial = startColour;
        GetComponent<Rigidbody>().useGravity = false;
        GetComponent<Rigidbody>().isKinematic = true;
    }

--- /code ---

Which code would you use to make the GameObject respond to gravity?

--- choices ---

- ( ) 

--- code ---
---
language: cs
filename: TileController.cs
line_numbers: false
line_number_start: 1
line_highlights: 
---

GetComponent<Rigidbody>().useGravity = false;
GetComponent<Rigidbody>().isKinematic = false;

--- /code ---

  --- feedback ---

Not quite. You do need to set `useGravity` to `false` but there's something else you need to do. 

  --- /feedback ---

- ( ) 

--- code ---
---
language: cs
filename: TileController.cs
line_numbers: false
line_number_start: 1
line_highlights: 
---

GetComponent<Rigidbody>().useGravity = false;
GetComponent<Rigidbody>().isKinematic = true;

--- /code ---

  --- feedback ---

  That's not correct. `isKinematic` is `true` means that the movement of the GameObject is controlled completely with code. 

  --- /feedback ---

- ( ) 

--- code ---
---
language: cs
filename: TileController.cs
line_numbers: false
line_number_start: 1
line_highlights: 
---

GetComponent<Rigidbody>().useGravity = true;
GetComponent<Rigidbody>().isKinematic = true;

--- /code ---

  --- feedback ---

  That's not correct. `isKinematic` is `true` means that the movement of the GameObject is controlled completely with code. 

  --- /feedback ---

- (x) 

--- code ---
---
language: cs
filename: TileController.cs
line_numbers: false
line_number_start: 1
line_highlights: 
---

GetComponent<Rigidbody>().useGravity = true;
GetComponent<Rigidbody>().isKinematic = false;

--- /code ---

  --- feedback ---

That's correct. You need to set `isKinematic` to `false` **and** `useGravity` to `true` to be able to control movement with physics instead of code. 

  --- /feedback ---

--- /choices ---

--- /question ---
