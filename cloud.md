

Challenge Name:  Cloud Infiltration
Catagory:Cloud Security

Desc:

Elena, the lead security officer at TechCore Solutions, suspects a vulnerability in their cloud infrastructure. She’s given you limited access to their system to investigate. Your mission: navigate the cloud terminal, uncover hidden files, and retrieve the flag.

The first to find it will earn a special reward. Can you outsmart their defenses and crack the system?

Starting Point: [Cloud Terminal](https://insanecloud.s3.us-east-1.amazonaws.com/aws.html)



![image](https://github.com/user-attachments/assets/b8296b6e-82b5-4942-8dae-5f6980b8973c)


 Walkthrough

 1. Starting the AWS Session  
Begin by configuring AWS CLI with the provided credentials:
```bash
aws configure
```
- Access Key: `AKIAVRUVTQEOE56R3NET`
- Secret Key: `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`
- Region: `us-east-1`

---

 2. Check EC2 Instance Status  
Verify the status of the instance:
```bash
aws ec2 describe-instance-status
```
Output:
- Instance ID: `i-01664eeea278b8c48`
- State: Running

---

 3. Establishing SSM Session  
Connect to the instance using AWS Systems Manager:
```bash
aws ssm start-session --target i-01664eeea278b8c48
```
This successfully initiated a session with the instance.

---

 4. Navigating the Filesystem  
Explore the file structure:
```bash
ls
cat Hint.txt
```
- Hint: "The flag is in `/home/ubuntu/flag.txt`."

  ![image](https://github.com/user-attachments/assets/007d8cae-1597-4ca0-83fb-534846321164)


---

 5. Encountering Challenges  
Initial attempts to access `/home/ubuntu` failed due to:
- Mistyping `ubuntu` as `ubunut`.
- Permission issues for navigating directly to `/home/ubuntu`.

---

 6. Switching to the Correct User  
Switch to the `ubuntu` user using `sudo`:
```bash
sudo su - ubuntu
```


---

 7. Retrieving the Flag  
As the `ubuntu` user:
```bash
cd ~
ls
cat flag.txt
```
- Flag: `r00t@localhost{c10udy_d4ys_4re_fun_1f_cr34tiv3_th1ngs_t0_d0_happens}`
