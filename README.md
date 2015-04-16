# aws-ssoup
SSOUP on AWS with Kubernetes

Manual steps :

- create an AWS account free tier
- create an AWS T2.micro EC2instance with Ubuntu. Take note of the ip address (172.31.55.229 in this example)
- expose port 80
- install Kubernetes as explained here: https://github.com/GoogleCloudPlatform/kubernetes/blob/master/docs/getting-started-guides/ubuntu_single_node.md
- Run a test replicationContainer like this:

        kubectl run-container nginx --image=nginx --replicas=5

- Expose the port 80 of the nginx replicationContainer to the outside world :

        kubectl expose rc nginx --port=80 --target-port=80 --public-ip=172.31.55.229

- open a browser and go to http://172.31.55.229 and you should see nginx login page

