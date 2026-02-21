<p align="center">
  <img src="./img.png" alt="Project Banner" width="100%">
</p>

# [Project Name] 🎯

## Basic Details

### Team Name: Slaybyte

### Team Members
- Member 1: Aleesha Sujith Abraham - Muthoot Institute of Technology and Science
- Member 2: Gowri Krishna - Muthoot Institute of Technology and Science

### Hosted Project Link
[mention your project hosted link here]

### Project Description
Impact Focused
  Women creators face thousands of sexist comments daily, with no fast way to identify, document, or report them. Detoxify uses machine learning to instantly scan YouTube comment sections, flag harmful content, and package evidence for reporting — turning a painful manual process into a 10 second task.

### The Problem statement
  Women creators face thousands of sexist comments daily, with no fast way to identify, document, or report them. Detoxify uses machine learning to instantly scan YouTube comment sections, flag harmful content, and package evidence for reporting — turning a painful manual process into a 10 second task.

### The Solution
Detoxify solves this by combining a machine learning model specifically trained on sexist and gendered harassment data with the YouTube Data API. Any creator can paste a video link and instantly receive a color-coded breakdown of their entire comment section — flagged by severity, sorted by danger level, and packaged into a downloadable evidence report ready for platform reporting or legal documentation. What previously took hours of traumatic manual reading now takes seconds.

## Technical Details

### Technologies/Components Used

**For Software:**
- Languages used: Python, JavaScript, HTML5, CSS3 
- Frameworks used: Flask 3.1.0 ,Flask-CORS 
- Libraries used:google-api-python-client 2.163.0	,python-dotenv 1.1.0	,transformers >=4.40.0 (HuggingFace)	,torch >=2.0.0 (PyTorch)	,jsPDF 3.0.3	,jspdf-autotable 5.0.2
- Tools used: VS Code ,Git / GitHub ,Google Cloud Console ,HuggingFace Hub



## Features

List the key features of your project:
1. YouTube Comment Extraction
Fetches the first 100 comments from any YouTube video using the YouTube Data API v3. Users simply paste a video URL, and the system automatically extracts comment text, author names, timestamps, and like counts for analysis.

2. Toxicity Detection using Logistic Regression
A Logistic Regression model trained on a labeled dataset of offensive and non-offensive text classifies each comment. The model outputs a confidence score and assigns severity levels — High (>90%), Medium (>75%), and Low — making it lightweight, interpretable, and efficient compared to complex deep learning approaches.

3. Interactive Analysis Dashboard
A real-time dashboard displays key statistics: total comments analyzed, flagged vs. safe counts, toxicity percentage, and a severity breakdown. An animated toxicity bar gives an instant visual summary. Filter tabs (All / Safe / Flagged / High Severity) let users drill down into specific categories.

4. PDF Evidence Report Generation
Users can download a branded PDF report of flagged comments using jsPDF. The report includes video metadata, a summary of analysis results, and a detailed table of all offensive comments with their severity and confidence scores — useful for documentation and reporting harassment.

---

## Implementation

### For Software:

#### Installation
pip install -r requirements.txt


#### Run
TRAIN THE MODEL
cd backend
python model_train.py

RUN THE BACKENED
cd backend
python app.py

## Project Documentation

### For Software:

#### Screenshots (Add at least 3)
<img width="1919" height="902" alt="Screenshot 2026-02-21 085817" src="https://github.com/user-attachments/assets/4167e90a-caff-49c1-aba5-fbe49daf99db" />   Homepage
This is the home page of how it looks.

<img width="1919" height="912" alt="image" src="https://github.com/user-attachments/assets/0b775705-598b-4414-bc91-7486609c72a0" />  Classification
This is when the url is copied and then pasted over here in which shows the comments and how many of them are safe,flagged and all.

<img width="1918" height="599" alt="image" src="https://github.com/user-attachments/assets/12b6067d-e758-4496-adce-92e17cb41520" />  Flagged section
This is the section where the flagged details are shown.

<img width="989" height="833" alt="image" src="https://github.com/user-attachments/assets/8b3e2e10-75c1-4c72-87bf-976f01dcfa4a" />   PDF
This is how the pdf is shown.

#### Diagrams

**System Architecture:**

