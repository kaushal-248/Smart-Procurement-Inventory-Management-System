# Smart Procurement & Inventory Management System

A modern **SAP backend application** designed to streamline procurement and inventory operations by managing vendors, purchase requisitions, purchase orders, goods receipts, and inventory.

The project demonstrates enterprise backend development using **SAP ABAP, SAP HANA, ABAP Objects, CDS Views, RAP, and OData**.

---

## 📌 Project Overview

The **Smart Procurement & Inventory Management System** provides a structured backend solution for managing the complete procurement lifecycle:

```text
Vendor
   ↓
Purchase Requisition
   ↓
Approval
   ↓
Purchase Order
   ↓
Goods Receipt
   ↓
Inventory Update
   ↓
Procurement Analytics
```

The system focuses on implementing business logic within the SAP backend while exposing functionality through modern RESTful services.

---

## 🎯 Objective

The project demonstrates the development of a modern SAP backend application using:

* **SAP ABAP**
* **SAP HANA**
* **ABAP Objects**
* **ABAP Dictionary**
* **Open SQL / ABAP SQL**
* **Core Data Services (CDS)**
* **RESTful ABAP Programming Model (RAP)**
* **OData**

It applies enterprise backend concepts such as data modeling, business logic, API development, transactional processing, and procurement workflow management.

---

## 🚀 Features

### 👤 Vendor Management

* Create and maintain vendor records
* Manage vendor contact information
* Track vendor status
* Maintain vendor-related procurement data

### 📝 Purchase Requisition

* Create purchase requisitions
* Add multiple materials/items
* Specify required quantities
* Define required delivery dates
* Track approval status

### 🛒 Purchase Order

* Create purchase orders from approved requisitions
* Assign vendors
* Add PO items
* Calculate total order value
* Track purchase order status

### 📦 Inventory Management

* Maintain material/product information
* Track warehouse stock
* Record stock movements
* Update inventory after goods receipt
* Identify low-stock materials

### 🚚 Goods Receipt

* Record received materials
* Update inventory automatically
* Track received quantities
* Maintain goods receipt history

### 📊 Procurement Analytics

CDS-based analytical views can provide:

* Total procurement value
* Vendor-wise spending
* Pending purchase orders
* Inventory status
* Low-stock materials
* Monthly procurement trends

---

## 🏗️ System Architecture

```text
                    ┌─────────────────────┐
                    │   Fiori / Frontend  │
                    └──────────┬──────────┘
                               │
                              OData
                               │
                    ┌──────────▼──────────┐
                    │         RAP         │
                    │  Business Objects   │
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
                    │     CDS Views       │
                    │ Data & Analytics     │
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
                    │      ABAP OO        │
                    │   Business Logic    │
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
                    │      SAP HANA       │
                    │      Database       │
                    └─────────────────────┘
```

---

## 🗄️ Data Model

The system uses custom SAP database tables for procurement and inventory management.

### Core Tables

| Table        | Purpose                      |
| ------------ | ---------------------------- |
| `ZVENDOR`    | Vendor master data           |
| `ZPRODUCT`   | Product/material information |
| `ZWAREHOUSE` | Warehouse information        |
| `ZSTOCK`     | Inventory and stock data     |
| `ZPR_HEADER` | Purchase requisition header  |
| `ZPR_ITEM`   | Purchase requisition items   |
| `ZPO_HEADER` | Purchase order header        |
| `ZPO_ITEM`   | Purchase order items         |
| `ZGR_HEADER` | Goods receipt header         |
| `ZGR_ITEM`   | Goods receipt items          |

### Example Relationship

```text
ZVENDOR
   │
   └────────── ZPO_HEADER
                    │
                    └────────── ZPO_ITEM
                                   │
                                   └────────── ZPRODUCT
                                                  │
                                                  └──── ZSTOCK
```

---

## 🛠️ Technology Stack

| Technology                 | Usage                     |
| -------------------------- | ------------------------- |
| **SAP ABAP**               | Backend development       |
| **SAP HANA**               | Database                  |
| **ABAP Dictionary (DDIC)** | Data modeling             |
| **ABAP Objects**           | Business logic            |
| **Open SQL / ABAP SQL**    | Database operations       |
| **CDS Views**              | Data modeling & analytics |
| **RAP**                    | RESTful business services |
| **OData**                  | API exposure              |
| **SAP Fiori**              | Frontend integration      |

---

## 🔄 Procurement Workflow

```text
┌──────────────────────┐
│ Create Purchase      │
│ Requisition          │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Approval              │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Create Purchase      │
│ Order                 │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Vendor Processes     │
│ Purchase Order       │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Goods Receipt        │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Inventory Updated    │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Procurement          │
│ Analytics            │
└──────────────────────┘
```

---

## 🔌 API Layer

The application exposes backend functionality through **OData services**.

Example operations:

```http
GET    /PurchaseOrders
GET    /PurchaseOrders('100001')
POST   /PurchaseOrders
PATCH  /PurchaseOrders('100001')
DELETE /PurchaseOrders('100001')
```

The API layer can be consumed by SAP Fiori or other authorized frontend applications.

---

## 📊 CDS Views

Example CDS views planned for the project:

```text
ZC_PURCHASE_ORDER
ZC_VENDOR_SPEND
ZC_INVENTORY_STATUS
ZC_PROCUREMENT_ANALYTICS
```

These views provide reusable data models for transactional applications and analytics.

---

## 📁 Project Structure

```text
Smart-Procurement-Inventory/
│
├── README.md
│
├── src/
│   ├── abap/
│   │   ├── classes/
│   │   ├── interfaces/
│   │   ├── reports/
│   │   └── function_modules/
│   │
│   ├── cds/
│   │   ├── interface_views/
│   │   ├── consumption_views/
│   │   └── analytical_views/
│   │
│   └── rap/
│       ├── behavior_definitions/
│       ├── service_definitions/
│       └── service_bindings/
│
├── database/
│   ├── tables/
│   └── data_model.md
│
├── docs/
│   ├── architecture.md
│   ├── workflow.md
│   └── screenshots/
│
└── .gitignore
```

---

## 🔐 Security & Validation

The backend incorporates validation and business rules such as:

* Mandatory field validation
* Quantity validation
* Vendor validation
* Stock availability checks
* Purchase order status validation
* Authorization checks
* Error and exception handling

---

## 📈 Future Enhancements

Planned improvements include:

* SAP Fiori application
* Advanced procurement dashboards
* Role-based authorization
* Automated approval workflow
* Supplier performance scoring
* Inventory forecasting
* Low-stock notifications
* Integration with external procurement systems
* AI-assisted demand and inventory prediction

---

## 🎓 Learning Outcomes

Through this project, the following SAP backend concepts are demonstrated:

* ABAP programming
* ABAP Objects
* Internal tables
* Open SQL
* Database design
* SAP HANA
* ABAP Dictionary
* CDS Views
* Associations
* RAP
* Behavior definitions
* Service definitions
* Service bindings
* OData APIs
* Backend validation
* Enterprise application architecture

---

## 👨‍💻 Author

**Kaushal Chaudhary**

B.Tech — Artificial Intelligence & Data Science

Interested in **SAP ABAP, Backend Development, Data Engineering, and Enterprise Applications**.

---


