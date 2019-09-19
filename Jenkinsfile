node('docker'){
    def dockerImage = "bhuvanakadiveti/nodeapp:1.0"
    deleteDir()
    stage('Checkout'){
        
        git 'https://github.com/Bhuvana0509/uppy'
    }
    
    
    stage('Build Docker Image'){
        sh "sudo apt-get clean"
        sh "docker build -t ${dockerImage} ."
    }
    
    stage('Push image to registry'){
		withCredentials[(usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
      sh "docker login -u bhuvanakadiveti -p ${dockerhubPwd}"
		}
        
        sh "docker push ${dockerImage}"
    }
  
}
