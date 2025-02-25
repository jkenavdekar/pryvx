# PryvX

## Overview

PryvX is a comprehensive package that provides multiple privacy-enhancing technologies, including Private Set Intersection (PSI), Secure Multi-Party Computation (SMPC), Homomorphic Encryption (HE), Federated Learning, Differential Privacy, and more.

This documentation focuses on the PSI module.

# PSI Package

## Overview

The PSI Package provides a simple implementation of Private Set Intersection (PSI) using Oblivious Pseudorandom Functions (OPRF). This package allows two parties to find the intersection of their private datasets without revealing any additional information about their datasets.

## What is OPRF?

### Oblivious Pseudorandom Function (OPRF)

An Oblivious Pseudorandom Function (OPRF) is a cryptographic protocol that allows a client to evaluate a pseudorandom function (PRF) on an input, using a key held by a server, without revealing the input to the server and without the client learning the key. The server also does not learn the input provided by the client.

## Mathematical Definitions

### Pseudorandom Function (PRF)

A **Pseudorandom Function (PRF)** is a function \( F: K \times X \to Y \) where:
- \( K \) is the key space,
- \( X \) is the input space,
- \( Y \) is the output space.

Given a key \( k \in K \), the function \( F(k, \cdot) \) is computationally indistinguishable from a truly random function to any efficient adversary who does not know \( k \).

### OPRF Protocol

The **Oblivious Pseudorandom Function (OPRF) Protocol** involves two parties:
- **Server:** Holds a secret key \( k \).
- **Client:** Holds an input \( x \in X \).

The protocol ensures that:
- The client learns \( F(k, x) \) without learning \( k \).
- The server learns nothing about \( x \).


### PSI Using OPRF

In the context of Private Set Intersection (PSI), OPRF allows two parties to compute the intersection of their sets without revealing the actual sets to each other. Each party hashes their elements using the OPRF and compares the hashed values to find the intersection.

## Installation

### Prerequisites

Ensure you have Python installed. This package supports Python 3. or >

### Installing the PSI Package

You can install the package using pip. First, download the `.whl` file and then install it:

```sh
pip install pryvx
```

## Usage

### Example Usage

Here is a basic example of how to use the PSI package:

```python
from pryvx import PSI

# Generate a key for the server
server_key = PSI.get_key()

# Define the datasets from Party A and Party B
set_a = ["Alice", "Bob", "Charlie"]
set_b = ["Bob", "David", "Charlie"]

# Compute the intersection
batch_size = 2
intersection = PSI.oprf(set_a, set_b, batch_size, server_key)

# Print the intersection
print(intersection)  # Output: {'Bob', 'Charlie'}
```

### Detailed Explanation

1. **Generate Server Key**:
   ```python
   server_key = PSI.get_key()
   ```
   This generates a random 256-bit key that will be used by the server to perform the OPRF.

2. **Define Datasets**:
   ```python
   set_a = ["Alice", "Bob", "Charlie"]
   set_b = ["Bob", "David", "Charlie"]
   ```
   These are the datasets from Party A and Party B. In a real-world scenario, these could be lists of sensitive data that the parties do not want to share in plaintext.

3. **Compute Intersection**:
   ```python
   batch_size = 2
   intersection = PSI.oprf(set_a, set_b, batch_size, server_key)
   ```
   The `oprf` function takes the datasets, a batch size, and the server key to compute the intersection of the datasets using OPRF. The batch size determines the number of elements processed in parallel.

4. **Print Intersection**:
   ```python
   print(intersection)  # Output: {'Bob', 'Charlie'}
   ```
   The result is the intersection of the datasets, indicating the common elements.

## Conclusion

The PSI Package provides an easy-to-use implementation of Private Set Intersection using OPRF. By following the installation and usage instructions, you can integrate PSI into your applications to securely compute intersections of private datasets.
