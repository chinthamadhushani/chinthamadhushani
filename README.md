- 👋 Hi, I’m @chinthamadhushani
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
chinthamadhushani/chinthamadhushani is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
---><! new code using python ---->
import random

def is_prime(n):
  """
  Check if a number is prime.
  """
  if n <= 1:
    return False
  for i in range(2, int(n**0.5) + 1):
    if n % i == 0:
      return False
  return True

def generate_prime_and_primitive_root(p_min, p_max):
  """
  Generate a prime number and a primitive root.
  """
  while True:
    p = random.randint(p_min, p_max)
    if is_prime(p):
      for g in range(2, p):
        if pow(g, p-1, p) == 1:
          return p, g
      break

def diffie_hellman(p, g, a, b):
  """
  Perform the Diffie-Hellman key exchange.
  """
  A = pow(g, a, p)
  B = pow(g, b, p)
  shared_key = pow(B, a, p)
  return A, B, shared_key

# Generate a prime number and a primitive root
p, g = generate_prime_and_primitive_root(100, 1000)

# Tim's private and public keys
a = random.randint(2, p-2)
A = pow(g, a, p)

# Stephen's private and public keys
b = random.randint(2, p-2)
B = pow(g, b, p)

# Shared key
shared_key = pow(B, a, p)

print("Prime number:", p)
print("Primitive root:", g)
print("Tim's private key:", a)
print("Tim's public key:", A)
print("Stephen's private key:", b)
print("Stephen's public key:", B)
print("Shared key:", shared_key)
