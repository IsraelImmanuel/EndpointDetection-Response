This lab simulates a real-world cyber attack and endpoint detection and response scenario. Following Eric Capuano's online guide, virtual machines will be used to represent both the attacker and victim machines. The attack machine will employ 'Sliver' as the C2 framework to target a Windows endpoint, which will be protected by 'LimaCharlie' as the EDR solution.

The first step of the lab involves setting up both machines: the attack machine will use Ubuntu Server, while the endpoint will run Windows 11. To ensure the lab operates smoothly, Microsoft Defender and other relevant settings on the Windows machine should be disabled. On the Ubuntu machine, Sliver will be installed as the primary attack tool. Meanwhile, LimaCharlie will be configured on the Windows machine as the EDR solution, with a sensor linked to it and Sysmon logs being imported for analysis.

Windows 11 Machine - 
![1](https://github.com/user-attachments/assets/01bff9d4-2919-47bc-8012-02c8332cbd02)
![2](https://github.com/user-attachments/assets/798481aa-d167-4834-841b-0a8a265aa7db)
![3 5](https://github.com/user-attachments/assets/475024b9-ca68-4fad-9537-df4106cc6ce3)
![3](https://github.com/user-attachments/assets/f0c0a9e8-9fd1-4d33-925d-af062985fef9)

Ubuntu Machine-
![4](https://github.com/user-attachments/assets/ec2724f6-86c2-48de-9703-dd80a02ba04c)
