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

![Screenshot 2025-07-29 131911.png](attachment:b7393aa1-a7f1-48ac-992a-c997c994132a:Screenshot_2025-07-29_131911.png)

![Screenshot 2025-07-29 131940.png](attachment:e3578a5a-15be-4b17-b073-3049ca5be690:Screenshot_2025-07-29_131940.png)

-m specifies the type of hash 

-a specifies the type of attack

-o specifies the output file 

hash.txt specifies the hash list which we created

/usr/share/wordlists/rockyou.txt specifies the wordlist

![Screenshot 2025-07-29 131956.png](attachment:529ac5f2-1fd0-4fda-aada-80abd769b485:Screenshot_2025-07-29_131956.png)

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

![Screenshot 2025-07-29 132020.png](attachment:e26f94a3-0d22-4530-a1fd-de687a24e063:Screenshot_2025-07-29_132020.png)

**RAINBOWCRACK**

First we would be generating the rainbow table

```bash
sudo rtgen md5 loweralpha 1 3 0 1000 1000 0

```

![Screenshot 2025-07-29 132034.png](attachment:6c346ddd-3931-458c-9e74-f08bfbaceced:Screenshot_2025-07-29_132034.png)

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

![Screenshot 2025-07-29 132108.png](attachment:790322c4-0611-48f4-bcaf-8e56ba036727:Screenshot_2025-07-29_132108.png)
