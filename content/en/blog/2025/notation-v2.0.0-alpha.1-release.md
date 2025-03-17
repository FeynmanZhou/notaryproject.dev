---
title: Announcing Notation v2.0.0-alpha.1 to enable signing and verification of any arbitrary blob files!
author:  "Notary Project Community"
date: 2025-03-17
draft: false
---

We are thrilled to announce the release of [Notation v2.0.0-alpha.1](https://github.com/notaryproject/notation/releases/tag/v2.0.0-alpha.1), marking a significant milestone in our commitment to enhancing artifact signing and verification. This alpha release also introduces several improvements designed to provide a more versatile and efficient experience for our users.

## Key Highlights

### Breaking Changes

In `notation v1.x`, the `notation sign` command defaults to storing signatures using the [OCI referrers tag schema](https://github.com/opencontainers/distribution-spec/blob/v1.1.1/spec.md#referrers-tag-schema) for maximum compatibility. As of this release, the default behavior has changed to use the [OCI referrers API](https://github.com/opencontainers/distribution-spec/blob/v1.1.1/spec.md#listing-referrers) since most of the popular registries are compliant with OCI v1.1. However, users can still opt for the referrers tag schema using `--force-referrers-tag true` if needed.

### Expanded support for signing any arbitrary blob files

In addition to container images and OCI artifacts, Notation now enables signing and verification of arbitrary blob files. This enhancement broadens the scope of artifacts you can securely manage, offering greater flexibility in your workflows. The new notation blob command, along with its subcommands (sign, verify, policy, and inspect), facilitates these operations. Trust policies for blobs are configurable via the trustpolicy.blob.json file.

### OCI v1.1 Compliance

Aligning with the latest OCI specifications v1.1, Notation v2.0.0-alpha.1 adopts the OCI Referrers API for storing signatures by default. This shift ensures seamless integration with OCI v1.1-compliant registries, enhancing compatibility and adherence to industry standards. For environments requiring the previous referrers tag schema, users can still opt-in using the `--force-referrers-tag` flag during the signing process.

### Delta CRL Support

To optimize security and performance, this release introduces support for Delta Certificate Revocation Lists (CRLs). Delta CRLs allow Notation to process only the changes since the last CRL update, resulting in faster and more efficient revocation checks. This enhancement reduces bandwidth usage and accelerates the verification process, ensuring up-to-date validation of certificates.

## Getting Started with Notation v2.0.0-alpha.1

We encourage you to explore these new features and enhancements by downloading Notation v2.0.0-alpha.1 from our GitHub releases page. As this is an alpha release, we welcome your feedback to help us refine and improve the maturity. Please report any issues or suggestions on our GitHub issues page.

Thank you for your continued support and contributions to the Notary Project. Together, we're advancing the security and integrity of software supply chains.