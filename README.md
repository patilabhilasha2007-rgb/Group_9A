# Group_9A
# **Digital Queue Management System for Health Camps**

This is a good full-stack student project because it solves a real-world problem and allows you to demonstrate frontend development, backend development, database management, and multiple-user login.

Let's plan it step by step. We will first finalize the project structure, features, modules, database design, and development phases. **We won't start coding until the planning is clear.**

[OPD Queue Management System for Hospitals | Apex Cura](https://images.openai.com/static-rsc-4/nfazZVXkMsRth7yHtKYnWL3948ZxqoQssrCh5jv-xn-NiX5eTo0Gl0GXmCxFBD1MleDw9cXG6PXVdh9HWhB-LRjf6NCqJubE4UmGQ_rhSneM1ba3IgOcHD2C6JpIQSMFGSpjSjEMNkpPXhJqlvGq0VZBAKqdiwWtbZIW7_fYgtg?purpose=inline)

[apexcura.com](https://www.apexcura.com/products/apex-opd-queue-system?utm_source=chatgpt.com)

## **1. Project overview**

**Project title:** Digital Queue Management System for Health Camps

**Project idea:**

In health camps, many patients come for checkups at the same time. They usually wait in long queues, and managing patients manually becomes difficult.

Our system will digitize this process.

When a patient registers for a health camp, the system generates a unique queue token. Patients can see their token number and queue status. Doctors or camp administrators can manage the queue and call patients one by one.

**Main objective:**

To reduce waiting confusion, manage patient flow efficiently, and make health camp operations easier using a lightweight web application.

## **2. Technology stack**

We will use only the technologies you mentioned.

| Technology | Purpose                     |
| ---------- | --------------------------- |
| HTML       | Webpage structure           |
| CSS        | Design and styling          |
| JavaScript | Frontend functionality      |
| Node.js    | Backend runtime             |
| Express.js | Backend server and APIs     |
| JSON       | Lightweight data storage    |
| Localhost  | Run the application locally |

**Database decision:** We will initially use JSON files instead of MongoDB or MySQL.

Why?

- Easy to understand for students.
- No separate database installation.
- Lightweight.
- Data can be stored in JSON files.
- Suitable for a small demonstration project.

One important point: JSON files are suitable for a small local project, but they are not ideal for simultaneous production use by many users. We will design the backend to control data updates and avoid duplicate token generation.

## **3. User roles – Multiple login system**

Our project will have three different user roles.

**1. Admin**

Controls the entire health camp system

Admin features:

- Admin login.
- Add and manage doctors.
- View registered patients.
- Monitor all queue tokens.
- View completed and pending patients.
- Manage health camp details.

  **2. Doctor**

  Manages patient consultations

  Doctor features:
- Doctor login.
- View assigned patients.
- View current token number.
- Call the next patient.
- Mark patient as completed.
- Skip a patient if necessary.

  **3. Patient**

  Registers and checks queue status

  Patient features:
- Patient registration.
- Patient login.
- Select available doctor or department.
- Receive a unique token number.
- View current serving token.
- Check their waiting status.
- View their queue position.

## **4. Main modules of the project**

We can divide the complete application into six modules.

| Module             | Function                          |
| ------------------ | --------------------------------- |
| Authentication     | Login and registration            |
| Admin dashboard    | Manage camp, doctors and patients |
| Patient management | Store patient details             |
| Token generation   | Generate unique queue tokens      |
| Queue management   | Call next, skip and complete      |
| Queue display      | Show current and upcoming tokens  |

## **5. How the complete system works**

Let's understand the actual workflow.

## **System workflow**

**Patient Registration**

Patient enters personal and contact details

**Token Generation**

System assigns a unique token number

**Patient Joins Queue**

Patient waits for their turn

**Doctor Calls Next Token**

Doctor attends the next patient

**Consultation Completed**

Doctor marks patient as completed

## **6. Database planning using JSON**

We can maintain separate JSON files inside a `database` folder.

| JSON file     | Information stored               |
| ------------- | -------------------------------- |
| users.json    | Login credentials and user roles |
| patients.json | Patient information              |
| doctors.json  | Doctor details                   |
| camps.json    | Health camp information          |
| tokens.json   | Token numbers and queue status   |

Example of the planned patient record:

```
{
  "patientId": "P001",
  "name": "Rahul",
  "age": 25,
  "gender": "Male",
  "phone": "9876543210",
  "campId": "C001"
}
```

Example of the planned token record:

```
{
  "tokenId": "T001",
  "tokenNumber": 1,
  "patientId": "P001",
  "doctorId": "D001",
  "status": "Waiting"
}
```

Possible token statuses:

- Waiting
- Serving
- Completed
- Skipped

We will also ensure that token numbers are unique within each doctor/department queue for a particular camp.

## **7. Proposed project folder structure**

This is how we will organize the project.

```
Health-Camp-Queue-System/
│
├── server.js
├── package.json
│
├── database/
│   ├── users.json
│   ├── patients.json
│   ├── doctors.json
│   ├── camps.json
│   └── tokens.json
│
├── routes/
│   ├── authRoutes.js
│   ├── adminRoutes.js
│   ├── doctorRoutes.js
│   └── patientRoutes.js
│
├── controllers/
│   ├── authController.js
│   ├── queueController.js
│   └── patientController.js
│
├── middleware/
│   └── authMiddleware.js
│
└── public/
    ├── index.html
    ├── login.html
    ├── register.html
    ├── admin.html
    ├── doctor.html
    ├── patient.html
    ├── queue.html
    │
    ├── css/
    │   └── style.css
    │
    └── js/
        ├── login.js
        ├── admin.js
        ├── doctor.js
        └── patient.js
```

## **8. UI design planning**

We should keep the interface simple, clean and professional.

[Hospital Management System Dashboard by Nazar Becks on Dribbble](https://images.openai.com/static-rsc-4/n2A97eIyyzz5Y4WWUxNvg-79cYq2OeRCNsmP7XWGBBsUvpQ_8mbbpde4Kn7y1Anyv68mP7PlmD5pETxIdWHrgBhs5nqnnS5pXxzqZDsOxg18P7zgEumeWkzvG766ZrinK16GCmmJ0QL7WDDTqjM1iDB6_0GmevkznEyOx1Mm1OE?purpose=inline)

**Admin dashboard**

Patient count, doctor count, waiting list and completed consultations.

[Drittech — Healthcare Automation, AI & Integration for Clinics and Hospitals](https://images.openai.com/static-rsc-4/rTLbLatgrriyekqPqmzswIG3rs9wVwfeexluDgbLIkgc-cVyqbleqQLTJ-NEMbCa54bGpUx29tZtnqhjAUw84ei57QLZbPoQl99ZvfKgsIy1kqnmXinpLiM7Uhp_EKZdSqc7mQjFnxlcGHnS6AmrbDt0AGBqibNTQSgNvMcn34s?purpose=inline)

**Doctor dashboard**

Current token, next patient and consultation controls.

[Patient Registration Projects :: Photos, videos, logos, illustrations and branding :: Behance](https://images.openai.com/static-rsc-4/vt0ufDsNtphEGsfB8tSNfVDDaNWsPGATvmH0ePiJXncThwWbnc9jtPf8iHOgcIJEai96i8bt0i50zHt1OV-2evZ57rfKPKBa8IlMiYuL1r9ec358NjxXs2CndRSw5uKkr4o77y6GVEGQyVA00Lt-o2Me0KU8-0dB0EkWtUsaKLE?purpose=inline)

**Patient registration**

Simple form to register for a health camp.

[Hospital Waiting Room Digital Signage | Pickcel](https://images.openai.com/static-rsc-4/MU3Lmnkqc_rQApRcrFvAh3QS1bLL_HsA1y_fA-0Fw3UEqk1LH75XyQDMe_v43aAIQohQhATEAjKW2x5mWnnL3KRi2wBtuYuLIjYPTHxklLaBuC_-zFSG80-eOPzQTMrsvPPgobfDSh2aTvdGM1_mnEIo4aUhr-yEUkk889Ka0ok?purpose=inline)

**Queue display**

Large token number and waiting patient information.

## **9. Development plan – Step by step**

We will develop the project in the following order.

| Phase    | Work to complete                       |
| -------- | -------------------------------------- |
| Phase 1  | Project setup and folder creation      |
| Phase 2  | Design login and registration pages    |
| Phase 3  | Implement multiple-user authentication |
| Phase 4  | Create admin dashboard                 |
| Phase 5  | Create patient registration            |
| Phase 6  | Implement token generation             |
| Phase 7  | Create doctor dashboard                |
| Phase 8  | Implement queue management             |
| Phase 9  | Create live queue display              |
| Phase 10 | Testing with multiple users            |

**Important:** For the first version, we can use periodic JavaScript polling to refresh the queue every few seconds. This avoids introducing WebSockets and keeps the project lightweight.

## **10. Additional features (optional)**

After completing the basic project, we can add:

- Estimated waiting time.
- Search patient by token number.
- Filter patients by doctor.
- Daily patient statistics.
- Print token receipt.
- Queue history.
- Priority queue for emergency cases.

For a student project, I recommend completing the basic features first and adding only two or three advanced features.

# **11. Let's finalize the project plan**

Before starting Phase 1, I want to finalize three important design decisions.

**1. How many user roles should we implement?**

2 roles – Admin and Patient

3 roles – Admin, Doctor and Patient (Recommended)

**2. How should the queue work?**

One common queue for the entire health camp

Separate queue for each doctor (Recommended)

Separate queue for each department

**3. How should login work?**

One login page with automatic role-based redirection (Recommended)

Separate login pages for Admin, Doctor and Patient

**4. Which extra features would you like?**

You can select more than one.

Waiting time

Print token

Patient search

Daily statistics

Queue history

Confirm project plan

**My recommendation:** Three roles, separate queues for each doctor, one common role-based login page, and a simple blue-and-white interface.

Once we finalize these decisions, we will start with Phase 1: setting up Node.js, VS Code, Express.js and the project folders. I'll explain what each file does and guide you step by step so that you understand the project rather than just copying code.
