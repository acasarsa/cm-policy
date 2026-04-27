# Collectable Moments — Privacy Policy Assembly Guide

_Last updated: April 7, 2026_

This guide serves three purposes:

1. Track what's in the policy, where it came from, and why
2. Track what was deliberately excluded and what triggers adding it
3. Provide a change log for future policy updates

---

## ⚠️ HIGH PRIORITY — BEFORE V1 LAUNCH

These items are required for the policy to be accurate and complete.
Do not launch without addressing these.

- [x] **TERMINOLOGY CONSISTENCY CHECK** — Run policy through Claude Code
      to find and replace inconsistent usage of the following terms:
  - "user" / "account holder" — replace with Publisher or Subscriber as appropriate
  - "viewer" / "invited user" / "anonymous viewer" — these terms no longer
    apply, replace with Subscriber or Website Visitor as appropriate
  - "personal data" / "personal information" — should use "personal data"
    except where a specific law requires its own term (COPPA, CCPA, CPRA)
  - "service" / "site" / "app" — should use "service" throughout

- [x] **Update Section 6 — Children's Privacy** to reflect Publisher/Subscriber
      distinction — 18+ applies to Publishers, Subscribers under 18 may access
      with parental permission

- [ ] **Update Section 7 — Your Commitments** — clickwrap applies to both
      Publishers and Subscribers at account creation. Needs to be built.

- [x] **Update Section 9 — Content Visibility** — replace "invited users"
      and "viewers" with "Subscribers" throughout

---

## DEVELOPER NOTES

_Items requiring dev implementation before policy goes live_

- [ ] Self-host Google Fonts — remove disclosure note from Section 4 when done
- [ ] Implement clickwrap at signup — checkbox required, consent recorded
  - Add `terms_accepted_at` (timestamp) and `terms_version` (date string matching
    policy "Last updated" date, e.g. "2026-04-27") to both `subscribers` and
    `users` tables. Set both fields when the checkbox is submitted.
  - Subscriber clickwrap: at the email entry step when accepting a Publisher's
    invitation. Publisher clickwrap: at account creation.
  - On next login after a material policy change, compare user's `terms_version`
    against current policy date — intercept with re-consent screen if they differ.
    See "Minor vs. Material Policy Changes" section below for guidance on when
    re-consent is required.
- [ ] Build self-service account deletion — update Section 10 when live
- [ ] Build self-service data export — update Section 11 when live
- [ ] Auto-delete rejected Subscribers — decide on retention window (suggested:
      30 days after `rejected_at`) and build a cleanup job. Update Section 10
      to disclose the retention period when built. Currently rejected Subscriber
      records (name, email) are retained indefinitely with no active purpose.
- [x] Confirm AWS region — fill in [AWS REGION TBD] throughout
- [ ] Confirm analytics implementation — expand Section 2e when confirmed
- [x] Sign/confirm DPAs with AWS and Brevo — verify during account setup
- [ ] Add upload-screen consent notice — "by uploading you confirm you
      have the right to share this content" (ties to Section 7)

---

## PRE-LAUNCH CHECKLIST

- [x] AWS region confirmed and filled in throughout
- [ ] Payment provider decided and filled in
- [ ] Contact/privacy email set up and filled in throughout
- [ ] Google Fonts self-hosted
- [ ] Intro paragraph final phrasing signed off
- [ ] Clickwrap implemented at signup
- [ ] Self-service account deletion built
- [ ] Self-service data export built
- [ ] Mailing address decided
- [x] All state/international boilerplate pasted in (Section 15a-15i)
- [ ] All [PLACEHOLDER] values filled in
- [x] Section numbers finalized and state/country pointer updated in preamble
- [x] DPAs/SCCs confirmed with AWS and Brevo — once confirmed, update Section 15h SCC language from softened Option B to affirming language

  **How to complete this item:**

  _AWS_ — SCCs are included in the AWS Data Processing Addendum (DPA).
  To formally accept it:
  1. Log into AWS console → go to **AWS Artifact**
  2. Under "Agreements," find and accept the AWS GDPR DPA
  3. Download a copy and keep it on file
     This takes ~10 minutes and is free.

  _Brevo_ — Brevo has a self-service DPA signing process:
  1. Log into Brevo → **Account Settings → Legal**
  2. Sign or download their DPA (includes SCCs)
     If not visible in settings, request it from Brevo support.

  _Payment Provider (TBD)_ — Confirm DPA availability before signing
  up with any provider. Stripe, for example, has a self-service DPA
  in their dashboard. Make DPA availability a selection criterion.

  Once all three are done: update the change log and upgrade Section
  15h from softened SCC language (Option B) to affirming language
  (Option A). Store signed DPA copies alongside this repo.

