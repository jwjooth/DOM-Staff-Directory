# 🎓 FINAL EXAM — JavaScript Document Object Model
### Issued by: Senior Lead Developer | Module: JavaScript DOM
### Prerequisite: JavaScript Modules ✅ | Next Module: JavaScript Async

---

> **📢 Message from Your Senior Lead Dev:**
>
> *"Alright, you passed the Modules exam. Good. But now we're stepping into something more real — the DOM. This is what users actually see and interact with. This is where JavaScript stops being theory and starts being a product.*
>
> *I'm not going to ask you to build a counter or a to-do list. That's tutorial work. I want to see a real, structured, interactive web app — one that uses every DOM concept we covered. You're going to build an internal tool that our team actually needs.*
>
> *Read the requirements carefully. This is a single-file HTML app — no frameworks, no npm, no build tools. Pure HTML, CSS, and JavaScript DOM manipulation only.*
>
> *You break it, you fix it. You miss a concept, you lose the points. Simple.*
>
> *— Senior Lead Dev"*

---

## 📋 PROJECT BRIEF

**Project Name:** `DOM Staff Directory — Internal HR Tool`

**Context:**
Your company's HR team needs a lightweight, browser-based **Staff Directory** app to manage employee records. The app must be built as a **single HTML file** (`index.html`) with embedded CSS and JavaScript. No external libraries. No frameworks.

The app must demonstrate mastery of every concept covered in the JavaScript DOM module — from basic document queries to dynamic table manipulation, form handling, events, and live style updates.

---

## 🗂️ Required File Structure

```
dom-staff-directory/
├── index.html        ← The entire app lives here (HTML + CSS + JS)
└── README.md
```

> ⚠️ Everything — HTML structure, CSS styles, and JavaScript logic — must exist in a **single `index.html` file**. No separate `.js` or `.css` files.

---

## 🖥️ Required UI Layout

The app must have the following visible sections rendered in the HTML:

```
┌──────────────────────────────────────────────────────┐
│  🏢  DOM Staff Directory         [Window Info Button] │
├──────────────────────────────────────────────────────┤
│  📋 DOM Inspector Panel                              │
│  (shows nodeType, nodeName, parentNode info)         │
├──────────────────────────────────────────────────────┤
│  ➕ Add New Staff (Form)                             │
│  [ Name ] [ Department ] [ Role ] [ Add Staff ]      │
├──────────────────────────────────────────────────────┤
│  🔍 Filter & Query Panel                             │
│  [ querySelector input ] [ Run Selector ]            │
│  [ Highlight by Class ] [ Highlight by Attr ]        │
├──────────────────────────────────────────────────────┤
│  📊 Staff Table                                      │
│  ID | Name | Department | Role | Status | Actions   │
│  ── | ──── | ────────── | ──── | ────── | ───────   │
│  .. rows added dynamically ..                        │
├──────────────────────────────────────────────────────┤
│  📝 DOM Activity Log                                 │
│  (logs every DOM action with timestamp)              │
└──────────────────────────────────────────────────────┘
```

---

## ✅ TASKS & COMPETENCY COVERAGE

---

### TASK 1 — Document & Window | *Document properties, methods, Window object*

**Competency tested:** `document` properties, `document` methods, `window` object

**Requirements:**

1. On page load, read and log the following `document` properties into the **DOM Activity Log** panel:
   - `document.title`
   - `document.URL`
   - `document.domain`
   - `document.readyState`
   - `document.body.nodeName`

2. Add a **"Window Info"** button in the header. When clicked, use `window.alert()` to display:
   ```
   Screen: {window.screen.width} x {window.screen.height}
   Inner: {window.innerWidth} x {window.innerHeight}
   Location: {window.location.href}
   ```

3. Use `document.createElement()` to dynamically build every row of the staff table — **never hardcode `<tr>` rows in HTML**.

> 💡 *Senior note: The document object is the entry point to everything. If you're using `document.getElementById()` without understanding what document IS, you're just copy-pasting. Show me you know the difference between document properties and methods.*

---

### TASK 2 — Node & Node Properties | *Node tree traversal, nodeType, nodeName, parentNode, childNodes*

