pipeline {
  agent any
  stages {
    stage("Pull") {
      steps {
        script {
          checkout([$class: 'GitSCM',
            branches: [[name: '*/main' ]],
            userRemoteConfigs: [[
            url: 'https://github.com/Nour9911/MyApp.git',
            credentialsId: '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'
            ]]
            ])
          }
        }
    }

    stage("Build") {
      steps {
        script{
          sh "ansible-playbook -K ansible/build.yml -i ansible/inventory/host.yml"
              }
            }
        }
   stage("docker") {
            steps {
                script{
                    sh 'ansible-playbook -K ansible/docker.yml -i ansible/inventory/host.yml'
                }
            }
        }
                       stage("docker-registry") {
            steps {
                script{
                    sh 'ansible-playbook -K ansible/docker-registry.yml -i ansible/inventory/host.yml'
                }
            }
        }

                        stage("Deployment with kubernetes replicas") {
                steps{
                    sh 'kubectl --token=eyJhbGciOiJSUzI1NiIsImtpZCI6ImxJcTA4OVZMVS00Mk16MVo0Sk41eU5fZUx6QlBMUkZMVzNNdVNMdnF0S28ifQ.eyJhdWQiOlsiaHR0cHM6Ly9rdWJlcm5ldGVzLmRlZmF1bHQuc3ZjLmNsdXN0ZXIubG9jYWwiLCJrM3MiXSwiZXhwIjoxNjY4MTAzNTA3LCJpYXQiOjE2NjgwOTk5MDcsImlzcyI6Imh0dHBzOi8va3ViZXJuZXRlcy5kZWZhdWx0LnN2Yy5jbHVzdGVyLmxvY2FsIiwia3ViZXJuZXRlcy5pbyI6eyJuYW1lc3BhY2UiOiJkZWZhdWx0Iiwic2VydmljZWFjY291bnQiOnsibmFtZSI6ImplbmtpbnMiLCJ1aWQiOiJmZDE4MjI1ZS00NjM0LTQ3ZjEtOTIzOS0xMDQ1MmY2NTgzNDMifX0sIm5iZiI6MTY2ODA5OTkwNywic3ViIjoic3lzdGVtOnNlcnZpY2VhY2NvdW50OmRlZmF1bHQ6amVua2lucyJ9.Tmg9uuEYRbN-xcGnMpoICIZ_xPg5WIgdujLPtOi6N8YsE66ZZW2lxyESlvCEsm4QnT8MgFVCn0xdw02lWQbRTO0513UUV-FKDjX_LzZ7AhWflhadsXiyPvVF8dGGnNBDYkzhLCfAgCVo_copNmI3rGXupyDYGmy9GvKpuTvLa_J0pKGBHOnmmUrcOe96-YXda_M8gFKEde-56YTGv5qO7HCIy48zQiXzib7ytFsX1cjbx7vwRfGjtsNNBmke8q8txHZE1uS3CNXPolcpZUu7AgecYfbobZDDop5TDZykuCd2pnmyhrlEypG4mDGrXHLoNdR76Y6VBvo80WzryjjyxQ create -f deployment.yml'
                }
             } 

  }
}
