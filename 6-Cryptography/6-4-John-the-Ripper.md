# Sec. 6.4. John the Ripper

#### **John the Ripper**

#### **Task 1 - Introduction**

John the Ripper is a well-known, well-loved, and versatile hash-cracking tool. It combines a fast cracking speed with an extraordinary range of compatible hash types.

John the Ripper is an open-source password-cracking tool used to audit password security by attempting to recover plaintext passwords from password hashes. It supports many hash formats and can perform dictionary attacks, brute-force attacks, and other password-cracking techniques.

#### **Task 2 - Basic Terms**

A hash is a way of taking a piece of data of any length and representing it in another fixed-length form. This process masks the original value of the data. The hash value is obtained by running the original data through a hashing algorithm. Many popular hashing algorithms exist, such as MD4, MD5, SHA1 and NTLM. 

If we take “polo”, a string of four characters, and run it through an MD5 hashing algorithm, we end up with an output of `b53759f3ce692de7aff1b5779d3964da`, a standard 32-character MD5 hash.

Likewise, if we take “polomints”, a string of 9 characters, and run it through the same MD5 hashing algorithm, we end up with an output of `584b6e4f4586e136bc280f27f9c64f3b`, another standard 32-character MD5 hash.

**What Makes Hashes Secure?** Hashing functions are designed as one-way functions. In other words, it is easy to calculate the hash value of a given input; however, it is a hard problem to find the original input given the hash value. In simple terms, a hard problem quickly becomes computationally infeasible in computer science. This computational problem has its roots in mathematics as P vs NP. In computer science, P and NP are two classes of problems that help us understand the efficiency of algorithms:

- **P (Polynomial Time)**: Class P covers the problems whose solution can be found in polynomial time. Consider sorting a list in increasing order. The longer the list, the longer it would take to sort; however, the increase in time is not exponential.
- **NP (Non-deterministic Polynomial Time)**: Problems in the class NP are those for which a given solution can be checked quickly, even though finding the solution itself might be hard. In fact, we don’t know if there is a fast algorithm to find the solution in the first place.

**Answer the questions below**

> What is the most popular extended version of John the Ripper? Jumbo John
> 

#### **Task 3 - Setting Up Your System**

Throughout the tasks of this room, we will be using the following :

- The “Jumbo John” version of John the Ripper
- The RockYou password list

If you use the attached lab machine or the AttackBox, you don’t need to install John the Ripper on your system. Consequently, feel free to skip through the installation section. If you prefer to use your system to follow along, please read along to learn how to proceed with the installation. We should note that if you use a version of John the Ripper other than Jumbo John, you might not have some of the required tools, such as `zip2john` and `rar2john`.

John the Ripper is supported on many Operating Systems, not just Linux Distributions. Before we go through this, there are multiple versions of John, the standard “core” distribution, and multiple community editions, which extend the feature set of the original John distribution. The most popular of these distributions is the “**Jumbo John**,” which we will use specific features of later.

You can double-check this by typing `john` into the terminal. You should be met with a usage guide for John, with the first line reading “John the Ripper 1.9.0-jumbo-1” or something similar with a different version number.

Many Linux distributions have John the Ripper available for installation from their official repositories. For instance, on Fedora Linux, you can install John the Ripper with `sudo dnf install john`, while on Ubuntu, you can install it with `sudo apt install john`. Unfortunately, at the time of writing, these versions provided core functionality and missed some of the tools available through Jumbo John.

**Wordlists:** Now that we have `john` ready, we must consider another indispensable component: wordlists. On the AttackBox and Kali Linux distributions, the `/usr/share/wordlists` directory contains a series of great wordlists.

