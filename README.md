# Practical-2
Creating a .txt hash file 

Use command:

```bash
echo -n 'password' | md5sum | awk '{print $1}’ > hash.txt
echo -n 'password123' | md5sum | awk '{print $1}’ >> hash.txt
echo -n 'Letmein!' | md5sum | awk '{print $1}’ >> hash.txt
echo -n 'ilovedog' | md5sum | awk '{print $1}’ >> hash.txt
echo -n '1234abcd' | md5sum | awk '{print $1}’ >> hash.txt
```

Using Hash Cat

```bash
sudo hashcat -m 0 -a 0 -o cracked.txt hash.txt /usr/share/wordlists/rockyou.txt

```
<img width="1177" height="438" alt="Screenshot 2025-07-29 131911" src="https://github.com/user-attachments/assets/d5137cdd-3757-4af8-abb8-6c41b6796653" />

<img width="762" height="399" alt="Screenshot 2025-07-29 131940" src="https://github.com/user-attachments/assets/402aa7b5-2f40-42c2-9cb7-4959cec70bbe" />

-m specifies the type of hash 

-a specifies the type of attack

-o specifies the output file 

hash.txt specifies the hash list which we created

/usr/share/wordlists/rockyou.txt specifies the wordlist

<img width="476" height="145" alt="Screenshot 2025-07-29 131956" src="https://github.com/user-attachments/assets/2b7f52cd-01b5-4eae-a937-bae6473a70d4" />


**JOHN THE RIPPER
Cracking the Password-Protected ZIP File**

Create a sample txt file

```bash
echo "Hello World" > sample.txt
```

Compress the file in a password protected zip folder

```bash
zip -e encrypted.zip sample.txt
```

Using the Zip2John tool convert the Zip file into Hash File.

```bash
zip2john encrypted.zip >encrypted.txt  
```

Then bruteforce the hashing using john tool

```bash
john —wordlist=/usr/share/wordlists/rockyou.txt encrypted.txt

```

<img width="1145" height="260" alt="Screenshot 2025-07-29 132020" src="https://github.com/user-attachments/assets/caf81900-779f-42d3-802f-f2099dee48ed" />


**RAINBOWCRACK**

First we would be generating the rainbow table

```bash
sudo rtgen md5 loweralpha 1 3 0 1000 1000 0

```
<img width="906" height="308" alt="Screenshot 2025-07-29 132034" src="https://github.com/user-attachments/assets/d4725f2d-ab58-4330-a604-055fe9a524e3" />


Then we would be sorting the table

```bash
sudo rtsort .
```

Generate a Random Hash Value:

```bash
echo -n ‘dog’ | md5sum | awk ‘{print $1}’
```

Then we would be cracking the hash

```bash
sudo rcrack -h 06d80eb0c50b49a509b49f2424e8c805

```
<img width="769" height="666" alt="Screenshot 2025-07-29 132108" src="https://github.com/user-attachments/assets/fea3b54c-d967-4346-af39-9ad98530e083" />

