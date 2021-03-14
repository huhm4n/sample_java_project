pipeline {
    agent any
    tools {
        maven '3.5.4'
        jdk 'jdk8'
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install' 
            }

        stage ('Publish') {
            steps {
                rtServer (
                    id: "local_artifact_server",
                    url: http://34.68.29.93:8081/artifactory,
                    credentialsId: admin
					)
					rtPublishBuildInfo (
                    serverId: "local_artifact_server"
                )
            }
        }
    }
}
}
