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
			}


 stage ('Publish artifact') {
            steps {
                rtServer (
                    id: "local_artifact",
                    url: 'http://34.68.29.93:8081/artifactory',
                    username: 'admin',
					password: 'Madipti1',
                )


				rtPublishBuildInfo (
                    serverId: "local_artifact"
                )
}
}
}
}
