# ccproject
Use of amazon EC2 service (IAAS) to host an instance and later use that instance as a web server/data server. Implementing EC2 services like auto-scaling and load balancing.

Abstract:
The project implements Information as a Service by storing files in various ways. Also the services provided by EC2 like auto-scaling and load balancing is implemented.


Introduction: 
Amazon Web Services (AWS), is a collection of cloud computing services that make up the on-demand computing platform offered by Amazon.com. These services operate from 12 geographical regions across the world. The most central and best-known of these services arguably include Amazon Elastic Compute Cloud, also known as "EC2", and Amazon Simple Storage Service, also known as "S3". AWS now has more than 70 services that range from compute, storage, networking, database, analytics, application services, deployment, management and mobile. Amazon markets AWS as a service to provide large computing capacity quicker and cheaper than a client company building an actual physical server farm.

Amazon EC2:Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers.Amazon EC2’s simple web service interface allows you to obtain and configure capacity with minimal friction. It provides you with complete control of your computing resources and lets you run on Amazon’s proven computing environment. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, allowing you to quickly scale capacity, both up and down, as your computing requirements change. Amazon EC2 changes the economics of computing by allowing you to pay only for capacity that you actually use. Amazon EC2 provides developers the tools to build failure resilient applications and isolate themselves from common failure scenarios.
Simple Storage Service(S3):Amazon S3 is object storage built to store and retrieve any amount of data from anywhere – websites and mobile apps, corporate applications, and data from IoT sensors or devices.S3 provides comprehensive security and compliance capabilities that meet even the most stringent regulatory requirements. It gives customers flexibility in the way they manage data for cost optimization, access control, and compliance. S3 provides query-in-place functionality, allowing you to run powerful analytics directly on your data at rest in S3. And Amazon S3 is the most supported storage platform available, with the largest ecosystem of ISV solutions and systems integrator partners.

Implementation details:
Storage using 3 ways:
Using cygwin
Cygwin is a Unix-like environment and command-line interface for Microsoft Windows. Cygwin provides native integration of Windows-based applications, data, and other system resources with applications, software tools, and data of the Unix-like environment. Thus it is possible to launch Windows applications from the Cygwin environment, as well as to use Cygwin tools and applications within the Windows operating context.
 
Using Filezilla
FileZilla is a free software, cross-platform FTP application, consisting of FileZilla Client and FileZilla Server. Client binaries are available for Windows, Linux, and Mac OS X, server binaries are available for Windows only. The client supports FTP, SFTP and FTPS (FTP over SSL/TLS). Support for SFTP (SSH File Transfer Protocol), which can be used to share folders over a network, is not implemented in FileZilla Server.
Using S3 bucket
Amazon S3 is cloud storage for the Internet buckets and objects are resources, and Amazon S3 provides APIs for you to manage them.Just by specifying the name of the bucket and region, a bucket can be created and files can be inserted in this bucket.It is scalable,reliable and cost effective too.
Properties of Cloud implemented:
Load Balancing: Cloud Load balancing is the process of distributing workloads and computing resources across one or more servers. This kind of distribution ensures maximum throughput in minimum response time. The workload is segregated among two or more servers, hard drives, network interfaces or other computing resources, enabling better resource utilization and system response time. Thus, for a high traffic website, effective use of cloud load balancing can ensure business continuity. The common objectives of using load balancers are to maintain system firmness,to improve system performance,to protect against system failures.
 
Auto-Scaling: Amazon EC2 Auto Scaling helps you ensure that you have the correct number of Amazon EC2 instances available to handle the load for your application. Auto Scaling can detect when an instance is unhealthy, terminate it, and launch an instance to replace it.Auto Scaling can help you ensure that your application always has the right amount of capacity to handle the current traffic demand.Auto Scaling can dynamically increase and decrease capacity as needed. 
Following has been used to access EC2 instance :
Filezilla      
               Steps  
 Enter hostname, username and password. Leave ‘port’ as blank. Click on ‘Quickconnect’
 Look for the status ‘Directory listing successful’        
Select the folder on your PC where you have placed the files to be uploaded. 
Select the directory on the server where you wish to upload your files.

Cygwin
    Command to connect to created instance :
        ssh -i instancename.pem servername@ipaddress
S3 bucket
    Steps : 
    1.After signing in your AWS account, click on Services tab and select S3.
    2. Click on Create Bucket.
    3.Specify the bucket details like bucket name,region.
    4.Set permissions to enable static webpage hosting by providing the filename.
    5.Set bucket policy by writing a small script.
    6.Upload the file to be hosted in the bucket using either Cygwin or directly through AWS interface
        Cygwin command : aws sync s3 /var/www/html/filename s3://bucketname
    7.Host the uploaded file.

Auto-scaling
Create an Amazon Machine Image(AMI) by right-clicking on the instance and select Image option.
Create Launch Configuration -> Choose Amazon Machine Image(AMI) and select newly created image -> Choose instance type -> set configuration details by specifying number of instances,network and subnet -> Set size -> Add Tags by setting Key and Value -> Configure security group by setting group name and add HTTp rule -> Select existing key pair -> Launch Instance

Create AutoScaling Groups. Step 1: Create a Launch Template -> Create an Auto Scaling Group  -> Verify Your Auto Scaling Group -> (Optional) Delete Your Scaling Infrastructure

Load-balancing
Step 1: Select a Load Balancer Type -> Define Your Load Balancer -> Assign Security Groups to Your Load Balancer in a VPC->Configure Health Checks for Your EC2 Instances -> Register EC2 Instances with Your Load Balancer -> Tag Your Load Balancer (Optional)->Create and Verify Your Load Balancer  ->  Delete Your Load Balancer (Optional) 





