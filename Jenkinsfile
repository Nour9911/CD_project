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
          sh "ansible-playbook -kK ansible/build.yml -i ansible/inventory/host.yml -e ansible_become_password=vagrant"
              }
            }
        }
    

  }
}
