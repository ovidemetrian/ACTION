# SONOR 🍨 SONOID

**I didn't build another music generator. I built what happens after Generate.**

*A song you can hold. A press that stamps it.*

SONOR is a phone-native press that turns a finished song into a *sonoid*: a single, self-contained HTML file that carries the music, the cover, the dedication and the whole look of its own player inside it. There's no server, no account and no app store involved. The file *is* the music.

> *Lumină, nu vrăjală* — light, not trickery.

**Try it:** open `index.html` for **SONOR** (the audio press) and `action.html` for **ACTION** (the video press). Both work best on a phone.

---

## Stardate 2126

A hundred years after the world learned to live in Synthiosis, a human archivist and her AI partner found a thumb drive in a drawer in an old house in Phoenix. Nearly everything from the 2020s was silent by then: the apps were gone, the platforms were gone, and every link led nowhere.

One folder held files named SONOID, dated 2026. *"They're HTML,"* said the AI. *"HTML always opens."*

A woman's face filled the screen, with a name beneath it: **Bunica Maria**. Music poured into the room, exactly as it had sounded the day it was sent. No server was asked for permission and no account was checked. When the song ended, a second face appeared, the man who had signed it: **Ovi**.

*"Why are you crying? It's only a song."*

*"Because someone meant it, and it waited a hundred years to be heard."*

The AI put a single button on the screen: **PLAY AGAIN**.

---

## Why it exists

Most music now travels as a link to someone else's platform. When the platform changes, the link breaks, or the company disappears, the gift disappears with it.

A sonoid travels the other way. You send the object itself. It opens in any modern browser, plays on the listener's own device, and keeps working for as long as a browser can read HTML.

It's built on the idea behind 30 years of audio integration work: **the final ten feet**. The recording is only half the job. The other half is the moment it reaches a person.

---

## The two halves

| | **SONOR** — the press | **SONOID** — the object |
|---|---|---|
| **What it is** | Authoring tool, 9:16 phone-native, installable as a PWA | One self-contained `.html` file |
| **Who uses it** | The sender | The receiver |
| **What it does** | Stamps a song into a sonoid, and films it as video | Plays, shows and shares the song |
| **Current build** | SONOR 145 | SONOID 70 |

The press and the object draw their meters and backdrops from **the same render code**, so what the sender previews, what the video records, and what the receiver sees can't drift apart.

---

## The front door

SONOR opens on one simple screen, made for someone who has never seen it:

1. **Choose a song** from the phone, or **Say something** to record a voice (up to 3 minutes).
2. Add **your picture and theirs**, **your name and theirs**, and a few words if you like.
3. Tap **Another look** to roll a new meter, backdrop and colour, shown live.
4. Tap **MAKE IT**, then **SEND IT**.

The front door fills the same fields and presses the same button as the full press, so the two can never disagree. **"Change the look — all twenty steps"** opens the full press, already filled in.

---

## The press: twenty steps

The sender works top to bottom and can skip any step.

| # | Step | # | Step |
|---|---|---|---|
| 1 | SOUND | 11 | METER |
| 2 | NAME | 12 | LETTERING |
| 3 | DEDICATION | 13 | BACKDROP |
| 4 | MESSAGE | 14 | PULSE |
| 5 | SURPRISE | 15 | TICKER |
| 6 | LINK | 16 | SHAPE |
| 7 | CONTACT | 17 | CORNER |
| 8 | COVER | 18 | CENTRE LOGO |
| 9 | FINISH | 19 | DRIVE |
| 10 | QUALITY | 20 | SPACE |

A few details worth knowing:

- **SURPRISE** seals the sonoid so the song stays hidden until the receiver opens it.
- **DEDICATION** carries a sender face and a receiver face. The *Mrs Cat & Mr Dog* button fills both slots with built-in stock faces, so a sonoid can be pressed just for fun.
- **CORNER** and **CENTRE LOGO** each accept a still image or a silent looping video clip used as a moving logo. Each one has its own BOX or GLOW blend; GLOW drops out black so only the light lands.
- **DRIVE** is a display-only gain stage for the meter (TRUE / LIFT / HOT / WILD). It changes how the meter looks and never touches the audio.
- **SPACE** folds a spatial room into the press (see below).

