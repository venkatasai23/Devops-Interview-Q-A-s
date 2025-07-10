# 🚀 CI/CD – Pipeline Design & Best Practices

---

## 1. Designing a Robust Pipeline

- **Modular Stages**: Separate build, test, deploy  

- **Parallel Jobs**: Speed up test suites  

- **Failure Notifications**: Slack/email on breakage  

---

## 2. Pipeline as Code Example (Jenkinsfile)

```groovy

pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }
    stage('Deploy') {
      when { branch 'main' }
      steps {
        sh './deploy.sh'
      }
    }
  }
  post {
    always {
      junit 'target/surefire-reports/*.xml'
    }
  }
}

```

## 3. Build‑Test‑Deploy Best Practices

Cache dependencies (e.g., Docker layer caching)

Fail fast on lint/security violations

Use artifacts repository (e.g., Nexus, Artifactory)

✅
