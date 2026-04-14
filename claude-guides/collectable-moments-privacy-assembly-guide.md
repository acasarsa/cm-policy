# Collectable Moments — Privacy Policy Assembly Guide
*Last updated: April 7, 2026*

This guide serves three purposes:
1. Track what's in the policy, where it came from, and why
2. Track what was deliberately excluded and what triggers adding it
3. Provide a change log for future policy updates

---

## POLICY STRUCTURE — CURRENT STATE

### Preamble / Promise *(top of page)*
**Status:** Drafted — original
**Source:** Original — inspired by Tinybeans' Promise format
**Content:**
> The Collectable Moments Promise
> - Your photos belong to you, always.
> - Only people you invite can ever see them.
> - We will never sell your data or use it to train AI.

---

### Intro Paragraph
**Status:** Working draft — revisit phrasing before launch
**Source:** Original — collaboratively drafted
**Content:**
> Collectable Moments ("We", "our service") was built because your family's
> memories shouldn't come with a price tag paid in data. We will never use
> your photos or data to train AI models, sell to third parties, or target
> you with ads. The only third-party services we use are those strictly
> required to operate the site — hosting, email delivery, and payments.
> No third-party algorithms or tracking.

**Note:** "Currently" considered for third-party services line but omitted
for cleanliness. Update intro if optional services are added.

---

### Who This Applies To (Preamble)
**Status:** Drafted
**Source:** Adapted from 37signals preamble — B2B end user paragraphs removed
**Content:**
> This policy applies to visitors, prospective users, and registered users
> of Collectable Moments. We refer collectively to these individuals as "you"
> throughout this policy. If you are a California resident, please see
> Section [STATE/INTERNATIONAL] for additional disclosures required by
> California law.

**Note:** Update California section number once final numbering is confirmed.

---

### Definitions
**Status:** Drafted — can expand over time
**Source:** FamilyAlbum Section 3 (adapted) + original hybrid definition
**Decisions:**
- "Personal data" not "personal information" — more GDPR-aligned, used throughout
- "Child" definition deliberately omitted — children are subjects not users
- Three definitions only for now — expand as policy grows

**Content:**
> (a) "Personal data" means any data which relates to you and from which
> you can be identified, or is reasonably capable of being associated with
> you. It may include contact details, other personal information as defined
> under applicable data protection laws, photographs, and videos.
>
> (b) "Processing" means any activity or operation that is carried out in
> respect of your personal data, including collecting, storing, using,
> transferring, and deleting.
>
> (c) "Service" refers to the Collectable Moments website and all features
> available through it.

---

### Section 1 — Who We Are
**Status:** Drafted — original
**Source:** Original + FamilyAlbum Section 2 "data controller" language
**Decisions:**
- "Independently operated by our team" — avoids legal entity claims before LLC formed
- "Data controller" line added for GDPR compliance
- LLC transition noted — update when formed

**Content:**
> Collectable Moments is currently operated by our team based in the United
> States. We intend to transition to a limited liability company (LLC) in
> the future. This policy will be updated to reflect that change when it occurs.
>
> For the purpose of applicable data protection laws, Collectable Moments
> is the data controller with respect to your personal data.
>
> Contact: [CONTACT EMAIL]

---

### Section 2 — What We Collect and Why
**Status:** Drafted
**Source:** Multiple — see subsections

#### 2a. Account Information
**Source:** 37signals "Identity and access" (adapted — company name, newsletter removed)
+ Tinybeans 1(a) "we do not collect unless voluntarily provided"
**Decisions:**
- Profile picture included — feature exists in codebase
- Newsletter/survey language removed — feature not built
- "Personal data" used throughout not "personal information"

#### 2b. Billing Information
**Source:** 37signals "Billing information" (adapted)
**Decisions:**
- "Doesn't hit our servers" line kept — important trust signal
- Aggregate billing for marketing removed — don't do this

#### 2c. Your Content
**Source:** 37signals "Product interactions" (adapted)
+ Original liability disclaimer (adapted from Tinybeans + BackThen)
**Decisions:**
- "Your Content" header chosen over "Photos and Media" — broader, covers written posts
- Invited user liability disclaimer added — covers misuse of shared links
- 60-day deletion timeline from 37signals

