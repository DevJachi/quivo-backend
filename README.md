# Quivo Backend

Quivo is an **AI-powered job discovery platform** that helps users find relevant job opportunities by analyzing their resumes and matching them to real-time job listings.

This repository contains the **backend service** responsible for resume parsing, AI-powered keyword extraction, and job search aggregation.

---

## 🚀 What Quivo Does

At a high level, Quivo allows users to upload their resume and receive job recommendations tailored to their skills and experience.

At a system level, the backend:
1. Parses the uploaded resume
2. Extracts relevant keywords using AI
3. Uses those keywords to query a third-party job search API
4. Returns structured job results to the frontend

---

## 🧠 How It Works (Backend Flow)

1. **Resume Parsing**
   - Resumes are parsed using a resume parsing library to extract raw text content.

2. **AI Keyword Extraction**
   - The extracted resume content is sent to **Google Gemini (Flash 2.5)**.
   - Gemini identifies relevant skills, roles, and keywords from the resume.

3. **Job Search Aggregation**
   - The extracted keywords are used to query the **Adzuna Job Search API**.
   - Job listings are fetched and normalized for frontend consumption.

4. **Response Delivery**
   - Processed job results are returned to the frontend application.

---

## 🛠 Tech Stack

**Runtime & Framework**
- Node.js

**AI & APIs**
- Google Gemini (Flash 2.5)
- Adzuna Job Search API

**Libraries & Tools**
- Axios (HTTP requests)
- Resume parsing library

---

## 📦 Features

- Resume parsing and text extraction
- AI-powered keyword generation
- Real-time job search using third-party APIs
- Clean separation of concerns for scalability

---

## 🔐 Environment Variables

This project uses environment variables for configuration.

Create a `.env` file based on the example below:

```env
GEMINI_API_KEY=
ADZUNA_APP_ID=
ADZUNA_API_KEY=
```
## ⚙️ Setup & Run

Clone the repository

Install dependencies

``` npm install ```


Create a .env file and add required keys

Start the server

``` npm run dev ```

## 🔄 Performance & Future Improvements

The backend is currently deployed on **Render** and operates using a synchronous request-response flow.  
Because resume parsing, AI keyword extraction, and third-party job searches are handled within a single HTTP request cycle, responses may take several seconds under certain conditions.

### Planned Architecture Improvement

To improve performance and responsiveness, the following architectural changes are planned:

- Move resume parsing, AI processing, and job search logic into a **background worker**
- Decouple heavy computation from the main HTTP request lifecycle
- Introduce **WebSocket-based communication** between the backend and frontend
- Notify the frontend in real time once background processing is complete

This approach will:
- Reduce perceived latency
- Improve scalability under load
- Allow the API to remain responsive while long-running tasks are processed asynchronously

This refactor is part of ongoing work focused on building a more scalable and production-ready system.

