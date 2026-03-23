# 🏢 DOM Staff Directory — Internal HR Tool

<div align="center">

![JavaScript](https://img.shields.io/badge/JavaScript-DOM_API-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-Single_File_App-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-Embedded-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![Status](https://img.shields.io/badge/Status-Final_Exam_Project-brightgreen?style=for-the-badge)
![No Dependencies](https://img.shields.io/badge/Dependencies-Zero-success?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

<br/>

> A fully interactive, single-file browser app that demonstrates complete mastery of the **JavaScript Document Object Model (DOM) Web API** — from Node traversal and Element creation to Form handling, Table manipulation, Event delegation, and CSS Query Selectors.

</div>

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Project Structure](#-project-structure)
- [DOM Concept Map](#-dom-concept-map)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Running the App](#running-the-app)
- [UI Sections](#-ui-sections)
- [DOM API Coverage](#-dom-api-coverage)
- [Event Architecture](#-event-architecture)
- [Query Selector Reference](#-query-selector-reference)
- [Key Constraints](#-key-constraints)
- [Tech Stack](#-tech-stack)
- [Author](#-author)

---

## 🔍 Overview

The **DOM Staff Directory** is a browser-based HR management tool built entirely with **vanilla JavaScript** and the **native DOM Web API** — zero frameworks, zero dependencies, zero build tools.

The app manages employee records through a live interactive interface, demonstrating every major DOM concept from the *JavaScript Document Object Model* course: Document traversal, Node tree inspection, Element creation, Attribute management, Event handling, Form API, Table API, Style manipulation, and Query Selectors.

This project was built as a **final exam submission** for the JavaScript DOM module by Eko Kurniawan Khannedy (ProgrammerZamanNow).

---

## ✨ Features

- 📋 **DOM Inspector Panel** — click any cell to inspect its `nodeType`, `nodeName`, `parentNode`, and `childNodes` in real time
- ➕ **Dynamic Staff Form** — add employees with validation, using `HTMLFormElement` API and `document.forms` access
- 📊 **Live Staff Table** — built entirely via `HTMLTableElement` API (`insertRow`, `deleteRow`, `insertCell`)
- 🔍 **Filter & Query Panel** — 7 different CSS selector patterns demonstrated interactively
- 🎨 **Inline Style Control** — row colors driven by `element.style` with camelCase DOM properties
- ✏️ **Edit In-Place** — click Edit to swap a cell to an `<input>` using `innerHTML`, save to restore it
- 👁️ **Staff Preview Card** — click a row to render a styled card via `innerHTML`
- 📝 **Activity Log** — timestamped record of every DOM operation performed
- ⌨️ **Keyboard & Mouse Events** — live key logging and mouse coordinate tracking
- 🗑️ **Event Delegation** — single `<tbody>` listener handles all row button clicks via `event.target`

---

## 🗂️ Project Structure

```
dom-staff-directory/
│
├── index.html       ← Entire app: HTML structure + embedded CSS + embedded JS
└── README.md
```

> **Single-file architecture** is intentional. The constraint forces explicit use of the DOM API to build every element programmatically in JavaScript rather than relying on pre-written HTML markup or CSS files.

---

## 🗺️ DOM Concept Map

```
Browser loads index.html
         │
         ▼
 DOMContentLoaded fires
         │
         ├──► document properties logged (title, URL, domain, readyState)
         │
         ├──► initialStaff[] seeded via HTMLTableElement.insertRow()
         │         │
         │         └──► Each row built with:
         │               ├── document.createElement("td")
         │               ├── document.createTextNode()      ← Text Node
         │               ├── document.createAttribute()     ← Attr object
         │               ├── element.setAttribute()
         │               ├── element.style.backgroundColor  ← Style API
         │               └── row.insertCell()               ← HTMLTableElement
         │
         ├──► Event listeners attached:
         │         ├── addEventListener (form, buttons, window)
         │         ├── element.onclick (Edit buttons)       ← GlobalEventHandler
         │         ├── keyup on name input                  ← KeyboardEvent
         │         ├── mousemove on header                  ← MouseEvent
         │         └── click on tbody (delegation)          ← event.target
         │
         └──► Query Selector Panel ready:
                   ├── querySelectorAll("*")                ← Universal
                   ├── querySelectorAll("tr")               ← Type
                   ├── querySelectorAll(".row-active")      ← Class
                   ├── querySelector("#id")                 ← ID
                   ├── querySelectorAll("[data-department]")← Attribute
                   └── querySelectorAll("td[data-name^='J']")← Operator
```

---

## 🚀 Getting Started

### Prerequisites

| Requirement | Details |
|-------------|---------|
| Modern Browser | Chrome 80+, Firefox 75+, Edge 80+, Safari 13.1+ |
| Local Web Server | Required — browser security blocks some DOM APIs over `file://` |
| Code Editor | VS Code recommended |

> ⚠️ **Do not open `index.html` by double-clicking it.** Some DOM APIs and event behaviors work differently or throw errors over the `file://` protocol. Always use a local server.

### Running the App

**Option A — VS Code Live Server (Recommended)**

1. Install the [Live Server extension](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
2. Clone the repo:
   ```bash
   git clone https://github.com/your-username/dom-staff-directory.git
   cd dom-staff-directory
   ```
3. Right-click `index.html` in VS Code → **Open with Live Server**
4. Navigate to `http://localhost:5500`

**Option B — Python HTTP Server**

```bash
cd dom-staff-directory
python -m http.server 8080
# Visit: http://localhost:8080
```

**Option C — Node.js**

```bash
npx serve .
# Visit: http://localhost:3000
```

### Verify It's Working

Open **DevTools** (`F12`) → **Console** tab. On load you should see:

```
DOM ready — initial data loaded
[Document] title: DOM Staff Directory
[Document] readyState: complete
[Document] domain: localhost
[Live NodeList] rows: 3
[Static Snapshot] rows: 3
```

---

## 🖥️ UI Sections

### 1. Header
Contains the app title and the **Window Info** button which calls `window.alert()` with screen dimensions and location.

### 2. DOM Inspector Panel
Displays real-time Node information when any table cell is clicked:
- `nodeType` number + label (e.g. `1 — ELEMENT_NODE`)
- `nodeName`
- `parentNode.nodeName`
- `childNodes.length`
- `textContent`

### 3. Add Staff Form
- Accessed via `document.forms["staffForm"]`
- Inputs accessed via `document.forms["staffForm"]["staffName"].value`
- Validates on submit — highlights empty fields in red
- Resets with `form.reset()` on success
- Fires `"change"` event on department select

### 4. Filter & Query Panel
Seven interactive query selector demonstrations, each using a different CSS selector type. See [Query Selector Reference](#-query-selector-reference).

### 5. Staff Table
Fully dynamic — no hardcoded `<tr>` in HTML. Built using:
- `table.insertRow()` — add row
- `row.insertCell()` — add cells
- `table.deleteRow(rowIndex)` — remove row
- `table.rows` — access all rows for sort/export

### 6. Staff Preview Card
Clicking a row renders a formatted preview using `innerHTML` with a structured template.

### 7. Activity Log
Timestamped log of every DOM operation. Supports `removeEventListener` to detach its own click handler via the "Remove Log Listener" button.

---

## 🧩 DOM API Coverage

| API / Concept | Used In | Method/Property |
|---------------|---------|-----------------|
| `document` properties | Task 1 | `.title`, `.URL`, `.domain`, `.readyState` |
| `document` methods | Task 1, 3 | `.createElement()`, `.createTextNode()`, `.createAttribute()` |
| `window` object | Task 1 | `window.alert()`, `window.screen`, `window.innerWidth` |
| Node tree traversal | Task 2 | `.parentNode`, `.childNodes`, `.nodeType`, `.nodeName` |
| Node methods | Task 2, 3 | `.appendChild()`, `.removeChild()` |
| Element properties | Task 3 | `.classList`, `.getAttribute()`, `dataset` |
| Element methods | Task 3 | `.classList.add/remove/toggle()`, `.setAttribute()` |
| `Attr` object | Task 4 | `document.createAttribute()`, `.setAttributeNode()` |
| `NamedNodeMap` | Task 4 | `element.attributes`, iteration |
| Live NodeList | Task 5 | `element.childNodes` |
| Static NodeList | Task 5 | `document.querySelectorAll()` |
| `Text` Node | Task 6 | `document.createTextNode()` |
| `textContent` | Task 6 | `element.textContent` |
| `innerText` | Task 6 | `element.innerText` |
| `innerHTML` read | Task 7 | `element.innerHTML` |
| `innerHTML` write | Task 7 | Edit-in-place, preview card |
| `element.style` | Task 8 | `.backgroundColor`, `.borderLeft`, `.fontWeight`, `.cssText` |
| `addEventListener` | Task 9 | All major interactive elements |
| `GlobalEventHandler` | Task 9 | `element.onclick = fn` on Edit buttons |
| `removeEventListener` | Task 9 | Activity Log listener removal |
| `KeyboardEvent` | Task 10 | `"keyup"` — `.key`, `.keyCode` |
| `MouseEvent` | Task 10 | `"mousemove"` — `.clientX`, `.clientY` |
| Event delegation | Task 10 | Single `<tbody>` click handler via `event.target` |
| `DOMContentLoaded` | Task 10 | Initial data seeding |
| Query Selectors | Task 11 | All 7 selector types |
| `HTMLFormElement` | Task 12 | `document.forms`, `.reset()`, `"change"` event |
| `HTMLTableElement` | Task 13 | `.insertRow()`, `.deleteRow()`, `.insertCell()`, `.rows` |
| `nodeType` constants | Task 14 | `Node.ELEMENT_NODE`, `Node.TEXT_NODE` |

---

## ⚡ Event Architecture

```
document
  └── "DOMContentLoaded" → seed initial staff rows

window
  └── "resize" (optional) → update inner dimensions display

header
  └── "mousemove" → update live mouse coordinates span

#windowInfoBtn
  └── "click" → window.alert() with screen info

#staffForm
  ├── "submit" → validate → insertRow → form.reset()
  └── select[name="staffDept"]
        └── "change" → log department change

input[name="staffName"]
  └── "keyup" → log KeyboardEvent data

tbody (SINGLE LISTENER — Event Delegation)
  └── "click" → event.target inspection
        ├── .delete-btn    → table.deleteRow(rowIndex)
        ├── .toggle-btn    → classList.toggle + style update
        ├── .inspect-btn   → read NamedNodeMap → log to Activity Log
        └── td (any cell)  → update DOM Inspector Panel

.edit-btn (GlobalEventHandler)
  └── element.onclick = fn → innerHTML swap to <input>

.save-btn
  └── "click" → read input.value → restore cell innerHTML

#runSelectorBtn
  └── "click" → querySelectorAll(userInput) → log count

#removeLogListenerBtn
  └── "click" → removeEventListener from Activity Log
```

---

## 🔍 Query Selector Reference

| Button | Selector Used | Type |
|--------|--------------|------|
| Count All Nodes | `*` | Universal |
| Count Rows | `tr` | Type |
| Select by Class | `.{className}` | Class |
| Find by ID | `#{id}` | ID |
| Find Engineering Rows | `tr[data-department='Engineering']` | Attribute |
| Find Names Starting with J | `td[data-name^='J']` | Attribute Operator |
| Run Selector (custom) | User input — any valid CSS selector | Combined |

---

## 🔒 Key Constraints

- **Single file** — all HTML, CSS, and JS in `index.html`. No external files.
- **No frameworks** — no jQuery, React, Vue, Bootstrap JS, or any library.
- **No hardcoded rows** — every `<tr>` is created via JavaScript at runtime.
- **No `npm`** — zero `node_modules`, zero `package.json`.
- **Event delegation** — the `<tbody>` uses one listener for all row actions, not one per button.
- **Live Server required** — `file://` protocol not supported.

---

## 🛠️ Tech Stack

| Technology | Role |
|-----------|------|
| HTML5 | Page structure |
| CSS3 (embedded) | Styling — embedded in `<style>` tag |
| JavaScript ES2020+ | All DOM manipulation logic |
| Web DOM API | Core API used throughout |
| Browser DevTools | Debugging and verification |

---

## 👤 Author

**Course:** JavaScript Document Object Model
**Instructor:** Eko Kurniawan Khannedy
**Channel:** [ProgrammerZamanNow](https://youtube.com/c/ProgrammerZamanNow)
**Website:** [programmerzamannow.com](https://www.programmerzamannow.com)

---

## 📄 License

This project is licensed under the **MIT License**.

---

<div align="center">

Built with `document.createElement()` and zero shortcuts.

*"The DOM is not complicated. It's just big. Learn the tree, not just the methods."*

</div>
