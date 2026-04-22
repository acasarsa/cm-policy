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

## ⚠️ HIGH PRIORITY — BEFORE V1 LAUNCH

These items are required for the policy to be accurate and complete.
Do not launch without addressing these.

- [ ] **TERMINOLOGY CONSISTENCY CHECK** — Run policy through Claude Code
      to find and replace inconsistent usage of the following terms:
  - "user" / "account holder" — replace with Publisher or Subscriber as appropriate
  - "viewer" / "invited user" / "anonymous viewer" — these terms no longer
    apply, replace with Subscriber or Website Visitor as appropriate
  - "personal data" / "personal information" — should use "personal data"
    except where a specific law requires its own term (COPPA, CCPA, CPRA)
  - "service" / "site" / "app" — should use "service" throughout

- [ ] **Update Section 6 — Children's Privacy** to reflect Publisher/Subscriber
      distinction — 18+ applies to Publishers, Subscribers under 18 may access
      with parental permission

- [ ] **Update Section 7 — Your Commitments** — clickwrap applies to both
      Publishers and Subscribers at account creation. Website Visitors (no account)
      get browsewrap: "By browsing this site you agree to this policy."

- [ ] **Update Section 9 — Content Visibility** — replace "invited users"
      and "viewers" with "Subscribers" throughout

---

### April 2026 — Section 15 Assembly (State & International Laws)
**Trigger:** Policy assembly — paste-ins from FamilyAlbum reference policy
**Sections updated:** 15b (Colorado), 15c (Virginia), 15d (Oregon), 15e (Texas), 15f (Utah), 15g (Canada), 15h (EU/UK — in progress), 15i (Australia — pending)
**Key decisions:**
- All Disclosures subsections expanded from bare cross-references to plain-English explanations of what each section covers
- All Disclosures subsections include: "We do not sell your personal information to third parties."
- Opt-out paragraph standardized across all US state sections: explicitly states we do not sell/share for targeted advertising, do not process for profiling, and therefore no opt-out mechanism is required or provided
- "to not to receive" corrected to "to not receive" throughout (source error in FamilyAlbum boilerplate)
- Texas (15e): Removed FamilyAlbum NOTICE about selling Sensitive Personal Information — replaced with no-sell statement
- Canada (15g): Children subsection replaced with cross-reference to Section 6 — our 18+ standard exceeds PIPEDA requirements
- EU/UK (15h): Two open compliance questions documented below

#### ⚠️ Section 15h — EU/UK Compliance Notes

**Issue 1: EU/UK Representative (GDPR Article 27)**

Two options were considered:

- **Option A — Appoint a representative:** GDPR Article 27 technically requires a designated EU/UK representative for non-EU/UK controllers offering services to EU/UK residents. Third-party rep services (DP-Dock, DataRep, etc.) cost ~€200–500/year and are the fully compliant path.
- **Option B — Soften and disclose (chosen for now):** If EU/UK processing is occasional and limited in scope, enforcement risk is low. Policy will state we do not currently maintain a representative, disclose the basis, and commit to appointing one if that changes.

**Decision:** Option B adopted for launch. Language used:
> "We do not currently maintain an EU/UK representative as our processing of EU/UK personal data is occasional and limited in scope. If this changes we will update this policy and appoint a representative accordingly. For all data inquiries please contact us at [CONTACT EMAIL]."

**Trigger to revisit:** If EU/UK user base grows materially or we begin actively targeting EU/UK users, appoint a representative and update this section.

**Issue 2: Standard Contractual Clauses (SCCs)**

Two options were considered:

- **Option A — Affirm SCCs (original FamilyAlbum language):** States we "have entered into" SCCs with data recipients. This is a factual legal claim — only use if SCCs with AWS and Brevo have been confirmed and executed.
- **Option B — Soften to intent (chosen for now):** Avoids a factual claim we cannot yet verify. States we "take steps to ensure adequate safeguards are in place, including relying on standard contractual clauses where applicable."

**Decision:** Option B adopted for launch. Revert to Option A once DPAs/SCCs with AWS and Brevo are confirmed.

**Trigger to revisit:** When DPAs with AWS and Brevo are confirmed (also a pre-launch checklist item).

---

## DEVELOPER NOTES

_Items requiring dev implementation before policy goes live_

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
- [ ] DPAs/SCCs confirmed with AWS and Brevo — once confirmed, update Section 15h SCC language from softened Option B to affirm SCCs are in place (see Section 15h compliance notes above)
- [ ] Assess EU/UK user base at launch — if material or actively targeted, appoint an EU/UK representative and update Section 15h (see Section 15h compliance notes above)
- [ ] COPPA legal review — storing photos of children as subjects (not
      users). 18+ requirement and no-AI stance are strong but get a
      one-hour legal consult before launch to confirm position.
- [ ] Legal review by independent counsel before launch — even a one-hour
      consult creates a paper trail showing independent review was sought.
      Not blocking for soft launch but recommended before scaling.
- [ ] Consider iubenda or similar privacy policy maintenance service
      when LLC is formed
- [ ] CLAUDE.md drafted for privacy policy repo (for future gap analysis)