#### 2d. Technical Data
**Source:** 37signals "Geolocation data" (adapted, shortened)
**Decisions:**
- "Spammy signups" language kept for plain language feel
- IP not retained long-term — confirmed from Ryan's code analysis (Rack::Attack)

#### 2e. Analytics
**Status:** Placeholder — expand once confirmed with dev
**Source:** Original
**Decisions:**
- In-house only, aggregate, never shared with third parties
- Deliberately vague until analytics implementation confirmed

#### 2f. Communications
**Source:** 37signals "Voluntary correspondence" (first paragraph only)
**Decisions:**
- Surveys/customer interview paragraph removed — features not built yet

---

### Section 3 — What We Do Not Collect
**Status:** Drafted — original
**Source:** Original — core differentiator section
**Content:**
- No third-party behavioral analytics or tracking tools
- No advertising data
- No commercial user profiles
- No tracking cookies beyond authentication
- No AI, machine learning, or automated image analysis on photos

---

### Section 4 — Third-Party Services
**Status:** Drafted
**Source:** FamilyAlbum contract restriction language (adapted)
**Decisions:**
- Two-tier structure: Required vs. Optional
- Optional section deliberately empty — add when features built
- Google Fonts note included temporarily — remove when self-hosted
- "Contractually restricted" language borrowed from FamilyAlbum — confirmed
  DPAs likely accepted automatically during AWS/Brevo signup (verify before launch)

**Required Services Table:**
| Service | Provider | Data Shared | Purpose |
|---|---|---|---|
| File & Photo Storage | AWS — [AWS REGION TBD] | Uploaded photos and media | Secure file storage |
| Email Delivery | Brevo (formerly Sendinblue) | Email address, name | Transactional emails only |
| Payment Processing | [PAYMENT PROVIDER TBD] | Billing information | Subscription processing |

**Optional Services:** *(empty until features built)*

**Google Fonts Note:** *(remove when self-hosted)*
> Our site currently loads fonts from Google's CDN, which results in your
> IP address being sent to Google as a standard browser request. We are in
> the process of self-hosting these fonts to eliminate this.

---

### Section 5 — Cookies
**Status:** Drafted
**Source:** Tinybeans definition + FamilyAlbum Section 9 structure + original cookie table
**Decisions:**
- Definition describes only what cookies do ON THIS SITE not generally
- No third-party cookie language — none used
- Actual cookies from Ryan's code analysis

**Cookie Table:**
| Cookie | Purpose | Expires |
|---|---|---|
| `_cm_remember` | Keeps account holders logged in | 1 year |
| `_cm_subscriber` | Keeps invited viewers logged in | 1 year |

---

### Section 6 — Account Holders
**Status:** Drafted
**Source:** Tinybeans Section 8 (18+ language) + FamilyAlbum Section 12 (COPPA)
+ BackThen (age of majority concept, adapted to plain US English)
**Decisions:**
- 18+ for account holders — consistent with Tinybeans
- Parental permission carve-out included — allows teens to view family photos
- "Age of majority" language avoided — too British
- "Children" used sparingly — once in this section only
- "Minors" only in boilerplate sections
- COPPA "verifiable parental consent" term kept exactly — signals legal awareness
- Under-13 line included — necessary since parental carve-out opens door to under-18s

---

### Section 7 — Your Commitments
**Status:** Drafted
**Source:** BackThen Section 10 (adapted)
**Decisions:**
- Clickwrap framing — "by creating an account and agreeing" not "by using the service"
- Covers both age confirmation and content rights
- Deliberately short — BackThen's version was longer but this covers what matters

**Content:**
> By creating an account and agreeing to this Privacy Policy, you confirm
> that you are 18 years of age or older, or that you have the express
> permission of a parent or legal guardian. You also confirm that you have
> the right to upload and share any content you post, including any photos
> or videos in which other individuals appear.

---

### Section 8 — Data Security
**Status:** Drafted
**Source:** 37signals "How we secure your data" + dev codebase specifics
**Decisions:**
- bcrypt password hashing called out explicitly — from code analysis
- Log filtering called out — sensitive params auto-filtered
- Rate limiting mentioned — Rack::Attack confirmed in codebase
- "Not 100% secure" disclaimer kept — standard and important

