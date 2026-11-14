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
                echo "Ejecutando OWASP Dependency-Check..."
                dependencyCheck additionalArguments: '--project "ProyectoSeguridad" --scan . --format HTML --format XML', odcInstallation: 'Default'
            }
        }
        
        stage('Control de Calidad y Reporte') {
            steps {
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
    }
}
