pipeline{
    agent any
    stages{
        stage('Repositorio'){
            steps{
                echo 'Clonamos el repositorio'
                git url: 'https://github.com/ALICLEME/ejemploWebapp'
            }
        }
        stage('Empaquetado'){
            steps{
                echo 'Empaqueto mediante maven'
                sh 'mvn package'
            }
        }
        stage('Etapa 3'){
            steps{
                echo 'Despliegue'
                deploy adapters: [tomcat9(credentialsId: 'e8746319-2240-4ffe-943f-81b1985a7cb1', path: '', url: 'http://localhost:8082')], contextPath: 'prueba1', war: 'target/miweb.war'
            }
        }
    }
    post{
        always{
            echo 'YO me ejecuto siempre'
        }
        success{
            echo 'YO me ejecuto cuando todo ha ido bien'
        }
        failure{
            echo 'YO me ejecuto cuando ha ido mal'
        }
        changed{
            echo 'YO me ejecuto si esta ejecucion no acaba en el mismo estado que la anterior'
        }
    }
}