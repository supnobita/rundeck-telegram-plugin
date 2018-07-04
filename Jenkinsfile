pipeline {
    agent any
    
    stages {

        stage('SonarQube analysis') {
            steps {
                sh "SONAR_SCANNER_HOME=${tool name: 'sonarscanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'} sbt sonarScan"
            }
        }

        stage('Build') {
            steps {
                echo "Compiling..."
                sh 'printenv'
                sh "${tool name: 'sbt', type: 'org.jvnet.hudson.plugins.SbtPluginBuilder$SbtInstallation'}/bin/sbt rundeckPlugin"
            }
        }
     
    }
}
