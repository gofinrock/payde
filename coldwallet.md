# 🔐 Finrock's Multisig HSM-Based Cold Wallet
In the world of digital asset management, security is non-negotiable—especially for institutions and businesses handling high volumes of cryptocurrency. At Finrock, we’re proud to introduce our Multisig HSM-Based Cold Wallet, engineered for maximum protection, zero online exposure, and enterprise-grade control.

## 🧱 What is a Cold Wallet?
A cold wallet is a crypto wallet stored completely offline, isolated from internet access. It’s widely considered the most secure method for storing long-term crypto assets because it removes the risk of online hacks, malware, and phishing attacks.

But while cold wallets are secure, they’ve historically been cumbersome, hard to scale, and not designed for multi-user business workflows.

## 🔐 Finrock’s Cold Wallet => Multisig + HSM
At Finrock, we’ve combined two powerful technologies to reinvent cold storage for businesses:

✅ 1. Multi-Signature (Multisig) Security

Multisig requires multiple approvals to authorize a single transaction. This means no single party can move funds alone—eliminating insider risk and accidental transfers.
- Set policies like 2-of-3, 3-of-5, or custom thresholds
- Define signer roles with Finrock’s Spending Rules Engine
- Integrates seamlessly with mobile and desktop approvals

✅ 2. Hardware Security Module (HSM) Integration

Finrock’s cold wallet leverages certified HSM devices to store private keys in tamper-resistant hardware.
- FIPS 140-2 Level 3 compliant HSMs
- Full key isolation with no internet exposure
- Physical protection from unauthorized access or key exfiltration
- Air-gapped signing workflow

Together, Multisig + HSM ensures that your assets are protected both cryptographically and physically.

## 📴 Air-Gapped Signing with QR Code Workflow
Finrock offers a fully air-gapped transaction signing process using QR codes, eliminating the need for internet/network access at any stage of the signing process.

🔐 How It Works:
- Transactions initiated from the Finrock platform are converted into PSBT or equivalent unsigned payloads.
- These payloads are displayed as QR codes on Finrock workspace (platform).
- An airgapped device device running the Finrock Mobile App (in airplane mode or without SIM/network) scans the QR code.
- The app signs the transaction entirely offline using private keys stored in secure enclave/HSM or key shards.
- The app then displays a signed transaction as a return QR code, which can be scanned back into the platform for broadcasting.

✅ Key Benefits:
- No network connections required: The signing device can remain in a completely offline state.
- Immune to remote exploits or malware: Ideal for highly sensitive treasury environments.
- Frictionless UX: Designed for real-world business operations, not just security theory.

This air-gapped QR signing model is perfect for institutions looking to combine the ultimate cold storage security with operational usability.

## 🛡️ Why Finrock’s Cold Wallet?
- ✅ Zero online exposure
- ✅ Multisig enforcement across users or devices
- ✅ HSM-grade key storage and isolation
- ✅ Fully auditable and compliant with enterprise policies
- ✅ Seamless integration with your hot wallets or exchanges
- ✅ Backed by Finrock’s non-custodial infrastructure

