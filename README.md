# NEXUS JAM – Hackathon Registration Form

A sleek and responsive **HTML, CSS, and JavaScript** registration form designed for the **NEXUS JAM Hackathon** hosted by **Mangayarkarasi College of Engineering**.  
The form collects participant details, validates input, and includes a **Google Pay (UPI) payment integration** .

---

## 🌟 Features

- **Responsive UI** – Works on desktop and mobile devices.
- **Modern Design** – Gradient backgrounds, smooth animations, and clean form styling.
- **Form Validation** – Ensures required fields are filled before submission.
- **Google Pay Integration** – Redirects to UPI payment link (dummy UPI ID provided for testing).
- **Success & Error Messages** – Displays user-friendly alerts after submission.
- **Google Apps Script Ready** – Can be connected to store data in Google Sheets.

---
## 📱Screenshots

![form](https://github.com/user-attachments/assets/ea91365b-9434-4faa-9035-fe7e08a473cd)
**The Values in Registration Form will be updated in the google sheet**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c61afc44-d5b1-43fc-8f92-518581dcc74e" />


## 📋 Form Fields

- **First Name** 
- **Last Name** 
- **Email Address** 
- **Phone Number** 
- **College/University** 
- **Year of Study** 
- **Department** 
- **Programming Experience** 
- **Technical Skills**
- **Transaction ID** 

---

## 💳 Payment Details

- **Registration Fee:** ₹100 per participant
- **UPI ID:** `hackathon@nexusjam` *(dummy for testing)*
- **Payment Method:** Google Pay (UPI link opens payment app on mobile devices)

---

## 🚀 How It Works

1. **Fill in all required fields** in the registration form.
2. **Click the “Pay with Google Pay”** button to initiate payment.
3. Enter your **transaction ID** in the form.
4. **Click “Register for Hackathon”** to submit your details.
5. The form sends data to your configured **Google Apps Script URL**.

---

## 📂 Project Structure
```bash
📦 nexus-jam-registration
├── index.html 
```
---

## 🔧 Setup Instructions

1. **Clone the repository**
```bash
   git clone https://github.com/your-username/nexus-jam-registration.git
   cd nexus-jam-registration
```

2. **Configure Google Apps Script**
- Create a new Google Apps Script linked to a Google Sheet.
- Add a script to handle form submissions.
```bash
function doPost(e) {
  try {
    var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
    
    // Parse form data
    var data = e.parameter;

    // Append a new row
    sheet.appendRow([
      new Date(),                  // Timestamp
      data.firstName || "",
      data.lastName || "",
      data.email || "",
      data.phone || "",
      data.college || "",
      data.year || "",
      data.department || "",
      data.experience || "",
      data.skills || "",
      data.transactionId || ""
    ]);

    // Return success response
    return ContentService
      .createTextOutput(JSON.stringify({ result: 'success', row: sheet.getLastRow() }))
      .setMimeType(ContentService.MimeType.JSON);
  } catch (error) {
    // Return error response
    return ContentService
      .createTextOutput(JSON.stringify({ result: 'error', error: error.toString() }))
      .setMimeType(ContentService.MimeType.JSON);
  }
}
```
- Deploy as a Web App and get the script URL.

Replace: javascript
```bash
const GOOGLE_SCRIPT_URL = 'YOUR_GOOGLE_SCRIPT_URL_HERE';
```
with your actual URL.

3. **Test the form**
- Open index.html in your browser.
- On mobile, click Pay with Google Pay to test payment redirection.
- On desktop, payment will not open unless an appropriate handler is installed.

### 📱 Mobile vs Desktop Behavior
- Mobile: Clicking “Pay with Google Pay” opens the payment app.
- Desktop: Payment redirection might not work since Google Pay is not supported natively on laptops/desktops.

### ⚠️ Note
- The current UPI ID is a dummy ID for demonstration purposes.
- Replace it with your actual UPI ID for production use.
- This form does not store data unless the Google Apps Script integration is set up.
## 🤝 Contributing
 🎉Contributions are welcome! 

**Live Demo:** [https://nexus-jam-registration.netlify.app/]
