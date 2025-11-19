minikube start --driver=docker
kubectl create deployment myapp --image=nginx
 kubectl get pods
 kubectl expose deployment myapp --type=NodePort --port=80
 minikube service myapp --url
node{
    stage('Checkout'){
        git branch: 'main',url: "https://github.com/lavanya-panthulu/maven-webproject.git"
    }
    stage('Build'){
        bat 'mvn clean install'
    }
    stage('Test'){
        bat 'mvn test'
    }
    stage('Package'){
        bat 'mvn package'
    }
    stage('Deploy'){
        deploy adapters:[
            tomcat9(
                credentialsId: 'tomcat-cred',
                url:'http://localhost:8085'
                )],
                contextPath:'webpath',
                war:'target/*.war'
    }
}
