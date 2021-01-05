# stable-jenkins-aws


                                                  Step-1
                                                  ------

Docker build and push
---------------------


docker build -f Dockerfile -t your_account_user/customize-jenkins-agent:latest .

docker login

docker push your_account_user/customize-jenkins-agent:latest






                                                  Step-2
                                                  ------
                                                  

Step-1)   Create three PVC ( jenkins-aws-credentials  ,  jenkins-aws-kubeconfig  , jenkins-slave-pvc-maven ) using efs as persistence storage 

* Here we are using efs storage so that our jenkins agent pod can schedule on any node.
* If we use block storage then there is a case jenkins agent start on different node which might be on different availability zone and in AWS block storage are specific to         availability zone.



Jenkins Installation using Helm
-------------------------------
helm repo add stable https://kubernetes-charts.storage.googleapis.com/
Kubectl create ns jenkins
helm install jenkins stable/jenkins -n jenkins -f jenkins-stable-values.yaml




Step 1)  Create an image using Dockerfile as  jenkins-agent:stable

Step 2) Create a pipeline that runs around 20 mins so that you can exec into jenkins slave pod and copy your kubeconfig file as 
        /root/.kube/config 
        and
        aws credential file as
        /root/.aws/credentials

