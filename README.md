# CTF-Compendium

> UMass Pentest Club

---

A list of CTF problems, techniques and guides mean to be a lookup table to possible solutions of CTF problems

## **Cryptography**

---

* Caesar Cipher

	The most well known subsitution cipher. It is a type of substitution cipher in which each letter in the plaintext is 'shifted' a certain number of places down the alphabet. For example, with a shift of 1, A would be replaced by B, B would become C, and so on.

	Beware! Sometimes the alphabet used is more than just the 26 characters and can use custom character sets like all 255 ASCII characters.
	
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

## **Web**

---

* Robots.txt 
	
	When given a website, always check for a /robots.txt file at the root link. You may never know what will be hidden there.

* Tools

    * [Burpsuite](https://portswigger.net/burp)

        - Modern tool for analyzing web applications.

    * [EditThisCookie](http://www.editthiscookie.com/)

        - Open-source web browser extension for editing cookies.

    * [DirBuster](https://tools.kali.org/web-applications/dirbuster)

        - Multi-threaded java application that can use wordlists/brute force to find directories and files on web servers.


## Forensics


## Reversing

Ghidra is an open-source reverse engineering tool developed by the NSA.

## Binary Exploitation


