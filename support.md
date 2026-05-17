# Talkli — Support

Need help with Talkli? You're in the right place. Below are the most common questions, troubleshooting steps, and how to reach us if you're still stuck.

**Last updated:** 2026-05-16

---

## Quick contact

- **Email:** hello@talkli.app
- **Privacy questions:** privacy@talkli.app
- **Press / business:** hello@talkli.app

We aim to reply within 1–2 business days.

---

## Most common questions

### Subscriptions

**How do I cancel my Talkli Pro subscription?**

Subscriptions are managed through your Apple ID, not in the App:

1. Open the **Settings** app on your iPhone
2. Tap your name at the top
3. Tap **Subscriptions**
4. Find **Talkli** in the list
5. Tap **Cancel Subscription**

Your Pro access continues until the end of your current billing period.

**How do I restore a Pro subscription on a new device?**

1. Install Talkli on the new device, sign in to the same Apple ID you used for the original purchase
2. Open Talkli → **You** tab → **Subscription**
3. Tap **Restore Purchases** at the bottom of the paywall

This works for the Resume Optimizer one-time unlock as well.

**Can I get a refund?**

Refunds are processed by Apple, not by us. Visit https://reportaproblem.apple.com, sign in with the Apple ID you used to purchase, find the Talkli transaction, and request a refund. Apple reviews each request individually.

**What's the difference between Talkli Pro Monthly and Annual?**

Same features, different billing cadence. Annual is roughly 33% cheaper per month, billed once a year. You can switch between Monthly and Annual at any time via Settings → Subscriptions; Apple prorates the difference.

**Is the Resume Optimizer included with Pro?**

Yes. Pro subscribers get the Resume Optimizer automatically — no separate purchase needed. The standalone $29 unlock is for users who don't want a subscription.

---

### Permissions

**Talkli is asking for my microphone — is that safe?**

Yes. The microphone is required for the core speaking-coach feature (we need to hear you to give feedback). All audio processing happens on your device using Apple's native Speech Recognition framework. **No audio is ever uploaded to our servers** — it's analyzed and discarded within 60 seconds. See our [Privacy Policy](privacy) for details.

**Why does Talkli want camera access?**

Camera is **optional**. If granted, Talkli analyzes eye contact and posture during sessions using on-device computer vision. **No video frames are saved or uploaded.** You can deny camera permission and Talkli still works — you'll just miss the body-language metrics.

**How do I change permissions after onboarding?**

1. iPhone **Settings** → scroll down → **Talkli**
2. Toggle Microphone / Camera / Notifications as you like

---

### Privacy

**Where does my session data go?**

Everywhere on your phone — and nowhere else. Audio, video, transcripts, and resume content are all processed using Apple's native on-device APIs (Speech Recognition, Vision, PDFKit). The App stores your session scores, history, and uploaded resume content in local encrypted storage on your iPhone.

**How do I delete my data?**

You tab → **Privacy Center** → **Clear All Data**. This wipes every session, score, uploaded file, and onboarding choice from your device.

**Can I export my data?**

Yes. You tab → **Privacy Center** → **Export Data** generates a JSON file with your session history that you can save via the share sheet.

---

### Troubleshooting

**The microphone isn't picking up my voice during a session.**

1. Confirm you've granted microphone permission (iPhone Settings → Talkli → Microphone is **On**)
2. Make sure no other app is using the microphone (Phone call, Voice Memos, etc.)
3. Try increasing your input volume — speak about 6–12 inches from the phone
4. Restart the App: swipe up to close, then reopen
5. If still broken: restart your iPhone

**My scores look off — way too high or way too low.**

The on-device scoring uses heuristics (words-per-minute, filler-word frequency, energy levels). It works best when:
- You speak naturally — don't whisper or shout
- You speak for the suggested duration — too-short sessions skew metrics
- You're in a relatively quiet space — heavy background noise can confuse the system

If scores are consistently off, email us with the session length and what you were practicing. We use this feedback to tune the scoring model.

**The Resume Optimizer can't read my file.**

Make sure your file is one of: **PDF, DOCX, RTF, TXT**. Scanned PDFs (where the text is actually an image) won't work because there's no text to extract — re-export from your editor as a text-based PDF. If you have a `.doc` file (older Word format), re-save it as `.docx` in Word.

If the file is in a supported format and you're still seeing errors, try:
1. Closing and reopening Talkli
2. Picking the file again
3. As a last resort, copy your bullets into the paste field manually — the scoring and rewrites still work

**The App crashed.**

If you have Crash Reporting enabled (You → Privacy Center), we already received the stack trace and are looking into it. If you want to send additional context, email us with:
- What you were doing when it crashed
- iPhone model and iOS version (Settings → General → About)
- Talkli version (You tab → scroll to bottom)

**I forgot which Apple ID I used to subscribe.**

Check your Apple **Wallet & Apple Pay** or your iPhone **Settings → your name → Subscriptions** — your active subscriptions show the Apple ID that owns them. If you have multiple Apple IDs, sign into the right one before tapping **Restore Purchases**.

---

### Feature requests + feedback

We read every message. Email us at **hello@talkli.app** with:
- What feature you'd like to see
- Why it would matter for how you practice
- Any rough idea of how you'd want it to work

We can't promise to ship every request, but the most-requested features shape our roadmap.

---

## Compatibility

- **iOS 15.1 or later** — required (we use iOS 15.1+ frameworks)
- **iPhone only** — no iPad support in v1
- **Internet not required for the core experience** — voice coaching works fully offline. An internet connection is needed only for: in-app purchases, subscription state checks, and crash report uploads (if you opt in).

---

## Reporting a bug

Email **hello@talkli.app** with:
1. What you did (e.g., "Tapped Start Session on the Practice tab")
2. What you expected to happen
3. What actually happened
4. iPhone model + iOS version
5. Talkli version
6. Screenshots, if relevant

Bonus points if Crash Reporting is on — that gives us the technical detail to investigate fast.

---

## Stay updated

Talkli ships updates regularly. To get them:
- Open the **App Store** app → tap your profile → scroll to "Available Updates"
- Or turn on **automatic updates** in iPhone Settings → App Store → App Updates

---

## Refund policy

Refunds for Talkli purchases (subscriptions or one-time unlocks) are handled by Apple. See https://support.apple.com/en-us/HT204084 for Apple's refund policy and request process. We don't process refunds directly because we never see your payment info.

---

## Still need help?

**Email: hello@talkli.app**

We're a small team. Replies come from a real human and usually arrive within 1–2 business days. If your issue is urgent (App is unusable, refund question, privacy concern), say so in the subject line and we'll bump it up the queue.

---

*Mas Dinero Ventures LLC · 2026*
