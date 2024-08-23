# Jenkins CI/CD Pipeline Setup

## Introduction

This guide provides steps to set up a Jenkins job for building and deploying a project from a GitHub repository, including Continuous Integration and Continuous Deployment (CI/CD).

## Part 1: Creating the Jenkins Job

1. **Login to Jenkins:**
   - Access your Jenkins console.

2. **Create a New Job:**
   - Navigate to the Jenkins dashboard.
   - **Source Code Management:**
     - Repository: `https://github.com/mohamedjavith820/Javith-mj`
     - Branch: `*/main`
   - **Build:**
     - Root POM: `pom.xml`
     - Goals: `clean install package`

## Part 2: Adding Deployment Steps

1. **Install Plugin:**
   - Navigate to `Manage Jenkins` > `Jenkins Plugins` > `Available`.
   - Install `deploy to container` plugin.

2. **Set Up Credentials:**
   - Go to `Credentials` > `Global credentials` > `Add credentials`.
   - Use `deployer` for Username, `XXXXXXX` for Password, and `Tomcat_user` for ID.

3. **Modify Job for Deployment:**
   - Post Steps: Deploy `**/*.war` to `Tomcat 8.x` using `Tomcat_user`.
   - Tomcat URL: `http://<PUBLIC_IP>:<PORT_NO>`

## Part 3: CI/CD Configuration

1. **Build Triggers:**
   - Enable `Poll SCM` with schedule `*/2 * * * *`.

2. **Test CI/CD:**
   - Modify code in GitHub to trigger an automatic build.

## Example Output

You can access the deployed web application at [http://54.173.18.73:8080/webapp/](http://52.91.196.140:8080/webapp/).

![Web Application Screenshot](Capture1.PNG)

_Description_: This screenshot shows the welcome page of the deployed web application, displaying the message "Hello, Welcome JAVITH !!!".

## Conclusion

Your Jenkins job is now set up for automated build, deployment, and CI/CD, ensuring continuous integration and deployment of changes to a Tomcat server.
