# Odyssey

Odyssey is an offline audio guide for ancient places. A visitor downloads one curated walking route, then walks it with the phone in a pocket or in one hand. Each stop has a single human narration. Numbered markers on the main photograph open a silent museum label: a picture, a short text, and an evidence tag that says how strong the claim is.

The same stops are the teaching unit later. A guide, a teacher, or a student can return to a monument without a network connection and without a second, different product.

This repository is the public product record: the design system and the system architecture. It does not contain narration scripts, photography, audio masters, or credentials.

Odyssey is a separate product from [trkutuphane.com](https://www.trkutuphane.com). The site is a library for working tourist guides. Odyssey is the field guide those places deserve.

## The problem

At an archaeological site the network is a courtesy, not a guarantee. Shade is scarce, the screen is in sun, and one hand is often holding a bag, a child, or the phone itself. Most audio guides still assume a live connection, a menu of features, and a visitor who will stand still and operate an app.

The interpretation problem is older than the network problem. A façade carries rebuilt stone, later restoration, and a guide's paraphrase in the same glance. Visitors cannot see which sentence is inscription, which is a reasonable reconstruction, and which is commentary. Odyssey treats that distinction as part of the interface, not as a footnote.

## What a visit is

1. **Keşfet.** A short catalog of real places. The first release opens on this catalog. There is no province picker and no search until the catalog is large enough to need them.
2. **Acquire.** The visitor downloads one destination pack. The pack is the route, the narrations, the photographs, and the labels.
3. **Çantam.** Downloaded packs live here, with their storage cost visible. This is the second and last tab.
4. **Saha.** Field mode is full screen. The tab bar is gone. The visitor moves stop to stop. Nothing starts playing by itself.
5. **Durak.** One narration. One hero photograph. A few numbered markers. Tapping a marker opens a label. The narration keeps playing.
6. **Leave.** Closing field mode returns to the pack. Playback position stays on the device.

A destination is one curated walk. The visitor does not draw a route, and the map does not invent one. The polyline and the pins ship inside the pack.

## Product rules that do not move

These are summarized here and specified in [tasarim_kurallari.md](tasarim_kurallari.md).

- Two tabs only: Keşfet and Çantam. Account is an avatar push, not a tab.
- One narration per stop. Markers do not have their own audio.
- Evidence is labeled Kanıtlı, Olası, or Yorum. The tag matches the weakest claim in the label, and a Dayanak line says why.
- No autoplay. Standing near a stop is not consent to hear it.
- Field mode stays light. Brand terracotta and the field action color are different colors, for contrast in sunlight.
- The interface follows Apple's Human Interface Guidelines. The interface language is Turkish.

Out of scope, on purpose: augmented reality, a generated 3D city, a third or fourth tab, a map the visitor edits, and a separate podcast for each photograph.

## Design language

The accent is terracotta, `#E05D34`, used as identity: primary actions in the calm catalog, the active tab, large marks. It does not pass for small text on white. Field actions use `#C2410C`, which does. Surfaces are white and the system gray `#F2F2F7`. One accent family, light theme only, until a dark field theme can be tested outdoors rather than on a desk.

The full token set, type ramp, touch sizes, navigation, mini player, marker behavior, and field-mode rules are in [tasarim_kurallari.md](tasarim_kurallari.md).

## Architecture

The client is offline after the pack is on the device. The cloud exists to store masters, build an immutable pack, and hand the visitor a download that can finish before they lose signal.

The target stack is small:

| Concern | Service |
| --- | --- |
| Private masters and versioned packs | Amazon S3 |
| Download distribution | Amazon CloudFront |
| Speech transcode | AWS Elemental MediaConvert |
| Pack assembly and catalog API | AWS Lambda, Amazon API Gateway |
| Catalog, pack versions, entitlements | Amazon DynamoDB |
| Accounts, when accounts exist | Amazon Cognito |
| Pipeline and download health | Amazon CloudWatch |

Frankfurt (`eu-central-1`) is the home region. CloudFront is the edge. The reasoning, the pack format, the failure behavior, and the build phases are in [ARCHITECTURE.md](ARCHITECTURE.md).

## Status

November 2026. The design system and the architecture are in force. The client and the pack pipeline are the build in front of us. This repository will gain code as those land. It will not gain placeholder screenshots presented as a finished app.

What "done" means for the first destination: a pack downloads, verifies, and opens in field mode with the radio off.

## What is not in this repository

- Narration manuscripts and interview recordings
- Photography and audio masters
- Visitor data
- Signing keys, cloud credentials, or payment configuration

Public documents describe behavior and structure. They do not publish the text of a monument label before an archaeologist has signed it.

## Contact

Ersin Emre
Founder, [trkutuphane.com](https://www.trkutuphane.com)
[ersin@trkutuphane.com](mailto:ersin@trkutuphane.com)