**Competency tested:** Node tree, Node properties, nodeType constants

**Requirements:**

1. Create a **DOM Inspector Panel** (a `<div>` visible on the page).
2. When the user **clicks any cell** in the staff table, the inspector panel must update and display:
   - `node.nodeType` (show the number AND the label, e.g. `1 — ELEMENT_NODE`)
   - `node.nodeName`
   - `node.parentNode.nodeName`
   - `node.childNodes.length`
   - `node.textContent`

3. Use `Node.appendChild()` when adding rows to the table (not `innerHTML` for row insertion).

4. Use `Node.removeChild()` when deleting a staff row via the Delete button.

**Node Type reference you must handle in your display:**

| Value | Constant |
|-------|----------|
| 1 | ELEMENT_NODE |
| 3 | TEXT_NODE |
| 8 | COMMENT_NODE |
| 9 | DOCUMENT_NODE |

> 💡 *Senior note: A lot of devs never traverse the Node tree manually. Understanding parentNode, childNodes, and nodeType separates someone who uses the DOM from someone who understands it.*

---

### TASK 3 — Element & Element Methods | *createElement, querySelector, classList, getAttribute*

**Competency tested:** Element creation, Element properties, Element methods

**Requirements:**

1. Use `document.createElement()` to create each of these elements programmatically during the table row build:
   - `<tr>` — the row
   - `<td>` — each cell
   - `<button>` — action buttons (Edit, Delete, Toggle Status)

2. Each `<tr>` must have:
   - A `data-id` attribute (auto-incremented)
   - A `data-department` attribute
   - A class of either `"row-active"` or `"row-inactive"` based on status

3. Use `element.classList.add()`, `element.classList.remove()`, and `element.classList.toggle()` appropriately when toggling staff status.

4. Use `element.getAttribute()` when reading a row's `data-id` to identify which staff to delete or edit.

---

### TASK 4 — Attr & NamedNodeMap | *createAttribute, setAttribute, getAttribute, attributes collection*

**Competency tested:** Attr object, setAttribute, getAttribute, NamedNodeMap

**Requirements:**

1. When creating a new `<tr>`, use **`document.createAttribute()`** and **`element.setAttributeNode()`** for setting the `data-id` attribute (at least once — to demonstrate you know the Attr object).

2. For all other attributes (`data-department`, `class`, `id`), use the shorthand `element.setAttribute(name, value)`.

3. Add an **"Inspect Attributes"** button to each row. When clicked, it must read all attributes using `element.attributes` (the `NamedNodeMap`) and display them in the Activity Log like:
   ```
   [Attributes of row #3]
   data-id = 3
   data-department = Engineering
   class = row-active
   ```

> 💡 *Senior note: Most devs skip straight to `setAttribute`. But knowing the Attr object and NamedNodeMap is what separates someone reading docs from someone who actually understands the Web API.*

---

### TASK 5 — NodeList: Live vs Static | *childNodes (live) vs querySelectorAll (static)*

**Competency tested:** Live NodeList, Static NodeList, the behavioral difference

**Requirements:**

1. In the Activity Log, every time a new staff row is added, log both:
   - The count from `tableBody.childNodes.length` — label it `[Live NodeList]`
   - The count from `document.querySelectorAll("tbody tr").length` — label it `[Static Snapshot]`

2. Both counts should match right after insertion. Add a comment in your code explaining **why they're the same immediately after insertion but why live vs static matters** in async scenarios.

3. Add a "Count Rows" button that re-reads both counts and logs them again, demonstrating that `querySelectorAll` always returns a new static snapshot.

---

### TASK 6 — Text Node | *createTextNode, textContent, innerText*

**Competency tested:** Text Node creation, textContent vs innerText

**Requirements:**

1. For the staff table header row (`<th>` cells: ID, Name, Department, Role, Status, Actions), use **`document.createTextNode()`** to insert the text content — do not just assign `td.textContent = "text"` for headers.

2. Create a `<div id="text-demo">` with nested HTML like:
   ```html
   <div id="text-demo">
     Staff Count: <strong>hidden</strong>
     <span style="display:none">secret text</span>
   </div>
   ```
   Then in JS, log to the Activity Log:
   - `textContent` of `#text-demo` — shows ALL text including hidden
   - `innerText` of `#text-demo` — shows only VISIBLE text

