# Privacy Policy for Nytcrew (formerly Sifty)

**Last Updated:** October 20, 2026
**Effective Date:** October 20, 2026

---

## The short version

- **Your photos never leave your phone.** Nytcrew looks at your photos with an AI model that runs on your phone. No photo, thumbnail or copy of a photo is ever uploaded, to us or to anyone else.
- **To decide what's clutter, Nytcrew sends a short text description of each photo** (one or two sentences, plus up to 25 words of text visible in the photo) and the photo's age in days to our server, which asks Google's Gemini to score it. Emails, links, @handles and long numbers are masked on your phone before anything is sent.
- **We back up your results** (scores, the masked description and your keep/delete choices) to your Nytcrew account so you don't lose them if you reinstall.
- **We don't sell your data, show ads or use advertising trackers.**

The rest of this policy explains each point in detail.

---

## 1. Who we are

Nytcrew, formerly called Sifty ("we", "our", "us"), is an Android app that keeps your photo gallery clean and searchable. It is developed by an independent developer, reachable at **mohdjun95@gmail.com**.

This policy covers the Nytcrew app, version 2.6 and later ("Private Mode"). Earlier versions (2.4 and older) worked differently and sent compressed photos to the cloud for analysis; their policy is [here](https://mohdjun95.github.io/privacy-policies/sift-v1.html). If you still use an older version, please update.

---

## 2. What stays on your phone

These never leave your device:

- **Your photos**, in any form: originals, thumbnails or compressed copies.
- **The full text read from your photos.** Nytcrew uses Google ML Kit, on your phone, to read text in photos (for example on a screenshot or a document) so that you can search for it. That text is stored only on your phone.
- **Visual fingerprints** used to find similar shots (a small numeric summary of how a photo looks).
- **Your search history.**
- **The AI model itself** (about 330 MB to 1.6 GB, depending on the app version), which is stored in the app's private storage and excluded from Android backup.

---

## 3. What we collect, and why

### 3.1 Account information
When you sign in with Google or with an email and password, Firebase Authentication stores your **email address**, your **name** (if you signed in with Google) and a **user ID**. We use these only to keep your account and your backup.

### 3.2 Text descriptions sent for scoring
For each photo, your phone sends our server (a Firebase Cloud Function):
- a **short description** written on your phone (for example, "A screenshot of a train ticket booking page"),
- **up to 25 words of text visible in the photo**, if it has any,
- the **photo's age in days**.

Before sending, the app masks email addresses, web links, @handles, long digit runs (such as phone, card or account numbers) and code-like strings.

Our server forwards this text to **Google's Gemini API**, which returns seven scores (for example, how likely the photo is a memory, a document or clutter). Our server does not store the text: it returns the scores to your phone and keeps only a record of when each request was made, to limit how often the server can be called. Google processes the text under the [Gemini API terms](https://ai.google.dev/gemini-api/terms).

### 3.3 Your cloud backup
So you don't lose your results when you change phones or reinstall, Nytcrew stores the following in your account (Firebase Firestore), for each photo it has scored:
- the photo's **file name and folder** on your phone, its media ID, file size and last-modified date,
- the **masked description** and the seven scores,
- whether Nytcrew suggested keeping it, and **your keep/delete choice** in Review.

It also stores:
- your **learned preferences**: the weights Nytcrew learned from your Review choices,
- **night-scan statistics**: counts of how nights went (for example, "scanned while charging" or "battery too low") and a battery-level band. These are counts only, with no times or locations.

We use this data only to restore your results and to improve how Nytcrew works for you. Only you (signed in) and our backend can read it. Security rules prevent anyone else from accessing it.

### 3.4 Crash and error reports
When the app crashes or a scan fails, **Firebase Crashlytics** receives a report with the error, the app version and technical details about your phone: maker and model, Android version, RAM, processor type and, for scans, how long the scan ran. If the on-device AI has trouble with a photo, the report also includes the free memory and battery level at that moment, how long the photo took, and the photo's file type and size (never its name or folder). Reports never include your photos, descriptions, file names, folders or email address, and they are not linked to your account.

### 3.5 App integrity checks
**Firebase App Check** (using Google Play Integrity) confirms that requests to our server come from the genuine Nytcrew app. This helps stop abuse of our servers. Google processes device integrity signals for this check.

### 3.6 Model download
The first time you allow photo access, Nytcrew downloads its AI model from **Hugging Face** (huggingface.co). Like any download, Hugging Face can see your IP address. No personal data is sent with the download.

### 3.7 What we do NOT collect
- No photos, thumbnails or copies of photos
- No location data
- No contacts, messages or call logs
- No advertising ID, and no advertising or analytics trackers
- No payment details (the current version has no in-app purchases)

---

## 4. Permissions

| Permission | Why Nytcrew needs it | Required? |
|---|---|---|
| **Photos** (READ_MEDIA_IMAGES; READ_EXTERNAL_STORAGE on older Android) | To look at your photos on your phone | Yes. Nytcrew can't work without it. If you allow only some photos, Nytcrew works on those |
| **Notifications** (POST_NOTIFICATIONS) | To show scan progress and let you review photos from a notification | Optional |
| **Background scanning** (FOREGROUND_SERVICE, FOREGROUND_SERVICE_DATA_SYNC, WAKE_LOCK) | To keep scanning with the screen off, with a visible notification while it runs | Required for scanning |
| **Battery optimization exemption** (REQUEST_IGNORE_BATTERY_OPTIMIZATIONS) | So nightly scans aren't stopped by Android. You grant this in Android's settings | Optional |
| **Media management** (MANAGE_MEDIA, Android 12+) | "One-tap delete": move photos you chose to delete to the phone's trash without an extra Android prompt. You grant this in Android's settings | Optional |
| **Internet** (INTERNET) | To sign in, score descriptions, back up results and download the model | Yes |

Nytcrew never deletes a photo on its own. Photos are deleted only when you choose to delete them, and they go to your phone's trash, where Android keeps them for 30 days.

---

## 5. Who we share data with

We **never sell or rent** your data, and we don't share it for advertising.

Data is processed only by these service providers, to run the app:

| Provider | What for | Privacy policy |
|---|---|---|
| Google Firebase (Authentication, Firestore, Cloud Functions, Crashlytics, App Check) | Account, backup, scoring server, crash reports, integrity checks | [firebase.google.com/support/privacy](https://firebase.google.com/support/privacy) |
| Google Gemini API | Scoring the text descriptions | [policies.google.com/privacy](https://policies.google.com/privacy) |
| Hugging Face | Hosting the AI model download | [huggingface.co/privacy](https://huggingface.co/privacy) |

We may also disclose data if the law requires it, or to protect the safety of our users or the public.

---

## 6. How long we keep data

- **On your phone:** until you uninstall Nytcrew or clear its data.
- **Account and cloud backup:** while your account exists. When you delete your account (see section 7), we delete your account and backup within 30 days.
- **Scoring text:** not stored by our server. It is processed and discarded. The request times kept for rate limiting are removed with your account.
- **Crash reports:** kept by Firebase Crashlytics for up to 90 days.

---

## 7. Your choices and rights

- **Delete your account and data:** email **mohdjun95@gmail.com** from the address you signed in with, with the subject "Delete my Nytcrew account". We'll delete your account, your cloud backup, your learned preferences and your night statistics within 30 days and confirm by email. Your photos are not affected: they stay on your phone.
- **Get a copy of your data:** email us and we'll send you your cloud backup.
- **Correct your data:** email us.
- **Withdraw permissions:** turn off photo, notification or other access at any time in Android's settings. Nytcrew stops scanning without photo access.
- **Stop scanning:** tap Stop at any time, or turn off nightly scans and the bedtime reminder in Settings.

Depending on where you live, you may have further rights:
- **India (Digital Personal Data Protection Act, 2023):** you can access, correct and erase your data, nominate someone to exercise your rights, and raise a grievance with us at the email above. If you're not satisfied with our response, you can complain to the Data Protection Board of India.
- **EU/UK (GDPR):** you can also object to or restrict processing, ask for data portability, and complain to your data protection authority. We process your data to provide the service you asked for (contract) and, for crash reports and integrity checks, for our legitimate interest in keeping the app reliable and secure.
- **California (CCPA/CPRA):** you can know, delete and correct your data. We do not sell or share personal information for advertising.

---

## 8. Security

- All data is sent over encrypted connections (HTTPS/TLS).
- Your cloud backup can only be read or written by your signed-in account. Our database security rules enforce this.
- Our scoring server accepts only requests from signed-in users of the genuine app, and limits how often it can be called.
- Sign-in details on your phone are kept in Android's encrypted secure storage.

No system is perfectly secure, but we design Nytcrew to keep as little data off your phone as possible.

---

## 9. Children

Nytcrew is not intended for children under 13 and we don't knowingly collect their data. In India, users under 18 should use Nytcrew only with a parent's or guardian's consent. If you believe a child has given us personal data, email us and we will delete it.

---

## 10. International transfers

Our service providers may process data in countries other than yours, including the United States. They protect it under their own data protection terms.

---

## 11. Changes to this policy

When we change this policy, we'll update the date at the top. For important changes, such as sending new kinds of data off your phone, we'll tell you in the app before the change takes effect.

---

## 12. Contact

Questions, requests or complaints (including grievances under India's DPDP Act):

**Email:** mohdjun95@gmail.com

---

## Version history

- **v2.1** (October 20, 2026): The app is now called Nytcrew (formerly Sifty). Crash reports can include memory, battery and timing details for a photo the on-device AI had trouble with.
- **v2.0** (October 14, 2026): Rewritten for Private Mode (app version 2.6+). Photos are no longer uploaded. Analysis is done on the device, and only masked text descriptions are scored in the cloud.
- **v1.0** (December 27, 2025): Initial policy (cloud analysis of compressed photos, app versions up to 2.4).
