pipeline{
  agent {label 'dev'}
  stages{
    stage('code checkout'){
      steps {
        git branch: 'Vinod_feature', url:'https://github.com/devvikasmanda/demo-project.git'
      }
    } 
    stage('mvn install aagain'){
          steps {
        sh 'mvn clean install'
      }
    }
  } 
}
     
