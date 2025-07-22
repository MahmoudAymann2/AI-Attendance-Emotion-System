<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>AI Attendance & Emotion Detection System</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      line-height: 1.7;
      padding: 2rem;
      background: #f9f9f9;
      color: #333;
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
      text-decoration: none;
    }
    ul {
      margin-left: 2rem;
    }
  </style>
</head>
<body>

  <h1>AI Attendance & Emotion Detection System</h1>

  <p>
    A Flask-based web application by <strong><a href="https://github.com/MahmoudAymann2" target="_blank">@MahmoudAymann2</a></strong>
    that combines facial recognition for attendance with real-time emotion detection using deep learning.
  </p>

  <hr/>

  <h2>🚀 Features</h2>
  <ul>
    <li>Real-time webcam-based face detection and recognition</li>
    <li>Emotion classification using a CNN model (Keras)</li>
    <li>Attendance recorded in CSV and SQLite database</li>
    <li>Email notifications sent to present users (via SMTP)</li>
    <li>Live UI with HTML/CSS/JavaScript</li>
  </ul>

  <h2>📁 Project Structure</h2>
  <pre><code>
├── attendance.py                    # attendance main application
├── emotion.py                       # emotion detection main application
├── face_model.h5           # Trained emotion detection model
├── face_recognition.db     # SQLite DB for user registration
├── templates/
│   ├── index.html
│   ├── emotion.html
│   └── attendance.html
├── static/
│   ├── style.css
│   └── script.js
└── README.html             # This file
</code></pre>

  <h2>🔧 Setup Instructions</h2>

  <h3>1. Clone the Repository</h3>
  <pre><code>git clone https://github.com/MahmoudAymann2/AI-Attendance-Emotion-System.git
cd AI-Attendance-Emotion-System</code></pre>

  <h3>2. Install Requirements</h3>
  <pre><code>pip install -r requirements.txt</code></pre>

  <h3>3. Configure Email</h3>
  <pre><code># Use environment variables or .env file:
SMTP_USER=your_email@gmail.com
SMTP_PASS=your_email_app_password</code></pre>

  <h3>4. Run the App</h3>
  <pre><code>python app.py</code></pre>

  <p>Access at <a href="http://127.0.0.1:5000" target="_blank">http://127.0.0.1:5000</a></p>

  <h2>🧬 Face Embedding & Database Storage</h2>
  <p>
    When a user registers, the app captures their face via webcam and extracts a 128-dimensional face embedding using the <code>face_recognition</code> library. This embedding is serialized with <code>pickle</code> and stored in a SQLite database.
  </p>
  <pre><code># Generate embedding
encodings = face_recognition.face_encodings(rgb_frame)

# Save in DB
pickle.dumps(encodings[0]) → stored as BLOB
</code></pre>

  <p>
    This allows fast, vector-based face matching during live attendance.
  </p>

  <h2>🔍 Face Recognition Logic</h2>
  <ol>
    <li>Webcam captures frame (OpenCV)</li>
    <li>Faces detected using <code>face_recognition.face_locations</code></li>
    <li>128D encoding generated for each face</li>
    <li>Compared with stored embeddings (Euclidean distance)</li>
    <li>If <code>distance &lt; 0.4</code>, it's a match and the user is marked "Present"</li>
  </ol>
  <pre><code>distance = np.linalg.norm(known_embedding - live_embedding)</code></pre>

  <h2>😊 Emotion Detection (CNN Model)</h2>
  <ul>
    <li>Model format: <code>face_model.h5</code></li>
    <li>Input size: 48x48 grayscale face crop</li>
    <li>Output: 7 emotion classes</li>
  </ul>
  <pre><code>['Angry', 'Disgusted', 'Fear', 'Happy', 'Sad', 'Surprise', 'Neutral']</code></pre>

  <h3>Prediction Pipeline:</h3>
  <ol>
    <li>Convert webcam frame to grayscale</li>
    <li>Detect and crop face using Haar cascades</li>
    <li>Resize to 48x48 and normalize</li>
    <li>Pass to CNN model → Predict emotion</li>
  </ol>

  <pre><code>face = face.astype("float") / 255.0
face = img_to_array(face)
face = np.expand_dims(face, axis=0)
emotion = class_names[np.argmax(model.predict(face))]</code></pre>

  <h2>🗂 Attendance CSV Export</h2>
  <ul>
    <li>Each user is marked as Present/Absent</li>
    <li>Attendance is logged in CSV and optionally emailed</li>
    <li>File saved with timestamp in filename</li>
  </ul>

  <h3>CSV Format:</h3>
  <pre><code>Name, Age, Email, Timestamp
Mahmoud, 21, mahmoud@example.com, 2025-07-22 10:30:00</code></pre>

  <h2>🏗 System Architecture</h2>
  <ul>
    <li><strong>Frontend:</strong> HTML5, CSS, JS (canvas, AJAX)</li>
    <li><strong>Backend:</strong> Flask, OpenCV, Keras, face_recognition</li>
    <li><strong>Storage:</strong> SQLite3 (face encodings), CSV (attendance)</li>
    <li><strong>Email:</strong> SMTP (smtplib, EmailMessage)</li>
  </ul>

  <h2>🧠 Technologies Used</h2>
  <ul>
    <li>Python 3</li>
    <li>Flask</li>
    <li>OpenCV</li>
    <li>face_recognition</li>
    <li>TensorFlow / Keras</li>
    <li>SQLite3 + Pickle</li>
    <li>smtplib (email)</li>
  </ul>

  <h2>🛠️ To-Do & Future Improvements</h2>
  <ul>
    <li>Add emotion labels on live video stream</li>
    <li>Admin dashboard for user/attendance management</li>
    <li>Deploy with Docker / Heroku / Render</li>
    <li>Allow multiple encodings per user (for accuracy)</li>
  </ul>

  <h2>👨‍💻 Author</h2>
  <p>
    Built by <strong><a href="https://github.com/MahmoudAymann2" target="_blank">@MahmoudAymann2</a></strong> with ❤️.
  </p>

  <h2>📄 License</h2>
  <p>
    This project is licensed under the MIT License.
  </p>

</body>
</html>