---

### Section 9 — Content Visibility
**Status:** Drafted — original
**Decisions:**
- "No content is publicly accessible" avoided — overclaim if shared links misused
- "We are not responsible for how you or invited users share access" added
- Covers both account holder and invited viewer misuse of links

---

### Section 10 — Data Retention and Deletion
**Status:** Drafted
**Source:** 37signals "What happens when you delete content" + "Data retention"
**Decisions:**
- 30-day photo deletion timeline — from 37signals
- 60-day account deletion timeline — from 37signals
- Authentication tokens and technical logs added — from code analysis
- Self-service deletion noted as coming soon — feature not yet built

---

### Section 11 — Your Rights
**Status:** Drafted
**Source:** 37signals rights section (verbatim where possible) + original additions
**Decisions:**
- "Personal data" not "personal information" throughout
- All GDPR (Articles 15-22) and CCPA rights included even if not applicable
- "We never have and never will sell your personal data" parenthetical kept
- Right to Opt-Out of Sale or Sharing given own bullet — legally separate from Restrict Processing
- "For advertising purposes" added to Opt-Out bullet — legally precise for CCPA
- Right to Withdraw Consent added — GDPR Article 7
- Right to Limit Sensitive Personal Information added — CPRA 2023
- Automated Decision-Making kept as-is — no parenthetical added, future-proofed
- Export tool "coming soon" — self-service feature not yet built

---

### Section 12 — Location of Data
**Status:** Drafted
**Source:** 37signals "Location of site and data" (verbatim, adapted)
**Decisions:**
- AWS region placeholder added
- Pointer to GDPR boilerplate section added for EU/UK users

---

### Section 13 — Sharing and Disclosure
**Status:** Drafted
**Source:** 37signals "When we access or disclose your information" (adapted)
**Decisions:**
- Ad exclusion list sharing removed — no ads
- Third-party integration paragraph removed — no integrations yet
- Tax audit billing disclosure included — relevant once payments active
- Acquisition/merger line kept — important user protection
- "No team member looks at your content" line kept — important trust signal

---

### Section 14 — Government Requests
**Status:** TO BE DRAFTED
**Source:** → COPY: 37signals "When required under applicable law"
**Notes:** Best written version of this language by far. Keep verbatim.
Replace 37signals company name with Collectable Moments.

---

### Section 15 — State and International Laws
**Status:** TO BE ASSEMBLED — paste-ins from reference policies

#### 15a — California (CCPA)
→ COPY: 37signals California Notice at Collection (Document 6)
Update table categories to match our data collection.
Include Shine the Light disclosure.
Note: Much cleaner than Tinybeans version since we don't sell data.

#### 15b — Colorado (CPA)
→ COPY: FamilyAlbum Full Policy, Section 14

#### 15c — Virginia (VCDPA)
→ COPY: FamilyAlbum Full Policy, Section 18

#### 15d — Oregon (OCPA)
→ COPY: FamilyAlbum Full Policy, Section 15

#### 15e — Texas (TDPSA)
→ COPY: FamilyAlbum Full Policy, Section 16
REMOVE: "NOTICE: We may sell your Sensitive Personal Information" — does not apply.

#### 15f — Utah (UCPA)
→ COPY: FamilyAlbum Full Policy, Section 17

#### 15g — Canada (PIPEDA)
→ COPY: FamilyAlbum Full Policy, Section 19

#### 15h — EU/UK (GDPR)
→ COPY: Tinybeans Section 14 for legal bases language
→ COPY: FamilyAlbum Section 20 for SCCs and rep contact structure
Combine both — Tinybeans has better substance, FamilyAlbum has better structure.

#### 15i — Australia (Privacy Act 1988)
→ COPY: FamilyAlbum Full Policy, Section 21

---

### Section 16 — Changes to This Policy
**Status:** TO BE DRAFTED
**Source:** → COPY: 37signals "Changes and questions"
Remove mailing list reference.
Material changes → notify by email.
Minor updates → reflected by date at top of page.

---

