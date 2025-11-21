# Tools – Smart Yield Saving

This folder contains operational spreadsheets and supporting resources used for **Smart Yield Saving** modeling, simulation, and risk management.  
All files here are intended for production reference and collaborative analysis.

---

## 📊 Contents
- **smart-yield-saving-tools.xlsx**  
  Spreadsheet with stepwise inputs and outputs for:
  - Phase 1: Initial pool setup, leverage, buffer allocation
  - Phase 2: Collateral repositioning and spot/short balancing
  - Phase 3: Advanced notes, harvesting conditions, and operational checklists

---

## 🛠 Usage Guidelines
1. **Do not modify directly in production.**  
   - Use a local copy for scenario testing.  
   - Submit changes via pull request with clear rationale.

2. **Versioning**  
   - Increment file name with suffix if structure changes (e.g., `smart-yield-saving-tools-v2.xlsx`).  
   - Keep older versions for auditability.

3. **Documentation Linkage**  
   - Each phase in the spreadsheet corresponds to a Markdown guide in `../docs/`.  
   - Example: `Phase 1` → `01-phase-1-setup.md`.

4. **Collaboration**  
   - Contributors must document parameter changes in commit messages.  
   - Use English for technical notes; bilingual annotations allowed in comments if needed.

---

## 🔒 Security & Hygiene
- Ensure `.gitignore` excludes sensitive exports (logs, temp files, DB dumps).  
- Only `.xlsx` files relevant to modeling should be committed.  
- No personal API keys or credentials should ever be stored here.

---

## ✅ Best Practices
- Keep spreadsheet formulas transparent and auditable.  
- Align terminology with glossary in `../docs/README.md`.  
- Run scenario checks before merging updates.  
- Maintain consistency across phases (setup → reposition → advanced → maintenance).

---

## 📌 Next Steps
- Future enhancements may include CSV/JSON exports for automated testing.  
- Consider linking this folder with simulation scripts in `scripts/` (if added later).  