**RockYou:** For all of the tasks in this room, we will use the infamous `rockyou.txt` wordlist, a very large common password wordlist obtained from a data breach on a website called rockyou.com in 2009. If you are not using any of the above distributions, you can get the `rockyou.txt` wordlist from the [SecLists(opens in new tab)](https://github.com/danielmiessler/SecLists) repository under the `/Passwords/Leaked-Databases` subsection. You may need to extract it from the `.tar.gz` format using `tar xvzf rockyou.txt.tar.gz`.

**Answer the questions below**

> Which website’s breach was the rockyou.txt wordlist created from? [rockyou.com](http://rockyou.com/)
> 

#### **Task 4 - Cracking Basic Hashes**

There are multiple ways to use John the Ripper to crack simple hashes. 

**John Basic Syntax:** The basic syntax of John the Ripper commands is as follows. We will cover the specific options and modifiers used as we use them.

`john [options] [file path]`

- `john`: Invokes the John the Ripper program
- `[options]`: Specifies the options you want to use
- `[file path]`: The file containing the hash you’re trying to crack; if it’s in the same directory, you won’t need to name a path, just the file.

**Automatic Cracking:** John has built-in features to detect what type of hash it’s being given and to select appropriate rules and formats to crack it for you; this isn’t always the best idea as it can be unreliable, but if you can’t identify what hash type you’re working with and want to try cracking it, it can be a good option! To do this, we use the following syntax:

`john --wordlist=[path to wordlist] [path to file]`

- `-wordlist=`: Specifies using wordlist mode, reading from the file that you supply in the provided path
- `[path to wordlist]`: The path to the wordlist you’re using, as described in the previous task

**Example Usage:** `john --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt`

**Identifying Hashes:** Sometimes, John won’t play nicely with automatically recognising and loading hashes, but that’s okay! We can use other tools to identify the hash and then set John to a specific format. To use hash-identifier, you can use `wget` or `curl` to download the Python file `hash-id.py` from its GitLab [page(opens in new tab)](https://gitlab.com/kalilinux/packages/hash-identifier/-/raw/kali/master/hash-id.py). Then, launch it with `python3 hash-id.py` and enter the hash you’re trying to identify. It will give you a list of the most probable formats. These two steps are shown in the terminal below.

**Format-Specific Cracking:** Once you have identified the hash that you’re dealing with, you can tell John to use it while cracking the provided hash using the following syntax:

`john --format=[format] --wordlist=[path to wordlist] [path to file]`

- `-format=`: This is the flag to tell John that you’re giving it a hash of a specific format and to use the following format to crack it
- `[format]`: The format that the hash is in

**Example Usage:** `john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt`

**A Note on Formats:** When you tell John to use formats, if you’re dealing with a standard hash type, e.g. md5 as in the example above, you have to prefix it with `raw-` to tell John you’re just dealing with a standard hash type, though this doesn’t always apply. To check if you need to add the prefix or not, you can list all of John’s formats using `john --list=formats` and either check manually or grep for your hash type using something like `john --list=formats | grep -iF "md5"`.

**Practical:** Now that you know the syntax, modifiers, and methods for cracking basic hashes, try it yourself! The files are located in `~/John-the-Ripper-The-Basics/Task04/` on the attached lab machine.

**Answer the questions below**

> What type of hash is hash1.txt? md5
> 

<img width="686" height="396" alt="image" src="https://github.com/user-attachments/assets/46113792-9317-44a7-8c75-2f582aabae4c" />

<img width="690" height="393" alt="image 1" src="https://github.com/user-attachments/assets/22a02b5b-46ab-4eba-8725-7e85f0e102d1" />


> What is the cracked value of hash1.txt? biscuit
> 

<img width="683" height="241" alt="image 2" src="https://github.com/user-attachments/assets/f505fbc0-da84-4acf-8ebf-9bcd6fdbd04d" />


> What type of hash is hash2.txt? sha1
> 

<img width="636" height="203" alt="image 3" src="https://github.com/user-attachments/assets/871ef554-aa9b-428b-8b53-e114b9396bd9" />


> What is the cracked value of hash2.txt? kangeroo
> 

<img width="688" height="417" alt="image 4" src="https://github.com/user-attachments/assets/2daff852-fd3c-42da-a28d-c627a55a0c08" />


> What type of hash is hash3.txt? sha256
> 

<img width="682" height="236" alt="image 5" src="https://github.com/user-attachments/assets/1029f4c0-adcd-407c-9481-fed13a792ade" />


> What is the cracked value of hash3.txt? microphone
> 

<img width="687" height="261" alt="image 6" src="https://github.com/user-attachments/assets/c4b85282-ab65-41dd-89c0-0816c41e4858" />


> What type of hash is hash4.txt? whirlpool
> 

<img width="693" height="192" alt="image 7" src="https://github.com/user-attachments/assets/605f869e-900c-4652-b6db-78db48c4adee" />


> What is the cracked value of hash4.txt? colossal
> 

<img width="683" height="222" alt="image 8" src="https://github.com/user-attachments/assets/b7266c17-cf87-446c-b3bf-c9fb333bcbbf" />


#### **Task 5 - Cracking Windows Authentication Hashes**

Authentication hashes are the hashed versions of passwords stored by operating systems; it is sometimes possible to crack them using our brute-force methods. To get your hands on these hashes, you must often already be a privileged user, so we will explain some of the hashes we plan on cracking as we attempt them.

**NTHash / NTLM:** NThash is the hash format modern Windows operating system machines use to store user and service passwords. It’s also commonly referred to as NTLM, which references the previous version of Windows format for hashing passwords known as LM, thus NT/LM.

**Practical:** Now that you know the theory behind it, see if you can use the techniques we practised in the last task and the knowledge of what type of hash this is to crack the `ntlm.txt` file! The file is located in `~/John-the-Ripper-The-Basics/Task05/`.

**Answer the questions below**

> What do we need to set the --format flag to in order to crack this hash? nt
> 

> What is the cracked value of this password? mushroom
> 

<img width="642" height="270" alt="image 9" src="https://github.com/user-attachments/assets/be051f84-bbf8-43dd-b6c4-ec895f16ffda" />


#### **Task 6 - Cracking /etc/shadow Hashes**

**Cracking Hashes from /etc/shadow :** The `/etc/shadow` file is the file on Linux machines where password hashes are stored. It also stores other information, such as the date of last password change and password expiration information. It contains one entry per line for each user or user account of the system. This file is usually only accessible by the root user, so you must have sufficient privileges to access the hashes. However, if you do, there is a chance that you will be able to crack some of the hashes.

**Unshadowing:** John can be very particular about the formats it needs data in to be able to work with it; for this reason, to crack `/etc/shadow` passwords, you must combine it with the `/etc/passwd` file for John to understand the data it’s being given. To do this, we use a tool built into the John suite of tools called `unshadow`. The basic syntax of `unshadow` is as follows:

`unshadow [path to passwd] [path to shadow]`

- `unshadow`: Invokes the unshadow tool
- `[path to passwd]`: The file that contains the copy of the `/etc/passwd` file you’ve taken from the lab machine
- `[path to shadow]`: The file that contains the copy of the `/etc/shadow` file you’ve taken from the lab machine

**Example Usage: :** `unshadow local_passwd local_shadow > unshadowed.txt`

When using `unshadow`, you can either use the entire `/etc/passwd` and `/etc/shadow` files, assuming you have them available, or you can use the relevant line from each, for example:

**FILE 1 - local_passwd :** Contains the `/etc/passwd` line for the root user: `root:x:0:0::/root:/bin/bash`

**FILE 2 - local_shadow :** Contains the `/etc/shadow` line for the root user: `root:$6$2nwjN454g.dv4HN/$m9Z/r2xVfweYVkrr.v5Ft8Ws3/YYksfNwq96UL1FX0OJjY1L6l.DS3KEVsZ9rOVLB/ldTeEL/OIhJZ4GMFMGA0:18576::::::`

**Cracking:** We can then feed the output from `unshadow`, in our example use case called `unshadowed.txt`, directly into John. We should not need to specify a mode here as we have made the input specifically for John; however, in some cases, you will need to specify the format as we have done previously using: `--format=sha512crypt`

`john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt`

**Practical:** Now, see if you can follow the process to crack the password hash of the root user provided in the `etchashes.txt` file. Good luck! The files are located in `~/John-the-Ripper-The-Basics/Task06/`.

**Answer the questions below**

> What is the root password? 1234
> 

<img width="641" height="656" alt="image 10" src="https://github.com/user-attachments/assets/fb371566-2fa7-45fa-bcf9-77e77cd4575d" />

<img width="630" height="250" alt="image 11" src="https://github.com/user-attachments/assets/c9781b6a-e161-4819-aea6-64e2f3686986" />


#### **Task 7 - Single Crack Mode**

So far, we’ve been using John’s wordlist mode to brute-force simple and not-so-simple hashes. But John also has another mode, called the **Single Crack** mode. In this mode, John uses only the information provided in the username to try and work out possible passwords heuristically by slightly changing the letters and numbers contained within the username.

**Using Single Crack Mode:** To use single crack mode, we use roughly the same syntax that we’ve used so far; for example, if we wanted to crack the password of the user named “Mike”, using the single mode, we’d use: `john --single --format=[format] [path to file]`

- `-single`: This flag lets John know you want to use the single hash-cracking mode
- `-format=[format]`: As always, it is vital to identify the proper format.

**Example Usage:**`john --single --format=raw-sha256 hashes.txt`

**A Note on File Formats in Single Crack Mode:** If you’re cracking hashes in single crack mode, you need to change the file format that you’re feeding John for it to understand what data to create a wordlist from. You do this by prepending the hash with the username that the hash belongs to, so according to the above example, we would change the file `hashes.txt`

**From** `1efee03cdcb96d90ad48ccc7b8666033`

**To** `mike:1efee03cdcb96d90ad48ccc7b8666033`

**Practical:** Now that you’re familiar with the Syntax for John’s single crack mode, access the hash and crack it, assuming that the user it belongs to is called “Joker”. The file is located in `~/John-the-Ripper-The-Basics/Task07/`.

**Answer the questions below**

> What is Joker’s password? Jok3r
> 

<img width="635" height="548" alt="image 12" src="https://github.com/user-attachments/assets/18f18ba1-cfac-4606-86b0-818057191c11" />


#### **Task 8 - Custom Rules**

**What are Custom Rules?** As we explored what John can do in Single Crack Mode, you may have some ideas about some good mangling patterns or what patterns your passwords often use that could be replicated with a particular mangling pattern. The good news is that you can define your rules, which John will use to create passwords dynamically. The ability to define such rules is beneficial when you know more information about the password structure of whatever your target is.

**Common Custom Rules** Many organisations will require a certain level of password complexity to try and combat dictionary attacks. In other words, when creating a new account or changing your password, if you attempt a password like `polopassword`, it will most likely not work. The reason would be the enforced password complexity. As a result, you may receive a prompt telling you that passwords have to contain at least one character from each of the following:

- Lowercase letter
- Uppercase letter
- Number
- Symbol

Password complexity is good! However, we can exploit the fact that most users will be predictable in the location of these symbols. For the above criteria, many users will use something like the following:

`Polopassword1!`

Consider the password with a capital letter first and a number followed by a symbol at the end. This familiar pattern of the password, appended and prepended by modifiers (such as capital letters or symbols), is a memorable pattern that people use and reuse when creating passwords. This pattern can let us exploit password complexity predictability.

Now, this does meet the password complexity requirements; however, as attackers, we can exploit the fact that we know the likely position of these added elements to create dynamic passwords from our wordlists.

**How to create Custom Rules:** Custom rules are defined in the `john.conf` file. This file can be found in `/opt/john/john.conf` on the TryHackMe Attackbox. It is usually located in `/etc/john/john.conf` if you have installed John using a package manager or built from source with `make`.

The first line: `[List.Rules:THMRules]` is used to define the name of your rule; this is what you will use to call your custom rule a John argument.

We then use a regex style pattern match to define where the word will be modified; again, we will only cover the primary and most common modifiers here:

- `Az`: Takes the word and appends it with the characters you define
- `A0`: Takes the word and prepends it with the characters you define
- `c`: Capitalises the character positionally

These can be used in combination to define where and what in the word you want to modify. Lastly, we must define what characters should be appended, prepended or otherwise included. We do this by adding character sets in square brackets `[ ]` where they should be used. These follow the modifier patterns inside double quotes `" "`. Here are some common examples:

- `[0-9]`: Will include numbers 0-9
- `[0]`: Will include only the number 0
- `[A-z]`: Will include both upper and lowercase
- `[A-Z]`: Will include only uppercase letters
- `[a-z]`: Will include only lowercase letters

Please note that:

- `[a]`: Will include only `a`
- `[!£$%@]`: Will include the symbols `!`, `£`, `$`, `%`, and `@`

Putting this all together, to generate a wordlist from the rules that would match the example password `Polopassword1!` (assuming the word `polopassword` was in our wordlist), we would create a rule entry that looks like this:

`[List.Rules:PoloPassword]`

`cAz"[0-9] [!£$%@]"`

Utilises the following:

- `c`: Capitalises the first letter
- `Az`: Appends to the end of the word
- `[0-9]`: A number in the range 0-9
- `[!£$%@]`: The password is followed by one of these symbols

**Using Custom Rules:** 

We could then call this custom rule a John argument using the  `--rule=PoloPassword` flag.

As a full command: `john --wordlist=[path to wordlist] --rule=PoloPassword [path to file]`

As a note, I find it helpful to talk out the patterns if you’re writing a rule; as shown above, the same applies to writing RegEx patterns.Jumbo John already has an extensive list of custom rules containing modifiers for use in almost all cases. If you get stuck, try looking at those rules [around line 678] if your syntax isn’t working correctly.

**Answer the questions below**

> What do custom rules allow us to exploit? Password complexity predictability
> 

> What rule would we use to add all capital letters to the end of the word? Az"[A-Z]"
> 

> What flag would we use to call a custom rule called THMRules? -rule=THMRules
> 

#### **Task 9 - Cracking Password Protected Zip Files**

We can use John to crack the password on password-protected Zip files. Again, we’ll use a separate part of the John suite of tools to convert the Zip file into a format that John will understand, but we’ll use the syntax you’re already familiar with for all intents and purposes.

**Zip2John:** Similarly to the `unshadow` tool we used previously, we will use the `zip2john` tool to convert the Zip file into a hash format that John can understand and hopefully crack. The primary usage is like this:

`zip2john [options] [zip file] > [output file]`

- `[options]`: Allows you to pass specific checksum options to `zip2john`; this shouldn’t often be necessary
- `[zip file]`: The path to the Zip file you wish to get the hash of
- `>`: This redirects the output from this command to another file
- `[output file]`: This is the file that will store the output

**Example Usage:** `zip2john zipfile.zip > zip_hash.txt`

**Cracking**

We’re then able to take the file we output from `zip2john` in our example use case, `zip_hash.txt`, and, as we did with `unshadow`, feed it directly into John as we have made the input specifically for it.

`john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt`

**Practical:** Now, have a go at cracking a “secure” Zip file! The file is located in `~/John-the-Ripper-The-Basics/Task09/`.

**Answer the questions below**

> What is the password for the secure.zip file? pass123
> 

<img width="647" height="527" alt="image 13" src="https://github.com/user-attachments/assets/9a63f75d-52ba-4188-896f-8509b71a9360" />


> What is the contents of the flag inside the zip file? THM{w3ll_d0n3_h4sh_r0y4l}
> 

<img width="647" height="362" alt="image 14" src="https://github.com/user-attachments/assets/8d5c9f17-6695-4d2f-b042-5dd01b91975e" />


#### **Task 10 - Cracking Password-Protected RAR Archives**

**Cracking a Password-Protected RAR Archive:** We can use a similar process to the one we used in the last task to obtain the password for RAR archives. If you aren’t familiar, RAR archives are compressed files created by the WinRAR archive manager. Like Zip files, they compress folders and files.

**Rar2John:** Almost identical to the `zip2john` tool, we will use the `rar2john` tool to convert the RAR file into a hash format that John can understand. The basic syntax is as follows:

`rar2john [rar file] > [output file]`

- `rar2john`: Invokes the `rar2john` tool
- `[rar file]`: The path to the RAR file you wish to get the hash of
- `>`: This redirects the output of this command to another file
- `[output file]`: This is the file that will store the output from the command

**Example Usage** `/opt/john/rar2john rarfile.rar > rar_hash.txt`

**Cracking** Once again, we can take the file we output from `rar2john` in our example use case, `rar_hash.txt`, and feed it directly into John as we did with `zip2john`.

`john --wordlist=/usr/share/wordlists/rockyou.txt rar_hash.txt`

**Practical:** Now, have a go at cracking a “secure” RAR file! The file is located in `~/John-the-Ripper-The-Basics/Task10/`.

**Answer the questions below**

> What is the password for the secure.rar file? password
> 

<img width="642" height="436" alt="image 15" src="https://github.com/user-attachments/assets/80b3bbb6-81cf-4e31-96de-7145611590bf" />


> What are the contents of the flag inside the rar file? THM{r4r_4rch1ve5_th15_t1m3}
> 

<img width="626" height="287" alt="image 16" src="https://github.com/user-attachments/assets/c52fdaf8-9a56-4777-af08-4f641cdc3edf" />

<img width="643" height="447" alt="image 17" src="https://github.com/user-attachments/assets/b8ff02db-78ec-4199-a08d-00c90a587af1" />


#### **Task 11 - Cracking SSH Keys with John**

**Cracking SSH Key Passwords:** Frequently in CTF challenges—using John to crack the SSH private key password of `id_rsa` files. Unless configured otherwise, you authenticate your SSH login using a password. However, you can configure key-based authentication, which lets you use your private key, `id_rsa`, as an authentication key to log in to a remote machine over SSH. However, doing so will often require a password to access the private key; here, we will be using John to crack this password to allow authentication over SSH using the key.

**SSH2John:** Who could have guessed it, another conversion tool? Well, that’s what working with John is all about. As the name suggests, `ssh2john` converts the `id_rsa` private key, which is used to log in to the SSH session, into a hash format that John can work with. Jokes aside, it’s another beautiful example of John’s versatility. The syntax is about what you’d expect. Note that if you don’t have `ssh2john` installed, you can use `ssh2john.py`, located in the `/opt/john/ssh2john.py`. If you’re doing this on the AttackBox, replace the `ssh2john` command with `python3 /opt/john/ssh2john.py` or on Kali, `python /usr/share/john/ssh2john.py`.

`ssh2john [id_rsa private key file] > [output file]`

- `ssh2john`: Invokes the `ssh2john` tool
- `[id_rsa private key file]`: The path to the id_rsa file you wish to get the hash of
- `>`: This is the output director. We’re using it to redirect the output from this command to another file.
- `[output file]`: This is the file that will store the output from

**Example Usage:** `/opt/john/ssh2john.py id_rsa > id_rsa_hash.txt`

**Cracking:** For the final time, we’re feeding the file we output from ssh2john, which in our example use case is called `id_rsa_hash.txt` and, as we did with `rar2john`, we can use this seamlessly with John:

`john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa_hash.txt`

**Practical:** Now, I’d like you to crack the hash of the `id_rsa` file relevant to this task! The file is located in `~/John-the-Ripper-The-Basics/Task11/`.

**Answer the questions below**

> What is the SSH private key password? mango
> 

<img width="727" height="281" alt="image 18" src="https://github.com/user-attachments/assets/ca0e03a5-5364-4f63-b1bd-3ea06ebb667e" />