3. This demonstrates the difference between `textContent` and `innerText`.

---

### TASK 7 — innerHTML | *innerHTML for reading and writing complex content*

**Competency tested:** innerHTML read, innerHTML write with HTML tags

**Requirements:**

1. Add an **"Edit"** button per row. When clicked, the Name cell of that row must switch from plain text to an editable `<input>` tag — achieved by setting `cell.innerHTML = '<input type="text" value="...">'`.

2. Add a **"Save"** button that replaces the input back to plain text by reading the input value and setting `cell.innerHTML = newValue`.

3. Add a **"Preview"** section below the table. When a row is clicked, set the preview `div.innerHTML` to display a formatted staff card:
   ```html
   <h3>John Doe</h3>
   <p><strong>Department:</strong> Engineering</p>
   <p><strong>Role:</strong> Backend Developer</p>
   <p class="status-badge">● Active</p>
   ```

> ⚠️ *Senior note: innerHTML is powerful but dangerous if you use it with user-provided data. In this project, since we control the data, it's fine — but add a comment in your code about XSS risk when using innerHTML with external input.*

---

### TASK 8 — Style Manipulation | *element.style, camelCase CSS properties*

**Competency tested:** `element.style`, CSS property naming in DOM (camelCase)

**Requirements:**

1. When a staff status is **Active**, the row's style must be set using `element.style`:
   - `element.style.backgroundColor = "#e8f5e9"` (light green)
   - `element.style.borderLeft = "4px solid #43a047"`

2. When status is **Inactive**:
   - `element.style.backgroundColor = "#ffebee"` (light red)
   - `element.style.borderLeft = "4px solid #e53935"`

3. Add a **"Highlight Engineering"** button that sets `element.style.fontWeight = "bold"` and `element.style.color = "#1565c0"` on all Engineering department rows.

4. Add a **"Reset Styles"** button that removes all inline styles using `element.style.cssText = ""`.

> 💡 *Senior note: CSS uses `background-color`. DOM uses `backgroundColor`. If you mix them up in code, nothing breaks but nothing works either. Prove you know the difference.*

---

### TASK 9 — Event Handler: EventTarget & GlobalEventHandler | *addEventListener, onclick*

**Competency tested:** `addEventListener`, GlobalEventHandler (`onclick`), event removal

**Requirements:**

1. Use `addEventListener("click", callback)` for:
   - The "Add Staff" form submit button
   - The "Window Info" button
   - The "Run Selector" button
   - All dynamically created row buttons (Delete, Toggle Status, Inspect Attributes)

2. Use **GlobalEventHandler** (`element.onclick = function() {}`) for:
   - The "Edit" button on each row (use this style specifically to demonstrate you know both approaches)

3. For the "Highlight Engineering" button, add the event listener **after** a 2-second delay using `setTimeout` to demonstrate that event listeners can be added at any time dynamically.

4. Add a **"Remove Log Listener"** button. When clicked, it must use `removeEventListener()` to detach the click handler from the Activity Log panel (after which, clicking the log should do nothing). This proves you understand listener removal.

---

### TASK 10 — Event Object | *event.type, event.target, MouseEvent, KeyboardEvent*

**Competency tested:** Event object data, event.target, event.type, different event types

**Requirements:**

1. On the **Name input** in the Add Staff form, listen for the `"keyup"` event. On each keypress, log to the Activity Log:
   ```
   [KeyboardEvent] key: "A" | keyCode: 65 | target: input#staff-name
   ```

2. On the staff **table body**, use **event delegation** — attach one single `"click"` event listener to the `<tbody>`, and inside the callback use `event.target` to determine which button was clicked (Delete, Toggle, or Inspect).

3. On the header of the app, listen for `"mousemove"` and display live coordinates in a small `<span>`:
   ```
   Mouse: x=342, y=87
   ```

4. On the `"DOMContentLoaded"` event of `document`, initialize the 3 default staff rows and log `"DOM ready — initial data loaded"` to the Activity Log.

---

