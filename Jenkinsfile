pipeline {
    agent any
    
    stages {
        stage('Подготовка окружения') {
            steps {
                echo 'Установка зависимостей и клонирование...'
                dir('ansible') {
                    ansiblePlaybook(
                        playbook: 'run_playbook.yml',
                        inventory: 'hosts',
                        tags: 'deploy',
                        colored: true
                    )
                }
            }
        }
        
        stage('Запуск приложений') {
            steps {
                echo 'Запуск контейнеров через Docker Compose...'
                dir('ansible') {
                    ansiblePlaybook(
                        playbook: 'run_playbook.yml',
                        inventory: 'hosts',
                        tags: 'up',
                        colored: true
                    )
                }
            }
        }
    }
}