- [ ] Assess EU/UK user base at launch — if material or actively targeted, appoint an EU/UK representative and update Section 15h (see Section 15 change log entry above)
- [ ] COPPA legal review — storing photos of children as subjects (not
      users). 18+ requirement and no-AI stance are strong but get a
      one-hour legal consult before launch to confirm position.
- [ ] Legal review by independent counsel before launch — even a one-hour
      consult creates a paper trail showing independent review was sought.
      Not blocking for soft launch but recommended before scaling.
- [ ] Consider iubenda or similar privacy policy maintenance service
      when LLC is formed
- [x] CLAUDE.md drafted for privacy policy repo (for future gap analysis)

## POLICY STRUCTURE — CURRENT STATE

### Preamble / Promise _(top of page)_

**Status:** Drafted — original
**Source:** Original — inspired by Tinybeans' Promise format
**Content:**

> The Collectable Moments Promise
>
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
- "Personal data" is the standard term throughout — exceptions apply where
  specific laws use their own defined terms (see Terminology Rule below)

**Terminology Rule:** "Personal data" is used as the standard term throughout
this policy. Exceptions apply where a specific law uses its own defined term,
in which case the exact legal term is preserved verbatim:

- "Sensitive personal information" — CPRA defined term
- "Verifiable parental consent" — COPPA defined term
- "Personal information" — used in CCPA boilerplate sections only

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

#### 2a. Data Collection by User Type

**Source:** Original — tiered structure based on three user types
**Three user tiers:**

- **Website Visitor** — no account, browses public pages only, basic
  technical data (IP, browser type) for security/operational purposes only
- **Subscriber** — registered account holder who accesses and follows
  Publisher content. Collects: name, email, password (bcrypt hashed),
  optional avatar, notification preferences, last access timestamp.
  Clickwrap at account creation.
- **Publisher** — paid subscription, creates and shares content.
  All Subscriber data plus uploaded content and billing information.
  Clickwrap at account creation.
  **Decisions:**
- No anonymous viewer tier — all content viewers sign up with email
- Website Visitors don't need a formal definition — brief mention in Section 2 only
- Comments only for logged-in users (Subscribers and Publishers)
- Profile picture optional for Subscribers and Publishers
- "Personal data" used throughout not "personal information"
- Newsletter/survey language removed — features not built
- Geographic aggregation for ad spend NOT YET included — see Watchlist
- Original source: 37signals "Identity and access" adapted for tiered structure
  - Tinybeans 1(a) "we do not collect unless voluntarily provided"

#### 2b. Billing Information

**Source:** 37signals "Billing information" (adapted)
**Decisions:**

- "Doesn't hit our servers" line kept — important trust signal
- Aggregate billing for marketing removed — don't do this

#### 2c. Your Content

**Source:** 37signals "Product interactions" (adapted)

- Original liability disclaimer (adapted from Tinybeans + BackThen)
  **Decisions:**

* "Your Content" header chosen over "Photos and Media" — broader, covers written posts
* Invited user liability disclaimer added — covers misuse of shared links
* 60-day deletion timeline from 37signals

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
| File & Photo Storage | AWS — us-east-1 | Uploaded photos and media | Secure file storage |
| Email Delivery | Brevo (formerly Sendinblue) | Email address, name | Transactional emails only |
| Payment Processing | [PAYMENT PROVIDER TBD] | Billing information | Subscription processing |

**Optional Services:** _(empty until features built)_

**Google Fonts Note:** _(remove when self-hosted)_

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

### Section 6 — Children's Privacy

