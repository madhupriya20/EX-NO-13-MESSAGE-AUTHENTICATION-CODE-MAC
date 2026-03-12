# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC

## AIM:
To implement MESSAGE AUTHENTICATION CODE(MAC)

## ALGORITHM:

1. Message Authentication Code (MAC) is a cryptographic technique used to verify the integrity and authenticity of a message by using a secret key.

2. Initialization:
   - Choose a cryptographic hash function \( H \) (e.g., SHA-256) and a secret key \( K \).
   - The message \( M \) to be authenticated is input along with the secret key \( K \).

3. MAC Generation:
   - Compute the MAC by applying the hash function to the combination of the message \( M \) and the secret key \( K \): 
     \[
     \text{MAC}(M, K) = H(K || M)
     \]
     where \( || \) denotes concatenation of \( K \) and \( M \).

4. Verification:
   - The recipient, who knows the secret key \( K \), computes the MAC using the received message \( M \) and the same hash function.
   - The recipient compares the computed MAC with the received MAC. If they match, the message is authentic and unchanged.

5. Security: The security of the MAC relies on the secret key \( K \) and the strength of the hash function \( H \), ensuring that an attacker cannot forge a valid MAC without knowledge of the key.

## Program:
```
import hashlib

# Function to generate MAC
def generate_mac(message, key):
    data = key + message
    mac = hashlib.sha256(data.encode()).hexdigest()
    return mac

# Sender side
message = input("Enter the message: ")
key = input("Enter the secret key: ")

mac = generate_mac(message, key)

print("\nGenerated MAC:", mac)

# Receiver side verification
recv_message = input("\nEnter received message: ")
recv_mac = input("Enter received MAC: ")

new_mac = generate_mac(recv_message, key)

if new_mac == recv_mac:
    print("\nMessage is authentic and not altered.")
else:
    print("\nMessage integrity compromised!")
```


## Output:
<img width="444" height="297" alt="image" src="https://github.com/user-attachments/assets/879ac20f-4666-4b17-ad08-193725eb8021" />



## Result:
The program is executed successfully.
