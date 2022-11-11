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
 
 stage("prometheus") {
            steps {
                script{
                    sh 'ansible-playbook -K ansible/prometheus.yml -i ansible/inventory/host.yml'
                }
            }
        }
stage("grafana") {
            steps {
                script{
                    sh 'ansible-playbook -K ansible/grafana.yml -i ansible/inventory/host.yml'
                }
            }
        }
stage("node exporter") {
            steps {
                script{
                    sh 'ansible-playbook -K ansible/node-exporter.yml -i ansible/inventory/host.yml'
                }
            }
        }

  }
}