**Status:** Drafted
**Source:** Tinybeans Section 8 (18+ language) + FamilyAlbum Section 12 (COPPA)

- BackThen (age of majority concept, adapted to plain US English)
  **Decisions:**

* 18+ for account holders — consistent with Tinybeans
* Parental permission carve-out included — allows teens to view family photos
* "Age of majority" language avoided — too British
* "Children" used sparingly — once in this section only
* "Minors" only in boilerplate sections
* COPPA "verifiable parental consent" term kept exactly — signals legal awareness
* Under-13 line included — necessary since parental carve-out opens door to under-18s

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

**Status:** Drafted
**Source:** 37signals "When required under applicable law" (verbatim, adapted)
**Decisions:**

- Kept verbatim — best written version of this language
- Replaced 37signals company name with Collectable Moments

---

### Section 15 — State and International Laws

**Status:** Complete — assembled April 2026

**SECTION NUMBER MAPPING — FamilyAlbum to Collectable Moments:**
When copying FamilyAlbum boilerplate, replace all cross-references to
FamilyAlbum section numbers with our equivalent sections:

| FamilyAlbum Reference | Their Section | Our Equivalent                      |
| --------------------- | ------------- | ----------------------------------- |
| Purpose of Processing | Section 5     | Section 2 — What We Collect and Why |
| Your Rights           | Section 10    | Section 11 — Your Rights            |
| CCPA / California     | Section 13.a  | Section 15a — California            |
| Colorado              | Section 14    | Section 15b — Colorado              |
| Oregon                | Section 15    | Section 15d — Oregon                |
| Texas                 | Section 16    | Section 15e — Texas                 |
| Utah                  | Section 17    | Section 15f — Utah                  |
| Virginia              | Section 18    | Section 15c — Virginia              |
| Canada                | Section 19    | Section 15g — Canada                |
| EU/UK                 | Section 20    | Section 15h — EU/UK                 |
| Australia             | Section 21    | Section 15i — Australia             |

Also replace throughout:

- "FamilyAlbum" → "Collectable Moments"
- "the App" → "the service"
- "support@family-album.com" → "[CONTACT EMAIL]"

**CLAUDE CODE PROMPT FOR SECTION 15 ASSEMBLY:**

```
Read the assembly guide in claude-guides/

Then assemble Section 15 — State and International Laws in
drafts/cm-privacyPolicy-legal.md by:

1. Colorado (15b) → copy Section 14 from references/family-album/pp-legal.md
2. Virginia (15c) → copy Section 18 from references/family-album/pp-legal.md
3. Oregon (15d) → copy Section 15 from references/family-album/pp-legal.md
4. Texas (15e) → copy Section 16 from references/family-album/pp-legal.md,
   remove the "NOTICE: We may sell your Sensitive Personal Information" line
   and the paragraph beginning "The TDPSA defines the sale..." and replace
   with "We do not sell your Personal Information."
5. Utah (15f) → copy Section 17 from references/family-album/pp-legal.md
6. Canada (15g) → copy Section 19 from references/family-album/pp-legal.md
7. EU/UK (15h) → copy Section 20 from references/family-album/pp-legal.md
8. Australia (15i) → copy Section 21 from references/family-album/pp-legal.md

Leave Section 15a (California) as is — already completed.

Throughout all sections make these replacements:
- "FamilyAlbum" → "Collectable Moments"
- "the App" → "the service"
- "support@family-album.com" → "[CONTACT EMAIL]"

For all cross-references to FamilyAlbum section numbers, replace
with our equivalent sections using this mapping:
- FamilyAlbum Section 5 → our Section 2
- FamilyAlbum Section 10 → our Section 11
- FamilyAlbum Section 13.a → our Section 15a
- FamilyAlbum Section 14 → our Section 15b
- FamilyAlbum Section 15 → our Section 15d
- FamilyAlbum Section 16 → our Section 15e
- FamilyAlbum Section 17 → our Section 15f
- FamilyAlbum Section 18 → our Section 15c
- FamilyAlbum Section 19 → our Section 15g
- FamilyAlbum Section 20 → our Section 15h
- FamilyAlbum Section 21 → our Section 15i

Insert each completed subsection into the correct location in
drafts/cm-privacyPolicy-legal.md after Section 14.

For all state sections (15b-15f) that contain opt-out of sale/targeted
advertising/profiling language, add the following after that language:

We do not sell or share your personal information for targeted advertising
purposes and have not done so in the preceding 12 months. We do not process
personal information for profiling in furtherance of solely automated
decisions. As such, no opt-out mechanism is required or provided.
```

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
REMOVE: "NOTICE: We may sell your Sensitive Personal Information"
REMOVE: The entire paragraph beginning "The TDPSA defines the sale of Personal Information..."
REPLACE WITH: "We do not sell your Personal Information." (borrowing from Utah/Virginia language)
Note: Texas law requires explicit disclosure on selling — your statement that you don't sell is both legally compliant and stronger than FamilyAlbum's version.

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

