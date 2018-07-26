pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'download.sh'
            }
        }

        stage('Nexus IQ Scan'){
            steps {
                nexusPolicyEvaluation failBuildOnNetworkError: false, iqApplication: 'pytest', iqStage: 'build', jobCredentialsId: ''
            }

            // steps {
            //     sh 'java -jar /opt/nexus-iq/nexus-iq-cli -i webgoat-example -s http://localhost:8070 -a admin:admin123 ./target/WebGoat-${BUILD_VERSION}.war -r ./scan.json'
            // }
        }   
    }
}


