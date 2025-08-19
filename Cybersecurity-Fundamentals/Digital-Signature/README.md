# Understanding and Implementing Digital Signatures and Public Key Distribution

Author: Egwu peter
Environment: Kali Linux (CLI-based)
Project link: https://github.com/petersoneg/Cyber-Security-Projects/tree/main/Cyber-Security-Fundamentals/Digital-Signature-and-PKI


## 🛠 Tools Used
Operating System: Kali Linux
Software: GPG (GNU Privacy Guard)
Text Editor: nano
Terminal: Bash Shell
Digital Signature Project Report


Digital-Signature-and-PKI/
├── img/                          # All project screenshots
├── Fuhad_Download/               # Files that Temmy received
├── message.txt                   # Original message file
├── public_key.asc                # Exported public key
├── README.md                     # This project report
└── signed_message.sig            # Signed message file



# Introduction

This report documents the process of implementing a digital signature project using GPG (GNU Privacy Guard) to ensure secure communication through message signing and verification. The project involves generating a key pair, signing a message, exporting and importing public keys, and verifying signatures, with steps to demonstrate both successful and failed verification scenarios. The steps are organized based on provided screenshot names, detailing the workflow and outcomes.

## 🧩 Project Steps

## Step 1. Generate a GPG Key Pair

![](./img/01.%20Generate%20a%20gpg%20key%20pair.png)

The project began with generating a GPG key pair, consisting of a private key and a public key. Using the "gpg --gen-key" command, a new key pair was created. This step establishes the cryptographic foundation for signing and verifying messages, ensuring the authenticity and integrity of communications.

## Step 2. Choose Key Length

![](./img/02.%20choose%20key%20lenght.png)

During key generation, the key length was selected (e.g., 2048 or 4096 bits). A longer key length enhances security but may increase computational overhead. For this project, a balance between security and performance was chosen, typically 2048 bits, as it provides strong encryption suitable for most applications.

## Step 3. Set Key Validity Period

![](./img/03.%20Set%20key%20validity%20period.png)

The key's validity period was configured to define its lifespan. A validity period (e.g., 1 year or no expiration) was set to ensure the key remains usable for the project's duration while allowing for future key rotation to maintain security.

## Step 4. Identity Construction

![](./img/04.%20identity%20construction.png)

The key pair was associated with an identity, including a name, email address, and optional comment. This step ties the key to the user’s identity, enabling recipients to verify the signer’s authenticity when checking signatures.

## Step 5. Final Options and Passphrase Choice

![](./img/05.%20final%20options%20and%20passphrase%20choice.png)

Final key generation options were confirmed, and a strong passphrase was set to protect the private key. The passphrase ensures that only authorized users can access the private key for signing, adding a layer of security against unauthorized use.

## Step 6. Create a Message

![](./img/06.%20creatre%20a%20message.png)

A plain text message was created for signing. This message serves as the content to be digitally signed, demonstrating the application of the digital signature to ensure its integrity and authenticity during transmission.

## Step 7. Signed Message

![](./img/07.%20signed%20message.png)

The message was signed using the private key with the gpg --sign command. This process generates a digital signature, embedding the message and signature together, allowing the recipient to verify both the sender’s identity and the message’s integrity.

## Step 8. List Keys

![](./img/08.%20List%20keys.png)

"The gpg --list-keys" command was used to display all keys in the GPG keyring, confirming the presence of the newly created key pair. This step ensures the key was successfully generated and is available for use.

## Step 9. Export Public Key

![](./img/09.%20Export%20public%20key.png)

The public key was exported using gpg --export to a file (e.g., publickey.asc). This file is intended for sharing with recipients who will use it to verify signed messages, enabling secure communication.

## Step 10. Verify the Export

![](./img/10.%20verify%20the%20export.png)

The exported public key file was checked to ensure it was correctly generated and contains the expected key data. This verification step confirms that the public key is ready for distribution without errors.

## Step 11. Send Files to Receiver

![](./img/11.%20Send%20files%20to%20receiver.png)

The signed message and the public key file were sent to the recipient. This step simulates real-world communication, where the recipient needs both the signed message and the sender’s public key to perform verification.

## Step 12. Open Downloads Folder in Terminal

![](./img/12.%20Downloads%20files.png)

On the recipient’s system, the terminal was navigated to the Downloads folder (or wherever the files were saved) using the cd command. This prepares the environment for importing the public key and verifying the signed message.

## Step 13: Open Downloads Folder in Terminal

![](./img/13.%20Open%20Downloads%20Folder%20in%20Terminal.png)

He navigates to the Downloads folder via terminal

14. ## Step 14: Import Public Key
Fuhad imports peters public key:

gpg --import public_key.asc

![](./img/14.%20Import%20Public%20Key.png)

The recipient verified the signed message using gpg --verify. This step confirmed that the signature is valid, the message is unchanged, and it was signed by the owner of the corresponding private key.

## Step 15.Verify the Signature
fuhad verifies that the signed file was indeed signed by peter

gpg --verify signed_message.sig
![](./img/15.%20Verify%20the%20Signature.png)

The content of the signed message was viewed to ensure it matches the original message sent. This step confirms that the message was not altered during transmission and that the signature verification process is successful.

## step 16. Tamper with the File

![](./img/16.%20Integrity%20Testing.png)

To demonstrate the security of digital signatures, the signed message file was intentionally modified (e.g., by editing the text). This simulates an attack where a malicious actor attempts to alter the message content.

## step 17. Veiew signed message
The content is in ASCII-armored format (encoded and compressed message + signature)
![](./img/17.%20View%20Signed%20Message%20Content.png)

## Step 18. Tamper with the File 
The tampered message was re-verified using gpg --verify. As expected, the verification failed, indicating that the message was altered since it was signed. This demonstrates the effectiveness of digital signatures in detecting unauthorized modifications.
![](./img/18.%20Tamper%20with%20the%20File.png)

## Step 19: Verify Again — Failure
After tampering, GPG detects corruption:

gpg --verify signed_message.sig
* gpg: CRC error...
* gpg: the signature could not be verified.

![](./img/19.%20Verify%20Again%20—%20Failure.png)

# Conclusion

The digital signature project successfully demonstrated the creation, signing, and verification of a message using GPG. The process included generating a key pair, signing a message, sharing the public key, and verifying the signature. The intentional tampering and subsequent verification failure highlighted the robustness of digital signatures in ensuring message integrity and authenticity. This project underscores the importance of cryptographic tools like GPG for secure communication in digital environments.

## 💡 Real-World Applications
* Secure email signing (PGP, S/MIME)
* Software distribution (verifying signed binaries)
* Git commit signing (to prevent commit forgery)
* Document authenticity checks (contracts, agreements)

# Recommendations





* Regularly rotate keys and update validity periods to maintain security.



* Use strong passphrases and secure storage for private keys.



* Educate recipients on the importance of verifying signatures to prevent trusting tampered messages.



* Explore advanced GPG features, such as encryption, for additional security layers.