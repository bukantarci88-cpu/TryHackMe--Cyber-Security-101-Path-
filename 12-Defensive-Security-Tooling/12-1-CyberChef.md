# Sec. 12.1. CyberChef

#### **CyberChef**

#### **Task 1 - Introduction**

CyberChef is a simple, intuitive web-based application designed to help with various “cyber” operation tasks within your web browser. Think of it as a **Swiss Army knife** for data - like having a toolbox of different tools designed to do a specific task. These tasks range from simple encodings like **XOR** or **Base64** to complex operations like **AES encryption** or **RSA decryption**. CyberChef operates on **recipes**, a series of operations executed in order.

#### **Task 2 - Accessing the Tool**

There are different ways to access and run CyberChef. Let's check the two most convenient methods!

**Online Access:** All you need is a web browser and an internet connection. Then, you can click this [link(opens in new tab)](https://gchq.github.io/CyberChef) to open CyberChef directly within your web browser.

**Offline or Local Copy:** You can run this offline or locally on your machine by downloading the latest release file from this [link(opens in new tab)](https://github.com/gchq/CyberChef/releases). This will work on both Windows and Linux platforms. As best practice, you should download the most stable version.

#### **Task 3 - Navigating the Interface**

CyberChef consists of four areas. Each consists of different components or features.

These are the following areas:

1. Operations
2. Recipe
3. Input
4. Output

![CyberChef's main page with all the features.](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1728731934241.png)

**The Operations Area:** This is a practical and comprehensive repository of all the diverse operations that CyberChef is equipped to perform. These operations are meticulously categorized, offering users convenient access to various capabilities. Users can utilize the search feature to locate specific operations quickly, enhancing their efficiency and productivity.

| **Operations** | **Description** | **Examples** |
| --- | --- | --- |
| From Morse Code | Translates Morse Code into (upper case) alphanumeric characters. | `- .... .-. . .- - ...` becomes `THREATS` when used with default parameters |
| URL Encode | Encodes problematic characters into percent-encoding, a format supported by URIs/URLs. | `https://tryhackme.com/r/room/cyberchefbasics` becomes `https%3A%2F%2Ftryhackme%2Ecom%2Fr%2Froom%2Fcyberchefbasics` when used with the parameter “Encode all special chars” |
| To Base64 | This operation encodes raw data into an ASCII Base64 string. | `This is fun!` becomes `VGhpcyBpcyBmdW4h` |
| To Hex | Converts the input string to hexadecimal bytes separated by the specified delimiter. | `This Hex conversion is awesome!` becomes `54 68 69 73 20 48 65 78 20 63 6f 6e 76 65 72 73 69 6f 6e 20 69 73 20 61 77 65 73 6f 6d 65 21` |
| To Decimal | Converts the input data to an ordinal integer array. | `This Decimal conversion is awesome!` becomes `84 104 105 115 32 68 101 99 105 109 97 108 32 99 111 110 118 101 114 115 105 111 110 32 105 115 32 97 119 101 115 111 109 101 33` |
| ROT13 | A simple Caesar substitution cipher which rotates alphabet characters by the specified amount (default 13). | `Digital Forensics and Incident Response` becomes `Qvtvgny Sberafvpf naq Vapvqrag Erfcbafr` |

![Hovering to an operation in CyberChef tool.](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1729081368672.png)

**The Recipe Area:** This is considered as the heart of the tool. In this area, you can seamlessly select, arrange, and fine-tune operations to suit your needs. This is where you take control, defining each operation's arguments and options precisely and purposefully. The recipe area is a designated space to select and arrange specific operations and then define their respective arguments and options to customize their behaviour further. In the recipe area, you can drag the operations you want to use and specify arguments and options.

Features include the following:

- `Save recipe`: This feature allows the user to save selected operations.
- `Load recipe`: Allows the user to load previously saved recipes.
- `Clear Recipe`: This feature will enable users to clear the chosen recipe during usage.

The bottom part of the image above is the `BAKE!` button. This processes the data with the given recipe. Additionally, you can tick the `Auto Bake` checkbox. This feature allows users to automatically cook using the selected recipe without manually clicking `BAKE!` every time. Additionally, it has the following features:

- `Add a new input tab`: This is where an additional tab is created for the user to use different values from the previous tab.

![Open a new input tab option under the Input Area.](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1728731934218.png)

- `Open folder as input`: This feature allows users to upload a whole folder as input value.

![Open folder as input option under the Input Area.](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1728731934186.png)

- `Open file as input`: This feature allows the user to upload a file as its input value.

![Open file as input option under the Input Area.](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1728731934210.png)

- `Clear input and output`: This feature allows the user to clear any input values inserted and the corresponding output value.
- `Reset pane layout`: This feature brings the tool's interface to its default window sizes.

**Output Area:** The output area is a visual space that showcases the data processing results. It neatly presents the outcomes of any manipulations or transformations you have applied to the input data, allowing for a clear and intuitive display of the processed information.

![The Output area of CyberChef tool with multiple options.](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1729081715061.png)

Features include:

- `Save output to file`: This feature allows the users to save the result into a .dat file.
- `Copy raw output to the clipboard`: This feature allows users to copy raw output directly to their clipboard, allowing them to quickly copy the results for use in other applications or documents.
- `Replace input with output`: This feature allows users to quickly overwrite the input data based on the operations' results.
- `Maximise output pane`: This feature brings the tool's interface to its default window sizes.

**Answer the questions below**

> In which area can you find "From Base64"? operations
> 

> Which area is considered the heart of the tool? Recipe
> 

#### **Task 4 - Before Anything Else**

Before even going to the actual thing, let's have a quick overview of the thought process when using CyberChef! This process consists of four different steps:

![This image illustrates the thought process when using CyberChef. The first box includes setting a clear objective and answering the question What do you want to achieve? The second box includes the steps you can do with your data. The third box includes which operations you might want to use. This can be a little bit tricky if you are not familiar with the data that you have. However, there are plenty of operations that we can choose from. The last box includes determining if the output is the desired one. If not, it states to repeat the process from the first box](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1726735685403.png)

To provide visual clarity to our example, see the figure below:

![This image illustrates a more detailed thought process by including actual samples. The first box mentions that a gibberish string was found during a security incident. And we need to determine what the hidden message is. Next, we put the strings in our input area. Third, we need to determine which operations we can use through research and find any information that might be relevant. In our case, we discovered relevant information that encryption might be used, and we decided to use any operations under the Encryption/Encoding category. The last box asks if we could decode the hidden message; if not, we must repeat the process.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f9c7574e201fe31dad228fc/room-content/5f9c7574e201fe31dad228fc-1729242272295.png)

**Answer the questions below**

> At which step would you determine, "What do I want to accomplish? 1
> 

#### **Task 5 - Practice, Practice, Practice**

We want you to be as prepared as possible. Therefore, we will explore some of this task's most commonly used operation categories. Recognizing which category to utilize can enhance your ability to use the tool more efficiently and effectively.

**Extractors:** The specific operations mentioned in the table below fall under the **Extractors** category.

| **Specific** | **Description** |
| --- | --- |
| Extract IP addresses | Extracts all IPv4 and IPv6 addresses. |
| Extract URLs | Extracts Uniform Resource Locators (URLs) from the input. The protocol (HTTP, FTP, etc.) is required, otherwise there will be far too many false positives. |
| Extract email addresses | Extracts all email addresses from the input. |

The `Extract IP addresses` will extract any valid IPv4/6 address from any given input. We recommend checking our existing room for a quick recap of networking: [Networking Concepts](https://tryhackme.com/r/room/networkingconcepts)

The `Extract email addresses` extracts any strings and characters with this format, anything@domain[.]com. Examples of domains include **hotmail.com**, **google.com**, **tryhackme.com**, and **yahoo.com**

`Extract URLs` extracts Uniform Resource Locator, commonly known as URL. , a URL is the address used to access resources on the internet. You can check the [Web Applications Basics](https://tryhackme.com/r/room/webapplicationbasics) room if you would like to dig deeper into URLs and web applications.

**Date and Time:** The specific operations in the table below fall under the **Date / Time** category.

| **Specific** | **Description** |
| --- | --- |
| From UNIX Timestamp | Converts a UNIX timestamp to a datetime string. |
| To UNIX Timestamp | Parses a datetime string in UTC and returns the corresponding UNIX timestamp. |

A UNIX timestamp is a 32-bit value representing the number of seconds since January 1, 1970 UTC (the UNIX epoch). To convert "**Fri Sep 6 20:30:22 +04 2024**" into a UNIX Timestamp, use the operations `To UNIX Timestamp`, where the result would be `1725654622`. If you wish to convert it back to a more readable format, you can use `From UNIX Timestamp`.

**Data Format:** The specific operations in the table below fall under the **Data format** category.

| **Operations** | **Description** | **Examples** |
| --- | --- | --- |
| From Base64 | This operation decodes data from an ASCII Base64 string back into its raw format. | `V2VsY29tZSB0byB0cnloYWNrbWUh` becomes `Welcome to tryhackme!` |
| URL Decode | Converts URI/URL percent-encoded characters back to their raw values. | `https%3A%2F%2Fgchq%2Egithub%2Eio%2FCyberChef%2F` becomes `https://gchq.github.io/CyberChef/` |
| From Base85 | notation for encoding arbitrary byte data. It is usually more efficient than Base64. This operation decodes data from an ASCII string (with an alphabet of your choosing, presets included). | `BOu!rD]j7BEbo7` becomes `hello world` |
| From Base58 | is a notation for encoding arbitrary byte data. It differs from Base64 by removing efficiently misread characters (i.e. l, I, 0, and O) to improve human readability. | `AXLU7qR` becomes`Thm58` |
| To Base62 | is a notation for encoding arbitrary byte data using a restricted set of symbols that humans can conveniently use and process by computers. The high number base results in shorter strings than with the decimal or hexadecimal system | `Thm62` becomes`6NiRkOY` |

Operations such as `Base(64, 85, 58, 62)` are known as **base encodings**. Base encoding takes binary data (strings of 0s and 1s) and transforms it into a text-based representation using a specific set of ASCII (American Standard Code for Information Interchange) characters.Although we have a dedicated room for [Hashing Basics](https://tryhackme.com/r/room/hashingbasics), let's have a quick overview and discuss the most commonly used operation, `Base64`. Our example would be to encode the letters "**THM**". We have a short ASCII Table here that we can use for reference. If you want to view the complete ASCII Table, please refer to this page [here(opens in new tab)](https://en.wikipedia.org/wiki/ASCII).

**Step 1: Convert To Binary and Merge(Manually):** Based on our table above, **T = 01010100**, **H=01001000**, **M = 01001101**. Next, concatenate these binaries and make sure they have 24 characters. You should have `010101000100100001001101`

**Step 2: Divide and Convert to Decimal(Manually):** Separate `010101000100100001001101` into 6 characters each. You should have `010101` `000100` `100001` `001101`. These are 6-bit characters; we should have four instances of this now. We need to convert each instance to Decimal. Let's convert, then!

| **Binary** | **Decimal (Base10)** |
| --- | --- |
| 010101 | 21 |
| 000100 | 4 |
| 100001 | 33 |
| 001101 | 13 |

**Step 3: Convert to Base64 (Manually):** Now that we have the Numbers from the previous step, which are `21`, `4`, `33`, and `13`, let's look for the equivalent characters from our table below. This table represents a base64 index table.

| **Index** | **Character** | **-** | **Index** | **Character** | **-** | **Index** | **Character** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | **A** |  | 26 | **a** |  | 52 | **0** |
| 1 | **B** |  | 27 | **b** |  | 53 | **1** |
| 2 | **C** |  | 28 | **c** |  | 54 | **2** |
| 3 | **D** |  | 29 | **d** |  | 55 | **3** |
| 4 | **E** |  | 30 | **e** |  | 56 | **4** |
| 5 | **F** |  | 31 | **f** |  | 57 | **5** |
| 6 | **G** |  | 32 | **g** |  | 58 | **6** |
| 7 | **H** |  | 33 | **h** |  | 59 | **7** |
| 8 | **I** |  | 34 | **i** |  | 60 | **8** |
| 9 | **J** |  | 35 | **j** |  | 61 | **9** |
| 10 | **K** |  | 36 | **k** |  | 62 | **+** |
| 11 | **L** |  | 37 | **l** |  | 63 | **/** |
| 12 | **M** |  | 38 | **m** |  |  |  |
| 13 | **N** |  | 39 | **n** |  |  |  |
| 14 | **O** |  | 40 | **o** |  |  |  |
| 15 | **P** |  | 41 | **p** |  |  |  |
| 16 | **Q** |  | 42 | **q** |  |  |  |
| 17 | **R** |  | 43 | **r** |  |  |  |
| 18 | **S** |  | 44 | **s** |  |  |  |
| 19 | **T** |  | 45 | **t** |  |  |  |
| 20 | **U** |  | 46 | **u** |  |  |  |
| 21 | **V** |  | 47 | **v** |  |  |  |
| 22 | **W** |  | 48 | **w** |  |  |  |
| 23 | **X** |  | 49 | **x** |  |  |  |
| 24 | **Y** |  | 50 | **y** |  |  |  |
| 25 | **Z** |  | 51 | **z** |  |  |  |

Upon checking from the table, we should have found its corresponding character by now.

| **Index** | **Characters** |
| --- | --- |
| 21 | V |
| 4 | E |
| 33 | h |
| 13 | N |

Combine these characters, and you should have the equivalent of "THM" in base64 format. The answer would be `VEhN`. Woah! Isn't that amazing? You just converted a set of characters into base64 manually. Now, let’s discuss the `URL Decode`. This works by converting the percent-encoded characters back to their raw values. For a reference of these values, you can check the page [here(opens in new tab)](https://en.wikipedia.org/wiki/Percent-encoding). Note that the default character set in HTML5 is **UTF-8**. Check the table below for a quick overview of what we can typically see in a URL.

| **Characters** | **From UTF-8** |
| --- | --- |
| : | %3A |
| / | %2F |
| . | %2E |
| = | %3D |
| # | %23 |

**Practical Exercise:** Click on the **Download Task Files** button at the top of this task to download the file that we will use to answer the questions below. Once downloaded, you can open the file, copy and paste the content into the input field, or use the `Open file as input` feature to upload the file. **Note:** Use the specific operations under the Extractors category for the first two questions. It's best to try to answer the questions first without using the hints.

**Answer the questions below:**

> What is the hidden email address? [hidden@hotmail.com](mailto:hidden@hotmail.com)
> 

> What is the hidden IP address that ends in .232? 102.20.11.232
> 

> Which domain address starts with the letter "T"? [TryHackMe.com](http://tryhackme.com/)
> 

> What is the binary value of the decimal number 78? 01001110
> 

> What is the URL encoded value of [https://tryhackme.com/r/careers](https://tryhackme.com/r/careers)? [https://tryhackme.com/r/careers](https://tryhackme.com/r/careers____________)
> 

#### **Task 6 - Your First Official Cook**

This task allows us to apply what we've learned from the previous tasks. We'll utilize CyberChef's areas and its features to answer the questions being asked. Now, this is the time that you truly shine! **Note:** It's best to try to answer the questions first without using the hints.

**Answer the questions below**

> Using the file you downloaded in Task 5, which IP starts and ends with "10"?  10.10.2.10
> 

> What is the base64 encoded value of the string "Nice Room!"? TmljZSBSb29tIQ==
> 

> What is the URL decoded value for https%3A%2F%2Ftryhackme%2Ecom%2Fr%2Froom%2Fcyberchefbasics? [https://tryhackme.com/r/room/cyberchefbasics](https://tryhackme.com/r/room/cyberchefbasics)
> 

> What is the datetime string for the Unix timestamp 1725151258? Sun 1 September 2024 00:40:58 UTC
> 

> What is the Base85 decoded string of the value <+oue+DGm>Ap%u7? This is fun!
> 

#### **Task 7 - Conclusion**

In this room, we discussed how CyberChef is a powerful tool for handling various data transformations and decoding tasks. Whether you need to work with Base64, Binary, or URLs, this digital wizard's kitchen provides a visual interface that makes data manipulation intuitive and straightforward. With a diverse recipe library, you can confidently tackle tasks ranging from extracting email addresses, IP addresses, and domains. We were able to navigate its interface and have a high-level discussion of the different areas, features, and parameters. However, note that for particularly large-scale processing, it's vital to benefit from support from other tools.
