node ('app-agent'){  
    def app
    stage('Cloning Git') {
        
      checkout scm
    }  
       
    stage('Build-and-Tag') {
         app = docker.build("lzeppa182/simpleweb:latest")
    }
    stage('Post-to-dockerhub') {
    
     docker.withRegistry('https://registry.hub.docker.com', 'docker') {
            app.push("latest")
        			}
         }
         
    stage('Pull-image-server') {
         
         sh "docker-compose down"
         sh "docker-compose up -d"
         	
      }
     
}
