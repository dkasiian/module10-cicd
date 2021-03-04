pipeline {
    agent any
    parameters {
        choice(
            choices: ['maven' , 'gradle'],
            description: 'Choose a build tool',
            name: 'BUILD_TOOL')
    }
    properties {
        promotions {
            promotion {
                name('QA')
                icon('star-silver')
                condition {
                    selfPromotion('false')
                }
            }
        }
     }
    stages {
        stage('Build with Maven') {
            when {
                expression { params.BUILD_TOOL == 'maven' }
            }
            steps {
                withMaven {
                    bat 'mvn clean compile'
                }
            }
        }
        stage('Build with Gradle') {
            when {
                expression { params.BUILD_TOOL == 'gradle' }
            }
            steps {
                withGradle {
                    bat './gradlew build'
                }
            }
        }
    }
}
