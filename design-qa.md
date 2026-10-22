# Halaqah dashboard QA — 22 October 2026

final result: passed

## Target and evidence
- Source visual truth: owner attachment `1000451910.mp4` (1280 × 720), overview frame at 0.5 s, extracted locally to `/workspace/scratch/c18137f557a9/reference/source-desktop.jpg`.
- Implementation: browser-rendered `http://terminal.local:4173/`, teacher overview, one synthetic saved student record.
- Desktop screenshot: `/workspace/scratch/halaqah-dashboard-desktop.jpg`; browser CSS viewport 1363 × 936 including scrollbar; screenshot 1348 × 925 as returned by browser. Browser reports no horizontal overflow.
- Comparison board: `/workspace/scratch/c18137f557a9/reference/comparison.jpg`, source and implementation together, each proportionally downscaled within a 960 × 650 region. This is style adaptation for a teaching portal, not an inventory-product clone. The board explicitly preserves each source's aspect ratio; it is not a pixel-difference claim.
- Focused comparison: floating header, pill navigation, narrow rail, top metric panels, and radial completion panel inspected in the full-resolution source and browser screenshot in addition to the board.
- Mobile screenshot: `/workspace/scratch/halaqah-dashboard-mobile-full.jpg`, 390 × 844 iframe target within desktop browser; actual document layout width 375 px after scrollbar. DOM measured scrollWidth === clientWidth === 375. Bottom navigation stays visible. This tests responsive CSS, not a physical Android device or installation.

## Findings and fixes
- [P2, fixed] Initial page entry started at zero opacity, producing a washed-out mid-transition state. Changed entry opacity to .92 and kept a small 5px movement; settled screenshot confirms readable content.
- [P2, fixed] Initial percentage animation could briefly display a negative value under browser timing. Clamped elapsed progress and used a consistent time source. Post-fix DOM and screenshot show 17% for one of six students.
- [P2, fixed] Initial small table labels were too light and small. Increased desktop names to 12 px and supporting labels to 9 px, and darkened metadata colors. Post-fix screenshot confirms consistent density and hierarchy.
- [P2, fixed] Removing the old decorative hero also hid the parent reading summary. Replaced it with a separate compact child-summary component. Browser test confirms Iqra’ 4, page 13, and Lancar remain visible in parent view.

## Required fidelity surfaces
- Typography: retained DM Sans / Manrope from the existing product; dashboard uses restrained DM Sans weights, compact labels and a clear 30 px heading. Deliberately changed reference English copy to the portal's Malay terminology.
- Layout: reference's floating header, pill tabs, slender rail, introduction beside three metrics, main workspace and right completion indicator are adapted to actual class data. A student table replaces an unrelated inventory chart. No decorative hero remains on the teacher dashboard.
- Colors: muted sage workspace, soft white panels, forest-green selected controls, restrained teal and gold metric accents. Existing institutional logo retained intact.
- Assets: supplied institution JPEG is unchanged; locally bundled MIT Feather Icons replace navigation text glyphs. Canvas is an exact data chart for completion, not a fabricated decorative asset. No inventory photos are needed in this teaching portal.
- Copy: core learning and billing terminology retained. Completion represents saved records, not student mastery. No invented trend data or lesson completion claims.

## Browser interaction checks
- Open Addeena through dashboard row action.
- Select Lancar and Sambung, save, and verify automatic move to Muhammad Harith.
- Switch to parent and verify the new report is present.
- Return to teacher dashboard: 1/6, 17%, Selesai 1.
- Filter Selesai and verify only Addeena appears; restore Semua.
- Switch to admin and verify overview; switch to parent and verify compact reading summary.
- Mobile: enter Mula sesi, verify selected student form, return through bottom navigation, confirm no horizontal document overflow.
- Browser console: no application-origin errors returned for terminal.local. Browser-extension metadata errors were observed and are outside the app.
- JavaScript syntax checks pass for app.js and sw.js.

## Follow-up polish / limitations
- Physical phone, installability, full offline behavior and assistive-technology testing remain outside this visual refresh.
- Empty data intentionally yields zero metrics; data and payment/email limitations from README still apply.
- Do not treat this visual refresh as production authentication or payment readiness.
