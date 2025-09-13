# 🧪 API Testing Project with Postman, Newman & Jenkins

This project demonstrates **API testing automation** using **Postman**, **Newman**, and **Jenkins CI/CD**.  
The goal is to show how to test APIs, generate professional reports, and integrate them into a CI/CD pipeline.

---

## 🚀 Project Overview

- **API Under Test:** [JSONPlaceholder](https://jsonplaceholder.typicode.com/) - a fake online REST API for testing and prototyping.
- **Tools Used:**
  - [Postman](https://www.postman.com/) → API requests & assertions
  - [Newman](https://github.com/postmanlabs/newman) → CLI test runner
  - [Newman Reporter htmlextra](https://www.npmjs.com/package/newman-reporter-htmlextra) → HTML reports
  - [Jenkins](https://www.jenkins.io/) → CI/CD automation

---

## 📂 Repository Structure

```
.
├── collections
│   └── JSONPlaceholder.json
├── envs
│   └── environment.json
├── jenkins
│   └── Jenkinsfile
├── reports
│   ├── jsonplaceholder-htmlextra.html
│   └── jsonplaceholder-report.html
├── .gitattributes
├── package.json
└── README.md
```

---

## ✨ Features

- **Comprehensive Test Coverage:** Includes a suite of API tests for various endpoints (Posts, Comments, Albums, Photos, Todos, Users).
- **Positive & Negative Testing:** Covers both expected outcomes and error conditions.
- **Data-Driven Testing:** (Example of how to set it up if you want to extend it).
- **CI/CD Integration:** Ready-to-use Jenkinsfile for automated test runs.
- **Detailed Reporting:** Generates easy-to-read HTML reports with test results.

---

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- [Node.js](https://nodejs.org/en/) (which includes npm)
- [Newman](https://www.npmjs.com/package/newman)
- [Newman Reporter htmlextra](https://www.npmjs.com/package/newman-reporter-htmlextra)

---

## ⚙️ Installation & Setup

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/mhmd-ashrf-saad/api-testing-project.git
    cd api-testing-project
    ```

2.  **Install Newman and the htmlextra reporter globally:**
    ```bash
    npm install -g newman newman-reporter-htmlextra
    ```

---

## ▶️ Running the Tests

To run the tests locally using Newman, execute the following command from the root of the project:

```bash
newman run collections/JSONPlaceholder.json -e envs/environment.json -r htmlextra --reporter-htmlextra-export reports/jsonplaceholder-htmlextra.html
```

This command will:

- Run the `JSONPlaceholder.json` collection.
- Use the `environment.json` environment file.
- Generate an HTML report using the `htmlextra` reporter.
- Save the report in the `reports` directory.

---

## 🧪 Test Scenarios

The Postman collection includes a variety of tests, such as:

- **Posts:**
  - `GET` all posts and verify the response.
  - `GET` a single post by ID.
  - `POST` a new post and validate the created data.
  - `PUT` to update a post.
  - `DELETE` a post.
  - Negative tests for invalid post IDs.
- **Comments:**
  - `GET` all comments.
  - `GET` comments for a specific post.
  - `POST` a new comment.
- **Users:**
  - `GET` all users and validate the structure.
  - `GET` a single user and verify their details.

...and many more for Albums, Photos, and Todos.

---

## 🤖 Jenkins CI/CD Integration

This project is set up for easy integration with Jenkins.

1.  **Jenkinsfile:** The `jenkins/Jenkinsfile` in this repository is configured to:

    - Check out the code from the Git repository.
    - Run the Newman tests.
    - Archive the generated HTML reports.

2.  **Setting up the Jenkins Job:**
    - Create a new "Pipeline" job in Jenkins.
    - In the "Pipeline" section, select "Pipeline script from SCM".
    - Choose "Git" as the SCM.
    - Provide the repository URL.
    - The script path should be `jenkins/Jenkinsfile`.
    - Save and run the build.

This will automate the entire process of testing and reporting within your CI/CD
