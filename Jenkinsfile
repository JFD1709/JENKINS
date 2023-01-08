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
    }

    stage('test') {
        steps {
            sh 'ng build'
        }
    }



}