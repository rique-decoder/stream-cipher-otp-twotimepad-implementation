
# Stream Cipher: OTP and Two-Time Pad

This repository demonstrates, in Python, how stream ciphers work and the risk of reusing the same key or keystream.

The project presents practical examples of:

- XOR encryption
- One-Time Pad (OTP)
- The attack known as **Two-Time Pad**
- Combining two ciphertexts
- Partial message recovery via *crib dragging*

## Repository Structure

- `stream-cipher.py`: demonstrates bit-level encryption and decryption with XOR and key reuse.
- `exemplo1.py`: presents the Two-Time Pad attack using byte messages.
- `exemplo2.py`: demonstrates a statistical analysis based on space characters.
- `lousa-aula-blockchain.png`: visual material used as a teaching aid.
- `LICENSE`: MIT license for the project.

## How It Works

A stream cipher generates a keystream `K` and combines this value with the plaintext message `M` using the XOR operation:

```text
C = M XOR K
M = C XOR K
```

Because applying XOR twice with the same value recovers the original data, the same keystream can be used for both encryption and decryption.

## Demonstrated Scenarios

### One-Time Pad

The `stream-cipher.py` file applies XOR to a binary message and a keystream:

```text
M = 10110011
K = 11001010
C = M XOR K
```

The exact same operation is used to decrypt the ciphertext.

### Two-Time Pad Attack

When two messages are encrypted with the same keystream:

```text
C1 = M1 XOR K
C2 = M2 XOR K
```

An attacker can compute:

```text
C1 XOR C2 = M1 XOR M2
```

This eliminates the key from the equation and reveals the relationship between the two original plaintexts.

The examples `exemplo1.py` and `exemplo2.py` demonstrate how this vulnerability can be exploited:

* Reusing the same key across multiple messages
* Comparing ciphertexts
* Guessing known words, or *crib dragging*
* Identifying spaces and characters through statistical analysis

## Running the Project

No external dependencies are required.

```bash
git clone [https://github.com/rique-decoder/stream-cipher-otp-twotimepad-implementation.git](https://github.com/rique-decoder/stream-cipher-otp-twotimepad-implementation.git)
cd stream-cipher-otp-twotimepad-implementation
```

Run the examples:

```bash
python stream-cipher.py
python exemplo1.py
python exemplo2.py
```

## Security Considerations

Reusing a key in a stream cipher is insecure. For a pad-based XOR cipher to be truly secure, the keystream must:

* Be truly random
* Be at least as long as the message
* Be used only once
* Be kept completely secret

This repository is for educational purposes only and must not be used as a cryptographic implementation in real-world systems.

## License

This project is available under the MIT License.

