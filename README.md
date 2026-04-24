🔐 Secure CI/CD Lab
A hands-on lab demonstrating how to build a secure CI/CD pipeline using GitHub Actions for a Python Flask application. This project showcases security best practices integrated directly into an automated pipeline — from code linting and dependency scanning to automated testing and safe deployment.

📌 Overview
This lab uses a minimal Flask web application as the target project, with the real focus being the security-hardened GitHub Actions workflow in .github/workflows/. The goal is to demonstrate how DevSecOps principles can be embedded into every stage of the CI/CD process.

📁 Project Structure
secure-ci-cd-lab/
├── .github/
│   └── workflows/
│       └── *.yml              # GitHub Actions CI/CD workflow(s)
├── app.py                     # Minimal Flask application
└── requirements.txt           # Python dependencies

🚀 The Application
app.py is a simple Flask web server used as the deployment target:
pythonfrom flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Secure CI/CD Pipeline Working Successfully"

if __name__ == "__main__":
    app.run(host="127.0.0.1", port=5000)
Visit http://127.0.0.1:5000/ to confirm the app is running.

⚙️ Requirements

Python 3.8+
Flask (see requirements.txt)

Install dependencies:
bashpip install -r requirements.txt
Run locally:
bashpython app.py

🔄 CI/CD Pipeline
The pipeline lives in .github/workflows/ and is triggered automatically on:

Push to the main branch
Pull requests targeting main

Pipeline Stages
Push / PR
   ↓
Checkout Code
   ↓
Install Dependencies
   ↓
Security Scan (dependency vulnerabilities)
   ↓
Static Analysis / Linting
   ↓
Run Tests
   ↓
Build & Deploy (if all checks pass)

🛡️ Security Practices Demonstrated
PracticeDescriptionDependency scanningChecks requirements.txt for known vulnerable packagesSecret managementCredentials stored as GitHub Secrets, never hardcodedLeast privilegeWorkflow permissions scoped to only what's neededBranch protectionPipeline must pass before merging to mainPinned actionsUses specific versions of GitHub Actions to prevent supply chain attacksAutomated testingTests run on every commit to catch regressions early

🧪 Running the Pipeline
Trigger automatically
Push any change to main or open a Pull Request — GitHub Actions will pick it up.
Trigger manually
Go to Actions → [Workflow Name] → Run workflow in the GitHub UI.
View results
Navigate to the Actions tab in the repository to see real-time logs for each job.

🔧 Customisation

Add more routes to app.py to expand the app and test the pipeline against real changes.
Extend the workflow with additional security tools such as:

bandit — Python static security analysis
safety — checks for known vulnerabilities in dependencies
gitleaks — secrets scanning
trivy — container image scanning (if Dockerising)


Add environments (staging, production) in GitHub Settings to gate deployments with manual approvals.


📚 Concepts Covered

GitHub Actions workflow syntax (on, jobs, steps, uses, run)
Environment variables and GitHub Secrets
Automated dependency vulnerability checks
Secure Flask application setup (binding to localhost)
DevSecOps: shifting security left in the development lifecycle


📄 License
This project is open for learning and experimentation. Feel free to fork and build upon it.
