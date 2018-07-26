pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'pip download -r requirements.txt'
            }
            post {
                success {
                    echo 'List files....'
                    sh 'ls -l'
                }
            }
        }

        stage('Nexus IQ Scan'){
            steps {
                //nexusPolicyEvaluation failBuildOnNetworkError: false, iqApplication: 'pytest', iqStage: 'build', jobCredentialsId: ''
                //nexusPolicyEvaluation failBuildOnNetworkError: false, iqScanPatterns: [[scanPattern: '*.whl'], [scanPattern: '**/*.whl'], [scanPattern: '**/*.tar.gz'], [scanPattern: '**/*.zip']], iqApplication: 'pytest', iqStage: 'build'
                sh 'java -jar /opt/nexus-iq/nexus-iq-cli -D zip=whl -i pytest -s http://localhost:8070 -a admin:admin123 -t build .'
            }


            // steps {
            //     sh 'java -jar /opt/nexus-iq/nexus-iq-cli -i webgoat-example -s http://localhost:8070 -a admin:admin123 ./target/WebGoat-${BUILD_VERSION}.war -r ./scan.json'
            // }
        }   
    }
}


