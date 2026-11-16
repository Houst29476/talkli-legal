# Privacy Policy

**Effective date:** 2026-08-04
**Last updated:** 2026-11-14
**Supersedes:** the version dated 2026-05-16

This Privacy Policy describes how Mas Dinero Ventures LLC ("**we**," "**us**," or "**our**") handles information when you use Talkli (the "**App**") on iPhone or Android. We built Talkli around a single promise: **your voice, your video, your résumé — they stay on your phone**. This policy explains exactly what that means, exactly where its one exception is, and the small set of other things we receive.

> **What changed in this revision.** The previous version was written before
> three things shipped and did not describe them accurately. It has been
> corrected to disclose: (a) that the optional Cloud AI Coach sends transcript
> text to **Google**, not Anthropic; (b) that product analytics and crash
> reporting go to our own analytics service and to Sentry respectively (they
> were enabled by default then; since 2026-11-14 both are **off by default** and
> start only if you turn them on) — Mixpanel is not and never was used; and (c) that the App
> checks for over-the-air updates with Expo on every launch. Nothing about what
> the App *does* with your audio, video or résumé changed: those still never
> leave your device. Since 2026-11-14 the App also asks you once, during setup,
> whether to share anonymous analytics; off remains the default (Section 3).

---

## 1. The short version

The things most likely to be private — your **audio, your video, your résumé content** — are processed entirely on your phone, and **never leave it**. We cannot listen to your practice, see your face during a session, or read your résumé. That is a property of how the App is built, not a policy we could quietly change: the analysis runs in your phone's own frameworks (iOS Speech Recognition, Vision and PDFKit; Android ML Kit on-device recognition).

There is exactly **one** way any of your practice content can leave the device, and it is off until you turn it on:

- **Cloud AI Coach** (off by default, Pro only). When you switch it on, the **text transcript** of a mock-interview answer is sent — never the audio — so a large language model can write the critique. See Section 2a.

Beyond that, the information we can see is limited to:

- **Anonymous app usage events** — **off by default**; sent only if you choose to share them when the App asks once during setup, or turn them on in the Privacy Center
- **Anonymous crash and error reports** — **off by default**; sent only if you turn them on in the Privacy Center
- **Subscription state** — managed by Apple or Google plus RevenueCat, needed to know whether you're Pro
- **App update checks** — the App asks Expo's update service on each launch whether a newer version exists

You can turn analytics and crash reporting off at any time in the App at **You → Privacy Center**, and you can delete every byte of local data with one tap.

If you want the long version, read on.

---

## 2. What stays on your device

All of the following is *processed* entirely on your phone, using the operating system's own frameworks. Everything in this table except one row is also *never transmitted*, and we never receive, store, or have access to it. The exception is called out in the table and detailed in §2a — we would rather put it in front of you than bury it.

| Data | How it's processed | When it's deleted |
|---|---|---|
| **Microphone audio** | On-device speech recognition — `SFSpeechRecognizer` with on-device recognition required on iOS, Google ML Kit on Android | The capture file lives in the App's private cache during the session and is deleted when the session ends |
| **Camera video frames** | On-device face detection (iOS Vision / ML Kit) | Never stored — analysed frame-by-frame in memory and immediately discarded |
| **Speech transcripts** — *the one exception* | Generated on-device for filler-word detection, pace and scoring | Stored locally on your device. Not transmitted — **unless you switch on Cloud AI Coach**, which sends transcript text (never audio) for interview critique. See §2a. |
| **Résumé content** (text from PDF, DOCX, RTF, TXT files) | Parsed on-device using Apple PDFKit plus the open-source fflate library | Held in memory while you're using the Résumé Optimizer. Optionally cached locally; removable via Clear All Data. |
| **Session scores + history** | Computed on-device | Stored locally on your device only. Removable via Clear All Data. |
| **Onboarding selections** (name, goals, coach persona, schedule) | Stored locally on your device only | Removable via Clear All Data. |

Your name, your résumé and your job-description text are never included in any analytics event, crash report or coaching request. There is no field in any outbound payload that can carry them.

When this policy says "local," we mean a storage container on your own phone (an encrypted `MMKV` store plus the standard file system). See Section 9 for what that encryption is and is not.

