pipeline {
    agent any

    environment {
        SCHOOL = "liora"
    }

    stages {
        stage("Env Variables") {
            environment {
                NAME = "Liora"
            }

            steps {
                echo "SCHOOL = ${env.SCHOOL}"
                echo "NAME = ${env.NAME}"

                script {
                    env.TEST_VARIABLE = "some test value"
                }

                echo "TEST_VARIABLE = ${env.TEST_VARIABLE}"

                withEnv(["ANOTHER_ENV_VAR=here is some value"]) {
                    echo "ANOTHER_ENV_VAR = ${env.ANOTHER_ENV_VAR}"
                }
            }
        }
    }
}
