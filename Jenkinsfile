pipeline {
    agent slave1
   stages { 
        stage('code checkout') {
            steps {
                git branch: 'Vinod_feature', url: 'https://github.com/devvikasmanda/demo-project.git'
            }
        }
   }
}
