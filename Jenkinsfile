pipeline {
    agent {
        kubernetes{
            yamlFile 'agents.yaml'
        }
    }
    stages {
        // stage("Linting") {
        //     steps {
        //         container("maven"){
        //             sh 'mvn clean site'
        //         }
        //     }
        // }
        stage("SCM Checkout"){
            steps{
                container("git"){
                    git branch: 'main', url: 'https://github.com/uglk/spring-framework-petclinic.git'
                }
            }
        }
        stage("Maven Build") {
            steps {
                container("maven"){
                   sh  'mvn clean install -Dmaven.test.skip=true'
                }
            }
        }
    }
}
