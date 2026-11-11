QUARK — ENHANCED PYTHON WEBSITE
================================

WHAT'S INCLUDED
- app.py: single-file Python web application (standard library only)
- assets/editorial-board.png: the supplied editorial board photograph
- assets/white-house.png: the supplied White House photograph
- SQLite database is created automatically as quark.db

RUN
1. Extract this ZIP into a folder.
2. Open Terminal in that folder.
3. Set a private dashboard password, then start the site:

   macOS / Linux:
   export QUARK_ADMIN_PASSWORD='choose-a-strong-password'
   python3 app.py

   Windows PowerShell:
   $env:QUARK_ADMIN_PASSWORD='choose-a-strong-password'
   python app.py

4. Open http://127.0.0.1:8000

HOW THE EDITORIAL BOARD RECEIVES ARTICLES
- Student submissions are saved in quark.db on the server.
- The board opens http://127.0.0.1:8000/editor
- Sign in with QUARK_ADMIN_PASSWORD.
- Editors can search submissions, read full article text and abstract, and change status:
  received, under review, revision requested, accepted, rejected, published.
- Students can check the latest status using their QRK reference number.

OPTIONAL EMAIL NOTIFICATIONS
To send an email alert whenever an article is submitted, configure SMTP environment
variables before starting the server:

  SMTP_HOST=smtp.your-provider.example
  SMTP_PORT=587
  SMTP_USER=your-smtp-username
  SMTP_PASSWORD=your-smtp-password
  SMTP_FROM=quark@your-domain.example
  BOARD_EMAIL=editorial-board@your-school.example

Use an email account/provider approved by your school. If SMTP is not configured,
submissions still save to the database and appear in the Editorial Desk; no email is sent.

IMPORTANT DEPLOYMENT NOTES
- The default dashboard password is 'change-this-password' only if
  QUARK_ADMIN_PASSWORD is not set. Set a strong password before any shared deployment.
- For access by the Editorial Board from different devices, deploy the app on a
  school-approved server with HTTPS and persistent storage. A copy running on one
  student's laptop is only reachable while that laptop/server is online and network
  access is configured.
- Keep quark.db backed up; it contains submitted student work and personal details.
- This version accepts article text in the form. It does not yet accept document
  attachments. Editors can read/copy the submitted text from the dashboard.
- The board dashboard is password-protected, but this is a lightweight school
  project implementation, not a substitute for a professionally audited system.
