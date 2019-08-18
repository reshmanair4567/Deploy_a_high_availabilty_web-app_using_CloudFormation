This projects aims to deploy Infrastructure as a Code


To create a new stack, run create. sh followed by the the stack name and template body
aws cloudformation create-stack --stack-name infrastack --region us-west-2 --template-body file://ourinfra.yml --parameters ourinfra-params.json

Example : ./create.sh infrastack ourinfra.yml ourinfra-params.json
The template body is a parameter file with default values
