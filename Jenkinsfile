pipeline {
    agent any

    environment {
        SONAR_SCANNER_HOME=/opt/sonar/sonar-scanner
    }

    stages {
        stage('Build') {
            steps {
                echo "Compiling..."
                sh 'printenv'
                sh "${tool name: 'sbt', type: 'org.jvnet.hudson.plugins.SbtPluginBuilder$SbtInstallation'}/bin/sbt sonarScan"
            }
        }
        
    }
}
