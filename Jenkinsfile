pipeline {
    environment {
      registry = '3.110.47.182:8081/repository/k8s-task/'
      registryCredential = 'nexus'
      dockerImage = ''
      SCANNER_HOME = tool 'sonarqube'
      }
    agent any
    stages {
      stage('Cloning Git') {
        steps {
          git branch: 'main', url: 'https://github.com/Devopsveeru/sonar_integration_veera.git'
        }
      }
      stage('Building image') {
        steps{
          script {
            sh 'docker build -t flask:8.0 .'
            //sh 'docker run -it -p 9090:9090 flask '  
          }
        }
       }
      stage('Deploy Image in to nexus registry') {
        steps{
          script {
            //sh 'curl "admin:ravali" -X PUT http://18.212.25.74:808/repository/k8s-task/flask:5.0 '
          //flask:3.0.push("latest")
            sh 'docker tag flask:8.0 3.110.47.182:8081/repository/k8s-task/flask:8.0'
            //sh 'docker login -u admin -p Veera123@'
            sh 'docker login -u admin -p Veera123@ 3.110.47.182:8081/repository/k8s-task/' 
            sh 'docker push 3.110.47.182:8081/repository/k8s-task/flask:8.0'
            sh 'docker logout http://3.110.47.182:8081/repository/k8s-task/'
              }
            }
         }
      //stage('Sonarqube') {
        //environment {
            //scannerHome = tool 'sonarqube'   
        //}
        //steps {
          //withSonarQubeEnv('sonarqube') {
            //sh "${scannerHome}/bin/sonar-scanner -X"
          //}
        //timeout(time: 2, unit: 'MINUTES') {
        //    waitForQualityGate abortPipeline: true
        //}
       //}
      //}
        // integrated test cases
        //stage('selinium-test') {
            //steps {
               //sh 'python hello.py'
            //}
       // }
    }
}    
