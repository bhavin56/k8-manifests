# clo835-assignment1

# Alias for kubectl
echo "alias k=kubectl" > ~/.bashrc
source ~/.bashrc

#push local docker image to ECR repository
optional: aws ecr create-repository --repository-name bhavin
aws ecr describe-repositories 
export ECR="462033369097.dkr.ecr.us-east-1.amazonaws.com/midterm-repo"
aws ecr get-login-password --region us-east-1 | docker login -u AWS 462033369097.dkr.ecr.us-east-1.amazonaws.com/cats-repo --password-std
docker tag flask_img(Hint:imagename) "${ECR}:v1.0"
docker images
docker push "${ECR}:v1.0"

#locally check the connectivity via port forwarding
kubectl port-forward --address localhost pod/cats 8888:80
kubectl logs dogs -n dogs