---

## 2a. Cloud AI Coach — the one thing that leaves your device

Cloud AI Coach is **off by default**. You turn it on yourself in Settings, and you can turn it off at any time. It is a Pro feature and is enforced as one on our server, not just in the App.

When it is on, and **only on the mock-interview surface**, Talkli sends the following to our coaching server at `talkli-api.vercel.app`:

- the **text transcript** of your answer, verbatim
- the interview question you were answering
- your coach persona and the interview category
- your six numeric scores (pace, filler rate, energy, duration, suggested duration, overall)
- your app language, so the critique comes back in your language
- your anonymous install identifier, so the server can confirm you have Pro

Our server forwards that to **Google** (the Gemini model family) to generate the critique, and returns the text to your phone. Google is the default and current provider; the server can be configured to use Anthropic's Claude instead, and this policy will name whichever is live. No model provider's key is ever held on your phone.

- **Your audio is never sent.** Not when this is on, not ever. The recording stays on the device, is used for on-device analysis, and is deleted.
- **Your video is never sent**, and neither is your résumé.
- Nothing is stored on our server: the transcript is used to produce the critique and dropped. It is not used to train any model.
- The request travels over TLS and passes through Vercel, which hosts the server and therefore handles it in transit and logs the request's IP address as ordinary server-access metadata.
- With the toggle off, **no part of your speech or transcript leaves the device.**

If you want the strongest guarantee, leave it off. Every core metric (pace, fillers, energy, eye contact, posture, confidence) is computed on-device either way, and with the toggle off the coaching you receive is generated locally.

---

## 3. What we receive

Each of the first two categories below is controlled by an explicit toggle in **You → Privacy Center**. Both are **off by default** (since 2026-11-14; installs from before then were switched off once by the update). Nothing in them is sent unless you turn the toggle on, and turning either off stops transmission immediately, not at the next launch.

**The one question during setup.** On the permissions step of setup, the App asks once whether you want to share anonymous product analytics (3.1) — not crash reports, which stay a Privacy Center toggle. The two answers, "Share analytics" and "Keep analytics off", carry equal weight and neither is pre-selected; you cannot skip past without picking one, and either one lets you continue. "Share analytics" turns on the same Analytics toggle; "Keep analytics off" leaves it off. Nothing is sent before you answer, the question is not asked again, and you can change your answer at any time in the Privacy Center.

### 3.1 Product analytics (off by default)

If you turn **Analytics** on, we receive anonymous event data such as:

- Which screens you visit (e.g. `today_viewed`, `session_started`)
- Which features you use (e.g. `script_generated`, `resume_ats_scored`)
- Aggregate counts, durations, and scores for those events
- Your device class (e.g. "phone"), the Talkli version, and a per-launch session identifier

We do **not** receive:

- Names, email addresses, or any personal identifier
- The content of your sessions, transcripts, scripts, résumé, or job descriptions
- Any free-form text at all — the event vocabulary is a fixed list defined in the App, with no field capable of carrying it
- Any data that could be used to identify you individually

Events are associated with a randomly generated install identifier (a v4 UUID) that we cannot tie to you personally, that is not derived from any device or advertising identifier, and that does not survive uninstalling the App.

Events are buffered on the device and sent in signed batches roughly every 30 seconds. Turning the toggle off discards the buffer and stops sending.

If you choose "Share analytics" during setup, the App also sends one event recording that this install was opened for the first time — the event it would have sent when you first opened it, which was not sent then because analytics was off — so your install is counted once. It is sent at the moment you answer and carries no more than any other event in 3.1. No other event from before your answer is sent.

**Where it goes:** our own first-party analytics service, which we operate — not a third-party analytics vendor. See Section 6.

### 3.2 Crash and error reports (off by default)

If you turn **Crash Reporting** on, when the App crashes or hits an error we send:

- The crash or error stack trace and message
- Recent in-app breadcrumbs (screen and action names, no content)
- Device model (e.g. "iPhone 15 Pro"), OS version, Talkli version and build
- A small sample (about 10%) of performance traces, so we can find slow screens
- The same anonymous install identifier described in 3.1

