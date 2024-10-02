<h2 align="center"> IDENTITY BASED ACCESS TO S3 BUCKET</h2>

This project demonstrates how to grant access to an S3 bucket based on identity.

<h3 align="left"> Case Study</h3>

Suppose the financial information of a company is stored in an S3 Bucket with both the sales and accounting departments having access to the bucket. The main folder of the bucket contains sales invoices only, while a subfolder named "Confidential" contains receipts, ledgers and other sensitive financial information. The Sales Department only have read access to the main S3 Folder, while the Accounting Department have full access to the S3 Bucket and the confidential folder. Two interns Bob and Claire are to join the Sales and Accounting respectively and need to be given the appropriate access to the S3 Bucket without being added to the departments. With the above scenario, I'll provide temporary access to both interns since I am not adding them to the department.

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/network-architecture.png" height="60%" width="70%"/>
</p>


<h3 align="left"> Creating The S3 Bucket</h3>

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/s3-bucket-creation1.png" height="55%" width="75%"/>
</p>

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/s3-bucket-creation2.png" height="55%" width="75%"/>
</p>

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/s3-bucket-creation3.png" height="75%" width="55%"/>
</p>


<h3 align="left"> Creating The Confidential Folder</h3>

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/folder-creation1.png" height="55%" width="75%"/>
</p>

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/folder-creation2.png" height="55%" width="75%"/>
</p>



<h3 align="left"> Copying Files into the S3 Bucket and Confidential Folder</h3>

Confirming Folder Bucket and Subfolder is Empty
```commandline
aws s3 ls
```
```commandline
aws s3 ls s3://financial-info-s3/
```
```commandline
aws s3 ls s3://financial-info-s3/confidential/
```
All folders have been confirmed to be empty

Copying Files into the S3 Bucket

```commandline
aws s3 cp invoice.txt s3://financial-info-s3/
```
```commandline
aws s3 cp ledger.txt s3://financial-info-s3/confidential/
```
```commandline
aws s3 cp sensitive.txt s3://financial-info-s3/confidential/
```
```commandline
aws s3 cp receipt.txt s3://financial-info-s3/confidential/
```
<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/copied-files1.png" height="55%" width="75%"/>
</p>
<h5 align="center"> invoice.txt copied into financial-info-s3 bucket</h5>

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/copied-files2.png" height="55%" width="75%"/>
</p>
<h5 align="center"> files copied into the confidential subfolder</h5>


<h3 align="left"> Policy Creation</h3>

Next, I created the identity-based policy which I will eventually attach to the users.

Deny Policy Creation
<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/deny-policy-creation1.png" height="55%" width="75%"/>
</p>

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/deny-policy-creation2.png" height="55%" width="75%"/>
</p>

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/deny-policy-creation3.png" height="55%" width="75%"/>
</p>

Click on Next

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/deny-policy-creation4.png" height="55%" width="75%"/>
</p>

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/deny-policy-creation5.png" height="55%" width="75%"/>
</p>

Allow Policy Creation

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/allow-policy-creation1.png" height="55%" width="75%"/>
</p>

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/allow-policy-creation2.png" height="55%" width="75%"/>
</p>

Click on Next

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/allow-policy-creation3.png" height="55%" width="75%"/>
</p>

<p align="center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/allow-policy-creation4.png" height="55%" width="75%"/>
</p>


<h3 align="left"> Creating the Users</h3>

Creating User Identity For Bob

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/bob1.png" height="55%" width="75%"/>
</p>

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/bob2.png" height="55%" width="75%"/>
</p>

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/bob3.png" height="55%" width="75%"/>
</p>

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/bob3.png" height="55%" width="75%"/>
</p>

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/bob5.png" height="55%" width="75%"/>
</p>

Creating User Identity For Claire

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/claire1.png" height="55%" width="75%"/>
</p>

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/claire2.png" height="55%" width="75%"/>
</p>

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/claire3.png?raw=true" height="55%" width="75%"/>
</p>

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/claire4.png" height="55%" width="75%"/>
</p>

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/claire5.png" height="55%" width="75%"/>
</p>

After creating users, the sign-in instructions are usually emailed to them, but for the sake of this demo, I downloaded the sign-in instructions.


<h3 align="left"> Test and Validation</h3>

To validate the setup, I'll sign in to both Bob and Claire's accounts and try to access the S3 Bucket. Since Bob is a sales intern and the sales department is allowed access to the financial-info-s3 bucket but not the subfolder (confidential), then Bob should only be able to access and open/view all the files in the main S3 folder but not the confidential folder, while Claire should have full access to the main folder and confidential folder since she is an Accounts Intern.

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/bob-sign-in.png" height="55%" width="75%"/>
</p>

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/bob-access1.png" height="55%" width="75%"/>
</p>
<h5 align="center"> Bob Listing the S3 Bucket Financial-Info-S3</h5>

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/bob-access2.png" height="55%" width="75%"/>
</p>
<h5 align="center"> Bob Listing the Files and Folders in the S3 Bucket</h5>

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/bob-deny-access.png" height="55%" width="75%"/>
</p>
<h5 align="center"> Bob Denied Access into the Confidential Folder</h5>

So far Bob has been unable to gain access to the confidential folder in the s3 bucket

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/claire-sign-in.png" height="55%" width="75%"/>
</p>

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/claire-access1.png" height="55%" width="75%"/>
</p>
<h5 align="center"> Claire Listing the S3 Bucket Financial-Info-S3</h5>

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/claire-access2.png" height="55%" width="75%"/>
</p>
<h5 align="center"> Claire Listing the Files and Folders in the S3 Bucket</h5>

<p align= "center">
<img src="https://github.com/Topzdomain/Granting-Identity-Based-Access-to-S3-Bucket/blob/main/screenshots/claire-access3.png" height="55%" width="75%"/>
</p>
<h5 align="center"> Claire Listing the Files and Folders in the S3 Bucket</h5>

So far, Claire was able to gain access to the confidential folder in the s3 bucket
