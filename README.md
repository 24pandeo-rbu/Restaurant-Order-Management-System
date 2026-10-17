# 🍽️ SmartServe – Restaurant Management System

A Restaurant Management System built using **C, HTML, CSS, JavaScript, and Python Flask**, combining web application development with Data Structures and Algorithms (DSA) to manage food menus, customer orders, kitchen queues, billing, and order history.

## 📌 Project Overview

SmartServe is a student project designed to demonstrate how restaurant operations can be managed through a web interface and backend APIs, alongside a C-based implementation of data structures and algorithms.

The project provides menu management, order creation, kitchen order processing, billing options, and order history. It also demonstrates how DSA concepts can be applied to restaurant workflows.

## ✨ Key Features

- **Dashboard:** Access the main restaurant management interface.
- **Food Menu Management:** View menu items and add food items with prices and descriptions.
- **Order Management:** Create and view customer orders.
- **Kitchen Queue:** Process pending orders using a FIFO-style workflow.
- **Billing:** Select an order and choose a payment method such as Cash, UPI, or Card.
- **Order History:** Review previously saved orders.
- **Flask Backend:** Connect the frontend to backend REST API endpoints.
- **Local Data Storage:** Store menu data in JSON and order data in a text file.
- **DSA Implementation:** Demonstrate data structures and algorithms through the C program.

**Note:** The payment method selection is for project demonstration. It does not perform real financial transactions or process payments through a payment gateway.

## 📸 Project Screenshots

### 1. Home Dashboard

![SmartServe Home Dashboard](Screenshot/Home%20Screen%20Dashboard%20.png)

### 2. Food Menu

![SmartServe Food Menu](Screenshot/Food%20Menu%20Side%20To%20add%20food%20In%20Menu.png)

### 3. Billing

![SmartServe Billing](Screenshot/Billing%20Side%20%20.png)

### 4. Kitchen Queue

![SmartServe Kitchen Queue](Screenshot/Kitchen%20Queue%20Pending%20Order%20%20.png)

### 5. Order History

![SmartServe Order History](Screenshot/Order%20History%20%20.png)

### 6. DSA Lab / Application Dashboard

![SmartServe DSA Dashboard](Screenshot/DSA%20Lab%20Side%20%20To%20check%20comple%20app%20dashboard%20%20.png)

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| C | DSA implementation and console-based operations |
| HTML | Frontend structure |
| CSS | User interface styling |
| JavaScript | Frontend interactions and API communication |
| Python | Backend development |
| Flask | REST API and server |
| JSON | Menu data storage |
| Text Files | Order data storage |
| Git and GitHub | Version control and project hosting |
| Visual Studio Code | Development environment |

## 🧠 Data Structures and Algorithms

The project uses or demonstrates DSA concepts in restaurant-related operations, including:

- **Queue (FIFO):** Processing kitchen orders in arrival order.
- **Stack (LIFO):** Managing recent-order operations.
- **Linked List:** Displaying and searching order records.
- **Trees:** Organizing and searching orders.
- **Searching and Sorting:** Working with menu or order data.
- **File Handling:** Saving and loading order information.

The exact operations available depend on the corresponding implementation in the C source code.

## 📂 Project Structure

```text
Restaurant Order Management System/
│
├── backend/
│   ├── app.py
│   └── requirements.txt
│
├── data/
│   ├── menu.json
│   └── orders.txt
│
├── frontend/
│   ├── index.html
│   ├── style.css
│   └── app.js
│
├── Screenshot/
│   ├── Home Screen Dashboard .png
│   ├── Food Menu Side To add food In Menu.png
│   ├── Billing Side  .png
│   ├── Kitchen Queue Pending Order  .png
│   ├── Order History  .png
│   └── DSA Lab Side  To check comple app dashboard  .png
│
├── src/
│   └── main.c
│
├── .gitignore
└── README.md
```

## ⚙️ Installation and Setup

### Prerequisites

Install the following before running the project:

- Python 3
- pip
- Visual Studio Code
- A modern web browser
- VS Code Live Server extension

### Step 1: Clone the Repository

Open the terminal and run:

```bash
git clone https://github.com/atul-nandanwar/SmartServe-Restaurant-Management-System1.git
cd SmartServe-Restaurant-Management-System1
```

### Step 2: Create a Python Virtual Environment

On Windows PowerShell, run:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

If PowerShell blocks activation, use the appropriate execution policy for your environment or run the project using the virtual environment's Python executable directly.

### Step 3: Install Backend Dependencies

```powershell
python -m pip install -r backend/requirements.txt
```

### Step 4: Start the Flask Backend

From the project root, run:

```powershell
python backend/app.py
```

Keep this terminal open while using the application.

The local backend is expected to run at:

```text
http://127.0.0.1:5000
```

### Step 5: Open the Frontend

1. Open the project folder in Visual Studio Code.
2. Locate `frontend/index.html`.
3. Right-click the file and select **Open with Live Server**.
4. Use the web application in the browser.

If the frontend cannot connect to the backend, verify the API base URL in `frontend/app.js` and ensure the Flask server is running.

## 🔌 Backend API Endpoints

The following endpoints are provided by the current Flask backend implementation.

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/api/health` | Check backend status |
| GET | `/api/menu` | Retrieve menu items |
| POST | `/api/menu` | Add a food item |
| GET | `/api/orders` | Retrieve orders |
| POST | `/api/orders` | Create an order |
| POST | `/api/orders/process-next` | Process the next pending order |
| GET | `/api/orders/<order_id>` | Retrieve a specific order |

These endpoints are accessed through the local Flask server. The actual request body and response format depend on the backend implementation.

## 🎯 Project Objectives

- Apply Data Structures and Algorithms to a practical use case.
- Develop a restaurant management web application.
- Connect frontend functionality with a Flask backend.
- Manage food items and customer orders.
- Demonstrate kitchen queue processing and billing workflows.
- Practice file handling, API integration, debugging, and version control.

## 🚀 Future Enhancements

- Integrate SQLite or MySQL for structured database storage.
- Store payment records persistently.
- Add authentication for administrators and restaurant staff.
- Generate sales reports and analytics.
- Integrate a real payment gateway with appropriate security.
- Add automated testing and cloud deployment.

## 👥 Project Team

This project was developed collaboratively by the following team members:

1. **Atul Nandanwar**
2. **Ishan Jaiswal**
3. **Sai Pohekar**
4. **Om Pande**
5. **Ashwini Goswami**

## 🔗 Project Links

- **GitHub Repository:** [SmartServe – Restaurant Management System](https://github.com/atul-nandanwar/SmartServe-Restaurant-Management-System1)
- **Author's GitHub Profile:** [Atul Nandanwar](https://github.com/atul-nandanwar)

## 📄 License

No license has been specified for this project. Add an appropriate license if you intend to permit others to reuse, modify, or distribute the code.
