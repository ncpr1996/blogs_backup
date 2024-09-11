---
title: "AWS Elastic Block Store { Part - II }"
datePublished: Wed Sep 11 2024 08:30:30 GMT+0000 (Coordinated Universal Time)
cuid: cm0xloyct001q08kz0pqz5gwr
slug: aws-elastic-block-store-part-ii
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1725859732548/f2fd695f-adb6-4a19-a7c1-4615248966e3.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1725862439042/7d1c6966-8b24-4902-b5cc-f3fb2570a0c7.png
tags: cloud, aws, cloud-computing, devops, ebs, aws-certified-solutions-architect-associate, devops-articles, devops-trends, aws-ebs, devops-journey, ebs-snapshots, devopscommunity, elastic-block-store, aws-ebs-pricing, aws-snapshot

---

## **Amazon EBS snapshots**

* Your Amazon EBS volumes are backed up at certain points in time using Amazon EBS snapshots.
    
* Just the data that has changed since the last snapshot has been kept since snapshots are incremental.
    
* This technique minimizes storage costs and shortens the time required to create a snapshot.
    
* Amazon S3 is where EBS snapshots are kept, however neither the S3 console nor the API allow direct access to them.
    
* Using either the Amazon EC2 console or the Amazon EC2 API, snapshots can be created and managed.
    
* All the information required to restore your data to a new EBS volume is contained in each snapshot.
    
* A new EBS volume that is created from a snapshot begins as an identical replica of the original volume.
    
* You can utilize the new volume immediately because it loads data in the background.
    
* The volume will rapidly download any unloaded data from Amazon S3 if you attempt to access it.
    
* Only the information specific to a snapshot is erased when it is deleted.
    

### **Snapshot pricing**

* The cost of a snapshot is based on the volume of data you store.
    
* Erasing a snapshot might not result in cheaper storage costs because they are incremental.
    
* Only the information specific to a snapshot is erased when it is deleted.
    
* Shared data doesn't get removed from storage; it stays in place.
    
* You can check the pricing of snapshots here [Amazon Elastic Block Store Volumes and Snapshots](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/checklistforunwantedcharges.html#checkebsvolumes)
    

## **How snapshots work**

* Your EBS volumes are backed up using Amazon EBS snapshots at a particular moment in time.
    
* **Snapshots are incremental**, meaning only the data that has changed since the last snapshot is saved. This saves time and storage space.
    
* **First snapshot:** When you take an EBS volume snapshot for the first time, all of its data is copied.
    
* **Subsequent snapshots**: After the first one, only the changes made to the volume since the last snapshot are saved.
    
    **Example :**
    
    * Imagine you have a 100 GB EBS volume.
        
    * You take the first snapshot, and it saves all 100 GB of data.
        
    * After some time, you change 10 GB of data on the volume.
        
    * When you take a second snapshot, it only saves the new 10 GB of changed data, not the entire 100 GB again.
        
* **Storage location**: You cannot view snapshots directly in the S3 console, they are kept in Amazon S3.
    
* **Restoring from a snapshot**: An EBS volume is initially created as a copy of the original volume when it is created from a snapshot.
    
* **Data loading**: The data is loaded in the background by the new volume, so you can use it immediately. The volume rapidly retrieves unloaded material from Amazon S3 when you attempt to access it.
    
    **Example:**
    
    * If you create a new EBS volume from the snapshot above, it will start as a copy of the original 100 GB volume.
        
    * You can start using it immediately, even if some of the data is still being loaded in the background.
        
* **Deleting snapshots**: Only the unique data contained in a snapshot is erased when it is deleted. The data will remain saved if it is shared by other snapshots.
    
    **Example:**
    
    * If the 10 GB of changed data is unique to the second snapshot, deleting that snapshot will remove the 10 GB.
        
    * If other snapshots also reference that 10 GB, the data will stay stored.
        

## **EBS Snapshot Lifecycle**

* When you create a snapshot from an EBS volume, the snapshot's lifecycle begins.
    
* Snapshots can be used to restore newly created EBS volumes.
    
* Snapshots can be duplicated within the same Region or across other Regions.
    
* Both publicly and privately shared snapshots with other AWS accounts are possible.
    
* Volumes can be created copies of in their own account or restored from shared snapshots by other accounts.
    
* If you don't require instant access to a snapshot, you can archive it to reduce storage expenses.
    
* There are various tasks you may complete inside the snapshot lifecycle, such as making, copying, sharing, restoring, and archiving snapshots.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725848901049/2a4cde03-e2cc-4385-981f-6399c3a2e762.png align="center")
    

