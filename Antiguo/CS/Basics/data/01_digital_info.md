
---
# 01 Digital Information

[Back to index](../README.md)

---
## Binary codes

| Name | Equals |
| --- | --- |
| 8b (bits) | 1B (byte) |
| 1kB | 10^3 B |
| 1kiB | 2^10 B |
| 1MB | 10^6 B |
| 1MiB | 2^20 B |
| 1GB | 10^9 B |
| 1GiB | 2^30 B |
| 1TB | 10^12 B |
| 1TiB | 2^40 B |
| 1PB | 10^15 B |
| 1PiB | 2^50 B |
## Logic data

- AND = `·` 
- OR  = `+` 
- NOT =  `¯` 
- XOR  = (exclusive NOR)
## Positional system

| 1234.5    | 1110.1b  | 2BC7.Ah    |
| --------- | -------- | ---------- |
| 1 * 10^3  | 1 * 2^3  | 2 * 16^3   |
| 2 * 10^2  | 1 * 2^2  | 11 * 16^2  |
| 3 * 10^1  | 1 * 2^1  | 12 * 16^1  |
| 4 * 10^0  | 0 * 2^0  | 7 * 16^0   |
| 5 * 10^-1 | 1 * 2^-1 | 10 * 16^-1 |
## Unsigned Numbers

- `16 = 2^4` → easy conversion bin to hex
- With `n` bits, `2^n` numbers can be represented
    - Range = `[ 0 , 2^n -1 ]`
- Overflow → Operations result out of range
## Signed Number

### Sign and magnitude

Most significant bit used to represent the sign
`0_101_b` = `5`
`1_101_b` = `-5`
`2^n-1` numbers can be represented
range = `[ -2^n-1 +1 ,  2^n-1 -1 ]`
Difficult to do arithmetical operations
### Excess - K
Adding `K` to num. we obtain a positive one
`num + K ≥ 0`

| Number |  Excess - 8 | 4 bits |
| --- | --- | --- |
| -9 | -9 + 8 = -1 | no (<0) |
| -7 | -7 + 8 = 1 | 0001 |
| 2 | 2 + 8 = 10 | 1010 |
| 8 | 8 + 8 = 16 | no (>17) |
- easy comparison
- difficult arithmetic operations
### **Two’s Complement**
def. `two’s complement(M) = 2^n - M`
where M is the number
**Steps:**
1. Encode M in bin
2. Copy from top right to the first 1
3. Invert the rest of bits
range = `[ -2^n-1 , 2^n-1 -1 ]`
**Adding or substracting**
Same as with unsigned numbers
When carry digit out of range remove it
**Overflow:**
- Positive + Positive = Negative
- Negative + Negative = Positive
## **Real Number**
To represent a real num. R we assign the closest valid num. R’
Rounding error = `| R - R’ |`
Relative rounding error (%) = `Rounding error / | R |`
**Representation:**
- Fixed Point
    Assign n positions to represent the integer part and m to represent the fractional one
    Two’s complement can be used
- Floating Point
    `R = (-1)^S * M * B^E`
    Where S represent the sign, M the mantissa, B the base and E the exponent
    Example: `R = (-1)^1 * 1.23456 * 10^2 = -123.456`

**IEEE-754 format**
Single precision (binary32) (java float)
Double precision (binary64) (java double)
Quadruple precision (binary128)
For single precision:
$$
R = (-1)^S * 1.F * 2 ^ {E-127}
$$

| 1 bit | 8 bits | 23 bits |
| --- | --- | --- |
| Sign (S) | Exponent (E) | Mantissa (1.F) |
## Characters

- ASCII
- ISO 8859 (ASCII extensions)
- Unicode (UTF-8 and UTF-16)