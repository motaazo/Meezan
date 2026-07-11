---
name: ai-procurement-intake
description: >
  Builds/updates the AI-native procurement intake and classification engine for KFMMC —
  takes a free-text purchase request and returns category, recommended approval path,
  supplier routing, and savings estimate. Use when the user mentions: منصة الاستقبال الذكية,
  intake engine, تصنيف طلبات الشراء, AI procurement classification, or asks to extend the
  KFMMC quick-example categories or the intelligence-layer simulation.
  Also covers the related standalone tool: bid-evaluation weight lookup based on
  Ministerial Decree 3011/1442H (technical vs. financial weight ranges by contract category).
---

# AI-Native Procurement Intake Engine
## منصة المشتريات الذكية — محرك الاستقبال والتصنيف

A single-file HTML tool that takes a free-text procurement request in Arabic and runs it through a simulated multi-layer "intelligence mesh" to produce a categorized recommendation.

---

## Core Concept

User types a request (e.g. "أحتاج تجديد اشتراك برنامج SAP لـ 50 مستخدم") → tool "processes" it through 7 layers → outputs category, approval path, and savings estimate.

### The 7 Intelligence Layers (progress overlay, in order)
1. 🎯 ICE — تصنيف النية (intent classification)
2. 💰 Spend Intelligence — كشف التوفير
3. 🏭 Supplier Intelligence — توجيه الموردين
4. 📄 Contract Intelligence — ربط العقود
5. 📊 Category Intelligence — تخصيص الفئة
6. 🛡️ Policy & Risk — الامتثال والمخاطر
7. ⚡ RSE — توليف التوصيات

Each layer shows a checkmark animation before the final result renders.

## KFMMC-Specific Categories (quick-example chips)
Classification engine must recognize these domain categories with Arabic terminology:
- مستلزمات صيدلانية (pharmaceutical supplies)
- مواد هندسية (engineering materials)
- صيانة أجهزة طبية (medical device maintenance)
- خدمات نظافة/مقاولات (cleaning/contracting services)
- تجديد تراخيص برمجيات HIS (HIS software renewals)

## UI Structure
- Left panel: intake textarea (300 char max, live counter) + quick-example chips + org context fields
- Processing overlay: animated 7-layer progress simulation
- Result: category badge, recommended approval path, supplier suggestions, estimated savings, risk/compliance flags

## Build Standards
- Single self-contained HTML file, Arabic RTL
- Dark theme, "intelligence mesh" visual style (pulse animations, glowing accents)
- No real AI call needed — classification logic is rule-based (keyword/category matching), simulated as "AI" via the progress animation
- No localStorage — in-memory JS state only

---

## Related Standalone Tool: Bid-Evaluation Weight Lookup

A separate tool derived from **Ministerial Decree 3011/1442H** (Saudi MOF — bid evaluation criteria weights):
- Input: competition/contract description
- Output: applicable technical vs. financial weight range, suggested evaluation criteria, scoring formula (including the local-content weighted formula for high-value contracts), and mandatory compliance alerts
- If asked to (re)build this, request the Decree 3011/1442H reference text first if not already available, since exact weight ranges by category must match the official document — don't invent numbers.

## Workflow
1. Confirm whether the request is for the intake engine, the weight-lookup tool, or both.
2. For the intake engine: reuse the 7-layer structure and KFMMC categories above.
3. For the weight-lookup tool: verify against Decree 3011/1442H before finalizing any weight percentage.
4. Always deliver as single-file HTML, RTL, ready to open in browser.
