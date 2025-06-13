**How to Crack Password-Protected ZIP Files Using John the Ripper on Kali Linux**
=================================================================================

![John the Ripper (password cracking software tool)](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*nZLDI_59a-To0cxhBboH5Q.png)

[Reference](https://medium.com/@nikhilsiri2003/how-to-crack-password-protected-zip-files-using-john-the-ripper-on-kali-linux-2a5b46fdc1de)

by [Nikhil Raj A](https://medium.com/@nikhilsiri2003?source=post_page---byline--2a5b46fdc1de---------------------------------------)


Learn how to crack password-protected ZIP files using John the Ripper on Kali Linux in this step-by-step cybersecurity project.

**Introduction**
----------------

John the Ripper is a powerful and widely used open-source password cracking tool designed to test password strength and perform security audits. In this blog, we’ll walk through a practical, hands-on cybersecurity project where we use John the Ripper in Kali Linux to crack a ZIP file password. This exercise is ideal for cybersecurity students and beginners looking to understand password hashing and cracking fundamentals in a controlled, ethical environment.

**What is John the Ripper?**
----------------------------

John the Ripper (JTR) is an advanced password recovery tool used in penetration testing and digital forensics. It supports various hash types and file formats, including ZIP, RAR, Linux shadow files, and more. It works by attempting dictionary or brute-force attacks on hashed passwords to recover the original plaintext passwords.

Why We Used a ZIP File
----------------------

We used a ZIP file because it’s a widely supported and beginner-friendly archive format that allows password protection. It integrates smoothly with John the Ripper through the `zip2john` utility, making it easy to extract password hashes. Compared to other formats like RAR or PDF, ZIP files are quicker to set up and crack, making them ideal for educational and demonstration purposes.

**Project Setup**
-----------------

For this project, we created a password-protected ZIP file. We used Kali Linux as our ethical hacking environment and accessed it via Remote Desktop Protocol (RDP).

**Steps Overview:**
-------------------

1.  Create a ZIP file with a password.
2.  Start Kali Linux with `sudo service xrdp start`.
3.  Use `ip add` to obtain the IP address of Kali.
4.  Connect via RDP and login.
5.  Transfer the ZIP file to Kali Linux Desktop.
6.  Use John the Ripper to extract and crack the password.

**Step-by-Step Implementation**
-------------------------------

1.  **Create a Password-Protected ZIP File :**
    Choose an existing file and archive it into a ZIP format.

![creating a file into ZIP format](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*fKKbukPRYOtHm_fVoyclAg.jpeg)

Secure the file with a password to make sure no one can access the file for sensitive information present inside the file. (e.g., `121314`).

![Providing password for the ZIP file](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Yr4wgxe8IULY1ivdnXEy0w.jpeg)

**2. Start Kali Linux Environment :**

![starting the kali-linux service](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*CLVH1MR6jnHrS3ubrOxgkg.png)

Launch Kali Linux and run the command to start the XRDP service. This allows us to **start** the Kali Linux Service. After entering the command, the system prompts us to enter the system password for authentication .

```
sudo service xrdp start
```

**3. Finding the IP Address of Kali Linux :**

![Finding the IP address](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*2wt-X4kpkk22Bydgo5cr8Q.png)

To connect to the Kali Linux machine from another desktop or device — especially when retrieving files like passwords — we’ll need its IP address. This address acts as a unique identifier on the network.

To find it, open the terminal in Kali Linux and run the following command:

```
ip add
```

From the output, locate the IP address assigned to your system. In our case, the IP address was _172.26.123.22_ . This IP will be used later when establishing a remote desktop session or transferring files to and from Kali Linux.

4. **Connecting to Kali Linux via Remote Desktop :**

![connection of kali-linux](https://miro.medium.com/v2/resize:fit:916/format:webp/1*SOmeEkb1zHl2OfMo7hP8kg.png)

Now that we have the IP address of our Kali Linux machine, it’s time to connect to it remotely from another device or laptop.

On your Windows system, open the **Remote Desktop Connection** app (you can simply search for it in the Start menu). Once it launches, you’ll see a field where you need to enter the IP address — in our case, it’s `172.26.123.22`. After typing it in, click **Connect**.

A login screen will appear asking for your Kali Linux credentials. Just enter your username and password, and you’ll be logged into the Kali desktop environment — all from your remote device!

5. **Logging into Kali Linux :**

Once the remote connection is established, you’ll be redirected to the Kali Linux login screen. Here, simply enter the **username** and **password** you set up earlier during the Kali installation.

![logging-in using username and password](https://miro.medium.com/v2/resize:fit:1204/format:webp/1*z8xzEisWhdlJVA52-2iJQQ.png)

After logging in successfully, you’ll have full access to the Kali Linux desktop environment — ready to explore its powerful tools and features, all from your remote device.

**7. Transfer the ZIP File :**
Once you’re logged into Kali Linux through the remote desktop, the next step is to transfer the file you previously created on your main desktop. This file needs to be copied and pasted into the **Kali Linux desktop environment**.

**8. Preparing the File for John the Ripper :**

![changing the directory](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*cAquEBD5pmkiyjzl8vVUfQ.png)

After successfully logging into Kali Linux, the next step is to transfer the file you created earlier on your main desktop to the **Kali Linux desktop**. This makes the file easily accessible for the **John the Ripper** tool, simplifying the cracking process.

Once the file is pasted onto the Kali desktop, open the **Terminal** to proceed. To navigate to the desktop where the file is located, use the following command:

```
cd Desktop
```

This command changes the current working directory to the desktop, allowing you to interact with the file directly from the terminal.

**9. Extracting the Hash from the ZIP File :**

With the Directory now pointed to the desktop, we can begin using **John the Ripper**. To extract the hash from the ZIP file, use the following command:

```
sudo zip2john cybersecurity.zip
```

In this command, `zip2john` is the tool that processes the ZIP file, and `cybersecurity.zip` is the name of the file you want to crack. Make sure you replace the filename if your ZIP file has a different name.

![Extracting the file into Hash format](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*JWn62k_wkcF3jT1UrBvvGA.png)

After running the command, the system will prompt you to enter your **sudo (admin) password** for authentication. Once authenticated, the tool will output the **encrypted hash** of the ZIP file — this is the data that John the Ripper will attempt to crack.

**10. Saving the Hash to a Text File :**

The encrypted data output by the `zip2john` command is in **hash format**, which John the Ripper can analyze and crack efficiently. To make the process smoother, we need to save this hash into a text file.

![Forwarding the hash output to a text file](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*9a5wGyJNDvSpqcGnqfi0Cw.png)

You can do this by running the following command in the terminal:

```
sudo zip2john cybersecurity.zip > hash.txt
```

This command redirects the hashed output into a file named `hash.txt`. By doing this, we allow John the Ripper to focus directly on the hash file, making the password-cracking process more streamlined and effective.

**11. Cracking the Password Using John the Ripper :**

Now that the hash has been successfully saved into a text file (`hash.txt`), it’s time to use **John the Ripper** to crack the password.

Run the following command in the terminal:

```
john hash.txt
```

This tells John the Ripper to begin analyzing the hash and attempt to recover the original password.

After a few moments, the tool will display the cracked password. In our case, it revealed:

```
121314
```

You’ll see the password appear alongside the filename on the terminal screen. And just like that — the password-protected ZIP file has been cracked successfully!

![Password Retireived succesfully](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*V_CPk6qH4XeAkGMAXTDRag.png)

**Results**
-----------

John the Ripper successfully cracked the ZIP file password. The output displayed the plaintext password next to the filename, verifying the tool’s capability to efficiently perform dictionary-based cracking.

**Conclusion**
--------------

This project demonstrated how ethical hackers and cybersecurity students can use John the Ripper to test the strength of password-protected files. It reinforces the importance of using strong, complex passwords and the need for continuous security awareness.
