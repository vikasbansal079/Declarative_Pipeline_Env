#!/usr/bin/env groovy

pipeline{
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '20'))
        timeout(time:240, unit: 'MINUTES')
    }
    
    parameters {
        string(name: 'SINGLE_TENANT_NAME', defaultValue: 'create_single_tenant', description: 'Name of the Tenant')
        string(name: 'GIT_BRANCH', defaultValue: 'origin/master')
    }
    environment {
        def BRANCH_DESIRED_STATE = "origin/master"
    }

    stages{
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
}
            