### TASK 11 — Query Selector (All Selector Types) | *querySelector, querySelectorAll, CSS selector patterns*

**Competency tested:** Universal, Type, Class, ID, Attribute selectors and operators

Build a **"Filter & Query Panel"** with the following controls — each must use a different selector type:

1. **Universal Selector** — A button "Count All Nodes" that runs `document.querySelectorAll("*")` and logs the total node count.

2. **Type Selector** — A button "Count Rows" that runs `document.querySelectorAll("tr")` and logs count.

3. **Class Selector** — An input + button: user types a class name (e.g. `row-active`), clicks "Select by Class", and all matching rows get a temporary yellow `background-color` for 2 seconds.

4. **ID Selector** — An input + button: user types an ID, clicks "Find by ID", and `document.querySelector("#" + id)` highlights that element.

5. **Attribute Selector** — A button "Find Engineering Rows" that uses `document.querySelectorAll("tr[data-department='Engineering']")` to select and highlight those rows.

6. **Attribute Operator Selector** — A button "Find Names Starting with J" that uses `document.querySelectorAll("td[data-name^='J']")` to highlight matching name cells.

7. **Live Custom Selector Input** — A text input and "Run Selector" button where the user can type any valid CSS selector and see the count of matched elements logged.

---

### TASK 12 — HTML Form Element | *HTMLFormElement, HTMLInputElement, form access via name*

**Competency tested:** Form element API, input properties, `document.forms[name]`

**Requirements:**

1. The Add Staff form must have:
   - `name="staffForm"` on the `<form>` tag
   - `name="staffName"`, `name="staffDept"`, `name="staffRole"` on inputs

2. Access the form using `document.forms["staffForm"]` (not `getElementById`).

3. Access individual input values using `document.forms["staffForm"]["staffName"].value`.

4. On form submit, validate that all fields are non-empty. If any field is empty:
   - Set `input.style.borderColor = "red"` on the empty fields
   - Log `[WARN] Form validation failed — empty fields` to Activity Log
   - Do NOT add the row

5. After successful submit, call `document.forms["staffForm"].reset()` to clear the form.

6. Listen for the `"change"` event on the Department select input. When changed, log: `"Department changed to: Engineering"`.

---

### TASK 13 — HTML Table Element | *HTMLTableElement API, insertRow, deleteRow, insertCell*

**Competency tested:** `HTMLTableElement`, `insertRow()`, `deleteRow()`, `insertCell()`, `rows` collection

**Requirements:**

1. Use `table.insertRow()` to create new rows (instead of `createElement("tr")` for this specific operation) — this tests your knowledge of the HTMLTableElement API.

2. Inside each row, use `row.insertCell()` to create cells.

3. Use `table.rows.length` to display a live row count in the header: `"Staff: 3 employees"`.

4. Use `table.deleteRow(rowIndex)` when the Delete button is clicked — get the row index using `row.rowIndex`.

5. Add a **"Sort by Name"** button that reads all rows via `table.rows`, sorts them alphabetically by name cell content, and re-inserts them in sorted order.

6. Add a **"Export Table"** button that reads the table using `table.rows` and logs the full table contents as a formatted string to the Activity Log.

---

### TASK 14 — Node Type Detection | *nodeType constants, filtering NodeList by type*

**Competency tested:** `node.nodeType`, filtering nodes by type

**Requirements:**

1. Add a **"Inspect Table Children"** button. When clicked, iterate over `tableBody.childNodes` and for each node, log its `nodeType` and `nodeName` to the Activity Log — this will reveal both ELEMENT_NODEs (the `<tr>` rows) and TEXT_NODEs (whitespace between rows if any).

2. Add a "Count Element Nodes Only" button that filters `childNodes` to only count nodes where `node.nodeType === Node.ELEMENT_NODE`.

3. In the DOM Inspector Panel (Task 2), display the nodeType label using a lookup object:
   ```js
   const NODE_TYPE_LABELS = {
     1: "ELEMENT_NODE",
     3: "TEXT_NODE",
     8: "COMMENT_NODE",
     9: "DOCUMENT_NODE",
     11: "DOCUMENT_FRAGMENT_NODE"
   };
   ```

---

## 📦 Initial Data