### Section 17 — Contact
**Status:** TO BE DRAFTED — original
> **Collectable Moments**
> [CONTACT EMAIL]
> [MAILING ADDRESS — optional]

---
---

## DELIBERATELY EXCLUDED — WATCHLIST

These items were reviewed and deliberately left out. Each entry explains
why, what triggers adding it, and where to find the best reference language.

---

### Facial Recognition / Automated Image Analysis
**Why excluded:** Feature not built. Making promises about future features
is risky. Language removed entirely.
**Trigger:** If facial recognition or automated photo grouping is ever built
**Best reference when needed:** FamilyAlbum Section 4 (they do use it — adapt
to show opt-in only version)
**Sections to update:** Section 2, Section 3, Section 4 (add to optional
services table)
**Legal note:** Self-hosted vs. third-party matters enormously here.
Third-party facial recognition sends photos to external servers —
contradicts privacy promise. Revisit with legal counsel before building.

---

### Printing / Optional Services
**Why excluded:** Feature not built. User-initiated, opt-in only.
**Trigger:** Any optional third-party service added (printing, gifts, etc.)
**Best reference when needed:** FamilyAlbum Section 6 (fulfillment language)
**Sections to update:**
- Section 4 — add Optional Services table
- Intro paragraph — update to reflect optional services language
- Section 13 — add sharing scenario for fulfillment providers

---

### Customer Support Tool
**Why excluded:** Feature not built.
**Trigger:** If a third-party support tool (Zendesk, Intercom etc.) is added
**Best reference when needed:** FamilyAlbum Section 6 (lists Zendesk)
**Sections to update:** Section 4 optional services table, Section 13

---

### Analytics Expansion
**Why excluded:** Current analytics are in-house and aggregate only.
Section 2e is deliberately vague pending dev confirmation.
**Trigger:** If any third-party analytics tool is added, OR when dev confirms
exact implementation of in-house analytics
**Best reference when needed:** 37signals "Website interactions" section
**Sections to update:** Section 2e, Section 3 (remove "no third-party analytics" if changed)
**Warning:** Adding third-party analytics directly contradicts Section 3 and
the intro paragraph. Major policy revision required if this changes.

---

### Social Login (Google, Apple, Facebook)
**Why excluded:** Feature not built.
**Trigger:** If social login is added
**Best reference when needed:** Cluster policy (they mention Facebook Connect)
**Sections to update:** Section 2a, Section 4, Section 13

---

### Surveys / Customer Interviews
**Why excluded:** Features not built. Second paragraph of 37signals
"Voluntary Correspondence" section removed.
**Trigger:** If user surveys or customer interviews are introduced
**Best reference when needed:** 37signals "Voluntary correspondence"
second paragraph (verbatim)
**Sections to update:** Section 2f

---

### CAPTCHA / Anti-Bot
**Why excluded:** Not currently implemented in codebase.
**Trigger:** If CAPTCHA is added to any forms
**Best reference when needed:** 37signals "Anti-bot assessments" section
**Sections to update:** Section 4 (add to required services table),
new subsection in Section 2

---

### Mobile App
**Why excluded:** No app exists yet.
**Trigger:** If iOS or Android app is built
**Best reference when needed:** 37signals "How we approach mobile app
permissions" + FamilyAlbum cookie opt-out links (iOS/Android)
**Sections to update:** Definitions ("Service" definition), Section 5
(add mobile opt-out links), Section 4, multiple sections

---

### Push Notifications
**Why excluded:** No app, no notifications system currently.
**Trigger:** If push notifications are implemented
**Best reference when needed:** FamilyAlbum Section 9, BackThen Section 2
**Sections to update:** Section 2, Section 4

---

### Location / EXIF Data
**Why excluded:** Not currently collected or processed.
**Trigger:** If photo EXIF data is ever read or used
**Best reference when needed:** FamilyAlbum Section 4 (they collect EXIF)
**Sections to update:** Section 2, Section 3 (remove if applicable)
**Warning:** EXIF data can contain precise GPS coordinates — sensitive
under CCPA and GDPR. Requires careful handling and likely legal review.

---

