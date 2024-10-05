This lab simulates a real-world cyber attack and endpoint detection and response scenario. Following Eric Capuano's online guide, virtual machines will be used to represent both the attacker and victim machines. The attack machine will employ 'Sliver' as the C2 framework to target a Windows endpoint, which will be protected by 'LimaCharlie' as the EDR solution.


SETUP

The first step of the lab involves setting up both machines: the attack machine will use Ubuntu Server, while the endpoint will run Windows 11. To ensure the lab operates smoothly, Microsoft Defender and other relevant settings on the Windows machine should be disabled. On the Ubuntu machine, Sliver will be installed as the primary attack tool. Meanwhile, LimaCharlie will be configured on the Windows machine as the EDR solution, with a sensor linked to it and Sysmon logs being imported for analysis.

Windows 11 Machine - 
![1](https://github.com/user-attachments/assets/01bff9d4-2919-47bc-8012-02c8332cbd02)
![2](https://github.com/user-attachments/assets/798481aa-d167-4834-841b-0a8a265aa7db)
![3 5](https://github.com/user-attachments/assets/475024b9-ca68-4fad-9537-df4106cc6ce3)
![3](https://github.com/user-attachments/assets/f0c0a9e8-9fd1-4d33-925d-af062985fef9)

Ubuntu Server Machine-
![4](https://github.com/user-attachments/assets/ec2724f6-86c2-48de-9703-dd80a02ba04c)



THE ATTACKS AND THE DEFENSE


The first step is to generate the payload using Sliver and implant the malware on the Windows host. Once the malware is executed on the endpoint, we can establish a command and control (C2) session.

![5](https://github.com/user-attachments/assets/c5c27bb5-a2f9-429f-bbc2-19a74842b941)
![6](https://github.com/user-attachments/assets/9d5bee94-71fc-4ad7-a96d-8b185a6565b8)
![7](https://github.com/user-attachments/assets/c5387421-b4f6-4397-b687-044b10280711)

.
.
.

With an active session established between the two machines, the attack machine can now start exploring the target. This includes checking privileges, gathering host information, and assessing the security measures in place on the host system.
![8](https://github.com/user-attachments/assets/50b6cf0a-794d-49bc-a0f5-45b3fd00717c)
![9](https://github.com/user-attachments/assets/c5f641b1-212f-4ce7-8a22-8530d45c3326)

.
.
.


On the host machine we can look inside our LimaCharlie SIEM and see telemetry from the attacker. We can identify the payload thats running and see the IP its connected to.
![10](https://github.com/user-attachments/assets/821e3313-d33b-4187-9352-12ef4d5dc512)
![11](https://github.com/user-attachments/assets/d0a212cd-d769-4095-9a00-822512b76e9d)
![12](https://github.com/user-attachments/assets/b14b286e-df62-4387-8dbb-329aaaab3aa8)

.
.
.

We can also use LimaCharlie to scan the payload's hash via VirusTotal; however, the result will be clean since the payload was just created by us.
![13](https://github.com/user-attachments/assets/c5b47c69-1cff-4c16-934d-815af746aa02)
![14](https://github.com/user-attachments/assets/ebe049a4-a6bc-491e-99c5-9b6ddeddcbbf)

.
.
.

On the attack machine, we can simulate a credential theft attack by dumping the LSASS memory. In LimaCharlie, we can monitor the sensors, review the telemetry, and create detection rules for this sensitive process.
![15](https://github.com/user-attachments/assets/472c71e8-46b9-44fc-914f-052a8b9cc844)
![16](https://github.com/user-attachments/assets/6ba5a41a-aeea-4c51-95aa-c698e8580469)
![17](https://github.com/user-attachments/assets/5a899c9f-2681-4edc-9cbb-9ad7e1793d19)


.
.
.


Instead of just focusing on detection, we can now use LimaCharlie to write a rule that both detects and blocks attacks originating from the Sliver server. On the Ubuntu machine, we can simulate aspects of a ransomware attack by attempting to delete the volume shadow copies. In LimaCharlie, we can observe the telemetry and then create a rule to fully block the attack. Once this rule is implemented in our SIEM, the Ubuntu machine will be unable to successfully carry out the same attack again.

![18](https://github.com/user-attachments/assets/2b54a0b1-416a-46d8-952d-5de814cca508)
![19](https://github.com/user-attachments/assets/342019ee-e01a-48f2-8676-6819778777f2)
![20](https://github.com/user-attachments/assets/7fe148fa-2e32-4841-b82e-4dd59b4ab41d)
![21](https://github.com/user-attachments/assets/4db16d41-3a09-4323-8440-3e0edffb9f1f)