<img width="729" height="495" alt="Screenshot 2026-02-21 091226" src="https://github.com/user-attachments/assets/5d4b7c9a-da09-4dc7-b34a-90bf3db7538e" />
1. Frontend Layer (Client-Side)
Component	Role
index.html	Page structure — input form, dashboard, filter tabs, comment cards, download button
script.js	Core logic — sends API requests, renders results, handles filtering, triggers PDF generation
style.css	Glassmorphism UI — frosted-glass cards, animated gradients, floating particles, pink/lavender palette
jsPDF + AutoTable	Generates downloadable PDF reports entirely in the browser (no server needed)
2. Backend Layer (Flask Server)
Component	Role
Flask REST API	Exposes two endpoints: POST /api/comments (main analysis) and GET /api/health (status check)
YouTube Service	Extracts the video ID from the URL, calls YouTube Data API v3 to fetch 100 comments with metadata
Logistic Regression Classifier	Trained on a labeled offensive language dataset. Classifies each comment as offensive or non-offensive with a confidence score
Analysis Engine	Aggregates results — counts flagged/safe, calculates toxicity %, assigns severity (High >90%, Medium >75%, Low)

**Application Workflow:**
<img width="184" height="485" alt="image" src="https://github.com/user-attachments/assets/017e3f56-9e46-425d-a4a2-55d2ffbb4c3a" />
This diagram shows how data flows through the system from frontend to backend and database.


## Additional Documentation

### For Web Projects with Backend:

#### API Documentation

**Base URL:** http://localhost:5000

##### Endpoints

**GET /api/endpoint**
- Description:Health check endpoint to verify the Flask server and ML model are running correctly.
- **Parameters:None
- **Response:**
- {
  "status": "healthy",
  "model": "loaded",
  "service": "Detoxify API"
}
  
{
  "status": "unhealthy",
  "error": "Model not loaded"
}


**POST /api/endpoint**
- **Description:Accepts a YouTube video URL, fetches the first 100 comments using the YouTube Data API v3, classifies each comment as offensive or non-offensive using Logistic Regression, and returns the results with analysis statistics
- Request Body:
{
  "url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
}
- **Response:**
{
  "success": true,
  "videoInfo": {
    "title": "Video Title",
    "channelTitle": "Channel Name",
    "publishedAt": "2024-01-15T10:30:00Z",
    "viewCount": "1500000",
    "likeCount": "45000",
    "commentCount": "3200",
    "thumbnail": "https://i.ytimg.com/vi/VIDEO_ID/hqdefault.jpg"
  },
  "comments": [
    {
      "author": "Username",
      "authorProfileImage": "https://yt3.ggpht.com/...",
      "text": "This is a comment",
      "likeCount": 12,
      "publishedAt": "2024-02-01T08:00:00Z",
      "isFlagged": false,
      "confidence": 0.95,
      "severity": "none"
    },
    {
      "author": "ToxicUser",
      "authorProfileImage": "https://yt3.ggpht.com/...",
      "text": "Offensive comment text here",
      "likeCount": 3,
      "publishedAt": "2024-02-02T14:30:00Z",
      "isFlagged": true,
      "confidence": 0.92,
      "severity": "high"
    }
  ],
  "analysis": {
    "totalComments": 100,
    "flaggedCount": 15,
    "safeCount": 85,
    "toxicityPercentage": 15.0,
    "highSeverity": 5,
    "mediumSeverity": 6,
    "lowSeverity": 4
  }
}










## Project Demo

### Video
[Add your demo video link here - YouTube, Google Drive, etc.]

*Explain what the video demonstrates - key features, user flow, technical highlights*

### Additional Demos
[Add any extra demo materials/links - Live site, APK download, online demo, etc.]

---

## AI Tools Used (Optional - For Transparency Bonus)

If you used AI tools during development, document them here for transparency:

**Tool Used:** [e.g., GitHub Copilot, v0.dev, Cursor, ChatGPT, Claude]

**Purpose:** [What you used it for]
- Example: "Generated boilerplate React components"
- Example: "Debugging assistance for async functions"
- Example: "Code review and optimization suggestions"

**Key Prompts Used:**
- "Create a REST API endpoint for user authentication"
- "Debug this async function that's causing race conditions"
- "Optimize this database query for better performance"

**Percentage of AI-generated code:** [Approximately X%]

**Human Contributions:**
- Architecture design and planning
- Custom business logic implementation
- Integration and testing
- UI/UX design decisions

*Note: Proper documentation of AI usage demonstrates transparency and earns bonus points in evaluation!*

---

## Team Contributions

- Aleesha: ML,documentation
- Gowri: Frontend and Backend


---



---

Made with ❤️ at TinkerHub
