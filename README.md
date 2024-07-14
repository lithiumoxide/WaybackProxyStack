# WaybackProxyStack
AWS CloudFormation template for deploying WaybackProxy.

See https://github.com/richardg867/WaybackProxy for details on how the proxy works.

### What this creates:
- VPC and internet gateway
- Route table, route, public subnet, and any necessary associations between them
- Security group
- EC2 instance

### Usage:
1. Log in to your AWS account with an appropriately privileged role, and choose your desired region.
1. In CloudFormation, create a new stack and upload this template
1. Change any input parameters you wish (see note below) and deploy the stack
1. The `Outputs` tab will contain the IP address of the proxy server (the port is always 8888 in this stack version)
1. Use this IP address and port in your computer/browser proxy settings to use WaybackProxy
1. Visit http://web.archive.org/ in your browser while the proxy is running to manage the proxy's options

### Parameter notes:
The input parameters are all optional, though you can modify them to add custom VPC and subnet IP ranges.

If you add the name of a public SSH key to the parameter `KeyName`, the template will automatically add a rule to the instance security group to allow traffic to port 22 from the IP range specified in `SecurityGroupIpRange`. So, if you use the default IP range, this will mean that port 22 is open to the internet, which you may not want to do.