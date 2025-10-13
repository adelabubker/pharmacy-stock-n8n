# 💊 Pharmacy Stock Management Workflow (n8n)

## 🧠 Overview
This project automates **pharmacy stock management** using:

- **Telegram Bot** – receive item names and quantities interactively  
- **Google Sheets** – store and update inventory data  
- **n8n** – handle automation, validation, and user feedback  

Example messages to the bot:  
Panadol 5
Amoxicillin -3



The workflow updates the item quantity in Google Sheets, logs who made the change and when, and sends a confirmation message back via Telegram. Negative quantities are supported for stock deductions.

---

## ⚙️ Workflow Components

| Component | Description |
|------------|--------------|
| **Telegram Trigger** | Listens for messages from the Telegram bot |
| **Code Node (JavaScript)** | Parses and validates the input (item name + quantity) |
| **Google Sheets Nodes** | Reads, updates, and appends data in Google Sheets |
| **Metadata Nodes** | Records operation details such as user, timestamp, and operation type |
| **Telegram Message Nodes** | Sends confirmation or error messages back to the user |

---

## 📊 Google Sheets Structure

### **Sheet1 – Inventory Table**
| Item_Name | Amount | ID (optional) |

### **Sheet2 – Operation Log**
| Date | User | Operation | Item | Quantity |

---

## 🚀 How to Use

1. Import the provided `.json` file into your **n8n** instance.  
2. Connect credentials for:
   - **Telegram API**
   - **Google Sheets (OAuth2)**  
3. Replace the sample Google Sheet ID with your own Sheet URL.  
4. Activate the workflow.  
5. Send messages to your Telegram bot, e.g.:
Amoxicillin 10
Amoxicillin -3

n8n will automatically:

- Update the stock count in Google Sheets  
- Log each transaction with user details and timestamps  
- Reply in Telegram with confirmation or errors  

---

## 🖼️ Workflow Diagram

```text
[ Telegram User ]
     ↓
[ Telegram Trigger Node ]
     ↓
[ Code Node (Parse & Validate) ]
     ↓
[ Google Sheets (Read/Update) ]
     ↓
[ Add Metadata + Log Entry ]
     ↓
[ Send Confirmation Message via Telegram ]


🧰 Tech Stack

n8n (Workflow automation)

Telegram Bot API

Google Sheets API

JavaScript (for parsing and validation)

🧑‍💻 Author

Project: Automating Pharmacy Stock Management with n8n
Created by: Adel Bassam
linkedin: https://www.linkedin.com/in/adel-abubker/
