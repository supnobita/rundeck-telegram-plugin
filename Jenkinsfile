pipeline {
    agent { node { label 'master' } }
    environment {
        HTTP_PROXY = 'http://proxy.hcm.fpt.vn:80'
        HTTPS_PROXY = 'http://proxy.hcm.fpt.vn:80'
        NO_PROXY = '172.0.0.1,*.local,172.27.11.207,172.17.0.6,172.27.11.0/24'
    }
    stages {

        stage('SonarQube analysis') {
            steps {
                sh "SONAR_SCANNER_HOME=${tool name: 'sonarscanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'} ${tool name: 'sbt', type: 'org.jvnet.hudson.plugins.SbtPluginBuilder$SbtInstallation'}/bin/sbt sonarScan"
            }
        }

        stage('Build') {
            steps {
                echo "Compiling..."
                //sh "rm -f ${WORKSPACE}/project/plugins.sbt"
                sh "${tool name: 'sbt', type: 'org.jvnet.hudson.plugins.SbtPluginBuilder$SbtInstallation'}/bin/sbt rundeckPlugin"
            }
        }
     
    }
}
