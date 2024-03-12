# ECDSA Key Pair Generation Contract

This Solidity contract, `Secp256k1`, is designed for operations related to elliptic curve cryptography on the secp256k1 curve, which is widely used in blockchain technologies, including Ethereum and Bitcoin. The contract includes functionalities for basic elliptic curve arithmetic, key pair generation, and verification processes.

## Features

- **Constants for secp256k1**: The contract defines constants such as the base point (Gx, Gy), curve parameters (A, B), and the prime (P) that characterizes the finite field over which secp256k1 is defined.
- **Inverse Modulo**: Calculates the modular inverse of a value.
- **Exponential Modulo**: Performs modular exponentiation.
- **Get Y Coordinate**: Derives the Y coordinate given an X coordinate and a prefix indicating which Y coordinate to select if more than one is possible.
- **On Curve Check**: Determines if a given point (x, y) lies on the secp256k1 curve.
- **Inverse Point**: Calculates the inverse of a point on the elliptic curve.
- **Point Subtraction**: Subtracts one point from another on the elliptic curve.
- **Point Addition**: Adds two points on the elliptic curve.
- **Public Key Derivation**: Derives a public key from a given private key using elliptic curve multiplication.

## Usage

To use this contract, deploy it to an Ethereum blockchain environment. The functions are marked as `pure` because they do not modify the contract's state, meaning they can be called without executing a transaction (no gas cost when called off-chain).

### Example

To derive a public key from a private key:

``` solidity
uint256 privateKey = ...; // Your private key here
(uint256 x, uint256 y) = Secp256k1.derivePubKey(privateKey);
```

This will return the x and y coordinates of the public key associated with the given private key.

## Dependencies

This contract assumes the existence of an `EllipticCurve` library that provides the low-level implementations of `invMod`, `expMod`, `deriveY`, `isOnCurve`, `ecInv`, `ecSub`, `ecAdd`, and `ecMul` functions. This library is available in this repository.

## License

The contract is released under a license specified in the contract file. Please check the `SPDX-License-Identifier: SEE LICENSE IN LICENSE` line at the top of the contract for more details.

## Disclaimer

This contract is provided as-is, and the use of cryptographic contracts in production requires careful testing and auditing. The author is not responsible for any loss or damage whatsoever resulting from the use of this contract.
