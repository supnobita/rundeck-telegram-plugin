pipeline {
    agent any

    environment {
        SONAR_SCANNER_HOME=/opt/sonar/sonar-scanner
    }

    stage('SonarQube analysis') {
    // requires SonarQube Scanner 2.8+
    def scannerHome = tool 'SonarQube Scanner 2.8';
    withSonarQubeEnv('sonarscanner') {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
    stages {
        stage('Build') {
            steps {
                echo "Compiling..."
                sh 'printenv'
                sh "${tool name: 'sbt', type: 'org.jvnet.hudson.plugins.SbtPluginBuilder$SbtInstallation'}/bin/sbt rundeckPlugin"
            }
        }
        
    }
}
