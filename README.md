# AWS-static-webhosting
This project was enabled me understand the process of hosting a static website both on an EC2 instance server and on S3 bucket.The project also requires that the same website was be routed using Route53 through a domain name which I purchased prior to this project. This was to eanble access to the website through domain name as agianst IP address. <br>
There are two sections to this project

- Hosting the static website through EC2 server 
- Hosting the website through S3 bucket
### A. Static Website Hosting through EC2 instance 

1. Provision a Linux EC2 instance, in this project I made use of Ubuntu
2. Updates was done 
![](./img-EC2/01%20update.png) 
2. Install Apache Web server Manually
![](./img-EC2/02%20install%20apache.png)
3. Download the static website zipped file from a repo or a known site (e.g tooplate.com)
4. Upload zipped static website file to the web server using Secure Copy Protocol
![](./img-EC2/03%20cp%20folder.png)
5. Unzip the file and copy the content to the path below on your Web Server;  Path => /var/www/html( this is the webserver pathused for hosting). You may need to install unzip first 
![](./img-EC2/04%20unzip.png)
![](./img-EC2/05.cp-files-to-serverfile.png)
6. Restart the apache server
![](./img-EC2/06.%20restart%20apache2.png)
6. Test that you can access the website from the Public IP address
![](./img-EC2/07.%20webpage.png)
7. Configure Route 53 with your Domain name if you have one.
    - Create an hosted zone
    ![](./img-EC2/08.create-hosted-zone.png)
    - create a record, and in this case, use the A record
    ![](./img-EC2/09.create-record.png) 
8. Test that you can access the site with the domain name  
![](./img-EC2/10webpage.png)

### B. Static Website Hosting through S3 Bucket

Use an S3 bucket to host a static website, although we are still using the same files for the website but here, the difference is that the website is hosted on an S3 bucket and there will be no need for IP address as we are not using any server for this section

1. Create an S3 bucket to host the static site, advisably, the name of the bucket should be the same as your domain name.
![](./retry/01.create.png)
2. Create a folder for server logging, call it serverLog, this is to enable tracking of all logs in the bucket
![](./retry/02createfolder.png)
![](./retry/03serverlog.png)
3. Under properties tab, edit server access logging 
![](./retry/04under-properties.png)
![](./retry/05edit-accesslogging.png)
4. Enable access log and choose the path to the new folder created
! [](./retry/06enableacesslog.png)
5. Upload the websites files 
![](./retry/07upload%20files.png)
![](./retry/08uploading.png)
6. Back to properties tab, scroll down to Static website hosting, and enable 
![](./retry/09enablewebsite.png)
7. Under the permission tab, untick the 'blockall public access'. This is to ensure that the bucket is accessible since we will be using it to launch a website
![](./retry/10offpublicaccess.png)
8. Edit the bucket policy to allow 'GetObject' and all objects should be geatable from the bucket
! [](./retry/11.editpolicy.png)
9. Back to the properties tab, scroll down to the static website hosting, copy the Bucket website endpoint and paste on your browser to verify the website
![](./retry/11.12.websiteendpoint.png)
10. Verify that the website is live.
![](./retry/12confirm%20page.png)
11. Under services on the AWS console, search for Route53, under the hosted zone, pick your domain name and click on create record
![](./retry/12.13.create.png)
![](./retry/13createrecord.png)
12 Access the website using your domain name.
![](./retry/14confirm%20with%20dns.png) 

