<h1>Backup and Restore</h1>


<h2>Description</h2>
Backup and Restore is a way to protect your data from being lost or damaged. It involves copying your data to another place and having a plan to get your system back up and running if something goes wrong. This can also protect against disasters by copying data to different locations. To make it easier to recover, it's best to use AWS services that redeploy your system automatically (AWS CloudFormation, AWS Cloud Development Kit (CDK),AWS CodePipeline, etc.). The following are steps taken to backup and restore an S3 bucket.
<br />

<h2>AWS Cloud Map</h2>
<p align="center">
<img src="https://i.imgur.com/UP7s4MS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


<h2>Services Used</h2>

- <b>S3 Cross-Region Replication (CRR)</b> 
- <b>CloudFormation</b>
- <b>AWS CloudShell</b>
- <b>AWS Backup</b>
- <b>Linux</b>
- <b>Amazon S3</b>
- <b>Primary Region</b>
- <b>Secondary Region</b>
- <b>CloudFormation</b>
- <b>Shell Scripting</b>

<h2>Environments Used </h2>

- <b>AWS Management Console</b> (21H2)

<h2>Backup and Restore walk-through:</h2>

<b>*Assume two seperate S3 buckets are already deployed in seperate regions*</b> 
- <b>Within Amazon S3, under the Mangement link, create a "Replication Rule" for the primary bucket</b>
- <b>Use AWS CloudShell to export objects from your primary bucket to your secondary bucket</b>
- <b>Use AWS Backup and navigate to your PRIMARY region to create an on-demand backup for your EC2 instance</b>
- <b>Use AWS Backup and navigate to your PRIMARY region to create an on-demand backup for your RDS database</b>
- <b>Use AWS Backup and navigate to your SECONDARY region to COPY the on-demand backup for your EC2 instance you previously created</b>
- <b>Use AWS Backup and navigate to your SECONDARY region to COPY the on-demand backup of your RDS database you previously created</b>

<b>*Manually simulate a Regional Service Disaster in your Primary region in order to utilize our disaster recovery technique*</b> 
- <b>Within Amazon Backup use the BACKUPS tab to launch the EC2 backup in the SECONDARY region</b>
- <b>Within Amazon Backup use the BACKUPS tab to launch the RDS backup in the SECONDARY region</b>
- <b>Within Amazon S3 verify the SECONDARY region by reviewing the Properties</b>



<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
