pipeline {
    agent any

    tools {
        nodejs "node"
    }


    parameters {
        string(name: 'container_name' , defaultValue: 'pagina_web' , description: 'Nombre del contenedor de docker.')
        string(name: 'image_name' , defaultValue: 'pagina_img' , description: 'Nombre de la image docker')
        string(name: 'tag_image' , defaultValue: 'lts' , description: 'Tag de la imagen docker')
        string(name: 'container_port', defaultValue: '80', description: 'Puerto del contenedor')
    }

    stages {
        stage('inatall'){
            steps {
                git branch: 'developer', url: 'https://github.com/JFD1709/JENKINS.git'
                sh 'npm install'
            }
        }
    
        stage('test') {
            steps {
                sh 'npm run build'
            }
        }    

        stage('build'){
            steps {
                script {
                    try {
                        sh 'docker stop ${container_name}'
                        // sh 'docker rm ${container_name}'
                        // sh 'docker rmi ${image_name}:${tag_image}'
                    } catch(Exception e){
                        echo 'Exception Ocurred: ' + e.toString()
                    }
                }

                sh 'docker build -t ${image_name}:${tag_image} .'

            }
        }

        // stage('deploy') {
        //     steps {
        //         sh 'docker run -d -p ${container_port}:80 --name ${container_name} ${image_name}:${tag_image}'
        //     }
        // }
    
    }

}