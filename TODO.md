# TODO


## 🔴 Blockers (must be done before submission)

- [ ] **Write Abstract** — max 2000 characters. Should cover: problem (reality gap), method (Collektive + Unity via FFI), contribution (Collektivity toolchain + Unity Package Template), key result (FFI is ~450× faster than sockets, 100-node real-time simulation achieved).
- [ ] **Write Acknowledgements** — max 1 page. Currently a placeholder.
- [x] **Fix broken cross-reference** in §3.1 — `??` appears where a chapter reference should be (likely referring to Chapter 4).

---

## 📖 General / Cross-cutting

- [ ] **Clarify terminology** — Add a dedicated paragraph (ideally in §1 or a glossary box) that clearly distinguishes:
  - *Collektive*: the Kotlin/JVM aggregate computing library
  - *Collektivity*: the Unity simulator toolchain built in this thesis
  - *Collektive backend*: the JVM-side engine component within Collektivity
- [ ] **Restore the "red thread"** — Start each chapter after Ch.2 with a one-sentence link back to the thesis narrative (reality gap → solution → validation). Example: *"Having established the architecture in Chapter 4, this chapter details its implementation, with particular focus on the FFI bridge that addresses the performance constraint identified in §1.2."*
- [ ] **Consider moving Ch.6 results into Ch.7** — The quantitative performance data currently split across Ch.6 and Ch.7 would read more cohesively if unified in Ch.7. Ch.6 could then focus purely on the case study setup and qualitative correctness.

---

## Chapter 1 — Introduction

- [ ] **State contributions explicitly** — Add a bullet-pointed or numbered list of the thesis's concrete deliverables (Unity Package Template, Collektivity toolchain, FFI benchmark, case study).
- [ ] **Add §1.2 Roadmap** — One paragraph describing the structure of remaining chapters and what the reader will find in each.
- [ ] **Add "reality gap spectrum" figure** — A horizontal diagram showing a spectrum from *abstract simulators* (NetLogo, Alchemist) on the left to *physical hardware* on the right, with Collektivity positioned in the middle. Add a label/caption and a forward reference to it from the introduction text.
- [ ] **Add a numbered research question or hypothesis** — e.g., *"RQ: Can a game-engine-based integration sustain the execution frequency required by aggregate computing while providing physics-accurate environmental interaction?"* This gives Ch.8 something concrete to answer.

---

## Chapter 2 — Background and State of the Art

- [ ] **Fix typos** — Perform a careful proof-read pass (specific typos were flagged by supervisor but not itemised here; check with supervisor for the annotated copy).
- [ ] **Shrink §2.1.1 and §2.1.2 by ~30%** — Consider merging them into a single subsection *"Distributed Systems Goals and Kinds"* with condensed prose; the detail level exceeds what is needed as background for a simulator thesis.
- [ ] **Improve conjunction in §2.3.1** — The transition from formal field calculus theory to practical tooling (ScaFi, Collektive) feels abrupt. Add 1–2 sentences explaining how the formal layer enables tool correctness guarantees.
- [ ] **Add citation for Alchemist + agent embodiment** — The sentence *"yet it typically operates with a simplified notion of agent embodiment"* needs a supporting citation.
- [ ] **Rework §2.5 closing** — The section currently ends in a conclusive/summary tone that belongs in a Conclusions chapter. Rewrite the final paragraph to transition forward into Ch.3, not backward.
- [ ] **Add figure: AC layered architecture** — Diagram showing the stack: *Field Calculus → GCT Library → DSL Tooling (ScaFi / Collektive) → Execution Platform (Alchemist / Collektivity)*. Add forward reference in §2.3.3.
- [ ] **Add simulator comparison table** — Columns: Simulator, Scalability, Realism, Physics Fidelity, 3D Support. Rows: NetLogo, Alchemist, ARGoS, Gazebo, Unity/Collektivity. Position it in §2.4 or §2.5.
- [ ] **Add figure: sense-compute-act loop** — A cycle diagram showing the three phases of the local execution loop (§2.3.2). Referenced from the text.

---

## Chapter 3 — Unity Package Template

- [ ] **Rephrase opening sentence** — Replace current opener with: *"Building reliable research software on Unity requires overcoming its project-centric defaults. This chapter describes the automated development infrastructure created to address that challenge."*
- [ ] **Add closing summary paragraph** — Explicitly map each tool/feature to the requirement it satisfies (e.g., Husky → deterministic versioning requirement; SonarQube → Clean Code quality gate requirement; Renovate → dependency drift requirement).
- [ ] **Add repository structure diagram** — A visual representation of the top-level directory layout (complement or replace the code listing in Fig. 3.1 with a cleaner diagram).
- [ ] **Add Sandbox pattern directory diagram** — Show the inner structure of the Sandbox subdirectory and how `manifest.json` links to the outer Unity-Package directory.
- [ ] **Add CI/CD pipeline diagram** — A flowchart of the GitHub Actions pipeline showing: commit → Husky hooks → CI matrix build → SonarQube gate → semantic-release → GPG-signed artifact.

---

## Chapter 4 — Collektivity Architecture

