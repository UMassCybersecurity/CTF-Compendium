# CTF-Compendium

## Overview

A list of techniques and resources compiled by the UMass Pentest Club meant to serve as lookup table to solutions of CTF problems.

## Cryptography

* Caesar Cipher

	The most well known subsitution cipher. It is a type of substitution cipher in which each letter in the plaintext is 'shifted' a certain number of places down the alphabet. For example, with a shift of 1, A would be replaced by B, B would become C, and so on.

	Beware! Sometimes the alphabet used is more than just the 26 characters and can use custom character sets like all 255 ASCII characters.
	
* Subsitution Cipher

	General subsitution ciphers are often hard to crack by hand. If your cipher text is letters only, you can use the tool [quipqiup](https://quipqiup.com/) to try and solve them. If this can't solve it, it may not be a subsitution cipher.

* Symmetric encryption

	For a stream cipher (ChaCha20 or AES-CTR), the keystream can be obtained by XORing the plaintext and the ciphertext. If nonces are reused, then this keystream can be used for message forgery. AES-GCM is also extremely fragile in this way.
	// TODO describe ECB-oracle attack

* RSA
	
	**Classic RSA**

	//TODO Add factoring websites to help solve for p and q

	RSA (Rivest–Shamir–Adleman) is one of the first public-key cryptosystems and is widely used for secure data transmission.

	N is a modulus used in the private and public key, and is calculated by the product of two large primes, _**p**_ and _**q**_. The security of RSA is dependent on the fact that _**N**_ is often hard to.

	```
	N = p * q
	```

	Compute _**λ(n)**_, where _**λ(n)**_ is the Totient Function. In classical RSA, this equals the product of one less of the primes _**p**_ and _**q**_.

	```
	phi(n) = (p-1) * (q-1)
	```

	Choose a value _**e**_, between 1 and _**λ(n)**_, such that _**e**_ and _**λ(n)**_ are coprime.

	Often the plain text will be changed into it's ascii values, and then transformed into one decimal integer for the equation.

	Encrypt the plaintext by raising it's decimal value, _**m**_ to the power _**e**_, then apply mod _**N**_ to the result.

	```
	c = (m^e) % N
	```

	To decrypt the ciphertext, you must first calculate _**d**_. _**d**_ is the modular multiplicative inverse of _**e**_ mod _**λ(n)**_.

	```
	d = e mod^-1 λ(n)
	```

	After obtaining _**d**_, raise _**c**_ to the power of _**d**_ mod _**N**_ to get the original message.

	```
	m = (c^d) mod N
	```

	**Small E Attack**

	If _**e**_ is a small number, usually 3 but it can be more, the cryptosystem may be vunerable to a small _**e**_ attack. This is where _**c**_ to the power _**e**_ is less than _**N**_, allowing you to simply inverse the exponent for the plaintext.

	```
	m = log(c, e) #First argument is the number, second is the baseß
	```

	**Chinese Reainder Theorm**

	//TODO

	**MultiPrime RSA**

	//TODO

	**LSB Oracle Attack**

	//TODO

## Web

* General Tactics

	Web exploits are usually able to be classified into three categories

	- Authentication

	- Session Management 

	- Access Control

* `robots.txt` 
	
	When given a website, always check for a `robots.txt` file at the index. You may never know what will be hidden there.

* Classic Tools

	* [Requests](https://pypi.org/project/requests/2.7.0/)

		- Python library used to create http requests, very useful for challenges

	* [Curl](https://curl.haxx.se/)

		- Terminal based tool to transfer data with URLs

    * [Burpsuite](https://portswigger.net/burp)

        - Modern tool for analyzing web applications

    * [EditThisCookie](http://www.editthiscookie.com/)

        - Open-source web browser extension for editing cookies

    * [DirBuster](https://tools.kali.org/web-applications/dirbuster)

        - Multi-threaded java application that can use wordlists/brute force to find directories and files on web servers

* SQL Injections
	
	**Classic SQL Injection**

	Often when parsing user input in SQL, the request formed will be something along the lines of: 

	```
	SELECT author,title,year FROM books WHERE publisher = ‘O’Reilly’ and published=1
	```

	If the parsing of input is done incorrectly, you can use a ``` ' ``` in a input field and break out of the statement to inject your own code.

	Often an injection will be something along the lines of 

	```
	admin' OR 1=1--
	OR 1=1--
	```
* JSON Web Tokens (JWT)

    [jwt_tool](https://github.com/ticarpi/jwt_tool)

## Forensics


## Reversing

* Least Significant Bit

    //TODO

* Resources

    * [Ghidra](https://www.nsa.gov/resources/everyone/ghidra/) 
        
        - A powerful open-source reverse engineering tool developed by the NSA.

## Binary Exploitation

* Resources

    * [LiveOverflow's Youtube channel](https://www.youtube.com/channel/UClcE-kVhqyiHCcjYwcpfj9w)

        - Very detailed youtube videos that thoroughly teach and explain many common binary exploitation methods. Heavily recommended especially if you are new to binary exploitation.

## General Resources

* [Awesome-CTF](https://github.com/apsdehal/awesome-ctf)

    - A curated list of CTF frameworks, libraries, resources, softwares and tutorials. 
