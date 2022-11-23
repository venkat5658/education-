pipeline {
    agent any

     stage('Build') { 
            steps { 
                script{
                 app = docker.build("httpd")
                }
            }
        }
     
 stage('Push') {
            steps {
                script{
                        docker.withRegistry('010762572680.dkr.ecr.ap-south-1.amazonaws.com/test:demo', 'ecr:ap-south-1:aws-credentials') {
                    app.push("${env.BUILD_NUMBER}")
                    app.push("latest")
                    }
                }
            } 
 }
        stage('kube deploy')
      {
       steps
        {
          sh 'sudo kubectl apply -f edu-dep.yaml'
          sh 'sudo kubectl apply -f dep-svc.yaml'
            sh 'sudo kubectl rollout restart deployment/httpd-deployment'
           
        }
      } 
    }

