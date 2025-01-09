Tags: [[Active Directory]] [[Labs]] #Active_Directory 


## Project Overview
### **Scenario: Galaxy Dynamics Corporation (GDC)**  
**Industry**: Technology and Aerospace  
**Description**:  
Galaxy Dynamics Corporation (GDC) is a multinational technology and aerospace company specializing in satellite communications, defense systems, and software development. With headquarters in **San Francisco**, GDC has regional offices across the globe and employs thousands of people in diverse roles.

The company uses Active Directory to manage its IT infrastructure, user accounts, and access permissions. You’re an IT administrator tasked with creating and managing an Active Directory setup that mirrors GDC’s organizational structure.

---

### **Active Directory Structure**

#### **Top-Level Organizational Units (OUs)**
1. **Corporate**  
2. **IT Department**  
3. **Engineering**  
4. **Human Resources**  
5. **Finance**  
6. **Marketing**  
7. **Sales**  
8. **Regional Offices**  

---

#### **Sub-OUs and Users**

**1. Corporate**  
- Sub-OUs:  
  - Executives  
  - Legal  
- Example Users:  
  - John Doe (CEO)  
  - Jane Smith (General Counsel)

**2. IT Department**  
- Sub-OUs:  
  - System Administrators  
  - Help Desk  
  - Cybersecurity  
- Example Users:  
  - Sarah Lee (SysAdmin)  
  - Mark Taylor (Help Desk Technician)  

**3. Engineering**  
- Sub-OUs:  
  - Aerospace Division  
  - Software Division  
  - Research & Development  
- Example Users:  
  - Alex Johnson (Aerospace Engineer)  
  - Mia Patel (Software Developer)  

**4. Human Resources**  
- Sub-OUs:  
  - Recruitment  
  - Employee Relations  
- Example Users:  
  - Emma White (Recruiter)  
  - Ethan Green (HR Manager)

**5. Finance**  
- Sub-OUs:  
  - Accounting  
  - Payroll  
- Example Users:  
  - Olivia Brown (Accountant)  
  - Liam Black (Payroll Specialist)

**6. Marketing**  
- Sub-OUs:  
  - Social Media  
  - Branding  
  - Public Relations  
- Example Users:  
  - Emily Adams (Social Media Manager)  
  - Noah Davis (PR Specialist)

**7. Sales**  
- Sub-OUs:  
  - North America  
  - Europe  
  - Asia-Pacific  
- Example Users:  
  - Michael Miller (Sales Rep, North America)  
  - Sophie Martinez (Sales Rep, Europe)

**8. Regional Offices**  
- Sub-OUs:  
  - North America  
  - Europe  
  - Asia-Pacific  
  - South America  
- Sub-sub-OUs:  
  - IT  
  - HR  
  - Engineering  
- Example Users:  
  - Chris Thompson (IT Admin, Europe)  
  - Ava Brown (HR, Asia-Pacific)

---

### **Group Policy Applications**
- **Corporate OU**:  
  - Strict security policies, such as requiring smart card logins for Executives.  

- **IT Department OU**:  
  - Full access to tools like PowerShell and remote management tools.  

- **Finance OU**:  
  - Enforce encryption on all shared finance folders.  

- **Marketing OU**:  
  - Set desktop backgrounds to the company logo and restrict certain websites.  

- **Regional Offices OUs**:  
  - Apply location-specific policies, such as time zone settings and language preferences.  

---

### **Shared Folders and Permissions**
1. **Engineering**:  
   - Shared Folder: **\\GDC-Files\Engineering**  
   - Access: Aerospace Division and Software Division only.  

2. **HR**:  
   - Shared Folder: **\\GDC-Files\HR**  
   - Access: HR staff only, with separate folders for Recruitment and Employee Relations.  

3. **Finance**:  
   - Shared Folder: **\\GDC-Files\Finance**  
   - Access: Restricted to Accounting and Payroll groups.

---

This setup provides a large, complex environment where you can practice managing users, creating and linking GPOs, and simulating real-world scenarios like cross-department access and troubleshooting.