# verified-c2pa-action-explainer
Explainer for a proposed c2pa.verified action

## Problem
People and organizations that want to adopt C2PA, but publish:

1. existing libraries of media, which do not have C2PA provenance
2. new media coming from cameras and editing flows which have not yet adopted C2PA, which also lack C2PA provenance.

These people and organizations need some way to attest that the media is authentic, and associate their organization's trustworthiness with this attestation.

## Proposed solution

This explainer proposes a new standard action (with an associated entry in `actors`) named `c2pa.verified`. This is a signal from the actor to future consumers that the media and its associated metadata have been editorially verified by the organization.

## Example

The following assertions would – as long as consumers trusted the signer – be a strong signal that "Trustworthny News Organization, Inc." had verified, as of 2024, using means other than C2PA metadata, that the associated media was captured from a real-life source using a digital camera on January 1, 2020, in San Francisco.

```
"assertions": [
  {
    "label": "c2pa.actions",
    "data": {
      "actions": [
        {
          "action": "c2pa.verified",
          "when": "2024-01-15T12:00:00-08",
          "actors": [
            {
              "name": "Trustworthy News Organization, Inc.",
              "identifier":"did:adobe:1234",
              "credential": [
                {
                  "alg": "sha256",
                  "hash": "IcZeS318070nuvDYmPqfQdZmOI7jGumMjHTxNshA2ao=",
                  "url": "self#jumbf=/c2pa/adobe:urn:uuid:12345678-9012-3456-7890-123456789012/c2pa.credentials/did:adobe:1234"
                }
              ]
            }
          ]
        }
      ]
    }
  },
  {
    "label": "c2pa.metadata",
    "data": {
      "@context" : {
	"Iptc4xmpCore": "http://iptc.org/std/Iptc4xmpCore/1.0/xmlns/",
	"Iptc4xmpExt": "http://iptc.org/std/Iptc4xmpExt/2008-02-29/"
      },
      "Iptc4xmpExt:DigitalSourceType": "https://cv.iptc.org/newscodes/digitalsourcetype/digitalCapture",
      "Iptc4xmpCore:DateCreated": "2020-01-01",
      "Iptc4xmpExt:LocationCreated": { 
        "Iptc4xmpExt:City": "San Francisco"
      }
    }
  }
]
```