Before anything is transmitted, an outbound filter strips a specific list of forbidden fields — transcripts, audio and recording paths, script bodies, résumé text, names and email addresses — so that user content cannot ride along in an error report. We do not send screenshots.

Turning the toggle off ends the reporting session immediately, including anything already queued.

**Processor:** Sentry — see Section 6.

### 3.3 Subscription state

When you purchase Talkli Pro or the Résumé Optimizer one-time unlock, Apple or Google processes the payment. To know whether your subscription is active across reinstalls and devices, we use RevenueCat, which holds:

- Your **anonymous install-generated user ID** (not your Apple ID, not your Google account, not your name)
- The product purchased (e.g. `pro_monthly`)
- Subscription status, expiration date, renewal date
- Transaction receipts issued by Apple or Google

RevenueCat receives no name, email, or other personally identifying information from us. This path has no opt-out toggle, because without it we cannot sell or restore a subscription.

**Processor:** RevenueCat — see Section 6.

### 3.4 App update checks (no opt-out)

Talkli ships over-the-air updates through Expo's EAS Update service. On **every launch**, the App asks `u.expo.dev` whether a newer JavaScript bundle exists for your build. That request carries the App's runtime version, its release channel, your platform (iOS or Android), and the identifier of the update you currently have — plus the IP address and user-agent that any HTTPS request necessarily reveals.

It carries no user content and no install identifier. There is no toggle for this: it is the mechanism by which we ship fixes to you.

**Processor:** Expo — see Section 6.

---

## 4. What we don't do

To be explicit:

- We do **not** sell your data to anyone. Ever.
- We do **not** use your data for advertising purposes. There is no ad SDK, no attribution SDK, and no advertising identifier is read.
- We do **not** track you across other apps or websites. (Talkli does not use the iOS App Tracking Transparency framework because we have nothing to track.)
- We do **not** share your data with employers, recruiters, schools, or any third party — except the processors described in Section 6.
- We do **not** use your sessions, scripts, résumés, or any other content to train AI models — neither ours nor a provider's.
- We do **not** send audio or video off your device under any setting, opt-in or otherwise.

**On AI, precisely:** all scoring and all six live metrics are computed on your device by deterministic algorithms and the platform's native speech and vision APIs. No large language model is involved in that. A large language model is involved in exactly one place — the optional Cloud AI Coach critique described in Section 2a — and only when you have switched it on. With that toggle off, no LLM ever sees anything of yours.

---

## 5. Your rights and controls

### Built into the App

- **Turn off analytics** at any time: You → Privacy Center → Analytics
- **Turn off crash reporting** at any time: You → Privacy Center → Crash Reporting
- **Turn off Cloud AI Coach** (or leave it off — it starts off): Settings → Cloud AI Coach
- **Export your local data**: You → Privacy Center → Export Data
- **Delete every byte of local data**: You → Privacy Center → Clear All Data
- **Cancel your subscription**: iPhone Settings → your Apple ID → Subscriptions → Talkli, or Google Play → Subscriptions → Talkli

### Under GDPR (if you're in the EU/EEA/UK)

You have the right to access, rectify, port, erase, or restrict processing of your personal data. Because we hold so little — and most of what exists is on your device — most of these rights are exercised by tapping **Clear All Data** in the App. For data held by our processors (for example subscription status at RevenueCat, or an event history keyed to your install identifier), email us and we will assist you within 30 days. If you send us your install identifier we can locate and delete the records associated with it.

Our legal bases: **consent** for analytics, crash reporting and Cloud AI Coach (each separately withdrawable in-app); **contractual necessity** for subscription state; and **legitimate interests** for the update check, which is limited to delivering software fixes.

### Under CCPA/CPRA (if you're in California)

You have the right to know what personal information is collected, the right to delete it, and the right to opt out of "sale" or "sharing" — we do neither. The categories we may collect are identifiers, commercial information (purchases), internet or network activity (app interactions and diagnostics), and, only if you enable Cloud AI Coach, the text you provide to it. These are described in Sections 2a and 3.1–3.4. To exercise these rights, email us.

### Contact for privacy requests

**Email:** privacy@talkli.app
We will respond within 30 days.

---

## 6. Third-party processors

