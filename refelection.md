
During this project, I learned how to build and deploy a serverless application using AWS services. Security was an important consideration throughout the implementation.

I followed the principle of least privilege by granting only the necessary permissions to the Lambda function through IAM roles. This reduced the risk of unauthorized access to AWS resources.

The application used API Gateway to securely expose backend functionality while keeping the database inaccessible from the public internet. DynamoDB was accessed only through Lambda, which improved security and reduced the attack surface.

I also learned the importance of monitoring and logging using CloudWatch. Monitoring helps identify performance issues and potential security incidents quickly. Setting up budget alerts provided visibility into cloud costs and helped prevent unexpected charges.

Another important lesson was understanding Cross-Origin Resource Sharing (CORS). Proper configuration was required to allow communication between the S3-hosted frontend and the API Gateway endpoint.

Using managed services such as DynamoDB and Lambda reduced the operational burden and ensured built-in security features were available. AWS automatically manages patching, infrastructure maintenance, and scalability.

Overall, this project provided practical experience with cloud security concepts, IAM permissions, monitoring, cost management, and secure application architecture. These practices are essential for building reliable and secure cloud-native applications in real-world environments.
