node('ubuntu'){
    def imgVersion = UUID.randomUUID().toString()
    def dockerImage = "bhuvanakadiveti/nodeapp:${imgVersion}"
    stage('Checkout'){
        
        git 'https://github.com/Bhuvana0509/uppy'
    }
    
    
    stage('Build Docker Image'){
        sh "docker build -t ${dockerImage} ."
    }
    
    stage('Push DockerHub'){
		withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerhubPwd')]) {
			sh "docker login -u bhuvanakadiveti -p ${dockerhubPwd}"
		}
        
        sh "docker push ${dockerImage}"
    }
  
}
