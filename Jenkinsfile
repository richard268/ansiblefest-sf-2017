pipeline {
  agent any
  stages {
    stage('Git Clone') {
      steps {
        git branch: 'master', url: 'https://github.com/ArctiqTeam/ansiblefest-sf-2017'

          }
      }
    stage ('Clean up local env'){
      steps {
        sh '''#!/bin/bash
        rm -rf /root/.ansible/*'''
      }
    }
    stage ('Test Connectivity'){
      steps {
      ansiblePlaybook inventory: '${WORKSPACE}/ansible/inventory/jenkins/hosts', playbook: '${WORKSPACE}/ansible/test.yml', sudoUser: null
      }
    }
    stage ('Configure OSPF'){
      steps {
      ansiblePlaybook inventory: '${WORKSPACE}/ansible/inventory/jenkins/hosts', playbook: '${WORKSPACE}/ansible/configure.yml', sudoUser: null
      }
    }
  }
}