| Processor | What they do | What they receive |
|---|---|---|
| **Apple** | On-device speech recognition and vision; payment processing | Speech and vision run locally and send Apple nothing. Apple receives IAP transactions. |
| **Google** (Android platform) | On-device speech recognition and face detection; payment processing | Recognition runs locally and sends Google nothing. Google Play receives IAP transactions. |
| **Google** (Gemini) | Generates the Cloud AI Coach critique — **only if you enable it** | Transcript text, the question, your coach persona, six numeric scores, your language |
| **Anthropic** | Alternate provider for the same critique; used only if we switch our server to it | The same fields as Google |
| **Vercel** | Hosts our coaching server and our analytics ingest endpoint | Handles the coaching request (including the transcript) in transit; logs request IP addresses as server-access metadata |
| **Supabase** | Database behind our first-party analytics service | Stores the anonymous analytics events described in 3.1 |
| **Sentry** | Crash, error and performance reporting (if left on) | Stack traces, breadcrumbs, device model, OS version, app version, anonymous install ID |
| **Expo** | Over-the-air app updates | Runtime version, channel, platform, current update ID, request IP |
| **RevenueCat** | Subscription state management | Anonymous install-generated user ID, subscription status, store receipts |

Each processor is bound by its own privacy commitments and by our agreements with them. Their privacy policies:

- Apple: https://www.apple.com/legal/privacy/
- Google: https://policies.google.com/privacy
- Anthropic: https://www.anthropic.com/legal/privacy
- Vercel: https://vercel.com/legal/privacy-policy
- Supabase: https://supabase.com/privacy
- Sentry: https://sentry.io/privacy/
- Expo: https://expo.dev/privacy
- RevenueCat: https://www.revenuecat.com/privacy

**We do not use Mixpanel.** An earlier version of this policy named Mixpanel as our analytics processor. That was never accurate — analytics have always gone to our own first-party service — and the reference has been removed.

---

## 7. Children

Talkli is not directed at children under 13, and we do not knowingly collect personal information from children under 13. If you believe a child under 13 has provided us with personal information, contact us at privacy@talkli.app and we will delete it.

Children under 17 should obtain a parent's or guardian's permission before using Talkli.

---

## 8. Data retention

- **On your device:** until you tap Clear All Data, uninstall the App, or wipe your phone.
- **Analytics events:** 12 months from collection in our own analytics database, after which they are deleted or aggregated into statistics that identify no install.
- **Cloud AI Coach transcripts:** not retained. The transcript is used to produce the critique and dropped; it is not written to a database by us.
- **Crash and performance reports (Sentry):** 90 days from collection.
- **Subscription state (RevenueCat):** for the life of your subscription plus 90 days after cancellation, to handle restoration requests.
- **Update-check logs (Expo, Vercel):** ordinary server-access logs, retained by those providers under their own policies and not used by us for any purpose beyond operating and debugging the service.

---

## 9. Security

We use industry-standard encryption (TLS 1.2+) for all data in transit between your device and our processors — every network path described in this policy is encrypted.

On your device, your Talkli data is held in an encrypted MMKV store using **AES-128**, with a random key generated on your phone at install and held in the operating system's keychain — it is never transmitted and never leaves the device. That store additionally sits inside the App's private container, protected by the operating system's own file encryption. (An earlier version of our in-app copy said AES-256. It was wrong, and we corrected the copy rather than quietly leaving it.)

We maintain no database of your practice content — no audio, no video, no résumés, no transcripts — so there is nothing of that kind for us to lose in a breach. If a breach affecting the opt-in data described in Section 3 occurs at one of our processors, we will notify affected users within 72 hours where required by law.

---

## 10. International transfers

Our processors are headquartered in the United States. If you are using Talkli outside the United States, the data described in Sections 2a and 3 may be transferred to and processed in the U.S. and other countries where our processors operate. We rely on standard contractual clauses and our processors' Data Processing Addenda to provide appropriate safeguards for these transfers.

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

*Plain-language summary: Your voice, your video and your résumé never leave your phone — all the speech analysis and scoring happens on the device. The only thing that can ever leave is the text transcript of a mock-interview answer, and only if you switch on Cloud AI Coach, which starts off. Anonymous usage and crash data are off by default and only sent if you turn them on at You → Privacy Center. We sell nothing and train nothing on you.*
