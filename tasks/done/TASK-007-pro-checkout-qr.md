---
id: TASK-007
title: Pro Subscription Mock Checkout QR and Unlimited Access Unlock
flow: FLOW-BUSINESS
step_in_flow: Step 1 of 1 (Monetization & Quota Gate)
assigned_to: frontend-dev
reviewer: tech-lead
status: DONE
created_at: 2026-10-25
updated_at: 2026-10-25
inputs:
  - docs/07_domain_startup_business/interface_business.md
  - docs/00_core/system_constants.md
  - docs/00_core/interface_learning_loop.md
outputs:
  - frontend/src/features/subscription/pages/CheckoutPage.tsx
  - frontend/src/features/subscription/pages/PricingPage.tsx
dependencies:
  - FLOW-GAMIFICATION
---

# Task: [TASK-007] Pro Subscription Mock Checkout QR and Unlimited Access Unlock

## 1. Flow Context
- **Target Flow**: FLOW-BUSINESS (Main Experience Phase 3 - Monetization)
- **Position in Flow**: Post-streak / login upgrade prompt.
- **Previous Flow**: FLOW-GAMIFICATION.

## 2. Acceptance Criteria (Product Owner)
- [x] Display pricing tiers: Free (3 AI chat turns/day, 1-Click Save) vs Pro (39.000đ/month, unlimited AI chat, personalized mascot feedback).
- [x] Render interactive mock VietQR payment screen with timer and "Simulate Instant Transfer" button for demo testing.
- [x] Instant transition to Pro status upon payment confirmation; lifts the 3 turns/day AI rate limit immediately.

## 3. Technical Constraints (Tech Lead)
- Seamless auth state sync between client store, localStorage, and API headers.