### Create EBS Snapshot

* An EBS volume snapshot can be made for data backup or to serve as a baseline for new volumes.
    
* If you take periodic snapshots, they are incremental, meaning each new snapshot only saves the data blocks that have changed since the last snapshot.
    
* Snapshots are created asynchronously:
    
    * The instantaneous creation of the snapshot is followed by a "pending" status until all modified data blocks are uploaded to Amazon S3.
        
    * When dealing with big or heavily modified snapshots, this operation can take several hours.
        
    * Reads and writes to the volume are not impacted while a snapshot is in progress.
        
* A volume that is being used can be snapshotted, but only data that is written to the EBS disk at the moment of the snapshot is saved.
    
    * Caches held by the operating system or applications may not contain data.
        
    * If at all possible, suspend file writes to the volume before taking the snapshot to ensure it is complete.
        
    * Unmount the volume, take a snapshot, and then remount it if you are unable to suspend writes.
        
    * The volume is still usable while the snapshot is being processed.
        
* You can add tags to your snapshots later or tag them when you create them to make maintaining snapshots easier.
    
    * For example, tags can describe the original volume or the device name used to attach the volume to an instance.
        

**Multi-Volume Snapshots**

* Multi-volume snapshots are point-in-time backups that you can do for some or all of the volumes that are connected to an instance.
    
* Multi-volume snapshots by default contain every volume connected to an instance, including the root and data volumes.
    
    * Instead of taking a photo of every attached volume, you can opt to take one for a single volume.
        
* You can tag multi-volume snapshots like single-volume snapshots.
    
    * During retention, copy, or restore, tagging helps in managing them collectively.
        
    * Additionally, tags from the source volume can be automatically copied to its snapshots. This maintains consistency between metadata and the source volume, including cost information and access controls.
        
* Every snapshot in a multi-volume set is handled as a separate snapshot after it has been created.
    
    * Just like with single snapshots, you may execute all snapshot operations across Regions or accounts, including restore, remove, and copy.
        
* Multi-volume, crash-consistent snapshots are usually restored as a group.
    
    * To distinguish these pictures as belonging to a set, it's useful to tag them with the instance ID, name, or other information.
        
* Once snapshots are created, they will show up in your EC2 console at the exact moment they were captured.
    
* In the case that one snapshot in a multi-volume collection fails, CloudWatch will send an error event to your AWS account and all other snapshots will display an error status.
    

### Copy a Snapshot

* You can make point-in-time snapshots of your volumes which are kept in Amazon S3 with Amazon EBS.
    
* You can copy a snapshot to a different AWS Region or within the same Region once it has been finished and copied to Amazon S3.
    
* Snapshot data is safeguarded during copying by means of server-side encryption (256-bit AES) provided by Amazon S3.
    
* A snapshot receives a new ID upon copying that differs from the original.
    
* Locate the snapshots using their tags, then copy each one separately to transfer multi-volume snapshots to a different Region.
    
* You must change the snapshot's permissions to grant access or make it public in order to allow another account to copy it.
    
    **Use Cases**
    
    * **Geographic expansion**: Launch applications in a new AWS Region.
        
    * **Migration**: Transfer an application to a different Region for more affordable and better availability.
        
    * **Disaster recovery**: In order to reduce data loss and recovery time in the event of a disaster, regularly backup data and logs across regions.
        
    * **Encryption**:
        
        * Encrypt a previously unencrypted snapshot.
            
        * Change the encryption key of a snapshot.
            
        * Create a copy of a shared encrypted snapshot that you own to create a new volume.
            
    * **Data retention and auditing**:
        
        * Transfer encrypted snapshots to a different AWS account for auditing or long-term storage.
            
        * In the event that the primary account is hacked, having a backup account increases security and helps avoid accidentally deletion.
            

