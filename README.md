[![CI](https://github.com/gruntwork-io/asdf-terragrunt/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/gruntwork-io/asdf-terragrunt/actions/workflows/ci.yml)

# asdf-terragrunt

[Terragrunt](https://github.com/gruntwork-io/terragrunt) plugin for the [asdf](https://github.com/asdf-vm/asdf) version manager.
Check out the [asdf](https://github.com/asdf-vm/asdf) readme for instructions.

### Install

```
asdf plugin add terragrunt https://github.com/ohmer/asdf-terragrunt
```

### Environment Variable Options

- `ASDF_TERRAGRUNT_OVERWRITE_ARCH`: Force the plugin to use a specified processor architecture rather than the
  automatically detected value. Useful, for example, for allowing users on M1 Macs to install `amd64` binaries when
  there's no `arm64` binary available.

- `ASDF_TERRAGRUNT_SKIP_CHECKSUM`: Skip the checksum verification when downloading the binary. This saves some time,
  but is less secure.

- `ASDF_TERRAGRUNT_SKIP_SIGNATURE`: Skip cryptographic signature verification of release assets. Set to `true` to
  disable verification (not recommended). Signature verification requires either `gpg` or `cosign` to be installed.
  Default: `false` (verification enabled).

- `ASDF_TERRAGRUNT_SIGNATURE_METHOD`: Choose the signature verification method. Options are:
  - `auto` (default): Tries GPG first, then Cosign if GPG is unavailable or fails.
  - `gpg`: Use GPG signature verification only. Requires `gpg` to be installed.
  - `cosign`: Use Cosign signature verification only. Requires `cosign` to be installed.

### Signature Verification

Terragrunt releases are cryptographically signed by Gruntwork. Signature verification is **enabled by default** to ensure
the binary you download is authentic and hasn't been tampered with.

**Note:** Signature verification is only available for Terragrunt versions `v0.98.0` and newer. Older versions will
skip signature verification automatically.

**Requirements:**
- For GPG verification: Install `gpg` (GnuPG). The plugin will automatically import Gruntwork's public key.
- For Cosign verification: Install `cosign` from [Sigstore](https://docs.sigstore.dev/cosign/installation/).

If neither tool is installed, the installation will fail. You can either:
1. Install `gpg` or `cosign` (recommended)
2. Disable signature verification (not recommended):
   ```bash
   export ASDF_TERRAGRUNT_SKIP_SIGNATURE=true
   asdf install terragrunt 0.50.0
   ```

### Special Thanks

This plugin was started by the community, and is now maintained by Gruntwork.

Thanks to [lotia](https://github.com/lotia) for creating the original plugin, and to [ohmer](https://github.com/ohmer) for maintaining it afterwards.

