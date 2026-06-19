# 🧮 Advanced Math / Number Theory Master Sheet (Interview Revision Guide)

This is the **high-frequency math toolkit** used in DSA + CP interviews.

---

# 0. When to Use Number Theory?

```text id="mt0"
Ask:

✔ Divisibility / factors / primes?
✔ GCD / LCM problems?
✔ Large exponentiation?
✔ Modulo constraints?
✔ “count / arrange / probability” style math?
```

If YES → Number Theory.

---

# 1. Core Building Blocks ⭐

---

## A) GCD (Greatest Common Divisor)

```cpp id="mt1"
int gcd(int a, int b){
    if(b == 0) return a;
    return gcd(b, a % b);
}
```

---

### Property:

```text id="mt2"
gcd(a, b) = gcd(b, a % b)
```

---

## B) LCM

```cpp id="mt3"
lcm(a, b) = (a / gcd(a, b)) * b
```

---

# 2. Prime Numbers ⭐⭐⭐⭐⭐

---

## A) Check Prime

```cpp id="mt4"
bool isPrime(int n){

    if(n < 2) return false;

    for(int i = 2; i * i <= n; i++){
        if(n % i == 0)
            return false;
    }

    return true;
}
```

---

## B) Sieve of Eratosthenes ⭐⭐⭐⭐⭐

```cpp id="mt5"
vector<bool> prime(n+1, true);

for(int i = 2; i * i <= n; i++){
    if(prime[i]){
        for(int j = i * i; j <= n; j += i)
            prime[j] = false;
    }
}
```

---

### Complexity:

```text id="mt6"
O(n log log n)
```

---

# 3. Modular Arithmetic ⭐⭐⭐⭐⭐

---

## Rules:

```text id="mt7"
(a + b) % m = (a%m + b%m) % m
(a * b) % m = (a%m * b%m) % m
```

---

## Why modulo?

```text id="mt8"
Avoid overflow + keep numbers small
```

---

# 4. Fast Exponentiation (Binary Power) ⭐⭐⭐⭐⭐

---

## A) Power function

```cpp id="mt9"
long long power(long long a, long long b, long long mod){

    long long res = 1;

    while(b > 0){

        if(b & 1)
            res = (res * a) % mod;

        a = (a * a) % mod;
        b >>= 1;
    }

    return res;
}
```

---

### Complexity:

```text id="mt10"
O(log b)
```

---

# 5. Modular Inverse ⭐⭐⭐⭐

---

## When mod is prime:

```text id="mt11"
a^(m-2) % m
```

---

## Code:

```cpp id="mt12"
long long modInverse(long long a, long long mod){
    return power(a, mod - 2, mod);
}
```

---

# 6. Factorization ⭐⭐⭐

---

## Find all factors:

```cpp id="mt13"
for(int i = 1; i * i <= n; i++){

    if(n % i == 0){

        cout << i;

        if(i != n / i)
            cout << n / i;
    }
}
```

---

# 7. Prime Factorization ⭐⭐⭐⭐

```cpp id="mt14"
for(int i = 2; i * i <= n; i++){

    while(n % i == 0){
        cout << i;
        n /= i;
    }
}

if(n > 1)
    cout << n;
```

---

# 8. Count Divisors ⭐⭐⭐

```text id="mt15"
If n = p1^a * p2^b

Divisors = (a+1)(b+1)
```

---

# 9. Euler’s Totient (φ function) ⭐⭐⭐⭐

```text id="mt16"
Count numbers coprime to n
```

---

## Formula:

```text id="mt17"
φ(n) = n * Π(1 - 1/p)
```

where p = prime factors

---

# 10. XOR Properties ⭐⭐⭐⭐⭐

```text id="mt18"
a ^ a = 0
a ^ 0 = a
commutative + associative
```

---

# 11. Fast Counting Tricks ⭐⭐⭐

---

## Even/Odd:

```cpp id="mt19"
if(n & 1) odd
else even
```

---

## Power of 2:

```cpp id="mt20"
(n & (n - 1)) == 0
```

---

# 12. Combinatorics ⭐⭐⭐⭐

---

## nCr:

```text id="mt21"
nCr = n! / (r!(n-r)!)
```

---

## Modular nCr:

Precompute factorials.

---

# 13. Inclusion-Exclusion ⭐⭐⭐

```text id="mt22"
A ∪ B = A + B - A∩B
```

---

# 14. Fibonacci (Matrix / DP link) ⭐⭐⭐

```text id="mt23"
F(n) = F(n-1) + F(n-2)
```

---

# 15. Common Number Theory Patterns

---

## Pattern 1: GCD/LCM problems

```text id="mt24"
reduce using Euclid
```

---

## Pattern 2: Prime checking

```text id="mt25"
sqrt optimization or sieve
```

---

## Pattern 3: Modular arithmetic

```text id="mt26"
avoid overflow problems
```

---

## Pattern 4: Exponentiation

```text id="mt27"
fast power (log n)
```

---

## Pattern 5: Factorization

```text id="mt28"
sqrt decomposition
```

---

# 16. Complexity Summary

```text id="mt29"
GCD → O(log n)
Prime check → O(√n)
Sieve → O(n log log n)
Power → O(log n)
Factorization → O(√n)
```

---

# 17. Problem → Pattern Mapping

| Problem         | Pattern                 |
| --------------- | ----------------------- |
| GCD of array    | Euclid                  |
| LCM problems    | GCD                     |
| Prime check     | sqrt method             |
| Count primes    | Sieve                   |
| Fast power      | Binary exponentiation   |
| Modular inverse | Fermat theorem          |
| Factor count    | Prime factorization     |
| Euler totient   | Multiplicative property |

---

# 18. Decision Rules ⭐⭐⭐

```text id="mt30"
Need divisibility?
→ GCD

Need primes?
→ Sieve / sqrt check

Need big power?
→ Fast exponentiation

Need modulo answers?
→ Modular arithmetic

Need factors?
→ Factorization
```

---

# 19. FINAL INSIGHT ⭐⭐⭐⭐⭐

```text id="mt31"
Number Theory = smart math shortcuts to avoid brute force
```

---

# 20. ONE-LINE SUMMARY

```text id="mt32"
Math + modular + primes + gcd = optimized computation toolkit
```

---
