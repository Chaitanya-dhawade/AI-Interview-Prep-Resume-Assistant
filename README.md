
#  AI Interview Prep & Resume Assistant

An AI-powered full-stack web application that helps job seekers prepare for interviews and improve their resumes using **Google Gemini AI**.

The application analyzes a user's **resume, self-description, and target job description** to generate personalized interview preparation material, identify skill gaps, create technical and behavioral questions, suggest a preparation plan, and generate an ATS-friendly resume in PDF format.

##  Features

*  **AI-Powered Interview Preparation**

  * Uses Google Gemini AI to analyze candidate information.
  * Generates personalized interview preparation reports.

*  **Resume Analysis**

  * Upload your resume in PDF format.
  * Extracts resume content automatically using `pdf-parse`.
  * Compares your skills with the target job description.

*  **Skill Gap Analysis**

  * Identifies missing or weak skills.
  * Highlights areas that need improvement before the interview.

*  **Technical Interview Questions**

  * Generates job-specific technical questions.
  * Questions are tailored according to the candidate's resume and job requirements.

*  **Behavioral Questions**

  * Generates personalized HR and behavioral interview questions.

*  **Preparation Plan**

  * Provides a structured roadmap to help candidates prepare for their target role.

*  **AI Resume Generation**

  * Generates an ATS-friendly resume based on candidate information.
  * Converts the generated HTML resume into a professional PDF using Puppeteer.

*  **Secure Authentication**

  * JWT-based authentication.
  * Password hashing using bcrypt.
  * Protected API routes.
  * Token blacklisting during logout.

*  **Modern React Frontend**

  * React Router for navigation.
  * Context API for global state management.
  * Custom hooks for API and application logic.
  * Responsive UI with SCSS.

##  Tech Stack

### Frontend

* React.js
* React Router
* Axios
* SCSS

### Backend

* Node.js
* Express.js
* MongoDB
* Mongoose

### AI & Processing

* Google Gemini AI
* pdf-parse
* Puppeteer

### Authentication & Security

* JWT
* bcrypt
* Token Blacklisting
* Protected Routes

### Testing & Development

* Postman
* Git & GitHub
* VS Code

## 🏗️ System Architecture

```text
                    ┌─────────────────────┐
                    │      React UI       │
                    │  Components/Pages   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Context & Hooks   │
                    │   State Management   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │      Axios API      │
                    └──────────┬──────────┘
                               │
                               ▼
              ┌────────────────────────────────┐
              │        Express.js API          │
              │ Routes → Controllers → Services│
              └───────────────┬────────────────┘
                              │
               ┌──────────────┼──────────────┐
               ▼              ▼              ▼
        ┌────────────┐ ┌────────────┐ ┌─────────────┐
        │  MongoDB   │ │ Gemini AI  │ │ PDF Parser  │
        │  Database  │ │            │ │  + Puppeteer│
        └────────────┘ └────────────┘ └─────────────┘
```

##  Project Structure

```text
AI-Interview-Prep/
│
├── backend/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── middleware/
│   ├── services/
│   ├── utils/
│   └── server.js
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── context/
│   │   ├── hooks/
│   │   ├── services/
│   │   └── App.jsx
│   └── package.json
│
├── .gitignore
└── README.md
```

##  How It Works

### 1. Create an Account

Users register and log in securely using JWT authentication.

### 2. Upload Resume

The user uploads their resume as a PDF.

The backend processes the uploaded file using **Multer** and extracts the text using **pdf-parse**.

### 3. Provide Job Details

The user provides:

* Self-description
* Target job description
* Resume

### 4. AI Analysis

The extracted information is sent to **Google Gemini AI** with a structured prompt and JSON schema.

Gemini analyzes the candidate and generates:

* Skill gaps
* Technical questions
* Behavioral questions
* Interview preparation topics
* Personalized preparation plan

### 5. View Interview Report

The generated report is stored and displayed through the React frontend.

### 6. Generate Resume

The application can create an improved, ATS-friendly resume based on the candidate's information.

Puppeteer converts the generated HTML into a downloadable PDF.

##  Authentication Flow

```text
User Login
    │
    ▼
Credentials Validation
    │
    ▼
Password Verification
    │
    ▼
JWT Token Generated
    │
    ▼
Authenticated Requests
    │
    ▼
Protected API Routes
```

During logout, the JWT is added to a blacklist so that it cannot be reused even if the token has not expired.

## 🤖 Gemini AI Integration

The application uses prompt engineering and structured JSON output to make AI responses predictable and easier to process on the backend.

Instead of relying on unstructured AI responses, the system requests information in a predefined structure.

Example:

```json
{
  "skillGaps": [],
  "technicalQuestions": [],
  "behavioralQuestions": [],
  "preparationPlan": []
}
```

This makes the generated content easier to validate, store in MongoDB, and display in the frontend.

## 📄 Resume Processing Pipeline

```text
PDF Resume
     │
     ▼
Multer Upload
     │
     ▼
PDF Text Extraction
     │
     ▼
Resume Content
     │
     ▼
Gemini AI Analysis
     │
     ▼
Personalized Report
```

## 📝 Resume Generation Pipeline

```text
Candidate Information
          │
          ▼
       Gemini AI
          │
          ▼
   Resume HTML Content
          │
          ▼
       Puppeteer
          │
          ▼
     PDF Resume
```

##  API Testing

The backend APIs were tested using **Postman** before integrating them with the React frontend.

Tested functionality includes:

* User Registration
* User Login
* User Logout
* Authentication
* Resume Upload
* Interview Report Generation
* Resume Generation
* PDF Download
* Protected Routes

##  Environment Variables

Create a `.env` file inside the backend directory:

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
GEMINI_API_KEY=your_gemini_api_key
```

> Never commit your `.env` file or expose API keys publicly.

##  Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/AI-Interview-Prep.git

cd AI-Interview-Prep
```

### 2. Install Backend Dependencies

```bash
cd backend
npm install
```

### 3. Configure Environment Variables

Create a `.env` file and add your MongoDB, JWT, and Gemini credentials.

### 4. Start the Backend

```bash
npm run dev
```

### 5. Install Frontend Dependencies

Open another terminal:

```bash
cd frontend
npm install
```

### 6. Start the Frontend

```bash
npm run dev
```

The application will then be available through the local Vite development server.

##  Use Cases

This application can help:

* Students preparing for placements
* Freshers preparing for interviews
* Developers switching jobs
* Candidates targeting specific job descriptions
* Job seekers improving their resumes
* Candidates identifying missing skills

##  Future Improvements

* 🎤 AI-powered mock interview with voice interaction
* 📊 Interview performance analytics
* 🗣️ Speech-to-text interview practice
* ⭐ Resume scoring and improvement suggestions
* 📈 Progress tracking dashboard
* 🔔 Personalized preparation reminders
* 🌐 Support for multiple resume formats
* 💬 Real-time AI interview chatbot
* 📱 Mobile application

##  Project Highlights

The project focuses on combining **Generative AI with full-stack web development** to solve a practical problem faced by students and job seekers.

It demonstrates experience with:

* Full-stack development
* REST API development
* Generative AI integration
* Authentication and authorization
* File processing
* MongoDB database design
* React state management
* PDF generation
* API testing
* Clean and modular architecture

##  Author

**Chaitanya Dhawade**

AI & Data Science Graduate | Full-Stack Developer | Generative AI Enthusiast

---

⭐ If you found this project useful, consider giving the repository a star!
