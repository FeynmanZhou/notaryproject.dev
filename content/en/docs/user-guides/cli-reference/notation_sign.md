---
title: "notation sign"
---

## notation sign

Sign artifacts

### Synopsis

Sign artifacts

	Note: a signing key must be specified. This can be done temporarily by specifying a key ID, or a new key can be configured using the command "notation key add"

```
notation sign [flags] <reference>
```

### Examples

```
# Sign an OCI artifact using the default signing key, with the default JWS envelope, and use OCI image manifest to store the signature:
notation sign <registry>/<repository>@<digest>
	
# Sign an OCI artifact using the default signing key, with the COSE envelope:
notation sign --signature-format cose <registry>/<repository>@<digest> 
	
# Sign an OCI artifact with a specified plugin and signing key stored in KMS 
notation sign --plugin <plugin_name> --id <remote_key_id> <registry>/<repository>@<digest>
	
# Sign an OCI artifact using a specified key
notation sign --key <key_name> <registry>/<repository>@<digest>
	
# Sign an OCI artifact identified by a tag (Notation will resolve tag to digest)
notation sign <registry>/<repository>:<tag>
	
# Sign an OCI artifact stored in a registry and specify the signature expiry duration, for example 24 hours
notation sign --expiry 24h <registry>/<repository>@<digest>

# [Experimental] Sign an OCI artifact and store signature using the Referrers API. If it's not supported (returns 404), fallback to the Referrers tag schema
notation sign --allow-referrers-api <registry>/<repository>@<digest>
	
# [Experimental] Sign an OCI artifact referenced in an OCI layout
notation sign --oci-layout "<oci_layout_path>@<digest>"
	
# [Experimental] Sign an OCI artifact identified by a tag and referenced in an OCI layout
notation sign --oci-layout "<oci_layout_path>:<tag>"
```

### Options

```
      --allow-referrers-api         [Experimental] use the Referrers API to sign signatures, if not supported (returns 404), fallback to the Referrers tag schema
  -d, --debug                       debug mode
  -e, --expiry duration             optional expiry that provides a "best by use" time for the artifact. The duration is specified in minutes(m) and/or hours(h). For example: 12h, 30m, 3h20m
  -h, --help                        help for sign
      --id string                   key id (required if --plugin is set). This is mutually exclusive with the --key flag
      --insecure-registry           use HTTP protocol while connecting to registries. Should be used only for testing
  -k, --key string                  signing key name, for a key previously added to notation's key list. This is mutually exclusive with the --id and --plugin flags
      --oci-layout                  [Experimental] sign the artifact stored as OCI image layout
  -p, --password string             password for registry operations (default to $NOTATION_PASSWORD if not specified)
      --plugin string               signing plugin name (required if --id is set). This is mutually exclusive with the --key flag
      --plugin-config stringArray   {key}={value} pairs that are passed as it is to a plugin, refer plugin's documentation to set appropriate values
      --signature-format string     signature envelope format, options: "jws", "cose" (default "jws")
  -m, --user-metadata stringArray   {key}={value} pairs that are added to the signature payload
  -u, --username string             username for registry operations (default to $NOTATION_USERNAME if not specified)
  -v, --verbose                     verbose mode
```

### SEE ALSO

* [notation]({{< ref "/docs/user-guides/cli-reference/notation" >}})	 - Notation - a tool to sign and verify artifacts

###### Auto generated by spf13/cobra on 19-Sep-2023