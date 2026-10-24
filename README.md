# First4AI Email Triage

The open-source core of First4AI's email triage: it reads incoming email, decides what each message is, and prepares a draft reply for a person to review.

> **Status: Phase 0, under construction.** The repository is being set up. There is no working code yet. This README describes what the engine is being built to do, and will be updated as each part lands.

## What it is

Email triage is a **routing workflow**. A language model classifies each email into a category, and ordinary code then sends it down the branch configured for that category (for example: quote request, existing order, support, admin, spam). Anything the model is unsure about goes to a "needs review" branch instead of being forced into a category.

## Draft only, by design

- The engine **cannot send email**. The mailbox interface has no send method.
- It can label or categorise messages and create drafts in the same thread.
- A person reviews, edits and sends each draft from their own mailbox.

This keeps a person in control and limits the damage a bad or manipulated draft can do.

## Planned contents

- **Classify-and-route core:** the triage logic, with categories and routing rules set by configuration rather than code.
- **`EmailProvider` interface:** one interface for mailboxes, with fake mailboxes for testing. Real Gmail and Microsoft 365 (Outlook) connectors will implement it.
- **Evaluation harness:** repeatable tests that measure classification accuracy against labelled examples.
- **Synthetic dataset:** generated example emails for the evaluation harness.

## Data policy

This repository uses **synthetic data only**. No real emails, client names or client configuration are ever committed here.

## Relationship to the First4AI platform

First4AI's private platform installs this package, so the code published here is the same code that runs in production, not a demo copy. Client-specific configuration and deployment files stay in the private platform repository.

## Licence

MIT. See the `LICENSE` file.