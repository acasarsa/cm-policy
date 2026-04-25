## Data You're Collecting

### Personal Identity
- **First name, last name** — publisher registration + subscriber upgrade
- **Email address** — both publishers and subscribers (normalized to lowercase)
- **Passwords** — hashed with bcrypt (good, never stored in plaintext)
- **Avatars** — profile photos uploaded to AWS S3

### Subscriber-Specific
- **Name + email** — collected at subscription signup
- **Approval state** — pending/approved/rejected + timestamps
- **Email frequency preference** — immediate/daily/weekly/monthly/unsubscribed
- **Interaction notification preference** — boolean toggle
- **`last_visited_at`** — tracks when subscriber last accessed a blog

### User-Generated Content
- **Comments** — body text (max 2000 chars), linked to author (subscriber or publisher)
- **Reactions/emoji** — linked to author
- **Posts** — title, rich text body, media attachments (publisher content)

### Authentication & Tokens
- **Session cookies** — `_treehouse_remember` (1 year, publisher auth), `_treehouse_subscriber` (1 year, contains email + subscriber IDs in JSON)
- **Magic link tokens** — hashed, with expiry and usage timestamps
- **Subscriber login tokens** — hashed, with expiry
- **Post access grants** — which subscriber accessed which post, when, and how

### Behavioral/Activity Data
- **Post view counts** — aggregate only, not per-user (good for privacy)
- **Notification records** — who commented/replied on what, read status
- **Token reissue attempts** — email + timestamp (rate limiting)

### Technical/Operational
- **IP addresses** — used transiently for Rack::Attack rate limiting (not persisted long-term)
- **Request logs** — request IDs, but sensitive params (password, email, token, etc.) are filtered out

---

## Third-Party Services That Touch User Data

| Service | Data Sent | Purpose |
|---------|-----------|---------|
| **Brevo (Sendinblue)** | Subscriber emails, names, post titles/excerpts | Transactional email delivery |
| **AWS S3** | Uploaded files (avatars, post media) | File storage |
| **Google Fonts CDN** | Browser makes requests to `fonts.googleapis.com` | Font loading (sends user IP/user-agent to Google) |

No analytics, no payment processing, no social login, no fingerprinting.

---

## GDPR Compliance Assessment

### What you're doing well
- **No third-party analytics or tracking** — major win
- **Password hashing** with bcrypt
- **Sensitive param filtering** in logs
- **Rate limiting** without persistent IP storage
- **Post views are aggregate**, not per-user
- **No localStorage tracking**
- **Cookie usage is functional only** (auth), not tracking

### Gaps to address for GDPR compliance

1. **Right to Erasure (Article 17)** — You mentioned wanting users to delete their data. Currently there's no "delete my account" flow in the app. You'll need:
   - Publisher account deletion (cascade to posts, comments, media, notifications)
   - Subscriber self-deletion from any blog they're subscribed to
   - Removal of their data from Brevo as well

2. **Data Export / Portability (Article 20)** — GDPR requires users can download their data in a portable format. No export feature exists yet.

3. **Cookie Consent** — The subscriber cookie stores email + subscriber IDs for 1 year. Under GDPR, even functional cookies need disclosure. You should have a cookie notice explaining what cookies you set and why. Since yours are strictly functional (no tracking), you likely don't need a consent *banner*, but you do need to disclose them in your privacy policy.

4. **Google Fonts** — This is a known GDPR issue. Loading fonts from Google's CDN sends user IP addresses to Google on every page load. An Austrian court ruled this violates GDPR. **Fix: self-host the Nunito font** instead of loading from `fonts.googleapis.com`.

5. **Brevo as Data Processor** — You need a Data Processing Agreement (DPA) with Brevo. They likely have a standard one — make sure it's signed and on file.

6. **Consent for Email** — Your subscriber signup implicitly collects consent, but your privacy policy should clearly state what emails subscribers will receive and how to unsubscribe. The email frequency preference is a good mechanism here.

7. **Data Retention Policy** — No documented retention periods. How long do you keep expired tokens, rejected subscribers, old notifications? GDPR expects you to not keep data longer than necessary.

8. **Privacy Policy itself** — Needs to clearly state:
   - What data you collect (this list)
   - Why (legal basis — likely "legitimate interest" for functional data, "consent" for email)
   - Who processes it (Brevo, AWS)
   - How long you keep it
   - How users can request deletion/export
   - Contact info for data inquiries

### For planned geographic aggregation

When you add state/region tracking for ad spend analysis, as long as you:
- Aggregate it (don't store per-user location)
- Derive it from shipping/billing info users voluntarily provide, or infer from IP at aggregate level
- Don't use third-party geolocation services that track individuals

...you'll stay in line with your privacy-first approach and GDPR.

---

## Priority Action Items

1. **Self-host Google Fonts** — quick fix, removes a GDPR liability
2. **Build account/data deletion flows** — needed before privacy policy can promise it
3. **Sign DPA with Brevo**
4. **Write the privacy policy** covering the data inventory above
5. **Add data export capability** (can be a simple JSON download of user's data)