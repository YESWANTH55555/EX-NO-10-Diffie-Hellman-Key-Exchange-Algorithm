# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:

```
#include <stdio.h>
#include <math.h>

long long power(long long base, long long exp, long long mod) {
    long long result = 1;
    for (int i = 0; i < exp; i++)
        result = (result * base) % mod;
    return result;
}

int main() {
    long long p, g, a, b, A, B, keyA, keyB;

    printf("Enter prime number (p): ");
    scanf("%lld", &p);
    printf("Enter primitive root of p (g): ");
    scanf("%lld", &g);

    printf("Enter private key for User A: ");
    scanf("%lld", &a);
    printf("Enter private key for User B: ");
    scanf("%lld", &b);

    A = power(g, a, p);
    B = power(g, b, p);

    printf("\nPublic key of User A: %lld", A);
    printf("\nPublic key of User B: %lld", B);

    keyA = power(B, a, p);
    keyB = power(A, b, p);

    printf("\n\nShared secret key for User A: %lld", keyA);
    printf("\nShared secret key for User B: %lld", keyB);

    if (keyA == keyB)
        printf("\n\nKey exchange successful! Shared key = %lld\n", keyA);
    else
        printf("\n\nKey mismatch! Something went wrong.\n");

    return 0;
}
```

## Output:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3d9679c8-a794-4d80-99f7-ca5b2a8cd0ca" />



## Result:
  The program is executed successfully
