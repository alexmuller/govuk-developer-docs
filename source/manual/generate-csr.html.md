---
owner_slack: "#govuk-2ndline"
title: Generate a Certificate Signing Request (CSR) for GOV.UK
section: Environments
layout: manual_layout
parent: "/manual.html"
last_reviewed_on: 2018-04-12
review_in: 6 months
---

When buying or renewing an SSL certificate for a GOV.UK domain, a certificate
signing request is required.

## Buying a new certificate

Execute the following on a POSIX-compliant machine, for example your
Mac:

    DOMAIN_NAME=example.service.gov.uk sh -c 'openssl req -nodes -newkey rsa:2048 -keyout ${DOMAIN_NAME//[^a-zA-Z0-9]/_}.key -out ${DOMAIN_NAME//[^a-zA-Z0-9]/_}.csr -subj "/C=GB/ST=England/L=London/O=UK government/OU=Government Digital Service/CN=${DOMAIN_NAME}/"'

Be sure to replace the value 'example.service.gov.uk' set in the
`DOMAIN_NAME` environment variable to the domain name the SSL
certificate is intended for.

The contents of the .key file must be kept secret. It should be stored encrypted
in the [govuk-secrets](https://github.com/alphagov/govuk-secrets) repository.

The contents of the CSR should be shared with the SSL certificate
provider. This allows them to generate the SSL certificate.

## Renewing a certificate

This is different from generating a new certificate in that we don't want to
have a whole new key, we want to generate a CSR against an existing key.

To find the existing key, decrypt Puppet hieradata for the required environment
and find the `wildcard_publishing` key. Save this to a file, for the next step.

Execute the following on a POSIX-compliant machine, for example your
Mac:

    DOMAIN_NAME=*.publishing.service.gov.uk sh -c 'openssl req -nodes -new -key /path/to/wildcard_publishing.key -out ${DOMAIN_NAME//[^a-zA-Z0-9]/_}.csr -subj "/C=GB/ST=England/L=London/O=UK government/OU=Government Digital Service/CN=${DOMAIN_NAME}/"'

Be sure to replace the value 'example.service.gov.uk' set in the
`DOMAIN_NAME` environment variable to the domain name the SSL
certificate is intended for.

The contents of the CSR should be shared with the SSL certificate
provider. This allows them to generate the SSL certificate.

Now delete the key file you saved.
