#!/usr/bin/env groovy

pipeline{
    agent {label master}
    options {
        buildDiscarder(logRotator(numToKeepStr: '20'))
        timeout(time:240, unit: 'MINUTES')
    }
    
    parameters {
        string(name: 'SINGLE_TENANT_NAME', defaultValue: 'create_single_tenant', description: 'Name of the Tenant')
        string(name: 'GIT_BRANCH', defaultValue: 'patch_7.6.55')
    }
    stage('Run create_single_tenant'){
        when {
          expression{
            env.GIT_BRANCH ==~ env.BRANCH_DESIRED_STATE   
          }
        }
        steps{
          bat "echo %env.GIT_BRANCH%"
        }
    }
}
            
