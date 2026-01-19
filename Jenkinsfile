pipeline {
    agent { label 'dev' }

    stages {

        stage('code checkout') {
            steps {
                git branch: 'Vinod_feature',
                    url: 'https://github.com/devvikasmanda/demo-project.git'
            }
        }

        stage('maven build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('code coverage') {
            steps {
                sh 'mvn site'
            }
        }

        stage('sonarqube code analysis') {
            steps {
                withSonarQubeEnv('my_sonar') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

        stage('quality gate') {
            steps {
                timeout(time: 5, unit: 'MINUTES') {
                    script {
                        def check = waitForQualityGate()
                        if (check.status != 'OK') {
                            error "Pipeline aborted due to Quality Gate failure: ${check.status}"
                        }
                    }
                }
            }
        }
stage('Artifactory_upload') {
            steps {
                script {
                    def server = rtServer(id: 'jfrog')
                    dir('./server/target/') {
                        rtUpload(
                            serverId: 'jfrog',
                            spec: '''{
                                "files": [{
                                    "pattern": "*.jar",
                                    "target": "vikas/"
                                }]
                            }'''
                        )
                    }
                }
            }
        }
    }
} 


     
