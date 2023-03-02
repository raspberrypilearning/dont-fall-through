
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
        this.GetComponent<Rigidbody>().useGravity = false;
        this.GetComponent<Rigidbody>().isKinematic = true;
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

  this.GetComponent<Rigidbody>().useGravity = false;
  this.GetComponent<Rigidbody>().isKinematic = false;

--- /code ---

  --- feedback ---

Not quite. 

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

  this.GetComponent<Rigidbody>().useGravity = true;
  this.GetComponent<Rigidbody>().isKinematic = false;

--- /code ---

  --- feedback ---

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

  this.GetComponent<Rigidbody>().useGravity = true;
  this.GetComponent<Rigidbody>().isKinematic = true;

--- /code ---

  --- feedback ---

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

  this.GetComponent<Rigidbody>().useGravity = true;
  this.GetComponent<Rigidbody>().isKinematic = false;

--- /code ---

  --- feedback ---

  --- /feedback ---

--- /choices ---

--- /question ---
