pipeline {
    agent any

    parameters {
            booleanParam(name: 'DRYRUN', defaultValue: true, description: 'Тестовый запуск')
            string(name: 'VERSION', defaultValue: 'D-01.002.7', trim: true, description: 'Введите версию компонента')
            text(name: 'COMMENT', defaultValue: 'Добавлены новые feature', description: 'Описание изменений в релизе')
            password(name: 'PASSWORD', defaultValue: 'changeme', description: 'Введите пароль')
            choice(name: 'ENV', choices: ['PROD', 'DEV', 'UAT'], description: 'Стенд:')
        }

    stages {
        stage('Build') {
            steps {
                echo "Building.."
                echo "Версия СПО ${VERSION}"
                echo "${COMMENT}"
                sh ("ansible --version")
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh ("git --version")
            }
        }

        stage('Approve') {
            input 'Do you approve deployment?'
        }

        stage('Deploy') {
            steps {
                echo "Deploying...."
                echo "Версия СПО ${VERSION}"
                echo "Устанавливаем на стенд ${ENV}"
                sh ("uptime -p")
            }
        }
    }
}