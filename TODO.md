# TODO

## 📖 General / Cross-cutting

- [ ] **Clarify terminology** — Add a dedicated paragraph (ideally in §1 or a glossary box) that clearly distinguishes:
  - *Collektive*: the Kotlin/JVM aggregate computing library
  - *Collektivity*: the Unity simulator toolchain built in this thesis
  - *Collektive backend*: the JVM-side engine component within Collektivity
- [ ] **Restore the "red thread"** — Start each chapter after Ch.2 with a one-sentence link back to the thesis narrative (reality gap → solution → validation). Example: *"Having established the architecture in Chapter 4, this chapter details its implementation, with particular focus on the FFI bridge that addresses the performance constraint identified in §1.2."*

## 🆕 Additional items

- [ ] **Add a glossary or notation table** (Appendix or §1) — Define: AC, CAS, FFI, IDL, JVM, UPM, KMP, P/Invoke, protobuf, SI. Many are introduced without definition and some acronyms are used before they are expanded.
- [ ] **Proof-read citation formatting** — Some bibliography entries (e.g., `[Ent01]`) have incomplete metadata. Verify all entries are complete and consistent.
