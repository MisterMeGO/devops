pipeline {
    agent any

    parameters {
            booleanParam(name: 'dryrun', defaultValue: true, description: 'Тестовый запуск')
            string(name: 'version', defaultValue: 'D-01.002.7', trim: true, description: 'Введите версию компонента')
            text(name: 'releaseNotes', defaultValue: 'Добавлены новые feature', description: 'Описание изменений в релизе')
            password(name: 'password', defaultValue: 'changeme', description: 'Введите пароль')
            choice(name: 'env', choices: ['PROD', 'DEV', 'UAT'], description: 'Стенд:')
        }

    stages {
        stage('Build') {
            steps {
                echo "Building.."
                echo "Версия СПО {version}"
                echo "${releaseNotes}"
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying...."
                echo "Версия СПО ${version}"
                echo "Устанавливаем на стенд ${env}"
            }
        }
    }
}