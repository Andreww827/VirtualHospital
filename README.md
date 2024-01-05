# MetaCare
.
The Clinic Management System streamlines patient registration, doctor requests, and administrative tasks. Patients can manage records, appointments, prescriptions, and health packages, while doctors gain a comprehensive view of patient data. The system enhances communication through video calls, making healthcare accessible.


## Build Status 🔨

* The project is currently in development.
*   The admin need some imbrovements
*   Course Page and API' needs Pagagination.
*   The Unit tests needs modifications.
*   A CI/CD pipeline needs to be migrated to Jenkins.
*   A caching layer needs to be added to the application.
  
[![Build Status](Your_CI_Service_Build_Badge_Link)](Your_CI_Service_Build_Link)

The build status reflects the current state of continuous integration for this project. It helps ensure that the latest changes in the repository pass automated tests and maintain the integrity of the codebase.

Please note the following considerations:

- *Styles:* Prefer using external styles (CSS files) over inline styles for better separation of concerns. This practice promotes maintainability and readability in the long run.

- *Reusable Components:* Encourage the use of reusable components, such as AppBars, to enhance code modularity and maintainability. The project encourages encapsulating common functionalities in separate components for easier maintenance and future enhancements.

Addressing these considerations will contribute to a more robust and maintainable codebase.

## Code Style📜

The project follows a consistent coding style to ensure readability and maintainability. Please adhere to the following guidelines when contributing to the codebase:

 ### 1. File Organization

- *Import Statements:* Keep import statements organized at the top of each file.

 ### 2. Component Structure

- Ensure a clear and organized structure for React components.

 ### 3. React Hooks

- Leverage React Hooks (useState, useEffect, etc.) for managing state and side effects in functional components.

 ### 4. Axios Requests

- Make asynchronous requests using Axios within the useEffect hook.

 ### 5. Conditional Rendering

- Use conditional rendering to provide a better user experience during loading states.

 ### 6. State Naming

- Maintain consistency in naming conventions for states.

### 7. Error Handling

- Provide meaningful error messages and log errors for debugging purposes.
Feel free to refer to the existing codebase for examples of these conventions.