Seed the app with these **3 staff records on load** (via `DOMContentLoaded`):

```js
const initialStaff = [
  { name: "Budi Santoso",   department: "Engineering",  role: "Backend Developer",  status: "active"   },
  { name: "Siti Rahayu",    department: "Design",       role: "UI/UX Designer",     status: "active"   },
  { name: "Joko Widodo",    department: "Marketing",    role: "Marketing Manager",  status: "inactive" },
];
```

---

## 🧪 EVALUATION CRITERIA

| # | Criteria | Points |
|---|----------|--------|
| 1 | Document properties logged on load + Window button works | 8 |
| 2 | Node Inspector Panel: nodeType, nodeName, parentNode, childNodes | 8 |
| 3 | Element creation via `createElement`, classList usage, data attributes | 8 |
| 4 | Attr object used (`createAttribute`/`setAttributeNode`) + NamedNodeMap inspect | 6 |
| 5 | Live vs Static NodeList demonstrated with comments | 6 |
| 6 | Text Node created via `createTextNode` + textContent vs innerText shown | 6 |
| 7 | innerHTML used for edit-in-place + preview card + XSS comment | 7 |
| 8 | Style manipulation via `element.style` with camelCase properties | 6 |
| 9 | `addEventListener` + GlobalEventHandler + `removeEventListener` all present | 8 |
| 10 | Event object used: KeyboardEvent, MouseEvent, event delegation, DOMContentLoaded | 8 |
| 11 | All 7 selector types demonstrated in Filter Panel | 10 |
| 12 | HTMLFormElement API: `document.forms`, `form.reset()`, validation, change event | 8 |
| 13 | HTMLTableElement API: `insertRow`, `deleteRow`, `insertCell`, `rows`, sort | 9 |
| 14 | nodeType detection, filtering, NODE_TYPE_LABELS lookup | 6 |
| **Total** | | **104** *(scaled to 100)* |

---

## ❌ AUTOMATIC FAIL CONDITIONS

- Using any external library (jQuery, React, Vue, Bootstrap JS, etc.)
- Using separate `.js` or `.css` files — everything must be in `index.html`
- Opening `index.html` via `file://` — use Live Server
- Hardcoding `<tr>` rows in HTML — all rows must be dynamically created via JS
- Missing the event delegation pattern in Task 10 (single listener on `<tbody>`)
- Not using `document.forms["formName"]` at least once (Task 12)
- Not using `table.insertRow()` / `table.deleteRow()` (Task 13)

---

## 📤 SUBMISSION CHECKLIST

- [ ] Single `index.html` file — no separate `.js` or `.css` files
- [ ] App runs on Live Server with zero console errors
- [ ] DOM Inspector Panel updates when any table cell is clicked
- [ ] Add Staff form validates, inserts row, resets form
- [ ] Delete removes row from table cleanly
- [ ] Toggle Status changes row background color via `element.style`
- [ ] Filter & Query Panel shows at least 6 of the 7 selector demos working
- [ ] Activity Log shows timestamped entries for every DOM operation
- [ ] `DOMContentLoaded` fires and seeds the 3 initial rows
- [ ] All 13 tasks have at least partial implementation

---

## 💬 Final Note from Senior Lead Dev

> *"The DOM is not complicated — it's just big. There are a lot of APIs. A lot of properties. A lot of methods. The developers who struggle aren't the ones who can't understand it — they're the ones who never bothered to read past `getElementById`.*
>
> *What I want to see from this project: that you can navigate the DOM tree, you know the difference between a Node, an Element, and a TextNode, you can handle events cleanly with delegation, and you know how to manipulate a table programmatically without innerHTML shortcuts.*
>
> *If your project is just getElementById everywhere with a few innerHTML hacks — that's a fail. I want to see the full range.*
>
> *Run it. Open DevTools. Check the console. Check the Elements panel while your app runs. If DOM nodes are appearing and disappearing correctly — you're on the right track.*
>
> *Good luck. I'll see you in JavaScript Async — if you pass this.*"
>
> — **Senior Lead Dev**

---

*Module: JavaScript Document Object Model | Instructor: Eko Kurniawan Khannedy | Exam Version: 1.0*
