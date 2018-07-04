pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Compiling..."
                sh 'printenv'
                sh "${tool name: 'sbt', type: 'org.jvnet.hudson.plugins.SbtPluginBuilder$SbtInstallation'}/bin/sbt rundeckPlugin"
            }
        }
     
        stage('SonarQube analysis') {
            steps {
                // requires SonarQube Scanner 2.8+
                def scannerHome = tool name: 'sonarscanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
                withSonarQubeEnv('sonarscanner 2') {
                     withEnv(['SONAR_SCANNER_HOME=${scannerHome}']) {
                        sh 'sbt sonarScan'
                    }
                }
            }
        }
    }
}
