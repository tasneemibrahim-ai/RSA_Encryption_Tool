# 🔐 RSA Encryption Demonstrator

> A Java command-line application that demonstrates the RSA public-key cryptography algorithm from first principles using core discrete mathematics concepts.

![Java](https://img.shields.io/badge/Java-JDK%208%2B-orange?style=flat-square&logo=openjdk)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)
![Purpose](https://img.shields.io/badge/Purpose-Educational-purple?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)

---

## 📖 Overview

This project implements RSA encryption and decryption **from scratch** — no cryptography libraries, no shortcuts. Given a plaintext message and two prime number upper limits, the program:

1. Selects two prime numbers `p` and `q`
2. Generates a **public key** `(e, n)` and a **private key** `(d, n)`
3. **Encrypts** the message into numerical cipher blocks
4. **Decrypts** the cipher blocks back to the original plaintext

Built as a practical bridge between abstract discrete mathematics and real-world cryptographic concepts.

---

## 🧮 Discrete Mathematics Concepts

| Concept | Role in RSA |
|---|---|
| **Prime Numbers** | Foundation of key generation — `p` and `q` |
| **Euler's Totient Function** | Computes `m = (p-1) × (q-1)` |
| **Greatest Common Divisor (GCD)** | Ensures public exponent `e` is coprime to `m` via the Euclidean Algorithm |
| **Modular Arithmetic** | Used throughout key generation, encryption, and decryption |
| **Modular Exponentiation** | Efficiently computes `x^y mod z` without integer overflow |

---

## ⚙️ How It Works

```
User Input: message + two upper limits
        ↓
Find primes p, q ≤ upper limits
        ↓
n = p × q        (modulus)
m = (p-1)(q-1)   (Euler's totient)
        ↓
Find e: gcd(e, m) = 1     → Public Key  (e, n)
Find d: (d × e) % m = 1   → Private Key (d, n)
        ↓
Encrypt: C = ASCII(char)^e mod n   (for each character)
Decrypt: P = C^d mod n             (for each cipher block)
```

---

## 🚀 Getting Started

### Prerequisites

- Java Development Kit (**JDK 8 or higher**) — tested on **JDK 21**
- A terminal / command prompt

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/your-username/RSA_Encryption_Tool.git

# 2. Navigate into the project directory
cd RSA_Encryption_Tool
```

### Compile

```bash
javac src/RSAEncryption.java
```

### Run

```bash
java -cp src RSAEncryption
```

---

## 💻 Sample Session

```
 enter your original message :
Hello

 Enter two distinct upper limits for the two primes p and q :
 Upper limit for p is :
50
 Upper limit for q is :
60

Your encrypted (cipher) message is :
ڌ웏웏ꦲ

Your decrypted message is :
Hello
```

---

## 📁 Project Structure

```
RSA_Encryption_Tool/
├── docs/
│   └── project_code.docx       # Original project documentation
├── src/
│   └── RSAEncryption.java      # Main application source code
├── .gitignore
└── README.md
```

---

## 🔩 Algorithms & Data Structures

| Component | Description |
|---|---|
| `getPrimeNumber(int)` | Finds the largest prime ≤ input using trial division — `O(n√n)` |
| `gcd(long, int)` | Euclidean Algorithm for computing the greatest common divisor |
| `power(double, int, long)` | Fast modular exponentiation using repeated squaring — `O(log y)` |
| `calculateE(long)` | Finds public exponent `e` coprime to totient `m` |
| `calculateD(int, long)` | Finds private exponent `d` as modular inverse of `e` |
| `ArrayList<Double>` | Dynamically stores encrypted/decrypted character blocks |

---

## ⚠️ Limitations

> **This is an educational tool — NOT suitable for real-world security use.**

- **Small primes:** Prime numbers used are trivially factorable
- **Naive primality:** Trial division is not optimized for large-scale prime searches
- **Data type overflow:** Uses `int`, `long`, and `double` — large primes will cause overflow (real RSA uses `BigInteger`)
- **ECB mode vulnerability:** Character-by-character encryption is susceptible to frequency analysis

---

## 🔮 Future Improvements

- [ ] Refactor to use `BigInteger` for realistically large primes
- [ ] Implement the **Miller-Rabin** primality test for faster, reliable prime generation
- [ ] Add **block encryption** to replace character-by-character processing
- [ ] Improve **input validation** and error handling

---

## 🛠️ Technologies

- **Language:** Java (Standard Library only)
- **Dependencies:** None

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## Author

Tasneem Ibrahim