### Biometric Data
**Why excluded:** No facial recognition, no biometric collection.
**Trigger:** If any biometric processing is introduced
**Best reference when needed:** FamilyAlbum Section 13 CCPA disclosures
(biometric category)
**Legal note:** Biometric data is "sensitive personal information" under
CCPA and several state laws. Requires explicit disclosure and likely
consent mechanisms. Get legal review before implementing.
**Sections to update:** Definitions, Section 2, Section 3, Section 11
(Right to Limit Sensitive PI becomes more relevant), all state sections

---

### Data Breach Notification
**Why excluded:** Not legally required to include in policy for US-only
operations at current scale. GDPR requires it but covered in GDPR boilerplate.
**Trigger:** When LLC is formed, when EU users are anticipated, or if
a breach actually occurs
**Best reference when needed:** GDPR Article 33/34, 37signals security page
**Sections to update:** Section 8, potentially new section

---

### Financial Incentives / Loyalty Programs
**Why excluded:** No such programs exist.
**Trigger:** If any discount or loyalty program is introduced that
collects personal data
**Best reference when needed:** Tinybeans Section 13 CCPA financial
incentives disclosure
**Sections to update:** State/international section for California

---
---

## CHANGE LOG

*Use this section to document every policy update. Include date, what
changed on the site or in the law, what policy gap it created, and
what language was added or modified.*

### FORMAT:
```
### [DATE] — [WHAT CHANGED]
**Trigger:** What site change or legal change prompted this
**Gap created:** What was now uncovered in the policy
**Sections updated:** Which sections were modified
**Language added/removed:** Brief description of changes
**Reviewed by:** Who approved the change
```

---

### April 2026 — Initial Policy Draft
**Trigger:** New site being built
**Gap created:** N/A — first draft
**Sections drafted:** All sections 1-13 plus Promise, Preamble, Definitions
**Sources used:** 37signals (primary), FamilyAlbum, Tinybeans, BackThen,
23 Snaps, Cluster
**Key decisions:**
- Single document with Promise section at top (not two separate docs)
- 18+ account holders with parental permission carve-out
- "Personal data" standardized throughout (not "personal information")
- All GDPR and CCPA rights included regardless of current applicability
- Facial recognition excluded entirely — revisit when/if feature built
- Optional services (printing etc.) excluded — add when built
- Analytics section left vague pending dev confirmation
**Reviewed by:** [NAME TBD — recommend legal review before launch]

---
---

## DEVELOPER NOTES

*Items requiring dev implementation before policy goes live*

- [ ] Self-host Google Fonts — remove disclosure note from Section 4 when done
- [ ] Implement clickwrap at signup — checkbox required, consent recorded
- [ ] Build self-service account deletion — update Section 10 when live
- [ ] Build self-service data export — update Section 11 when live
- [ ] Confirm AWS region — fill in [AWS REGION TBD] throughout
- [ ] Confirm analytics implementation — expand Section 2e when confirmed
- [ ] Sign/confirm DPAs with AWS and Brevo — verify during account setup
- [ ] Add upload-screen consent notice — "by uploading you confirm you
      have the right to share this content" (ties to Section 7)

---

## PRE-LAUNCH CHECKLIST

- [ ] AWS region confirmed and filled in throughout
- [ ] Payment provider decided and filled in
- [ ] Contact/privacy email set up and filled in throughout
- [ ] Google Fonts self-hosted
- [ ] Intro paragraph final phrasing signed off
- [ ] Clickwrap implemented at signup
- [ ] Self-service account deletion built
- [ ] Self-service data export built
- [ ] Mailing address decided
- [ ] All state/international boilerplate pasted in (Section 15a-15i)
- [ ] All [PLACEHOLDER] values filled in
- [ ] Section numbers finalized and California pointer updated in preamble
- [ ] DPAs confirmed with AWS and Brevo
- [ ] COPPA legal review — storing photos of children as subjects (not
      users). 18+ requirement and no-AI stance are strong but get a
      one-hour legal consult before launch to confirm position.
- [ ] General legal review recommended — especially GDPR section
- [ ] Consider iubenda or similar privacy policy maintenance service
      when LLC is formed
- [ ] CLAUDE.md drafted for privacy policy repo (for future gap analysis)
