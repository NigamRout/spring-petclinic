pipeline {
  environment {
    registry = "nigamrout/spring-petclinic"
    registryCredential = 'docker-hub'
    dockerImage = ''
  }
  
  agent any
  
  tools {
    maven 'M3'
  } 
  
  stages {
      
    stage('Cloning Git') {
      steps {
        git branch: 'main', url: "https://github.com/NigamRout/spring-petclinic.git"
      }
    }
    
    stage('MVN Compile') {
       steps {
         sh 'mvn compile'
       }
    }
    
    stage('MVN Test') {
      steps {
        sh '''
            mvn test
        ''' 
      }
    }
    
    stage('Local Install') {
      steps {
        sh '''
            mvn clean install
        ''' 
      }
    }
    
    
    stage('Upload Artifact') {
      steps {
        sh '''
            pwd; ls; curl -uadmin:admin -T target/spring-petclinic-2.6.0-SNAPSHOT.jar "http://localhost:8081/artifactory/libs-snapshot-local/$(date '+%Y%m%d-%H.%M')/"
        ''' 
      }
    }
    
    stage('Create Docker File') {
      steps {
        sh '''
			DOCKER_FILE_NAME="jfrog-petclinic-dockerfile"
			DOCKER_IMAGE_NAME="jfrog-petclinic-image"
			DOCKER_CONTAINR_NAME="jfrog-petclinic-container"			
			
            echo 'FROM openjdk:10                                                               '  > $DOCKER_FILE_NAME
            echo 'WORKDIR /app                                                                  ' >> $DOCKER_FILE_NAME
            echo 'COPY ./target/spring-petclinic-*-SNAPSHOT.jar ./spring-petclinic.jar          ' >> $DOCKER_FILE_NAME
            echo 'EXPOSE 8080                                                                   ' >> $DOCKER_FILE_NAME
            echo 'ENTRYPOINT ["java","-jar","/app/spring-petclinic.jar","--server.port=8080"]   ' >> $DOCKER_FILE_NAME
            cat $DOCKER_FILE_NAME
           
            docker build -f $DOCKER_FILE_NAME -t $DOCKER_IMAGE_NAME .
           
            echo $(docker inspect --format="{{ .State.Running }}" $DOCKER_CONTAINR_NAME)
            if [ $(docker inspect --format="{{ .State.Running }}" $DOCKER_CONTAINR_NAME) ] ; then docker rm -f $DOCKER_CONTAINR_NAME; fi
           
            docker run -d -it --name $DOCKER_CONTAINR_NAME -p 8082:8080 $DOCKER_IMAGE_NAME
           
            echo "Open [http://localhost:8082] in browser, you will have PetClinic App Running :)"
        ''' 
      }
    }

  }
}

