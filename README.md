# Linga back office: payments prototype

Clickable prototype of the Linga back office with white-label payments (Linga branding only, no processor UI visible).
Built from the Figma file "Stripe payments integration", section **Back Office Onboarding** (node `87:16577`).

## Flows

| Flow | Status | Start at |
| --- | --- | --- |
| Back-office onboarding | Built: 8 screens + leave-form dialog | `index.html#payments` |
| Freestanding onboarding | Built: 11 screens + sign-out dialog | `index.html#fs-payments` |
| Manage · Transactions | Built: page + 11 popups | `index.html#manage` |

`index.html` (no hash) opens the start page with all three flows.

## What you can click

- Accept payments → Business type → Personal details → Business details → Payout details → Public details → Review and submit → Confirmation.
- Every field is prefilled with sample data for "Naples store". Clear or change a field and press **Continue** to see the inline error states.
- The close (×) button opens the "Leave this form?" dialog. Leaving resets the sample data.
- The step name above each title opens a step list; finished steps are clickable.
- Payout: search banks, pick a bank to run a simulated "Link your bank" step, or enter routing/account numbers manually.
- Review: each **Edit** returns you to the step, and **Continue** brings you back to the review.
- The **Prototype** button (bottom right) restarts the flow, clears the current step, jumps to any screen, and can make the next submission fail.

### Freestanding onboarding

Accept payments → Get started (Create account / Login tabs) → Creating account → the same six steps as the back office → Confirmation, on a standalone Linga page.

- Sample account: `john.parker@naplesstore.com` / `Naples#2026`. The password rules turn green as they're met.
- The eye button shows or hides the password.
- After signing in, each step shows "Signed in as …" with **Sign out**, which opens the "Sign out?" dialog.
- With **Fail the next submission** on, Create account says the email is taken and Login says the password doesn't match.

### Manage · Transactions

Payments › Transactions in the back office (opens after onboarding, or from the start page).

- **Balance:** Pay out (Instant / Standard, amount checks, 2% instant fee, confirmation) and See details (Your balance). Paying out updates the balance on the page.
- **Recent transactions:** All and Disputes tabs, a working Status filter (plus Payment method / Reason), pagination, and Export (date ranges, custom dates, column sets).
- **Payment details:** fee breakdown, payment method, timeline, and Begin refund → Send refund (amount checks). Refunds update the status and timeline.
- **Disputed payment:** dispute card with step-by-step guide, Accept dispute (confirm), and Counter dispute: 3 prefilled steps (reason, customer details, evidence upload) plus a review step.
- **Fail the next submission** (Prototype menu) makes the next payout, refund or evidence submission fail.
- Account in the menu is a placeholder for the next design.

### Manage · Payouts

Payments › Payouts: the Instant Payouts banner (Pay out instantly), the balance with Pay out / See details, and a payouts table filtered to Paid by default (remove the chip or pick In transit, Failed, Canceled, or a method). A new payout appears in the table as In transit. Clicking a payout opens Payout details (overview, summary of charges/refunds/fees, and its transactions; each one opens the payment with a link back to the payout).

### Manage · Reports

Payments › Reports with Balance summary and Payout reconciliation tabs. Date range (Sep, Oct, or Nov month to date) and Timezone change every table; the sample numbers add up (starting balance + activity − payouts = ending balance). Download prepares the CSV and says it will be emailed, since the prototype can't save files.

## Run locally

The page loads its icons from `assets/`, so serve the folder rather than opening the file directly:

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000/.

## Assets

`assets/icons` and `assets/banks` are SVGs exported straight from the Figma nodes.
