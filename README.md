💻 Laptop Request Catalog Item

📌 Project Overview
This project focuses on creating a **Laptop Request Service Catalog Item** in ServiceNow to streamline the process of requesting laptops within the organization.  
The solution provides employees with a **user-friendly interface** to submit requests, incorporates **dynamic form behavior**, and ensures **governance via update sets** for deployment across instances.

---

🎯 Problem Statement
Employees in the organization need a quick and efficient way to request laptops for work.  
The current process is manual and prone to delays, with no dynamic form behavior to guide users or ensure accurate data collection.  

Objective:
- Provide a dynamic catalog item for requesting laptops.  
- Improve accuracy of data collection.  
- Allow users to reset the form if needed.  
- Ensure changes are tracked and portable across ServiceNow instances.  

---

⚙️ Steps Performed

1. Create Local Update Set
- Navigated to **System Update Sets → Local Update Sets**.  
- Created update set named **“Laptop Request”**.  
- Made it the current update set to capture all changes.  

📷 Screenshot:  
![Local Update Set](screenshots/local_update_set.png)

---

2. Create Service Catalog Item
- Path: **Service Catalog → Maintain Items**.  
- Created a catalog item:  
  - **Name:** Laptop Request  
  - **Catalog:** Service Catalog  
  - **Category:** Hardware  
  - **Short Description:** Use this item to request a new laptop  

📷 Screenshot:  
![Catalog Item](screenshots/catalog_item.png)

---

3. Add Variables
Added the following variables to the catalog item:  

1. **Laptop Model** → Single Line Text (Order: 100)  
2. **Justification** → Multi Line Text (Order: 200)  
3. **Additional Accessories** → Checkbox (Order: 300)  
4. **Accessories Details** → Multi Line Text (Order: 400)  

📷 Screenshot:  
![Add Variables](screenshots/add_variables.png)

---

4. Create Catalog UI Policies
- Created policy: **Show Accessories Details**.  
- Condition: When **Additional Accessories = true**.  
- UI Policy Actions:  
  - **Variable:** Accessories Details  
  - **Mandatory:** True  
  - **Visible:** True  

📷 Screenshot:  
![Catalog UI Policies](screenshots/catalog_ui_policies.png)

---

5. Create UI Action (Reset Form)
- Path: **System Definition → UI Actions**.  
- Created UI Action with:  
  - **Table:** Shopping Cart (sc_cart)  
  - **Order:** 100  
  - **Action Name:** Reset form  
  - **Client:** Checked  

Script:
```javascript
function resetForm() {
    g_form.clearForm(); // Clears all fields in the form
    alert("The form has been reset.");
}
```

📷 Screenshot:
![UI Action](screenshots/ui_action.png)

---

6. Exporting Update Set

- Completed the Laptop Request Project update set.
- Exported to XML for migration to another instance.

📷 Screenshot:
![Changing State and Exporting Update Set](screenshots/changing_state.png)

---

7. Retrieving Update Set

- Imported XML in target instance via Retrieved Update Sets.
- Previewed and committed changes.
- Verified updates appeared correctly.

📷 Screenshot:
![Retrieve Update Set](screenshots/retrieve_update_set.png)

---

8. Test Catalog Item

- Opened Service Catalog → Hardware → Laptop Request.

- Verified:
  - Three variables shown initially.
  -When Additional Accessories is checked → Accessories Details field becomes visible and mandatory.

📷 Screenshot:
![Testing](screenshots/ordered_laptop.png)

---

🎥 Demo Video
[Click here to watch the demo](https://vimeo.com/1122468086)

---

 📊 Deliverables

- ServiceNow Configuration: Catalog item, UI policies, and UI actions.
- Update Set: Captures all changes for deployment.
- Screenshots: Evidence of catalog setup and dynamic form behavior.
- Demo Video: Recording of the complete process.
- Documentation: README.md and Word report.

---

🚀 Tools Used

- ServiceNow Developer Instance
- Service Catalog
- System Update Sets
- UI Policies & UI Actions

---

⚡ Conclusion

- The Laptop Request Catalog Item successfully streamlines the process of requesting laptops in the organization.
- By leveraging ServiceNow’s Service Catalog, dynamic form rules, and update set management, the solution:
  - Eliminates manual errors
  - Provides an intuitive user interface
  - Ensures portability across instances
  - Enhances employee satisfaction and efficiency
