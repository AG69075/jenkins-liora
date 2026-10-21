pipeline {
    agent any

    environment {
        SCHOOL = "liora"
        NAME = "Anthony"
    }

    stages {
        stage("Env Variables") {
            environment {
                NAME = "lewis" // remplace la variable NAME définie au niveau du pipeline
                BUILD_ID = "2" // remplace la variable BUILD_ID par défaut
            }

            steps {
                echo "SCHOOL = ${env.SCHOOL}" // affiche "SCHOOL = liora"
                echo "NAME = ${env.NAME}"     // affiche "NAME = lewis"
                echo "BUILD_ID = ${env.BUILD_ID}" // affiche "BUILD_ID = 2"

                script {
                    env.SOMETHING = "1" // crée la variable env.SOMETHING
                }
            }
        }

        stage("Override Variables") {
            steps {
                script {
                    env.SCHOOL = "I LOVE LIORA!" // ne peut pas remplacer SCHOOL défini au niveau pipeline ou stage
                    env.SOMETHING = "2" // peut remplacer une variable créée impérativement
                }

                echo "SCHOOL = ${env.SCHOOL}"     // affiche "SCHOOL = liora"
                echo "SOMETHING = ${env.SOMETHING}" // affiche "SOMETHING = 2"

                withEnv(["SCHOOL=DEV UNIVERSITY"]) { // peut remplacer n'importe quelle variable
                    echo "SCHOOL = ${env.SCHOOL}" // affiche "SCHOOL = DEV UNIVERSITY"
                }

                withEnv(["BUILD_ID=1"]) {
                    echo "BUILD_ID = ${env.BUILD_ID}" // affiche "BUILD_ID = 1"
                }
            }
        }
    }
}
