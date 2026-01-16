pipeline{
  agent {label 'dev'}
  stages{
    stage('code checkout'){
      steps {
        git branch: 'master', url:'https://github.com/devvikasmanda/demo-project.git'
      }
    }
    stage('mvn installagain')
      steps {
        sh 'mvn clean install'
      }
    }
  }
}
     