```

**APPLICABILITY THRESHOLDS — STATE LAWS:**
Most state privacy laws only apply once you reach certain data processing
thresholds. We include these sections proactively since:
- You don't know when you'll cross the threshold
- Removing them later requires a policy update and user notification
- Including them proactively signals good faith
- Legal risk of having them unnecessarily = essentially zero
- Legal risk of not having them when required = real

| State | Threshold to become legally required |
|---|---|
| California (CCPA) | $25M revenue OR 100K+ consumers OR 50%+ revenue from data sales |
| Colorado (CPA) | 100K+ consumers OR 25K+ consumers with 50%+ revenue from data sales |
| Virginia (VCDPA) | 100K+ consumers OR 25K+ consumers with 50%+ revenue from data sales |
| Oregon (OCPA) | 100K+ consumers OR 25K+ consumers with 50%+ revenue from data sales |
| Texas (TDPSA) | 100K+ consumers (no revenue threshold) |
| Utah (UCPA) | $25M revenue AND 100K+ consumers OR 25K+ consumers with 50%+ from data sales |

Note: Since you never sell data, the "50%+ revenue from data sales" threshold
will never apply to you. The 100K consumer threshold is the one to watch.
At launch you almost certainly don't meet any of these thresholds.
Check with your team whether to include all sections or add them as you grow.



#### 15a — California (CCPA)
**Status:** Complete
Source: 37signals California Notice at Collection. Includes Shine the Light disclosure.

#### 15b — Colorado (CPA)
**Status:** Complete
Source: FamilyAlbum Section 14, adapted. Opt-out paragraph replaced with
no-sale/no-advertising/no-profiling disclosure.

#### 15c — Virginia (VCDPA)
**Status:** Complete
Source: FamilyAlbum Section 18, adapted. "We do not 'sell'" replaced with
"We do not sell your personal information to third parties."

#### 15d — Oregon (OCPA)
**Status:** Complete
Source: FamilyAlbum Section 15, adapted.

#### 15e — Texas (TDPSA)
**Status:** Complete
Source: FamilyAlbum Section 16, adapted. NOTICE about selling Sensitive PI
removed and replaced with "We do not sell your personal information to third
parties." — legally compliant and stronger than FamilyAlbum's version.

#### 15f — Utah (UCPA)
**Status:** Complete
Source: FamilyAlbum Section 17, adapted.

#### 15g — Canada (PIPEDA)
**Status:** Complete
Source: FamilyAlbum Section 19, adapted. Children subsection replaced with
cross-reference to Section 6 — our 18+ standard exceeds PIPEDA's age-14 threshold.

#### 15h — EU/UK (GDPR)
**Status:** Complete — two open items flagged for post-launch review (see compliance notes in change log)
Source: FamilyAlbum Section 20, adapted. Marketing/advertising legal bases
removed — not applicable to CM. Representative section replaced with
disclosure that we do not currently maintain an EU/UK rep.

#### 15i — Australia (Privacy Act 1988)
**Status:** Complete
Source: FamilyAlbum Section 21, adapted. Country list updated to United States only.

---

### Section 16 — Changes to This Policy
**Status:** Drafted
**Source:** 37signals "Changes and questions" (adapted)
**Decisions:**
- Mailing list reference removed — no mailing list
- Material changes → notify by email
- Minor updates → reflected by date at top of page only
- Closing question line doubles as lead-in to Contact section

**Content:**
> We may update this policy as needed to comply with relevant regulations
> and reflect any new practices. If we make material changes, we will
> notify registered users by email and update the date at the top of this
> page. Minor updates will be reflected by the updated date at the top of
> this page without direct notification.
>
> Have any questions, comments, or concerns about this privacy policy,
> your data, or your rights? Please get in touch at [CONTACT EMAIL].

---

### Section 17 — Contact
**Status:** Drafted — placeholder
**Source:** Original
**Decisions:**
- Minimal for now — contact email and optional mailing address
- Update when LLC is formed and legal entity name is confirmed
- Mailing address optional but recommended once LLC address established

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

### Geographic Aggregation for Ad Spend
**Why excluded:** Feature not built yet. Co-founder flagged this as a future
internal analytics feature — tracking state/region of userbase to inform
ad spend decisions.
**Trigger:** When geographic aggregation is implemented
**Key questions to answer before building:**
- How is location derived? (IP at signup, billing address, user profile?)
  Each has different privacy implications
- Is it truly aggregate only? (No per-user location stored)
- Is it derived server-side only? (No third-party geolocation service)
**Best reference when needed:** 37signals "General Geolocation data" section
**Sections to update:** Section 2e Analytics, Section 3 (if any third-party
geolocation service is used, remove "no third-party tracking" claim)
**Legal note:** IP-derived location is considered personal data under GDPR.
Aggregate-only, server-side derivation is the privacy-respecting approach.

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

## MINOR VS. MATERIAL POLICY CHANGES

Use this guidance to decide whether a policy update requires a new clickwrap
(re-consent) or email notification only.

### Minor changes — email notification only
Section 16 of the policy already commits to notifying users by email for
material changes. Minor changes only require updating the "Last updated" date.

- New state or international law sections added
- Typo or clarity fixes
- Contact info or mailing address updates
- Disclosures added for data practices already in place (e.g. adding 2f email
  disclosure for emails already being sent)
- Formatting or structural changes
- Removing features and their associated disclosures

### Material changes — new clickwrap required on next login
Compare the user's stored `terms_version` against the current policy date.
If they differ and the change was material, intercept on next login with a
re-consent screen before allowing access.

- New categories of personal data being collected
- New third-party processors added to Section 4
- New purposes for using existing data
- Longer data retention periods
- Reduction of user rights
- Changes to legal basis for processing (GDPR)
- Any change that would surprise a reasonable user

### When in doubt
Flag for legal review rather than making the call unilaterally. If the change
touches data collection, retention, sharing, or user rights — treat it as
material.

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

### April 2026 — Section 15 Assembly (State & International Laws)
**Trigger:** Initial policy build — completing planned state/international section assembly
**Gap created:** N/A — completing planned work
**Sections updated:** 15b (Colorado), 15c (Virginia), 15d (Oregon), 15e (Texas), 15f (Utah), 15g (Canada), 15h (EU/UK), 15i (Australia)
**Language added/modified:**
- All Disclosures subsections expanded from bare cross-references to plain-English explanations
- All Disclosures subsections include: "We do not sell your personal information to third parties."
- Opt-out paragraph standardized: no sale, no targeted advertising sharing, no profiling — no opt-out mechanism required
- Grammar fix: "to not to receive" → "to not receive" throughout (source error in FamilyAlbum boilerplate)
- Texas: Removed NOTICE about selling Sensitive PI; replaced with no-sell statement
- Canada: Children subsection replaced with cross-reference to Section 6
- EU/UK: SCC language softened (Option B — intent rather than affirmation); representative section replaced with disclosure we do not currently maintain EU/UK rep. See compliance notes below.
- Australia: Country list updated to United States only
**EU/UK compliance notes (two open items):**
- _SCC language_: Using softened Option B until DPAs with AWS/Brevo are confirmed. Revert to affirming language once confirmed. See pre-launch checklist.
- _EU/UK representative_: Not appointed. Basis: processing is occasional and limited in scope. Reassess if EU/UK user base grows materially. See pre-launch checklist.
**Reviewed by:** [NAME TBD]

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
```