## Screenshots 🖵
here is the Patient's main page
![Patient_Home](https://github.com/advanced-computer-lab-2023/The-Team-Clinic/assets/128983223/bb39b842-2318-4120-a117-fadf8d97f942)

Don't miss our discounts on the Health Packages
![Health_Packages](https://github.com/advanced-computer-lab-2023/The-Team-Clinic/assets/128983223/9e867f58-e7b7-42d0-af85-d5b7a7ad8aab)

changing your password is one button away
![Change_Password](https://github.com/advanced-computer-lab-2023/The-Team-Clinic/assets/128983223/cdbd7943-6121-46d8-b79c-d0fcd51f1147)

for our dear admins meet your new homepage
![Admin_Home](https://github.com/advanced-computer-lab-2023/The-Team-Clinic/assets/128983223/e71380a6-b9e1-4987-aafc-6c9ff5756cd9)

admins, here is all registered users at one glance
![User_Management](https://github.com/advanced-computer-lab-2023/The-Team-Clinic/assets/128983223/e6b48f4f-48a0-4086-b9ba-40f9b82eeba3)

welcome to our true heroes
![Doctor_Home](https://github.com/advanced-computer-lab-2023/The-Team-Clinic/assets/128983223/3b252ffd-b2a5-4967-b416-4fe77aae2d5e)

organize and book your appointment
![Doctor_Apppointments](https://github.com/advanced-computer-lab-2023/The-Team-Clinic/assets/128983223/aa8778b5-155f-4993-8123-ea3ed13766fa)

need meds? don't worry we got you covered
![Store](https://github.com/advanced-computer-lab-2023/The-Team-Clinic/assets/128983223/a9c971c3-0b5e-4106-817f-6f4c97f0a07d)

rest well knowing we accept only the best
![Pharmacist_Requests](https://github.com/advanced-computer-lab-2023/The-Team-Clinic/assets/128983223/32d6622e-be09-4934-90ce-dc02dc7041fb)

## Tech/Framework used 🧰
Frontend Development:
React.js: A JavaScript library for building user interfaces. It's commonly used for creating dynamic and responsive frontend applications.

Backend Development:
Node.js: A JavaScript runtime built on Chrome's V8 engine. It allows developers to run JavaScript on the server side, facilitating the use of a single language for both frontend and backend.

Database:
MongoDB: A NoSQL database that stores data in flexible, JSON-like documents. It's suitable for applications with evolving schemas.

Real-time Communication:
Socket.IO: A library for real-time web applications. It enables bidirectional communication between clients and servers.

APIs:
Express (Node.js): A minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications.

Styling:
CSS Frameworks (Bootstrap, Material-UI): Pre-built CSS frameworks that provide styles and components for designing responsive and visually appealing user interfaces.

Version Control:
Git: A distributed version control system for tracking changes in source code during software development.

## Features✨
The system serves different type of users (Admin, patient , doctor,guest)

As a guest I can,
Register  as a patient 
submit a request to register as doctor
upload and submit required documents upon registrationas a doctor 

As an admin I can,
change my password
reset a forgotten password through OTP sent to email
accept a request for the registration of a doctor


As a patient I can,
upload/remove documents (PDF,JPEG,JPG,PNG) for my medical history
login with username and password
change my password
view registered family members
filter appointments by date/status
view uploaded health records
view all new and old prescriptions and their statuses (filled/ not filled)
view health package options and details
view the amount in my wallet
chat with a doctor
view the details of my selected prescription
start/end a video call with the doctor




As a doctor I can,
login with username and password
edit/ update my email, hourly rate or affiliation (hospital)
view and accept the employment contract
filter appointments by date/status
view uploaded health records 
view all new and old prescriptions and their statuses (filled/ not filled)
view a list of all my patients
filter patients based on upcoming appointments
receive a notification of my appointment on the system and by mail 
filter appointments by date or status (upcoming, completed, cancelled, rescheduled)
start/end a video call with the doctor
view the amount in my wallet

## Code Examples💻
### Example 1: How to Create a Patient(Backend)

    const patientModel = require('../Models/patients');
    const patients = require('../Models/patients');
    const walletModel = require('../Models/Wallet'); // Import the wallet model
    const bcrypt = require('bcrypt');

    exports.createPatient = async (req, res) => {
     const {
    fullName,
    email,
    dateOfBirth,
    gender,
    mobileNumber,
    emergencyContactFullName,
    emergencyContactMobileNumber,
    emergencyContactRelationToPatient,
    password, 
    username,
    } = req.body;
    try {
 
      const salt = await bcrypt.genSalt(); 
      const hashedPassword = await bcrypt.hash(password, salt);
      const newPatient= new patientModel({
        username,
        fullName,
        email,
        dateOfBirth,
        gender,
        mobileNumber ,
        emergencyContactFullName ,
        emergencyContactMobileNumber,
        emergencyContactRelationToPatient,
        password: hashedPassword,
      });

      const newWallet = new walletModel({
        patient: newPatient._id, // Assuming patientModel has an _id field
        balance: 0, // You can set an initial balance if needed
      });
      // Save the wallet
      const savedWallet = await newWallet.save();
      // Update the patient with the wallet information
      newPatient.wallet = savedWallet._id;
      const savedPatient = await newPatient.save();
      res.status(200).json(savedPatient)
    } catch (error) {
      console.error(error);
      res.status(400).json({ error: error.message })
    } };


### Example 2: How to add medicine to cart(Backend)
    exports.addToCart = async (req, res) => {
    try {
    const { patientId, medicationId, quantity } = req.body;

    // Find the patient's cart or create one if it doesn't exist
    let cart = await Cart.findOne({ patientId });

    if (!cart) {
      cart = new Cart({patientId, medications: [] });
    }

    // Check if the medication is already in the cart
    const existingMedication = cart.medications.find(
      (item) => item.medicationId.toString() === medicationId
    );

    if (existingMedication) {
      // If the medication is already in the cart, update its quantity
      existingMedication.quantity += quantity;
    } else {
      // If not, add the medication to the cart
      cart.medications.push({ medicationId, quantity });
    }

    // Save the cart
    const updatedCart = await cart.save();

    res.status(200).json(updatedCart);
    } catch (err) {
    res.status(500).json(err);
    }
    };

### Example 2: How to Change Password(Frontend)
    import React, { useEffect, useState } from 'react';
    import axios from 'axios';
    import Alert from '@mui/material/Alert';
    import { useNavigate } from 'react-router-dom';
    import { useParams } from 'react-router-dom';
    const isValidPassword = (password) => {
    const regex = /^(?=.[A-Z])(?=.\d).{4,}$/;
    return regex.test(password);
    };
    const handleCloseChangePassword = () => {
    setChangePasswordOpen(false);
    };

    const updatePassword = async (newPassword) => {
    try {
    // Replace '/api/reset-password' with your actual API endpoint
    const response = await axios.put('http://localhost:3000/changepassword', { id, newPassword });
    console.log(response.data);
    setAlertType('success');
    setAlertOpen(true);
    } catch (error) {
    console.error('Error updating password:', error);
    setAlertType('error');
    setAlertOpen(true);
    }
    };

    const handleOpenChangePassword = () => {
    setChangePasswordOpen(true);
    };


## Installation 📥

Follow these steps to set up the project locally:

### Prerequisites

Make sure you have the following installed on your machine:

- [Node.js](https://nodejs.org/) 
- [npm](https://www.npmjs.com/) 
- [Git](https://git-scm.com/)

### Clone the Repository
git clone https://github.com/advanced-computer-lab-2023/The-Team-Clinic.git

### Install Dependencies

Navigate to the backend directory:
bash
cd backend


Install dependencies:

bash
npm Install


Frontend

Navigate to the frontend directory:
bash
cd frontend

Install dependencies:

bash
npm Install


###Run the Application

bash
cd backend
npm start

The backend server will run at http://localhost:3000.
bash
cd frontend
npm start


Visit http://localhost:3001 in your web browser to view the application.

## API Reference 📚
### Base URL
The base URL for all API endpoints is http://localhost:3000/.
### medsRoutes
http://localhost:3000/meds/

### DoctorsRouts
http://localhost:3000/doctors

### PatientsRoutes
http://localhost:3000/patients

### AppsRoutes 
http://localhost:3000/apps

### Health-PackagesRoutes
http://localhost:3000/health-packages

### Doctors-RequestsRouts
http://localhost:3000/api/drReq

### Health-RecordsRoutes
http://localhost:3000/HealthRecords

### PrescriptionRoutes
http://localhost:3000/Prescription

### AdminRoutes
http://localhost:3000/admin

### LoginRoutes
http://localhost:3000/login

### WalletRoutes
http://localhost:3000/wallet

### WalletdocRoutes
http://localhost:3000/walletDoc

### Cart
http://localhost:3000/cart

### AddressRoutes
http://localhost:3000/address

### MedhistoryRoutes
http://localhost:3000/medHistory

### EmploymentContract
http://localhost:3000/employmentContract

### OrderRoutes
http://localhost:3000/Order



## Tests 🧪
The api routes were tested using postman,
Postman is an application used for API testing. It is an HTTP client that tests HTTP requests, utilizing a graphical user interface, through which we obtain different types of responses that need to be subsequently validated. Postman offers many endpoint interaction methods. The following are some of the most used, including their functions:
*   GET: Obtain information
*   POST: Add information
*   PUT: Replace information
*   PATCH: Update certain information
*   DELETE: Delete information
& And we tested the behavior of our routes and if they produce the correct status code and response according to our project flow .you will fine the main routes in app.js. and the sub ones in each parts routes folder in the backend. For example, you will find something  like this in the app.js “app.use('/patients', PatientRoutes);” and something like this in the routes file of patients” router.get('/', PatientController.getPatient);” so you test like this.      http://localhost:3000/patients/  using “get” in postman. In this way you can test almost all aspects of the project for example here patient registration by getting all patients.



## How to use
 ### To run Backend
 -cd backend
 -cd server
 -node app

 ### To run Frontend
 -cd frontend
 -npm start

## Contribute
 We welcome contributions via pull requests! To contribute code, follow these steps:

1. Fork the repository to your GitHub account.
2. Create a new branch for your feature or bug fix: git checkout -b feature-branch.
3. Write tests for your changes if applicable.
4. Commit your changes with a clear and descriptive commit message.
5. Push your branch to your fork: git push origin feature-branch.
6. Open a pull request on the [main repository](https://github.com/advanced-computer-lab-2023/The-Team-Clinic.git) with a clear title and description of your changes.

 ## Credits
 The main resources that helped us in our implementation:
https://www.youtube.com/@NetNinja
https://mui.com/
https://react-bootstrap.github.io/getting-started/introduction/
https://www.npmjs.com/            MERN Stack Crash Course Tutorial
• MERN stack authentication + profile                         MERN Auth Tutorial

 ## Lisence
- [Stripe](https://stripe.com): Payment processing library (License: Apache 2.0)
- [Axios](https://axios-http.com): HTTP client for making requests (License: MIT)
- [FontAwesome](https://fontawesome.com): Icons used in the project (License: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/))
- [React](https://reactjs.org): JavaScript library for building user interfaces (License: MIT)
- [Node.js](https://nodejs.org): A JavaScript runtime (License: MIT)
- [MongoDB](https://www.mongodb.com): A NoSQL database (License: Server Side Public License (SSPL))
- [Socket.IO](https://socket.io): A library for real-time web applications (License: MIT)
- [Express (Node.js)](https://expressjs.com): A minimal and flexible web application framework (License: MIT)
- [Bootstrap](https://react-bootstrap.github.io): CSS framework (License: MIT)
- [Material-UI](https://material-ui.com): CSS framework (License: MIT)
- [Git](https://git-scm.com): Distributed version control system (License: GNU General Public License (GPL))
.