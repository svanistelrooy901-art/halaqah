# Halaqah

Interactive Malay-language prototype for a surau's Mengaji and Tajwid classes.

## Run
Serve `dist/` with any static HTTP server. No installation or build required. PWA assets use relative URLs for portability, including GitHub Pages.

## Prototype behavior
- Teacher: student search, last reading, tap-first assessments, optional Tajwid, local drafts, save and next, attendance, record history.
- Parent: two sample children, reports generated from teacher selections, simulated payment submission.
- Admin: overview, sample roster, idempotent monthly bill generation, simulated payment approval, editable assessment/topic choices and optional fields.
- Local browser storage only; no actual accounts, authentication, role permissions, shared database, email, bank QR, gateway, scheduler or official receipts. Role selector is a demonstration tool, not an authorization boundary. Use synthetic data only.
- PWA manifest and service worker included; installation depends on browser support. Offline cached prototype assets are best-effort; server synchronization is not implemented.
- Sample Quran surah list is intentionally partial. Pagination and ayah ranges need curriculum-approved reference data before real use.

## Next milestone
Connect owner-provided Git repository; agree surau curriculum/template and fee rules; implement tenant-aware authentication, role access, guardian links and durable records; payment-provider integration and verified notifications. Do not expose demo role switching for real student data.

## Design
Warm ivory, forest green and sage; responsive teacher-first workspace. All names and institutional content are examples.

## Pilot institution identity
Owner-supplied Halaqah Al-Quran As-Sa’adah logo is retained intact as `dist/institution-logo.jpg`. It identifies the pilot institution; Halaqah remains the product name. The Tajwid / Tasmik / Talaqqi wording is part of the supplied logo and does not add new functional modules.

## Dashboard refresh — 22 October 2026
Reference-led workspace with floating header, compact icon rail, segmented student filters, responsive bottom navigation, actual session completion dial, subtle page transitions and reduced-motion support. No invented trend or performance metrics are displayed. Teacher save-and-next, guardian reports and admin templates retain the existing local-data model.

Feather Icons 4.29.2 is bundled locally under MIT; see `dist/feather-LICENSE.txt`.