**Incremental snapshot copying**

* The most recent completed snapshot copy determines whether a snapshot copy is incremental.
    
* When these circumstances hold true, an incremental snapshot copy is created:
    
    * Prior to this, the snapshot was duplicated to the destination region or account.
        
    * The destination Region or account still has the most recent snapshot copy.
        
    * There is no archive for the most recent snapshot copy.
        
    * The snapshots in the target Region or account are all encrypted with the same KMS key, or they are all unencrypted.
        
* The next copy will be a full copy rather than an incremental copy if the most recent snapshot copy is removed.
    
* When you begin a second duplicate, it will wait until the first is finished if it is still in process.
    
* Snapshots will always be copied incrementally when they are copied inside the same account and Region using the same KMS key.
    
* By preventing data duplication during the copy process, incremental copying saves time and money.
    
* To trace the most current snapshot copy in the destination Region or account, it is advised to tag snapshots with the volume ID and creation time.
    

### Delete a snapshot

* When an Amazon EBS snapshot is no longer needed, it can be deleted.
    
* The original EBS volume is unaffected when a snapshot is deleted.
    
* Any snapshots taken from a volume remain unaffected even after it is deleted.
    

**Incremental snapshot deletion**

* Only the data blocks that have changed since the last snapshot are saved in the incremental snapshots that are taken on a periodic basis of a volume.
    
* You just need to save the most current snapshot in order to create new volumes, even if snapshots are incremental.
    
* Even if data from previous snapshots later gets deleted from the drive, it remains unique to those earlier snapshots.
    
* Only after every snapshot that references the unique data is removed will it be erased.
    
* Only the information specific to a snapshot is erased when it is deleted.
    
* Your ability to generate volumes from more recent snapshots is unaffected by deleting previous snapshots.
    
* Removing a snapshot may not result in a decrease in storage expenses since its data may still be referenced by other snapshots.
    
* The charges are carried over to a later snapshot if it makes use of data from a deleted snapshot.
    

## Best Practices for AWS EBS Volumes

* **Regularly Create Snapshots**: Plan frequent snapshots to guarantee that your data backups are current.
    
* **Use Tags**: To make managing and identifying your snapshots easier, tag them with important information such as volume ID, creation time, and environment.
    
* **Automate Snapshots**: Utilize lifecycle policies or AWS Backup to automate the creation and maintenance of snapshots.
    
* **Monitor Snapshot Status**: Keep an eye on the progress of your snapshots to make sure they are finishing up properly.
    
* **Manage Snapshot Costs**: Review and remove outdated or unnecessary snapshots on a regular basis to control storage expenses.
    
* **Use Incremental Snapshots**: Utilize incremental snapshots to shorten backup times and save storage expenses.
    
* **Test Restores**: Test recovering from snapshots on a regular basis to make sure you can retrieve your data when you need it.
    
* **Secure Snapshots**: To secure your snapshots, use encryption. Make sure the snapshots are encrypted, and if necessary, use the same KMS key.
    
* **Copy Snapshots for Disaster Recovery**: To make sure that data is safe in the event of a regional failure, copy snapshots to many AWS regions.
    
* **Use Snapshot Tags for Compliance**: Tag snapshots to guarantee appropriate monitoring and to meet with data retention and regulation requirements.
    
* **Monitor Snapshot Operations**: To keep an eye on and create alarms for failures and snapshot operations, use AWS CloudWatch.
    

## Conclusion

* **Reliable Backup Solution**: AWS EBS snapshots offer a dependable method for protecting your EBS volumes and guaranteeing data recovery in the event of problems.
    
* **Incremental and Cost-Effective**: Incremental snapshots minimize storage costs by storing only the changes made since the last snapshot.
    
* **Flexible Management**: Snapshots are simple to make, duplicate, maintain, and share with other accounts both inside and between AWS Regions.
    
* **Automatic and Manual Options**: You can create and manage snapshots manually as needed, but they can also be automatically created using AWS Backup or lifecycle policies.
    
* **Security and Compliance**: Snapshots can be tagged for improved management, security, and auditing needs. They also offer encryption for data protection.
    

## References

* [**AWS EBS Snapshots**](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-snapshots.html)