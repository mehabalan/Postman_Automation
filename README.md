# Postman API Automation Framework

## Overview

This project demonstrates an API automation framework built using Postman with Chai assertions, enhanced scripting, and data-driven testing capabilities. It uses Postman’s Pre-request Scripts, Post-response Scripts, Environment variables, and Collection-level configurations to create dynamic and reusable test workflows.

Newman is used for command-line execution and to generate test reports in HTML and Word formats.

---

## Features

* API automation using Postman Collections
* Assertions using Chai.js (pm.expect)
* Dynamic request handling with Pre-request Scripts
* Response validation using Post-response Scripts
* Environment variables for flexible configuration
* Collection variables for reusable test data
* Data-driven testing using external datasets (CSV/JSON)
* Command-line execution using Newman
* Automated report generation in HTML and Word formats

---

## Tech Stack

* Postman
* Chai Assertion Library
* Newman (CLI runner for Postman)
* Node.js

---

## Project Structure

```
├── collections/
│   └── api_collection.json
├── environments/
│   └── environment.json
├── reports/
│   ├── report.html
│   └── report.docx
└── README.md
```

---

## Key Concepts Used

### Pre-request Scripts

Used to prepare dynamic data before sending requests such as generating tokens, timestamps, or random values.

Example:

```javascript
pm.environment.set("timestamp", new Date().getTime());
```

---

### Post-response Scripts

Used to validate API responses using Chai assertions.

Example:

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response has expected property", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property("id");
});
```

---

### Environment and Collection Variables

Used to make requests dynamic and reusable across multiple environments like Dev, QA, and Production.

Example:

```javascript
pm.environment.set("base_url", "https://api.example.com");
```

---

### Data-Driven Testing

External data files (CSV or JSON) are used to run multiple iterations of the same request with different inputs.

---

## Running Tests with Newman

### Install Newman

```
npm install -g newman
```

### Basic Execution

```
newman run collections/api_collection.json -e environments/environment.json
```

---

## Report Generation

### HTML Report

```
newman run collection.json -e environment.json -r html --reporter-html-export reports/report.html
```

### Word Report

Using an additional reporter such as htmlextra or by converting HTML to Word format.

```
newman run collection.json -e environment.json -r htmlextra --reporter-htmlextra-export reports/report.html
```

---

## Benefits

* Scalable and maintainable test design
* Easy integration with CI/CD pipelines
* Reusable and modular scripting
* Clear and detailed test reports
* Supports dynamic and data-driven testing

---

## Future Enhancements

* CI/CD integration (Jenkins, GitHub Actions)
* Advanced reporting dashboards
* Integration with test management tools
* Automated environment switching

---

## Author

Developed as part of API automation practice using Postman and Newman.

---

## License

This project is for learning and demonstration purposes.