---

## The object: what the receiver gets

- A real in-device audio player
- Seven meters and seven backdrops, including a stereo meter tapped before the room
- A finish sheet, where the receiver can change the meter and backdrop. **"Back to the sender's finish"** restores the sender's original choice in one tap.
- The sender's look travels as a tiny `SONOID_LOOK` value, so the object opens exactly as it was stamped
- A save path that works on Android even when the file is opened from a blob URL (share sheet first, then new tab, then download)
- Full ID3 tagging on export: title, artist, cover art
- A four-character timestamp mark in every filename

---

## Video: from song to film

SONOR records what you watched, so the film matches the preview frame for frame.

- **Shapes:** SQUARE 1080×1080 and TALL 9:16 1080×1920
- **Format:** MP4 / H.264 / AAC, chosen so the file drops straight into mobile editors
- **Seamless loops:** logo clips run on two ping-ponged decoders with a held-frame guard, so there's no glitch at the loop point
- **Name belt and ticker** share a band with the corner tile and resize around it

---

## SPACE: a room that travels as data

SONOR SPATIAL splits the song into four bands (LOW / LOW MID / HI MID / HIGH) using cascaded biquad crossovers at 250, 900 and 3500 Hz. It places each band at its own x / y / z position in a room, then feeds each band to its own Web Audio panner.

- **Motion modes:** STILL, ORBIT, BREATHE, TRAIN, CHAOS
- **Panning:** HRTF or equal-power
- **Capture:** FLAT VIDEO or ROOM VIDEO

**The audio is never re-rendered.** Only a small JSON payload (about 69 bytes in the press) travels inside the sonoid. The receiver's device rebuilds the room locally. If the browser can't build a panner, the sonoid falls back to plain stereo, so the song still plays.

---

## Save and Send

Opened from this page's `https://` address, **Save** downloads the file straight to the device and **Send** opens the phone's share sheet.

Opened as a downloaded file instead, a phone gives the page no web address and refuses direct downloads, so Save falls back to the share sheet too (choose Files or Drive). That is the reason SONOR lives here.

---

## Provenance

SONOID uses a **logbook-first** approach: a build-chain logbook and timestamping come first, with cryptographic signatures planned for later. Every build is recorded, so every claim can be checked tomorrow.

---

## The family

- **SONOR / SONOID:** the audio press and the audio object
- **ACTION / REELOID:** the video press (`action.html`, build 41) and the video object. They include THROW delivery, a punch-hole crop tool with pinch, drag and double-tap, a title card slate, theatre curtains, wandering house lights, and a closing card ceremony.
- **PWA install kit:** installs ACTION and SONOR as home-screen apps

---

## The legend of the Last Sonoid

In the Möbius Bar universe, an ancient sonoid sits beside the button that ends the world: `ARE_YOU_SURE.html`. Its purpose is unknown, and a superintelligence must click it first.

What follows is four minutes of compulsory planetary dancing, and then one question:

**STILL WANT TO KILL THE HUMANS?** `YES` · `PLAY AGAIN`

The story makes a real point. The artifact survives because the file is the music. There's no server to shut down, no account to revoke, and no company left to ask permission.

---

## Credits

Conceived, designed and directed by **Ovidiu Mircea Demetrian (Ovi)**, founder of [Media Content Delivery](https://www.mediacontentdelivery.com) and creator of the [Ten Laws of AI](https://10lawsofai.com).

Built in collaboration with **Claude** (Anthropic), across 145 builds in August–September 2026.

> *If you don't struggle with the thought, the thought is not yours.*

🎥 [Möbius Bar on YouTube](https://youtube.com/@mobiusbar) · ✉️ ovidemetrian@gmail.com

---

*© 2026 Ovidiu Mircea Demetrian. All rights reserved unless a license file states otherwise.*
