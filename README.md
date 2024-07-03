#Nord js web app Deployment on AWS S3  via GitHub Actions

This YAML script automates the deployment of a React app to AWS S3 when changes are pushed to the `stage`, `dev`, or `main` branches in GitHub. It sets up Node.js, installs dependencies, builds the app, and uses AWS CLI to sync the `./dist` directory to `s3://docsforhealthweb`, ensuring old files are deleted.


