# 🚀 DevOps to MLOps — Build Systems, CI/CD & Packaging (Complete Notes)

## 📌 Overview

This document summarizes core concepts of:

* Build systems
* Artifacts
* Java vs Python workflows
* CI/CD (Jenkins)
* Transition into MLOps

It is written as a **beginner → intermediate learning guide** with real-world clarity.

---

# 🧠 1. Core Concepts

## 🔹 Source Code

* Human-readable instructions written by developers
* Examples:

  * Java → `.java`
  * Python → `.py`

---

## 🔹 Build

**Definition:**

> Process of converting source code into a runnable and deployable format

### Build includes:

* Dependency installation
* Compilation (if required)
* Testing
* Packaging

👉 **Build = Preparation of code for execution and deployment**

---

## 🔹 Artifact

**Definition:**

> Final output generated after build

### Examples:

* Java → `.jar`, `.war`
* Python → `.whl`, `.tar.gz`
* DevOps → Docker Image

👉 **Artifact = What we deploy**

---

# ⚙️ 2. Java Build System

## 🔹 Basic Flow

```bash
Hello.java → javac → Hello.class → JVM → Run
```

### Important:

* `javac` → Compiler
* JVM → Executes bytecode
* `.class` is NOT directly executable (needs JVM)

---

## 🔹 Problem in Real Projects

* Hundreds/thousands of files
* Multiple dependencies
* Manual compilation is not feasible

---

## 🔹 Solution → Build Tools

### Maven / Gradle

They automate:

* Dependency management
* Compilation
* Testing
* Packaging

---

## 🔹 Maven Build Lifecycle

```bash
mvn clean package
```

### Steps:

1. Read `pom.xml`
2. Download dependencies
3. Compile `.java → .class`
4. Run tests
5. Package into `.jar`

---

## 🔹 `.class` vs `.jar`

| Feature    | `.class`      | `.jar`               |
| ---------- | ------------- | -------------------- |
| Type       | Compiled file | Packaged application |
| Structure  | Scattered     | Organized            |
| Deployment | Difficult     | Easy                 |

---

## 🔹 Types of JAR

* **Normal JAR** → Only application code
* **Fat JAR (Uber JAR)** → Code + dependencies

---

# 🧪 3. Testing

## 🔹 What is Testing?

> Verifying that the code behaves correctly

### Types:

* Unit Testing → Test individual functions
* Integration Testing → Test modules together
* End-to-End Testing → Test full system

---

## 🔹 Why Testing?

* Catch bugs early
* Prevent regressions
* Ensure reliability

---

## 🔹 Key Insight

* **Build → Can it run?**
* **Test → Is it correct?**

---

# 🐍 4. Python Build Concept

## 🔹 Nature of Python

* Interpreted language
* Can run directly:

  ```bash
  python app.py
  ```

---

## 🔹 Real-World Challenges

* Dependency conflicts
* Multiple files
* Environment inconsistencies

---

## 🔹 Python “Build” Means

* Managing dependencies
* Packaging code
* Creating reproducible environments

---

## 🔹 Python Tools

### pip

```bash
pip install -r requirements.txt
```

### venv

```bash
python -m venv env
```

### Poetry (Modern Tool)

```bash
poetry install
poetry build
```

### build module

```bash
python -m build
```

---

## 🔹 Python Artifacts

* `.whl` (Wheel file)
* `.tar.gz`

👉 Equivalent to Java `.jar`

---

## 🔁 Java vs Python Comparison

| Concept      | Java              | Python                       |
| ------------ | ----------------- | ---------------------------- |
| Type         | Compiled          | Interpreted                  |
| Build Focus  | Compile + package | Package + dependency mgmt    |
| Artifact     | `.jar`            | `.whl`                       |
| Run raw code | Not possible      | Possible (not ideal in prod) |

---

# 🚀 5. CI/CD & Jenkins

## 🔹 Continuous Integration (CI)

* Developers push code frequently
* Automated build + test triggered

---

## 🔹 Build Server

Example: Jenkins

### Responsibilities:

* Pull code from repository
* Execute build
* Run tests
* Generate artifacts

---

## 🔹 CI Pipeline Flow

```
Developer → GitHub → Jenkins
        ↓
      Build
        ↓
      Test
        ↓
    Artifact
        ↓
     Deploy
```

---

# 🔥 6. Why Build is Necessary

Without build:

* Missing dependencies
* Inconsistent outputs
* Deployment issues
* Manual errors

With build:

* Automation
* Standardization
* Reliability

---

# 🐳 7. Docker (Modern Artifact)

## 🔹 What is Docker?

Docker packages:

* Application code
* Runtime
* Dependencies

👉 Into a single unit called **Docker Image**

---

## 🔹 Why Docker?

* Same environment everywhere
* Eliminates “works on my machine” problem
* Easy deployment

---

# 🤖 8. MLOps Perspective

## 🔹 Traditional DevOps

```
Code → Build → Artifact → Deploy
```

---

## 🔹 MLOps

```
Code + Data → Train → Model → Deploy
```

---

## 🔹 Mapping

| DevOps   | MLOps         |
| -------- | ------------- |
| Build    | Training      |
| Artifact | Model file    |
| Deploy   | Model serving |

---

## 🔹 ML Artifacts

* `.pt`
* `.bin`
* `.onnx`

---

## 🔹 Why Docker in MLOps?

* Reproducibility
* Dependency control
* Scalable deployment

---

# 🎯 9. Key Takeaways

* Build is more than compilation
* Build ensures consistency and deployability
* Testing ensures correctness
* Python also follows build concepts (different form)
* Docker is the modern deployment artifact
* MLOps extends DevOps principles with data + models

---

# 💥 Final Understanding

* Java build → Makes code runnable
* Python build → Makes code deployable
* MLOps build → Trains model

---

# 🧠 Golden Line

> **"Build transforms raw code into a reliable, reproducible, and deployable unit."**

---

# 📌 Next Steps

* Practice Maven basics
* Learn Python packaging (pip, Poetry)
* Learn Docker deeply
* Build a CI/CD pipeline (Jenkins or GitHub Actions)
* Explore MLOps tools (MLflow, Kubeflow)

---

# 🚀 Author

Krishna Pavan