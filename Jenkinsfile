
node {
    def nodeHome = tool name: 'node-9.3.0', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
    env.PATH = "${nodeHome}:${nodeHome}/bin:${env.PATH}"

    stage('check tools') {
        echo env.PATH
        sh "node -v"
        sh "npm -v"
        sh "npm i -g @angular/cli"
        sh "npm rebuild node-sass --force"
    }

    stage('checkout') {
        checkout scm
    }

    stage('npm install') {
        sh "npm install"
    }

    stage('npm run build dev') {
        sh "npm run build:dev"
    }

    stage('npm clean') {
        sh "npm run clean"
    }

    stage('npm run build prod') {
        sh "npm run build:prod"
    }

    stage('npm run build ssr') {
        sh "npm run build:ssr"
    }

    stage('npm test') {
        sh "xvfb-run npm run test:ci:jenkins"
    }

    stage('npm e2e') {
        sh "xvfb-run npm run e2e:ci"
    }

    stage('npm typedoc') {
        sh "npm run docs:typedoc"
    }

    stage('npm compodoc') {
        sh "npm run docs:compodoc"
    }
}
