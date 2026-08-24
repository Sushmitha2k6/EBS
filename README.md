# EBS
EBS -
# WORKING WITH EBS
## NAME: SUSHMITHA S
## REG NO: 212224230282

## Aim

To create and configure an Amazon Elastic Block Store (EBS) volume, attach and mount it to an Amazon EC2 instance, create a snapshot backup, and restore the snapshot to a new EBS volume.

---

## Algorithm / Steps

1. Create a new Amazon EBS volume with a size of 1 GiB.
2. Select the same Availability Zone as the EC2 instance.
3. Attach the EBS volume to the EC2 instance using `/dev/sdb`.
4. Connect to the EC2 instance using AWS Systems Manager Session Manager.
5. Check the available storage using `df -h`.
6. Create an `ext3` file system on the EBS volume.
7. Create the `/mnt/data-store` directory.
8. Mount the EBS volume to `/mnt/data-store`.
9. Configure `/etc/fstab` for automatic mounting.
10. Verify that the EBS volume is successfully mounted.
11. Create `file.txt` inside the mounted EBS volume.
12. Verify the contents of the created file.
13. Create an EBS snapshot named `My Snapshot`.
14. Delete `file.txt` from the original EBS volume.
15. Create a new EBS volume from the snapshot.
16. Attach the restored volume to the EC2 instance using `/dev/sdc`.
17. Create the `/mnt/data-store2` directory.
18. Mount the restored volume to `/mnt/data-store2`.
19. Verify that `file.txt` has been successfully restored.

---

## Program

### 1. Check Available Storage

```bash
df -h
```

### 2. Create an ext3 File System

```bash
sudo mkfs -t ext3 /dev/sdb
```

### 3. Create a Mount Directory

```bash
sudo mkdir /mnt/data-store
```

### 4. Mount the EBS Volume

```bash
sudo mount /dev/sdb /mnt/data-store
```

### 5. Configure Automatic Mounting

```bash
echo "/dev/sdb   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
```

### 6. View the File System Configuration

```bash
cat /etc/fstab
```

### 7. Verify the Mounted Volume

```bash
df -h
```

### 8. Create a File in the EBS Volume

```bash
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
```

### 9. Read the File

```bash
cat /mnt/data-store/file.txt
```

### 10. Delete the File

```bash
sudo rm /mnt/data-store/file.txt
```

### 11. Verify File Deletion

```bash
ls /mnt/data-store/
```

### 12. Create a Mount Directory for the Restored Volume

```bash
sudo mkdir /mnt/data-store2
```

### 13. Mount the Restored EBS Volume

```bash
sudo mount /dev/sdc /mnt/data-store2
```

### 14. Verify Snapshot Restoration

```bash
ls /mnt/data-store2/
```

Expected output:

```text
file.txt
```

---

## Outputs
<img width="1263" height="537" alt="image" src="https://github.com/user-attachments/assets/c08b79b3-1ecd-4dd7-955e-c1b09bf0adae" />
<img width="1263" height="537" alt="image" src="https://github.com/user-attachments/assets/d783c132-ced9-4d00-af89-2a6677b55d57" />


<img width="1263" height="521" alt="image" src="https://github.com/user-attachments/assets/042628f4-6318-4b2c-a061-4f5d21742c97" />

<img width="760" height="611" alt="image" src="https://github.com/user-attachments/assets/e8e2bfaa-b527-4fc4-a200-b1ce158ab6be" />

<img width="1277" height="707" alt="image" src="https://github.com/user-attachments/assets/12e02e29-70be-4915-8f09-18b9a3dee25f" />
<img width="1277" height="632" alt="image" src="https://github.com/user-attachments/assets/315cf7eb-a8e4-4ca5-8512-9f27640f9875" />
<img width="1370" height="718" alt="image" src="https://github.com/user-attachments/assets/5a151c04-6db2-48b8-8e92-302c1e4cccb5" />

<img width="1255" height="527" alt="image" src="https://github.com/user-attachments/assets/84bf016b-7bda-400d-b8a8-b9a7189ec324" />
<img width="1251" height="427" alt="image" src="https://github.com/user-attachments/assets/dd6399ec-738f-4302-af9f-00aa7f12d82f" />

## Result
Thus, an Amazon EBS volume was successfully created and attached to an Amazon EC2 instance. The volume was formatted with an ext3 file system, mounted, and used for storing data. An EBS snapshot was successfully created as a backup, and a new EBS volume was restored from the snapshot. The previously deleted file.txt was successfully recovered, demonstrating the backup and restore functionality of Amazon EBS.
