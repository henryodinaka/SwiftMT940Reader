pipeline {
   agent any

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
      stage('Docker Build') {
         steps {
            pwsh(script:'docker images -a')
            pwsh(script: """
            docker build .
            docker images -a

            cd ..
            """)
         }
      }

      stage('PowerShell') {
         steps {
            powershell label: '', script: 'Write-Output "Welcome to Powershell from jenkinsfile fro github"'
         }
      }
   }

}
