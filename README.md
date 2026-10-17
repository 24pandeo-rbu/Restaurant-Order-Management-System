# SmartServe – Restaurant Management System Using Data Structures and Algorithms

![C](https://img.shields.io/badge/C-DSA-00599C?logo=c&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-Frontend-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-Styling-1572B6?logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-Fetch%20API-F7DF1E?logo=javascript&logoColor=black)
![Python](https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-REST%20API-000000?logo=flask&logoColor=white)
![JSON](https://img.shields.io/badge/Storage-JSON%20%2B%20Text%20Files-555555)
![Git](https://img.shields.io/badge/Git-Version%20Control-F05032?logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-Repository-181717?logo=github&logoColor=white)
![VS Code](https://img.shields.io/badge/VS%20Code-IDE-007ACC?logo=visualstudiocode&logoColor=white)

SmartServe is a B.Tech mini-project that pairs a restaurant management web application (HTML, CSS, JavaScript and a Python Flask REST API) with a console program written in C that implements core data structures and algorithms on restaurant order data. It covers the menu, order creation, kitchen queue processing, billing and order history.

> **Project status:** Student project that runs locally. It is not deployed online, and payment options are for demonstration only (no real payments are processed).

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Screenshots](#screenshots)
- [Technology Stack](#technology-stack)
- [DSA Concepts and Use Cases](#dsa-concepts-and-use-cases)
- [Project Structure](#project-structure)
- [Getting Started (Windows)](#getting-started-windows)
- [Data Storage](#data-storage)
- [API Reference](#api-reference)
- [Known Limitations](#known-limitations)
- [Objectives and Learning Outcomes](#objectives-and-learning-outcomes)
- [Future Improvements](#future-improvements)
- [Project Team](#project-team)
- [Repository](#repository)
- [License](#license)

## Overview

The repository contains two parts that work with the same order data format:

1. **Web application** – a browser frontend (`frontend/`) that talks to a Flask REST API (`backend/app.py`). The API stores the menu in `data/menu.json` and orders in `data/orders.txt`.
2. **C console program** – `src/main.c` implements a queue, stack, linked list, binary search tree, searching, sorting and file handling over the same `data/orders.txt` record format.

```text
Browser (frontend: HTML + CSS + JavaScript)
        │  fetch() – JSON over HTTP
        ▼
Flask REST API (backend/app.py) ──► data/menu.json
                                └─► data/orders.txt ◄── C console program (src/main.c)
                                                        (run separately; same record format)
```

The Flask backend does not call the C program. The two are run independently and share only the `orders.txt` file format (see [Known Limitations](#known-limitations)).

## Key Features

**Web application (implemented)**

| Feature | Description |
|---|---|
| Dashboard | Summary cards for total, pending and processed orders and total order value (before GST), a recent-orders table and quick actions. |
| Food menu | Menu loaded from the API. New food items can be added with a name (up to 60 characters), a price greater than zero and an optional description. Duplicate names are rejected. |
| Order creation and management | Choose a menu item and quantity; the order is saved through the API and the total is calculated by the backend. Each order holds one menu item with a quantity. |
| Kitchen queue (FIFO) | Pending orders are listed with their FIFO position. **Process next order** marks the oldest pending order (lowest order ID) as processed. |
| Billing | Select an order to see the subtotal, a sample 5% GST and the total. Cash, UPI or Card can be selected and recorded as a demonstration. |
| Order history | Table of all saved orders with item, quantity, amount and Pending/Processed status. |
| DSA Lab page | Visual panels for the kitchen queue, recent-order stack, order linked list and an order-ID search. These panels are drawn in JavaScript from the orders returned by the API. |
| Flask API integration | The frontend reads and writes menu and order data through REST endpoints (see [API Reference](#api-reference)). |

**C console program (implemented in `src/main.c`)**

<details>
<summary>Menu options available in the console program</summary>

| Option | Action |
|---|---|
| 1 | Display food menu |
| 2 | Place customer order |
| 3 | View kitchen FIFO queue |
| 4 | Table booking (10 tables, kept in memory for the session) |
| 5 | Billing (subtotal, 5% GST, total) |
| 6 | Search food by ID |
| 7 | Sort food menu by price |
| 8 | Process next kitchen order |
| 9 | Order history |
| 10 | Display orders using linked list |
| 11 | Search order using linked list |
| 12 | Display recent-order stack (LIFO) |
| 13 | Peek latest order in stack |
| 14 | Pop latest order from stack |
| 15 | Display orders using binary search tree |
| 16 | Search order using binary search tree |
| 0 | Save and exit |

</details>

> **Payments:** The Cash, UPI and Card options are a demonstration only. The selected method is held in the browser's memory for the current page session; it is not sent to the backend, not saved, and no payment gateway is integrated. GST is an illustrative 5%.

## Screenshots

<table>
  <tr>
    <td width="50%" valign="top">
      <b>Home Screen Dashboard</b><br>
      <img src="Screenshot/Home%20Screen%20Dashboard%20.png" alt="SmartServe home screen dashboard" width="100%"><br>
      <sub>Order summary cards, recent orders and quick actions.</sub>
    </td>
    <td width="50%" valign="top">
      <b>Food Menu</b><br>
      <img src="Screenshot/Food%20Menu%20Side%20To%20add%20food%20In%20Menu.png" alt="SmartServe food menu with add food item form" width="100%"><br>
      <sub>Menu items from the API and the form to add a new food item.</sub>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <b>Billing</b><br>
      <img src="Screenshot/Billing%20Side%20%20.png" alt="SmartServe billing page" width="100%"><br>
      <sub>Bill with subtotal, sample GST, total and a payment-method selector (demo).</sub>
    </td>
    <td width="50%" valign="top">
      <b>Kitchen Queue / Pending Orders</b><br>
      <img src="Screenshot/Kitchen%20Queue%20Pending%20Order%20%20.png" alt="SmartServe kitchen queue with pending orders" width="100%"><br>
      <sub>Pending orders in FIFO order with the Process next order action.</sub>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <b>Order History</b><br>
      <img src="Screenshot/Order%20History%20%20.png" alt="SmartServe order history" width="100%"><br>
      <sub>All orders with quantity, amount and kitchen status.</sub>
    </td>
    <td width="50%" valign="top">
      <b>DSA Lab / Complete Application Dashboard</b><br>
      <img src="Screenshot/DSA%20Lab%20Side%20%20To%20check%20comple%20app%20dashboard%20%20.png" alt="SmartServe DSA lab page" width="100%"><br>
      <sub>Visual panels for queue, stack, linked list and order-ID search.</sub>
    </td>
  </tr>
</table>

## Technology Stack

| Layer | Technology | Purpose in this project |
|---|---|---|
| DSA implementation | C | Console program with queue, stack, linked list, BST, searching, sorting and file handling (`src/main.c`) |
| Frontend structure | HTML | Page layout and sections (`frontend/index.html`) |
| Styling | CSS | Responsive dashboard styling (`frontend/style.css`) |
| Frontend logic | JavaScript | UI interactions, rendering and API calls using `fetch` (`frontend/app.js`) |
| Backend | Python, Flask | REST API, validation and file persistence (`backend/app.py`) |
| Cross-origin access | Flask-Cors | Lets the frontend (served on a different local port) call the API |
| API style | REST (JSON over HTTP) | Frontend–backend communication |
| Data storage | JSON and text files | `data/menu.json` and `data/orders.txt` |
| Tooling | Git, GitHub, Visual Studio Code | Version control, hosting the repository and development |

Python dependencies are listed in `backend/requirements.txt`: `Flask` and `Flask-Cors`.

## DSA Concepts and Use Cases

All data structures below are implemented in `src/main.c`.

| Concept | Implementation | Use in SmartServe | Time complexity |
|---|---|---|---|
| Queue (FIFO) | Circular array (`kitchen_queue`) with `enqueue()` and `dequeue()` | Kitchen processes the oldest pending order first | Enqueue/dequeue: O(1) |
| Stack (LIFO) | Array (`order_stack`) with `push_order_index()`, `peek_order_stack()`, `pop_order_stack()` | Shows the most recent orders first; popping only removes the entry from the demo stack, not the saved order | Push/pop/peek: O(1) |
| Singly linked list | `OrderNode` list with head and tail pointers (`list_append()`) | Keeps orders in arrival order for display and search by order ID | Append: O(1); search: O(n) |
| Binary search tree | `BSTNode` keyed by order ID (`bst_insert()`, `bst_search()`, `bst_inorder()`) | Builds a temporary tree from current orders to search by ID and list orders in ascending ID order | Average O(log n); worst case O(n) |
| Searching | Linear search (`find_food()`, linked list search) | Look up a food item or an order by ID | O(n) |
| Sorting | Insertion sort on a copy of the menu (`sort_food_menu()`) | Display the menu sorted by price | O(n²) |
| File handling | `fopen`, `fgets`, `sscanf`, `fprintf` (`load_orders()`, `save_orders()`) | Load saved orders at start-up (rebuilding the list, stack and pending queue) and save after changes | O(n) |

On the web side, the Flask backend applies the same FIFO rule by processing the pending order with the lowest order ID, and the DSA Lab page visualises the queue, stack and linked list in the browser. The C program is where these structures are actually implemented.

## Project Structure

```text
SmartServe-Restaurant-Management-System1/
├── backend/
│   ├── app.py                 # Flask REST API
│   └── requirements.txt       # Flask, Flask-Cors
├── data/
│   ├── menu.json              # Menu items (JSON)
│   └── orders.txt             # Order records (text)
├── frontend/
│   ├── index.html             # Application layout
│   ├── style.css              # Styling
│   └── app.js                 # UI logic and API calls
├── Screenshot/                # README screenshots (6 images)
├── src/
│   └── main.c                 # C DSA console program
├── .gitignore
├── main.exe                   # Compiled Windows executable of the C program
└── README.md
```

## Getting Started (Windows)

All commands are run from the repository root in **Windows PowerShell**.

### Prerequisites

- Git
- Python 3 with pip
- A modern web browser
- Visual Studio Code with the **Live Server** extension (or use the Python alternative in step 3)
- A C compiler such as GCC from MinGW-w64 (only needed to recompile the C program)

### 1. Clone the repository

```powershell
git clone https://github.com/atul-nandanwar/SmartServe-Restaurant-Management-System1.git
cd SmartServe-Restaurant-Management-System1
```

### 2. Start the backend

Create and activate a virtual environment, install the dependencies and start Flask:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r backend/requirements.txt
python backend/app.py
```

If PowerShell blocks the activation script, allow it for the current terminal session only and activate again:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\.venv\Scripts\Activate.ps1
```

The API runs at `http://127.0.0.1:5000`. Keep this terminal open. To confirm it is running, open a second PowerShell window and run:

```powershell
Invoke-RestMethod http://127.0.0.1:5000/api/health
```

Expected result: `status` is `ok` and `service` is `SmartServe API`.

### 3. Open the frontend

The frontend calls the API at `http://127.0.0.1:5000/api` (set by `API_BASE` in `frontend/app.js`), so the backend must be running first.

**Option A – VS Code Live Server:** open the repository folder in VS Code, right-click `frontend/index.html` and choose **Open with Live Server**. The page opens at `http://127.0.0.1:5500/frontend/index.html`.

**Option B – Python static server:** in a second PowerShell window, from the repository root:

```powershell
python -m http.server 5500 --directory frontend
```

Then open `http://127.0.0.1:5500/index.html`.

When the page connects, the status pill in the top bar changes to **Live System**. If it shows **API Disconnected**, check that `python backend/app.py` is still running and refresh the page.

### 4. Run the C console program (optional)

The repository includes a compiled `main.exe`. Run it from the repository root, because the program reads and writes `data/orders.txt` using a relative path:

```powershell
.\main.exe
```

To recompile after editing `src/main.c` (GCC must be on your `PATH`):

```powershell
gcc src/main.c -o main.exe
.\main.exe
```

Read [Known Limitations](#known-limitations) before using the C program on data created through the web application.

## Data Storage

**`data/menu.json`** – a JSON array of menu items with the fields `id`, `name`, `price`, `emoji` and `desc`. If the file is missing, the backend creates it with six default items.

**`data/orders.txt`** – one order per line with five space-separated values:

```text
order_id food_id quantity total processed
```

For example, `7 5 6 480.00 0` is order 7 for food item 5, quantity 6, total 480.00, not yet processed (`0` = pending, `1` = processed). The backend writes these files through a temporary file followed by `os.replace` so a file is not left half-written.

## API Reference

Base URL: `http://127.0.0.1:5000`. These routes were checked against `backend/app.py`.

| Method | Endpoint | Description | Responses |
|---|---|---|---|
| GET | `/` | API status message with links to the menu and orders endpoints | 200 |
| GET | `/api/health` | Health check (`{"status": "ok", "service": "SmartServe API"}`) | 200 |
| GET | `/api/menu` | List all menu items | 200, 500 |
| POST | `/api/menu` | Add a menu item. Body: `name` (required, up to 60 characters), `price` (greater than 0), `desc` (optional) | 201, 400, 409 (duplicate name), 500 |
| GET | `/api/orders` | List orders with `totalOrders`, `pendingOrders` and `processedOrders` counts | 200, 500 |
| POST | `/api/orders` | Create an order. Body: `foodId` and `quantity` (1 to 100). The total is calculated by the server | 201, 400, 500 |
| POST | `/api/orders/process-next` | Mark the oldest pending order (lowest order ID) as processed; returns a "No pending orders" message if there is none | 200, 500 |
| GET | `/api/orders/<order_id>` | Get one order by integer ID | 200, 404, 500 |

Example (PowerShell). This creates a real order record in `data/orders.txt`:

```powershell
Invoke-RestMethod -Uri http://127.0.0.1:5000/api/orders -Method Post -ContentType "application/json" -Body '{"foodId": 1, "quantity": 2}'
```

## Known Limitations

- **Separate components:** the web app and the C program are not connected; the Flask backend does not call the C code.
- **Menu mismatch between components:** the C program has a built-in menu of six items. When it loads `data/orders.txt`, it skips orders for food IDs it does not know (for example, items added through the web form), and those orders are removed from the file the next time the C program saves. Back up `data/` before running the C program on data created in the web app, and do not run both at the same time.
- **Payments are demonstration only:** the selected payment method is kept in browser memory and is lost on page refresh. No payment gateway is integrated and GST is illustrative.
- **One item per order:** each order record holds a single menu item and quantity.
- **Order limit:** a maximum of 100 orders is supported by both the backend and the C program.
- **Local development setup:** the Flask server runs in development mode on localhost without authentication, and data is stored in flat files.
- **Browser-side DSA Lab:** the DSA Lab page is a visual demonstration built from the API data; the order-ID search there is a simple lookup in the browser. The tree, queue, stack and list implementations are in `src/main.c`.
- **Skewed BST:** order IDs are assigned in increasing order, so the BST built from them is skewed and behaves like a linked list.

## Objectives and Learning Outcomes

**Objectives**

- Apply data structures and algorithms to a practical restaurant-management use case.
- Build a web application that manages menu items, orders, the kitchen queue, billing and order history.
- Connect a JavaScript frontend to a Flask backend through REST APIs.

**Learning outcomes**

- Implementing a circular queue, stack, singly linked list and binary search tree in C, including dynamic memory allocation and clean-up.
- Applying searching and sorting algorithms and persisting data with file handling.
- Designing REST endpoints with input validation and appropriate HTTP status codes in Flask.
- Using `fetch` for API communication, handling errors in the UI, and enabling CORS for local development.
- Working with Git and GitHub, and documenting a project clearly.

## Future Improvements

These are planned ideas and are **not** implemented yet.

- Store data in SQLite or MySQL instead of flat files.
- Save payment records in the backend and add real payment-gateway integration with appropriate security.
- Support multiple items per order and editing or deleting menu items.
- Keep the menu in one shared source so the C program and web app stay consistent, or expose the C logic through the API.
- Use a self-balancing tree (such as an AVL tree) for order search.
- Add staff and administrator authentication.
- Generate sales reports and analytics.
- Add automated tests, pin dependency versions in `backend/requirements.txt`, and deploy the application online.

## Project Team

1. Atul Nandanwar
2. Ishan Jaiswal
3. Sai Pohekar
4. Om Pande
5. Ashwini Goswami

## Repository

- **GitHub:** [SmartServe-Restaurant-Management-System1](https://github.com/atul-nandanwar/SmartServe-Restaurant-Management-System1)

## License

This repository does not currently include a license file, so no license is granted for reuse, modification or distribution. If the team wants to allow others to reuse the code, add a `LICENSE` file with a license of your choice.