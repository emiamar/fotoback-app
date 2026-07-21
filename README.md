# Fotoback

**iPhone photo backup with end-to-end encryption, built for parents.**

[fotoback.app](https://fotoback.app) · [Join the beta (TestFlight)](https://testflight.apple.com/join/VsZG8HWY) · [Follow updates](#)

---

## What is Fotoback?

Fotoback is an iOS app that backs up your photos automatically — with end-to-end encryption and zero AI training on your images.

It's built specifically for parents who have years of irreplaceable family photos on their phone and don't want those photos living in Google Photos or iCloud where they can be scanned, analysed, or used to train AI models.

Your photos are encrypted on your device before they leave it. Nobody — not Fotoback, not any third party — can read your photos.

---

## Why not just use iCloud or Google Photos?

Both iCloud and Google Photos scan your photos on their servers to power search, face recognition, and suggestions. That means your family's most personal memories — your kids growing up, private moments, sensitive images — are readable by the platform, subject to data requests, and used to improve their AI systems.

Fotoback takes a different approach:

- Photos are **encrypted on your device** before upload
- All photo analysis (faces, objects, scenes) runs **on-device only**
- Your photos are **never used to train AI models**
- You can **export your entire library** at any time — no lock-in

---

## Features

### 🔒 End-to-end encrypted backup
Automatic background sync of your entire photo library. Photos are encrypted before they leave your phone. Storage is a fraction of the cost of an iCloud upgrade.

### 👶 Baby growth timeline
Fotoback reads your photos on-device and organises your child's photos into a growth timeline — automatically identifying milestones like first smile, first steps, first birthday. Instead of scrolling through thousands of photos, you get a curated visual story of your child growing up.

### 👗 Smart wardrobe organiser
Fotoback extracts clothing and outfit details from your photos and builds a wardrobe inventory automatically. You can also photograph a single item and the app identifies and catalogues it.

### 📱 Automatic, background sync
Set it once and forget it. Fotoback runs in the background and backs up new photos as you take them — no manual steps, no thinking required.

---

## Privacy model

| What happens | Where |
|---|---|
| Photo encryption | On your device, before upload |
| Face & object recognition | On-device only (Core ML) |
| Baby milestone detection | On-device only |
| Wardrobe extraction | On-device only |
| Cloud storage | Encrypted blob — unreadable without your key |
| AI training | Never. Your photos are not used to train any model. |

Fotoback's on-device AI and "no AI training" privacy guarantee are not in conflict. The AI runs locally using Apple's Core ML framework — your photos never leave your device in a readable form, and they are never sent to a training pipeline.

---

## Platform

- **iOS** — iPhone (iOS 16+)
- Android and web: on the roadmap

---

## Pricing

Fotoback is freemium.

- **Free tier:** Limited storage, core backup features
- **Paid plans:** Expanded storage, starting significantly below iCloud's equivalent tier

Exact pricing will be published at App Store launch.

---

## Beta (TestFlight)

Fotoback is currently in private beta on TestFlight.

👉 **[Join the beta](https://testflight.apple.com/join/VsZG8HWY)**

Beta users get:
- Free access to all features during the beta period
- Direct line to the founder for feedback and questions
- Early adopter pricing when the app launches publicly

---

## Roadmap

- [x] End-to-end encrypted backup
- [x] Baby growth timeline (on-device)
- [x] Wardrobe organiser (on-device)
- [x] Automatic background sync
- [ ] Shared family albums (encrypted)
- [ ] Android app
- [ ] Web viewer
- [ ] Self-hosted storage option

---

## Feedback & issues

This repo is the public home for Fotoback's roadmap, beta feedback, and feature requests.

- **Bug reports:** [Open an issue](../../issues)
- **Feature requests:** [Open an issue](../../issues) with the `feature-request` label
- **General questions:** [emiamar@gmail.com](mailto:emiamar@gmail.com)

---

## About

Fotoback is built by [Amar Savalagi](https://fotoback.app/about) — a parent who wanted a photo backup that was genuinely private and actually useful.

Website: [fotoback.app](https://fotoback.app)  
Follow along: [Indie Hackers](https://www.indiehackers.com/post/im-building-an-iphone-photo-backup-app-here-s-what-3-months-of-pre-launch-taught-me-892fa3d75f)
