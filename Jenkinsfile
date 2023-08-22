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
        stage("Maven Clean") {
            steps {
                container("maven"){
                   sh  'mvn clean'
                }
            }
        }
        stage("Maven Compile") {
            steps {
                container("maven"){
                   sh  'mvn compile test'
                }
            }
        }
        stage("Maven Package") {
            steps {
                container("maven"){
                   sh  'mvn package -Dmaven.test.skip=true'
                }
            }
        }
    }
}
