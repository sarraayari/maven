pipeline {
    environment{
            registry= "ayamenakkari/achat"
       registryCredential = "dockerhub"
            dockerImage = "achat"
    }
    agent any
    stages { 
    stage ('GIT'){
    steps {
        echo "Getting Project from Git"
        git branch:"master",
        url :"https://github.com/sarraayari/avec-maven.git"
    }
}
stage ('MVN CLEAN'){
    steps{
        sh 'mvn clean compile -DskipTests'
        sh 'mvn test'
    }
}

stage('MVN SONARQUBE'){
    steps{
        sh   "mvn sonar:sonar -Dsonar.projectKey=sonarqube -Dsonar.host.url=http://172.17.0.1:9000 -Dsonar.login=1cb20b8af49d61aff4b9b581e084c454c4a3ec4f"
    }
}
}
}
