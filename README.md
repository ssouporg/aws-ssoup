# aws-ssoup
SSOUP on AWS with Kubernetes

Manual steps to configure the instance:

- create an AWS account free tier
- create an AWS T2.micro EC2instance with Ubuntu. Take note of the public dns (ec2-52-4-195-214.compute-1.amazonaws.com in this example)
- expose http traffic on port 80 in the security group
- install Kubernetes as explained here: https://github.com/GoogleCloudPlatform/kubernetes/blob/master/docs/getting-started-guides/ubuntu_single_node.md
- Run a test replicationContainer like this:

        kubectl run-container nginx --image=nginx --replicas=5

- Take not of the internal ip address of the instance (172.31.55.229 in this example)
- Expose the port 80 of the nginx replicationContainer to the outside world :

        kubectl expose rc nginx --port=80 --target-port=80 --public-ip=172.31.55.229

- open a browser and go to http://ec2-52-4-195-214.compute-1.amazonaws.com/ and you should see nginx welcome page
