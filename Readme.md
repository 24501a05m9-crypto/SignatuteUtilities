# Signature Utilities Smart Contract

A simple and efficient Aptos Move smart contract for signature generation helpers and verification utilities.

## Overview

This smart contract provides essential cryptographic signature functionality on the Aptos blockchain, allowing users to store signature data and verify ED25519 signatures with built-in validation.

## Features

- **Signature Storage**: Store message, signature, and public key data with verification status
- **Signature Verification**: Verify stored signatures and return validation results
- **ED25519 Support**: Built-in support for ED25519 cryptographic signatures
- **Error Handling**: Comprehensive error codes for debugging and validation

## Contract Functions

### `store_signature_data`
```move
public fun store_signature_data(
    account: &signer,
    message: vector<u8>,
    signature: vector<u8>,
    public_key: vector<u8>
)
```
Stores signature data after verification. Creates or updates signature data for the account.

**Parameters:**
- `account`: Signer reference for the account
- `message`: Original message that was signed
- `signature`: ED25519 signature bytes
- `public_key`: Public key bytes for verification

### `verify_signature_data`
```move
public fun verify_signature_data(account_addr: address): bool
```
Verifies previously stored signature data and returns validation status.

**Parameters:**
- `account_addr`: Address of the account with stored signature data

**Returns:**
- `bool`: True if signature is valid, false otherwise

## Data Structures

### `SignatureData`
```move
struct SignatureData has key, store {
    message: vector<u8>,
    signature: vector<u8>,
    public_key: vector<u8>,
    is_verified: bool,
}
```

## Error Codes

- `E_INVALID_SIGNATURE (1)`: Invalid or missing signature data
- `E_INVALID_PUBLIC_KEY (2)`: Invalid public key format

## Prerequisites

- Aptos CLI installed
- Move compiler
- Aptos account with sufficient gas

## Deployment

1. Clone or download the contract file
2. Navigate to your project directory
3. Compile the contract:
   ```bash
   aptos move compile
   ```
4. Deploy to Aptos network:
   ```bash
   aptos move publish
   ```

## Usage Example

```move

signature_utilities::signature_utils::store_signature_data(
    &account,
    b"Hello World",
    signature_bytes,
    public_key_bytes
);


let is_valid = signature_utilities::signature_utils::verify_signature_data(account_address);
```

## Security Considerations

- Uses `signature_verify_strict` for enhanced security
- Validates signatures before storage
- Proper error handling for invalid inputs
- Uses Aptos standard library for cryptographic operations

## Dependencies

- `std::vector`
- `std::signer`
- `aptos_framework::account`
- `aptos_std::ed25519`
- `aptos_std::multi_ed25519`

## License

This smart contract is provided as-is for educational and development purposes.

## Contract details
0x8006502131cc1ce69254add4473caba9a2fedf71a084ed918eacdc66adfae0f9
![alt text](<Screenshot 2025-08-07 145938.png>)


