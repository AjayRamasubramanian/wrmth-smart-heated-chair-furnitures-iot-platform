# Wrmth – Smart Heated Chairs and Furnitures IoT Platform  
A Complete Guide to Features, APIs, and System Capabilities

Wrmth is a smart heated furniture platform that allows users to control the temperature, lighting, power, and comfort features of Wrmth heated chairs. The platform includes a secure web portal, mobile app functionality, OTA firmware updates, and real-time chair control through modern communication technologies such as Bluetooth and more.

This document provides a complete overview of system features, API endpoints, user roles, permissions, and OTA update flow. It also aims to help users, integrators, and partners understand how the Wrmth smart heated chair ecosystem works.

---

## 1.0 Overview

Wrmth provides a unified platform for managing smart heated chairs across organizations, homes, and workplaces.  
Through the web app and mobile app, users can:

- Control heating levels  
- Manage lighting  
- Power the chair on/off  
- View chair states in real time  
- Assign users and groups  
- Manage organizations and roles  
- Perform OTA firmware updates over Bluetooth  

This README serves as a complete guide to how the platform works at a functional level.

---

## 2.0 Summary (Purpose)

This document gives a structured overview of how Wrmth smart heated chairs work, how users interact with them, and what system functionalities are available.  
It summarizes:

- Core features  
- Role-based permissions  
- API endpoints  
- Group and user management  
- OTA firmware update flow  

The content ensures that anyone exploring Wrmth technology can understand its capabilities clearly.

---

## 3.0 Materials Required

To use or understand the Wrmth smart furniture platform, users will interact with:

- A Wrmth smart heated chair  
- A mobile app (iOS/Android) for Bluetooth-based setup and OTA firmware updates  
- A web application for organization-, user-, and chair-management  
- Access credentials for login  
- Internet connection for real-time updates and cloud syncing  

---

## 4.0 Key Features of the Wrmth Platform

### **Common Features for All Users**
- Secure login & logout  
- View and control assigned chair settings:  
  - **Temperature**  
  - **Light**  
  - **Power**  
- Real-time chair updates  
- View device status  
- Update personal profile  

---

## 5.0 Role-Based Functionality

### **Employee**
- Access only to groups they are assigned to  
- View and control chairs within their groups  
- View real-time chair status  

---

### **Manager**
Includes **all Employee features**, plus:

- Create & manage employees  
- Create and manage groups  
- Assign chairs to groups  
- Control and monitor group settings  

---

### **Super User (Admin)**
Includes **all Manager features**, plus:

- Create organizations and add users  
- Assign roles (SuperUser, Manager, Employee)  
- Modify default permissions for Manager and Employee roles  
- Override permissions for individual Managers or Employees  
- Full access to all chairs, groups, and users  

---

## 6.0 Permissions Summary

- **Manage Groups**  
  Create, edit, delete groups and assign chairs/users.

- **Add Chairs**  
  Add Wrmth chairs to an organization via mobile app.

- **Manage Users**  
  Create and update employees and managers.

- **Control Chairs**  
  Rename chairs and change temperature, light, and power settings.

These permissions can be customized by Super Users.

---

## 7.0 Role–Permission Matrix  
*(Default permissions; Super Users can modify these later.)*

| Action | Super User | Manager | Employee |
|--------|------------|----------|-----------|
| Sign In | Yes | Yes | Yes |
| Add Chairs | Yes | No | No |
| Manage Users | Yes | Yes (Employees Only) | No |
| Manage Groups | Yes | Yes | No |
| Transfer Roles | Yes | No | No |
| Define Default Role Permissions | Yes | No | No |
| Control Chairs | Yes | Yes | Yes (Only assigned groups) |

---

## 8.0 API Reference  
All APIs use structured request validation and access control.  
Below is the complete list of available API endpoints.

---

### **8.1 Authentication APIs**

| Endpoint | Method | Description |
|---------|--------|-------------|
| `/signup` | POST | Sign up a new user |
| `/invite` | GET | Invite a user via link |
| `/userPasswordReset` | GET | Trigger password reset flow |
| `/register` | POST | Register user via invite |
| `/login` | POST | Log in to the system |
| `/accessToken` | POST | Generate new access token |
| `/logout` | POST | Logout user |
| `/sendResetPasswordEmail` | POST | Send password reset email |
| `/resetPasswordVerify` | GET | Verify password reset link |
| `/resetPassword` | POST | Reset user password |

---

### **8.2 Group APIs**

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/getAllGroups` | GET | List all groups |
| `/addGroup` | POST | Create a group |
| `/editChairs` | PUT | Modify chairs in group |
| `/editUsers` | PUT | Modify group members |
| `/renameGroup` | PUT | Rename a group |
| `/renameChair` | PUT | Rename a chair |
| `/deleteGroup` | DELETE | Delete a group |

---

### **8.3 Role APIs**

| Endpoint | Method | Description |
|---------|--------|-------------|
| `/edit` | PUT | Edit role permissions |
| `/allRoles` | GET | Get all roles |
| `/getRolePermissions` | GET | Get permissions of a role |

---

### **8.4 User APIs**

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/profile` | GET | View user profile |
| `/getAllUsers` | GET | Get all users in organization |
| `/getUserPermissions` | GET | Fetch user-level permissions |
| `/createUser` | POST | Create new user |
| `/editProfile` | PUT | Edit user profile |
| `/editUserRole` | PUT | Update user role |
| `/editUserPermissions` | PUT | Override user permissions |
| `/deleteUser` | DELETE | Delete user |
| `/uploadUserPicture` | PUT | Upload user profile picture |
| `/deleteUserPicture` | DELETE | Remove user profile picture |

---

### **8.5 WebSocket Token API**

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/request-ws` | POST | Generate WebSocket token for real-time connection |

---

## 9.0 OTA Firmware Update Flow

Wrmth supports secure Over-The-Air (OTA) firmware updates for its heated chairs using Bluetooth Low Energy (BLE).

### **OTA Update Steps**
1. Smartphone app detects Wrmth chair via BLE scan.  
2. The chair responds with its current firmware version.  
3. The mobile app compares:
   - chair firmware version  
   - latest firmware version stored in the app  
4. If versions do not match, the app sends the new firmware to the chair over Bluetooth.  
5. The chair installs the firmware and restarts.

---