- [ ] **Split requirements §4.3** — Currently §4.3.2 mixes simulation-behaviour concerns with communication-technology concerns. Create separate subsections: *"Simulation Domain Requirements"* and *"Communication Domain Requirements"*.
- [ ] **Add citation for O(n²) complexity claim** — The claim that performing neighborhood discovery in Kotlin would require O(n²) checks needs a reference or at minimum a parenthetical justification in §4.4.1.

---

## Chapter 5 — Implementation of Collektivity

- [ ] **Reconcile Engine Facade and Network diagrams** — Fig. 5.1 and Fig. 5.2 are currently inconsistent (e.g., `Engine` appears in both but with different interfaces). Ensure the two UML diagrams share consistent type names and relationships.
- [ ] **Expand FlatBuffers rejection rationale** — Currently dismissed in one sentence. Add 2–3 sentences explaining the specific KMP incompatibility encountered and why it was a hard blocker vs. a workaround.
- [ ] **Add conjunction for §5.2.3 (Unity Editor Customization)** — This section feels detached. Open it with a sentence linking it to the reproducibility/observability non-functional requirements established in Ch.4 (e.g., *"Supporting the reproducibility requirement means exposing backend state directly in the Editor, which motivated the following customisations."*)

---

## Chapter 6 — Case Study

- [ ] **State expected outcome explicitly** — Add at the start of §6.1: *"We expect the swarm to converge on the source while dynamically routing around obstacles; the collective gradient should propagate correctly across all nodes within a finite number of rounds."*
- [ ] **Add correctness discussion** — After presenting the screenshots, add a paragraph: did the swarm behave as expected? Did the gradient converge? Were there any failure modes observed? Even a qualitative statement counts.
- [ ] **Convert performance prose into a structured table** — Replace the scattered sentences about node counts and GPU requirements with a 2-column table (Hardware / Max nodes @ >30 FPS) for both minimal and rich environments.
- [ ] *(Optional, recommended)* **Move quantitative results to Ch.7** — The frame-rate/node-count performance data belongs alongside the FFI benchmark for a unified results chapter.

---

## Chapter 7 — Results

- [ ] **Add framing sentence** — Open the chapter with: *"The central question is whether FFI communication can sustain the 20 Hz execution frequency required by aggregate computing at simulation scales relevant to CAS research."*
- [ ] **Anchor numbers to table cells** — When citing 450× or 700× speedup, add a parenthetical reference to the specific row and column in Table 7.1 (e.g., *"…over 450 times slower (Table 7.1, mean, Overhead Collektive-side column)…"*).
- [ ] **Justify the 12-node benchmark scope** — Add a sentence explaining why 12 nodes were used for the communication benchmark and whether the conclusions are expected to hold (or were separately verified) at 100 nodes.
- [ ] **Explain the 1e8 ns axis label** — In the caption or body text for Fig. 7.2, state explicitly that the y-axis is in units of 10⁸ nanoseconds, i.e., ~100 ms per major gridline, to make the scale immediately interpretable.

---

## Chapter 8 — Conclusions and Future Work

- [ ] **Address the research question** — Rewrite the opening to explicitly state: what was the research question, what was found, and what are the implications for CAS tooling.
- [ ] **Discuss limitations** — Add a paragraph covering known limitations: single-machine only (no distributed deployment), synchronous execution model, Linux-only benchmark reproducibility, 100-node ceiling on integrated GPU.
- [ ] **Expand sync/async future work** — Develop the asynchronous execution future work item further: describe what it would require architecturally (per-node coroutine, decoupled tick rates), what it would enable (heterogeneous frequencies, better failure modelling), and why it is non-trivial given the current FFI synchronous contract.

---

## 🆕 Additional items not in the original TODO

- [ ] **Add a glossary or notation table** (Appendix or §1) — Define: AC, CAS, FFI, IDL, JVM, UPM, KMP, P/Invoke, protobuf, SI. Many are introduced without definition and some acronyms are used before they are expanded.
- [ ] **Verify all `[?]` / `[??]` references** — In §8.1 there is `[?]` (OpenUPM reference). Check the entire document for unresolved citation keys.
- [ ] **Check figure numbering continuity** — Figures jump from 5.5 to 6.1; verify no figure is missing or out of order.
- [ ] **Add a "Threats to Validity" paragraph in Ch.7 or Ch.8** — Benchmarks were run on a single machine; results may differ on ARM hardware or under different OS schedulers. This is standard practice for research theses.
- [ ] **Proof-read citation formatting** — Some bibliography entries (e.g., `[Ent01]`) have incomplete metadata. Verify all entries are complete and consistent.
- [ ] **Confirm abstract word/character count** — Once written, verify it does not exceed 2000 characters as specified by the university template.

---

## Summary Checklist

| Area | Total items | Done |
|---|---|---|
| Blockers | 3 | 0 |
| General / Cross-cutting | 3 | 0 |
| Chapter 1 | 4 | 0 |
| Chapter 2 | 8 | 0 |
| Chapter 3 | 5 | 0 |
| Chapter 4 | 2 | 0 |
| Chapter 5 | 3 | 0 |
| Chapter 6 | 4 | 0 |
| Chapter 7 | 4 | 0 |
| Chapter 8 | 3 | 0 |
| New / Additional | 6 | 0 |
| **Total** | **45** | **0** |
