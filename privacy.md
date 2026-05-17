# Privacy Policy

**Effective date:** 2026-05-16
**Last updated:** 2026-05-16

This Privacy Policy describes how Mas Dinero Ventures LLC ("**we**," "**us**," or "**our**") handles information when you use Talkli (the "**App**"). We built Talkli around a single promise: **your voice, your video, your resume — they stay on your phone**. This policy explains what that means in practice, and the small set of things we *do* collect when you choose to share them.

---

## 1. The short version

Talkli processes the things most likely to be private — your **audio, your video, your resume content** — entirely on your iPhone. None of it is ever uploaded to our servers. We can't read your practice transcripts, see your face during sessions, or open your resume. The cryptography is the iPhone's own: native iOS Speech Recognition, Vision, and PDFKit frameworks.

The information we *can* see is limited to:

- **Anonymous app usage events** (only if you leave the Analytics toggle on)
- **Anonymous crash reports** (only if you leave Crash Reporting on)
- **Subscription state** (managed by Apple + RevenueCat — needed to know if you're Pro)

You can turn off analytics and crash reporting any time in the App at **You → Privacy Center**, and you can delete every byte of local data with one tap.

If you want the long version, read on.

---

## 2. What stays on your device (never uploaded)

The following data is processed entirely on your iPhone using Apple's native frameworks. We **never** receive, store, or have access to any of it.

| Data | How it's processed | When it's deleted |
|---|---|---|
| **Microphone audio** | iOS Speech Recognition on-device | Within 60 seconds of session end |
| **Camera video frames** | iOS Vision face detection on-device | Never stored — analyzed frame-by-frame in memory and immediately discarded |
| **Speech transcripts** | Generated on-device for filler-word detection | Stored locally on your device only (never uploaded). Removable via Clear All Data. |
| **Resume content** (text from PDFs, DOCX, RTF, TXT files) | Parsed on-device using Apple PDFKit + open-source fflate | Held in memory only while you're using the Resume Optimizer. Optionally cached locally; removable via Clear All Data. |
| **Session scores + history** | Computed on-device | Stored locally on your device only. Removable via Clear All Data. |
| **Onboarding selections** (name, goals, coach persona, schedule) | Stored locally on your device only | Removable via Clear All Data. |

When this policy says "local," we mean a local storage container on your iPhone (using `MMKV` and Apple's standard file system). Apple's encryption protects this storage at rest — the same protection your other apps' local data receives.

---

## 3. What we receive (when you opt in)

These are the only categories of data that ever leave your device, and each is controlled by an explicit toggle in **You → Privacy Center**:

### 3.1 Analytics (Product Interaction)

If you leave **Analytics** on, we receive anonymous event data such as:
- Which screens you visit (e.g., "today_viewed", "session_started")
- Which features you use (e.g., "script_generated", "resume_ats_scored")
- Aggregate counts and timing of those events

We do **not** receive:
- Names, email addresses, or any personal identifiers
- The actual content of your sessions, scripts, or resume
- Any data that could be used to identify you individually

Analytics events are associated with a randomly generated, device-local identifier that we cannot tie to you personally.

**Processor:** Mixpanel (or equivalent) — see Section 6 for the current list.

### 3.2 Crash Reports

If you leave **Crash Reporting** on, when the App crashes we send:
- The crash stack trace
- Device model (e.g., "iPhone 15 Pro")
- iOS version
- Talkli version + build number
- Approximate memory usage at crash time

We do **not** send screenshots, app state details, or any user-generated content.

**Processor:** Sentry — see Section 6.

### 3.3 Subscription state

When you purchase a Talkli Pro subscription or the Resume Optimizer one-time unlock, Apple processes the payment. To know whether your subscription is active across reinstalls and devices, we use RevenueCat, which holds:
- Your **anonymous device-generated user ID** (not your Apple ID, not your name)
- Subscription product purchased (e.g., `pro_monthly`)
- Subscription status, expiration date, renewal date
- Transaction receipts (issued by Apple)

RevenueCat does not receive your name, email, or any other personally identifying information from us.

**Processor:** RevenueCat — see Section 6.

---

## 4. What we don't do

To be explicit:

- We do **not** sell your data to anyone. Ever.
- We do **not** use your data for advertising purposes.
- We do **not** track you across other apps or websites. (Talkli does not use the iOS App Tracking Transparency framework because we have nothing to track.)
- We do **not** share your data with employers, recruiters, schools, or any third party — except as described in Section 6.
- We do **not** use your sessions, scripts, resumes, or any user-generated content to train AI models. Our AI scoring runs on-device using deterministic algorithms and Apple's native APIs; no LLM is used as of the effective date of this policy. If we add LLM features later, this policy will be updated to disclose what is and isn't sent.

---

## 5. Your rights and controls

### Built into the App
- **Turn off analytics** at any time: You → Privacy Center → toggle Analytics
- **Turn off crash reporting** at any time: You → Privacy Center → toggle Crash Reporting
- **Export your local data**: You → Privacy Center → Export Data
- **Delete every byte of local data**: You → Privacy Center → Clear All Data
- **Cancel your subscription**: iPhone Settings → your Apple ID → Subscriptions → Talkli

### Under GDPR (if you're in the EU/EEA/UK)
You have the right to access, rectify, port, erase, or restrict processing of your personal data. Because we hold so little — and most of what exists is on your device — most of these rights are exercised by tapping **Clear All Data** in the App. For data held by our processors (e.g., subscription status at RevenueCat), email us and we will assist you within 30 days.

### Under CCPA/CPRA (if you're in California)
You have the right to know what personal information is collected, the right to delete it, and the right to opt out of "sale" or "sharing" (we do neither). Categories of personal information we may collect are described in Sections 3.1–3.3 above. To exercise these rights, email us.

### Contact for privacy requests
**Email:** privacy@talkli.app
We will respond within 30 days.

---

## 6. Third-party processors

| Processor | What they do | What they receive |
|---|---|---|
| **Apple** | iOS speech recognition, payment processing | Audio (on-device only — never reaches Apple servers); IAP transactions |
| **RevenueCat** | Subscription state management | Anonymous device-generated user ID, subscription status |
| **Sentry** | Crash reporting (if opted in) | Crash stack traces, device model, OS version, app version |
| **Mixpanel** *(or equivalent)* | Product analytics (if opted in) | Anonymous event data with random user ID |

Each processor is bound by their own privacy commitments. Their privacy policies:
- Apple: https://www.apple.com/legal/privacy/
- RevenueCat: https://www.revenuecat.com/privacy
- Sentry: https://sentry.io/privacy/
- Mixpanel: https://mixpanel.com/legal/privacy-policy/

---

## 7. Children

Talkli is not directed at children under 13, and we do not knowingly collect personal information from children under 13. If you believe a child under 13 has provided us with personal information, contact us at privacy@talkli.app and we will delete it.

Children under 17 should obtain a parent's or guardian's permission before using Talkli.

---

## 8. Data retention

- **On your device:** Until you tap Clear All Data, uninstall the App, or wipe your phone.
- **Analytics events (Mixpanel):** 12 months from collection, after which they are deleted or anonymized into aggregate statistics.
- **Crash reports (Sentry):** 90 days from collection.
- **Subscription state (RevenueCat):** For the life of your subscription + 90 days after cancellation, to handle restoration requests.

---

## 9. Security

We use industry-standard encryption (TLS 1.2+) for any data in transit between your device and our processors. On-device data is protected by your iPhone's built-in encryption. We do not maintain a database of user content, so there is nothing for us to lose in a breach. If a breach affecting opt-in data occurs at one of our processors, we will notify affected users within 72 hours where required by law.

---

## 10. International transfers

Our processors are headquartered in the United States. If you are using Talkli outside the United States, the small amount of opt-in data described in Section 3 may be transferred to and processed in the U.S. and other countries where our processors operate. We rely on standard contractual clauses and our processors' Data Processing Addenda to provide appropriate safeguards for these transfers.

---

## 11. Changes to this policy

We may update this policy from time to time. When we do, we will update the "Last updated" date at the top and, for material changes, notify you in the App before the change takes effect. Your continued use of the App after a material change constitutes acceptance of the updated policy.

We will never make a material change in a way that affects already-collected data without giving you an opportunity to opt out.

---

## 12. Contact

**Mas Dinero Ventures LLC**
[YOUR BUSINESS ADDRESS — fill in before publishing]
Email: privacy@talkli.app

For general questions: hello@talkli.app
For privacy or data requests: privacy@talkli.app

---

*Plain-language summary: We built Talkli to be the rare app you don't have to worry about. Your voice, video, and resume content never leave your phone. The little we do receive (anonymous usage events and crash reports) is opt-in and never sold. Toggle off any time in You → Privacy Center.*
