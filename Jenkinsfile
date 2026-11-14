pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Análisis Estático de Seguridad (SAST)') {
            steps {
                echo "Ejecutando OWASP Dependency-Check con API Key..."
                dependencyCheck additionalArguments: '--project "ProyectoSeguridad" --scan . --format HTML --format XML --nvdApiKey 9BF8569E-C31C-4AAE-B548-7AA0DD0834E7', odcInstallation: 'Default'
            }
        }
        
        stage('Control de Calidad y Reporte') {
            steps {
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
    }
}
