# stable-jenkins-aws

Step 1)  Create an image using Dockerfile as  jenkins-agent:stable

Step 2) Create a pipeline that runs around 20 mins so that you can exec into jenkins slave pod and copy your kubeconfig file to ~/.aws/
