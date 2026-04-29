pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo '🏗️ Initializing Build Environment...'
                bat 'ping 127.0.0.1 -n 4 > nul'
                echo 'Build Successful: app-v1.0.jar created.'
            }
        }

        stage('Unit Tests') {
            steps {
                echo '🧪 Running Unit Tests...'
                bat 'ping 127.0.0.1 -n 3 > nul'
                
                // --- NEGATIVE SCENARIO INJECTION: Uncomment the line below to fail the build ---
                // error 'Test Results: 15% Failed. Aborting build due to low test coverage.'
                
                echo 'Test Results: 100% Pass.'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                echo '🔍 Scanning for Code Quality...'
                bat 'ping 127.0.0.1 -n 5 > nul'
                
                // --- NEGATIVE SCENARIO INJECTION: Uncomment the line below to fail the build ---
                // error 'SonarQube: Quality Gate FAILED ❌ (Security Vulnerabilities Found)'
                
                echo 'SonarQube: Quality Gate PASSED ✅'
            }
        }

        stage('Integration Tests') {
            steps {
                echo '🔗 Running Integration Tests against Mock DB...'
                bat 'ping 127.0.0.1 -n 6 > nul'
                echo 'Integration Tests: Successful.'
            }
        }

        stage('Artifactory Upload') {
            steps {
                echo '📦 Uploading Artifact to Repository...'
                bat 'ping 127.0.0.1 -n 4 > nul'
                echo 'Artifact stored at: http://dummy-artifactory/repo/app-v1.0.jar'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo '🚀 Deploying to Staging Environment...'
                bat 'ping 127.0.0.1 -n 5 > nul'
                echo 'Deployment Complete: http://staging-app-server:8080'
            }
        }
    }

    post {
        success {
            echo """
            ****************************************************
            SUCCESS: Pipeline Completed!
            Build: OK
            Tests: OK
            Sonar: OK
            Deploy: OK
            ****************************************************
            """
        }
        failure {
            echo """
            ****************************************************
            ALERT: Pipeline Failed!
            Check the stage logs above to identify the issue.
            ****************************************************
            """
        }
    }
}
