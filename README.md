<<<<<<< HEAD
Code Signing Portal (Flask + Bootstrap + MongoDB)

Prerequisites:
- Python 3.9+
- MongoDB (local or Atlas)
- OpenSSL in PATH
- SignTool available (Windows SDK) and in PATH

Install:
    pip install -r requirements.txt

Run:
    python app.py

Open http://127.0.0.1:5000

Default admin user (created on first run if users collection empty):
    username: admin
    password: admin
=======
🔐 Code-Signing-Portal

A Flask-based Code Signing Portal that uses OpenSSL to generate keys, create self-signed certificates, sign files, and verify signatures.
Supports RSA and ECDSA algorithms with .pfx export for compatibility with Microsoft signtool.

📌 Features

🔑 Generate RSA & ECDSA key pairs

📄 Create Certificate Signing Requests (CSR)

✅ Self-sign certificates for development/testing

🖊️ Digitally sign executables & files

🔍 Verify signatures for authenticity

📦 Export certificates as .pfx

👨‍💻 Role-based access (Admin/User)

📜 Logs for signing & verification actions

🛠️ Tech Stack

Backend: Python (Flask)

Crypto: OpenSSL (RSA, ECDSA)

Database: MongoDB

Frontend: HTML, CSS, Bootstrap

Extras: Flask-Mail (notifications), Session Management

⚙️ Installation & Setup
1️⃣ Clone Repository
git clone https://github.com/AtluriPurnaChand/Code-Signing-Portal.git
cd Code-Signing-Portal

2️⃣ Create Virtual Environment
python -m venv venv
venv\Scripts\activate   # Windows
source venv/bin/activate # Linux/Mac

3️⃣ Install Dependencies
pip install -r requirements.txt

4️⃣ Configure Environment

Create a .env file in the root directory:

FLASK_SECRET_KEY=your_secret_key
MAIL_SERVER=smtp.example.com
MAIL_PORT=587
MAIL_USERNAME=you@example.com
MAIL_PASSWORD=yourpassword
MONGO_URI=mongodb://localhost:27017/code_signing_portal

5️⃣ Run Flask Server
python app.py


Now open → http://127.0.0.1:5000

🔑 Usage Workflow

Login/Register → User authentication

Generate Keys → RSA or ECDSA private/public key

Create CSR → For certificate requests

Self-Sign Certificate → Issue a certificate

Export PFX → For use with signtool

Sign File → Protect executables with digital signatures

Verify File → Confirm integrity & authenticity

📂 Project Structure
Code-Signing-Portal/
│── app.py                # Flask main app
│── backend/
│   ├── signer.py         # OpenSSL key/cert/sign handling
│   ├── certs/            # Certificates (ignored by git)
│   └── uploads/          # Uploaded files (ignored by git)
│── requirements.txt      # Python dependencies
│── .gitignore            # Ignored files/folders
│── README.md             # Documentation

🧪 OpenSSL Commands Used
RSA
openssl genrsa -out rsa_private.key 2048
openssl rsa -in rsa_private.key -pubout -out rsa_public.key
openssl req -new -key rsa_private.key -out rsa_request.csr
openssl x509 -req -in rsa_request.csr -signkey rsa_private.key -out rsa_cert.crt -days 365

ECDSA
openssl ecparam -name prime256v1 -genkey -noout -out ecdsa_private.key
openssl ec -in ecdsa_private.key -pubout -out ecdsa_public.key
openssl req -new -key ecdsa_private.key -out ecdsa_request.csr
openssl x509 -req -in ecdsa_request.csr -signkey ecdsa_private.key -out ecdsa_cert.crt -days 365

🚀 Future Enhancements

Integration with real Certificate Authorities (CA)

Support for EdDSA (Ed25519)

Web-based dashboard with analytics

Multi-user certificate management


📜 License

This project is licensed under the MIT License.
>>>>>>> 013002583c9c6944a86a45dd2040e9c466978da7
