# Example Rust Cryptographic Machine Files

This is an example of how to verify and decrypt [cryptographic machine files](https://keygen.sh/docs/api/cryptography/#cryptographic-lic)
in Rust, using Ed25519 signature verification and AES-256-GCM encryption.

This example verifies the `aes-256-gcm+ed25519` algorithm.

## Running the example

Install dependencies with [`cargo`](https://doc.rust-lang.org/cargo/):

```bash
cargo build
```

Then run the example program, where `-p` is the path to a machine file,
`-k` is your Ed25519 public key, `-l` is a license key, and `-f` is the
machine's fingerprint. Feel free to use these example values:

```bash
cargo run -- -p examples/machine.lic \
  -k "e8601e48b69383ba520245fd07971e983d06d22c4257cfd82304601479cee788" \
  -f "af249c134edd21c508e2114f0dd52628caf36e002edd9cada71eedb2d52f6841" \
  -l "988214-879010-F1185E-B37E91-E53AF5-V3"
```

You should see output indicating that the machine file is valid, with its
decrypted dataset:

```
machine file was successfully verified!
  > {
      "enc": "zPPvatydyUFc9+/RK8q1BubMM4ybx+UvrjxrO3ZgDyvt3KYZoG930SSFm09jvw4SuA3IZ7eTTHMdv1NAWdyTnz/SA==",
      "sig": "/hx4qcpW7lyKyXQnYJRi1jWUKE+/zRIorXMNzg1TsPJeFZ3G8q0XDnI28CAQwfTnvLbLTW1uLIiMNux/Rb1HBw==",
      "alg": "aes-256-gcm+ed25519"
    }
machine file was successfully decrypted!
  > {
      "data": {
        "id": "14595d7a-84cd-4c7c-9a4e-a8620d20b484",
        "type": "machines"
        "attributes": {
          ...
        },
        "relationships": {
          ...
        }
      },
      "included": [
        ...
      ],
      "meta": {
        "expiry": "2024-10-30T20:12:27.468Z",
        "issued": "2023-10-31T15:32:33.468Z",
        "ttl": 31536000
      }
    }
```

For docs on how to check out a machine file, [go here](https://keygen.sh/docs/api/machines/#machines-actions-check-out).

## Questions?

Reach out at [support@keygen.sh](mailto:support@keygen.sh) if you have any
questions or concerns!
