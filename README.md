# Linga back office: payments prototype

Clickable prototype of the Linga back office with white-label payments (Linga branding only, no processor UI visible).
Built from the Figma file "Stripe payments integration", section **Back Office Onboarding** (node `87:16577`).

## Flows

| Flow | Status | Start at |
| --- | --- | --- |
| Back-office onboarding | Built: 8 screens + leave-form dialog | `index.html#payments` |
| Freestanding onboarding | Placeholder, waiting for Figma section | `index.html#freestanding` |
| Manage payments | Placeholder, waiting for Figma section | `index.html#manage` |

`index.html` (no hash) opens the start page with all three flows.

## What you can click

- Accept payments → Business type → Personal details → Business details → Payout details → Public details → Review and submit → Confirmation.
- Every field is prefilled with sample data for "Naples store". Clear or change a field and press **Continue** to see the inline error states.
- The close (×) button opens the "Leave this form?" dialog. Leaving resets the sample data.
- The step name above each title opens a step list; finished steps are clickable.
- Payout: search banks, pick a bank to run a simulated "Link your bank" step, or enter routing/account numbers manually.
- Review: each **Edit** returns you to the step, and **Continue** brings you back to the review.
- The **Prototype** button (bottom right) restarts the flow, clears the current step, jumps to any screen, and can make the next submission fail.

## Run locally

The page loads its icons from `assets/`, so serve the folder rather than opening the file directly:

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000/.

## Assets

`assets/icons` and `assets/banks` are SVGs exported straight from the Figma nodes.
