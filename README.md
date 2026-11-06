# Odyssey

Odyssey is an offline audio guide for ancient places. A visitor downloads one curated walk, then uses it with the radio off. The phone holds the pack. AWS builds the pack, stores it, signs it, and hands it out.

The production system is AWS, in `eu-central-1`, defined as AWS CDK stacks. There is no second cloud and no server left running between publishes. A publish is an AWS Step Functions execution. A download is Amazon CloudFront. A walk does not call AWS.

Odyssey is a separate product from [trkutuphane.com](https://www.trkutuphane.com). This repository is the product record: the design system and the AWS architecture. It does not contain narration, photography, or credentials.

## What a visit is

1. **Keşfet.** The catalog comes from Amazon API Gateway. The first release opens here. No province picker, no search, until the catalog is large enough to need them.
2. **Acquire.** The visitor asks for a pack. API Gateway checks Amazon DynamoDB, then returns a short-lived CloudFront URL. The bytes are an immutable object in Amazon S3.
3. **Çantam.** Downloaded packs and the space they use. This is the second and last tab.
4. **Saha.** Field mode is full screen. The tab bar is gone. Nothing starts playing by itself. This screen does not call AWS.
5. **Durak.** One narration. One hero photograph. A few numbered markers. A marker opens a silent label. The narration keeps playing.
6. **Leave.** Closing field mode returns to the pack. Playback position stays on the device.

A destination is one curated walk. The visitor does not draw a route. The polyline ships inside the pack.

## Product rules

Specified in [tasarim_kurallari.md](tasarim_kurallari.md).

- Two tabs: Keşfet and Çantam. Account is an avatar push, backed by Amazon Cognito when an account exists.
- One narration per stop. Markers have no audio of their own.
- Evidence is labeled Kanıtlı, Olası, or Yorum. The tag matches the weakest claim. A Dayanak line says why.
- No autoplay.
- Field mode stays light. Brand terracotta is `#E05D34`. Field actions are `#C2410C`, because small text on white must clear contrast in sun.
- The interface follows Apple's Human Interface Guidelines. The interface language is Turkish.

Out of scope: augmented reality, a generated 3D city, a third tab, a route the visitor draws, and a separate audio file per photograph.

## AWS, by job

| Job | Service |
| --- | --- |
| Masters, derivatives, versioned packs | Amazon S3 |
| Download to the phone | Amazon CloudFront, signed URLs, AWS WAF |
| Speech, wav to AAC | AWS Elemental MediaConvert |
| Publish orchestration | AWS Step Functions, Amazon EventBridge, AWS Lambda |
| Catalog, entitlements, signing | Amazon API Gateway, AWS Lambda, Amazon DynamoDB |
| Accounts | Amazon Cognito |
| Encryption and the signing key | AWS KMS, AWS Secrets Manager, IAM |
| TLS for the distribution | AWS Certificate Manager |
| Editor alert when a publish fails | Amazon SNS |
| Operations | Amazon CloudWatch, AWS X-Ray |
| The stacks | AWS CDK |

The reasoning, the table keys, the state machine, and the failure behavior are in [ARCHITECTURE.md](ARCHITECTURE.md).

## What the phone does without AWS

After the checksum matches, field mode makes no network call to play, to open a label, or to draw the route. AWS is the system of record up to that checksum. It is not in the path of the narration.

## Status

November 2026. The design system and the AWS architecture are the build. The first milestone is those stacks in `eu-central-1`, one destination, a pack that verifies, and a walk with the radio off. This repository will gain the client, the CDK stacks, and the Lambda handlers as they land. It will not gain placeholder screenshots presented as a finished app, and it will not gain a second backend "for now."

## What is not in this repository

- Narration manuscripts and recordings
- Photography and audio masters
- Visitor data
- Signing keys, cloud credentials, or payment configuration

Public documents describe behavior and structure. They do not publish a monument label before the person responsible for that destination has accepted the evidence tag.

## Contact

Ersin Emre
Founder, [trkutuphane.com](https://www.trkutuphane.com)
[ersin@trkutuphane.com](mailto:ersin@trkutuphane.com)
