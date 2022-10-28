pipeline {
    agent any

    stages {
        stage('build docker file') {
            steps {
                sh 'sudo docker build . -t venkat5658/myproject:latest'
            }
        }
      stage('docker hub push')
      {
       steps
        {
          sh 'docker login -u venkat5658 -p venkat5658@'
          sh 'docker push  venkat5658/myproject:latest'
        }
      } 
    }
}
