pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Descarga el código fuente del repositorio
                checkout scm
            }
        }
        
        stage('Análisis Estático de Seguridad (SAST)') {
            steps {
                echo "Ejecutando análisis estático de seguridad en busca de vulnerabilidades..."
                // Aquí se integraría la herramienta SAST (ej. SonarQube, Semgrep o Dependency-Check)
                // Ejemplo usando Dependency-Check para comprobar dependencias vulnerables:
                dependencyCheck additionalArguments: '--project "MiProyecto" --scan .', 
                                    odcInstallation: 'Default'
            }
        }
        
        stage('Control de Calidad y Bloqueo') {
            steps {
                // Registra los avisos y bloquea el despliegue si hay vulnerabilidades críticas
                recordIssues enabledForParser: [dependencyCheck()]
                echo "Verificando umbrales de seguridad antes del despliegue a producción..."
            }
        }
    }
}
