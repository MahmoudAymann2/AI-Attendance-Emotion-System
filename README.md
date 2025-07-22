<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>AI Attendance & Emotion Detection System</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      line-height: 1.6;
      margin: 2rem;
      color: #333;
      background: #f9f9f9;
    }
    h1, h2, h3 {
      color: #2c3e50;
    }
    code {
      background: #eee;
      padding: 2px 6px;
      border-radius: 4px;
    }
    pre {
      background: #f4f4f4;
      padding: 1rem;
      overflow-x: auto;
      border-radius: 6px;
    }
    a {
      color: #2980b9;
    }
    ul {
      margin-left: 2rem;
    }
  </style>
</head>
<body>

  <h1>AI Attendance & Emotion Detection System</h1>

  <p>
    A real-time AI-powered Flask application by <strong><a href="https://github.com/MahmoudAymann2" target="_blank">@MahmoudAymann2</a></strong>
    that combines facial recognition-based attendance tracking and live emotion detection using deep learning.
  </p>

  <hr/>

  <h2>🚀 Features</h2>
  <ul>
    <li>🎥 Real-time webcam face detection and recognition</li>
    <li>😊 Emotion classification with a trained CNN model</li>
    <li>🗂 Attendance records saved to CSV and SQLite</li>
    <li>📧 Email notifications to present users (via SMTP)</li>
    <li>🧾 User registration with age & email capture</li>
    <li>💻 Clean and responsive UI with HTML/CSS/JS</li>
  </ul>

  <h2>📁 Project Structure</h2>
  <pre><code>/
├── attendance.py                    # attendance main application
├── emotion.py                       # emotion detection main application
├── face_model.h5             # Keras emotion detection model
├── face_recognition.db       # SQLite database for users
├── templates/
│   ├── index.html
│   ├── emotion.html
│   └── attendance.html
├── static/
│   ├── style.css
│   └── script.js
└── README.html
</code></pre>

  <h2>🔧 Setup Instructions</h2>

  <h3>1. Clone the Repository</h3>
  <pre><code>git clone https://github.com/MahmoudAymann2/AI-Attendance-Emotion-System.git
cd AI-Attendance-Emotion-System</code></pre>

  <h3>2. Install Requirements</h3>
  <pre><code>pip install -r requirements.txt</code></pre>

  <h3>3. Set Environment Variables for Email</h3>
  <pre><code># Create a .env file or export manually:
SMTP_USER=your_email@gmail.com
SMTP_PASS=your_email_app_password</code></pre>

  <h3>4. Run the Application</h3>
  <pre><code>python app.py</code></pre>

  <p>Access the app at <a href="http://127.0.0.1:5000" target="_blank">http://127.0.0.1:5000</a></p>

  <h2>📦 Dependencies</h2>
  <ul>
    <li>Flask</li>
    <li>OpenCV</li>
    <li>face_recognition</li>
    <li>TensorFlow / Keras</li>
    <li>SQLite3, Pickle</li>
    <li>smtplib, email.message</li>
  </ul>

  <h2>🧠 Emotion Classes</h2>
  <ul>
    <li>Happy</li>
    <li>Sad</li>
    <li>Angry</li>
    <li>Surprise</li>
    <li>Fear</li>
    <li>Disgusted</li>
    <li>Neutral</li>
  </ul>

  <h2>📝 To-Do & Enhancements</h2>
  <ul>
    <li>Add emotion labels to live webcam feed</li>
    <li>Admin panel for attendance logs & user management</li>
    <li>Deploy to Heroku / Render with Docker support</li>
  </ul>

  <h2>👨‍💻 Author</h2>
  <p>Created with ❤️ by <a href="https://github.com/MahmoudAymann2" target="_blank">@MahmoudAymann2</a></p>

  <h2>📄 License</h2>
  <p>This project is licensed under the MIT License.</p>

</body>
</html>
