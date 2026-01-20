pipeline {
    agent {lable 'slave'}
   stages { 
        stage('code checkout') {
            steps {
                git branch: 'Vinod_feature', url: 'https://github.com/Vinod-ren/demo-project.git'
            }
        }
   }
}
