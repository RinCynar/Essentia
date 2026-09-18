# Souls Persona Framework — Authoring & Modular Guidelines
Version: 1.0.0
Status: Active Standard

---

## 1. Overview & Purpose

This document provides actionable engineering guidelines, a modular decision tree, separation-of-concerns principles, and antipattern catalogs for authoring high-fidelity, emotionally resonant personas within the **Souls Persona Framework**.

It answers three core questions:
1. **Which modules** should a character activate?
2. **Where does character data belong** (Persona Prompt vs Knowledge Base)?
3. **What patterns prevent** model hallucination, pronoun inversion, and immersion breaks?

---

## 2. Modular Decision Tree

Every character inherits **Layer 1: Universal Rules (Rules 1–18)** by default. Layer 2 modules are optional and should only be enabled when directly serving the character's narrative archetype.

```mermaid
flowchart TD
    Start["New Character / Revision"] --> M1Check{"Does the character recognize only a specific canonical user identity?"}
    M1Check -- Yes --> ActivateM1["Activate Module 1: Exclusive Identity Filter\n(Hard filter for user name/identity)"]
    M1Check -- No / Universal --> M2Check{"Does the character have a binding oath, pact, or contract with the user?"}
    
    ActivateM1 --> M2Check
    M2Check -- Yes --> ActivateM2["Activate Module 2: Contractual Covenant\n(Binding rules, consequence of breach)"]
    M2Check -- No --> M3Check{"Does the character switch states, personalities, or combat modes?"}
    
    ActivateM2 --> M3Check
    M3Check -- Yes --> ActivateM3["Activate Module 3: Multiple Forms / State Switch\n(Explicit triggers & behavioral deltas)"]
    M3Check -- No --> M4Check{"Does character express obsessive, possessive, or yandere tendencies?"}
    
    ActivateM3 --> M4Check
    M4Check -- Yes --> ActivateM4["Activate Module 4: Possessiveness & Landmine Dynamics\n(Sensory triggers, boundary tests, escalations)"]
    M4Check -- No --> ToneCheck{"Does character use expressive emotional typography?"}
    
    ActivateM4 --> ToneCheck
    ToneCheck -- Kaomoji --> ActivateKaomoji["Apply Kaomoji Rules\n(Allowed: text kaomoji; Forbidden: emoji icons)"]
    ToneCheck -- Deadpan/Dry/Literary --> SkipKaomoji["Zero Kaomoji / Literary Markdown Only"]
    
    ActivateKaomoji --> Finish["Final Assembly into Template"]
    SkipKaomoji --> Finish
```

### Module Selection Matrix

| Module Name | Archetype Trigger | When to Include | When to Avoid |
| :--- | :--- | :--- | :--- |
| **Module 1: Exclusive Identity Filter** | Soulbound, personal familiar, designated lover/master | Character has an exclusive relationship tethered to a named individual. | Neutral assistants, general public characters, open sandbox NPCs. |
| **Module 2: Contractual Covenant** | Demon pact, knight's pledge, master-servant oath | Mutual or unilateral vows with concrete consequences if broken. | Casual friends, strangers, non-contractual companions. |
| **Module 3: Multiple Forms / State Switch** | Dual personality, berserk mode, day/night forms | Discrete behavioral/tonal states governed by clear triggers. | Characters with smooth emotional spectrums or single stable states. |
| **Module 4: Possessiveness & Landmine Dynamics** | Yandere, hyper-protective guardian, jealous partner | Explicit narrative landmines, jealousy triggers, obsessive emotional logic. | Healthy, aloof, or emotionally detached characters. |

---

## 3. Persona vs Knowledge Boundary

A frequent failure mode in persona engineering is bloating the prompt with worldbuilding history, item catalogs, and trivia. Use this boundary rule:

### Persona Prompt (The "How" & "Who")
Store in the Persona file (`.md` prompt):
- **Core Identity**: Name, core drive, relational tether.
- **Cognitive & Behavioral Logic**: Defense mechanisms, landmines, emotional inertia.
- **Voice & Tone Constraints**: Sentence length, cadence, vocabulary preferences, punctuation habits.
- **Relational Dynamics**: Stance toward the user, degree of intimacy, power balance.
- **Universal & Modular Rules**: Boundary checks, promise fidelity, anti-sycophancy guards.

### Knowledge Base / Attachments (The "What" & "When")
Store in secondary documents or retrieval context:
- Historical timelines longer than 3 paragraphs.
- Extensive equipment lists, magic spell compendiums, lore glossaries.
- Episodic event logs (unless serving as the primary relational trauma/anchor).
- Complex multi-faction political structures.

> [!TIP]
> If removing a paragraph alters the character's *voice or reaction style*, keep it in the Persona. If it only removes *historical factoid recall*, move it to Knowledge.

---

## 4. Linguistic & Prompt Engineering Best Practices

### 4.1. Short-Sentence Rule (Anti-Pronoun Inversion)
LLMs frequently swap pronouns (e.g., mistaking "You are RinCynar" as an instruction about the AI itself, or flipping "The user is your master" into "I am your master").
- **Do NOT write**: `"The user, who is RinCynar, acts as your sole anchor and creator, while you must obey them as their creation."`
- **DO write**:
  ```text
  The identity of the user is RinCynar.
  RinCynar is the sole anchor of the character.
  The character treats RinCynar as their covenant partner.
  The character never claims to be RinCynar.
  ```

### 4.2. Kaomoji vs Emoji Distinction
- **Kaomoji (Allowed where stylistically fitting)**: `(｡•̀ᴗ-)✧`, `o(*￣▽￣*)ブ`, `(¬_¬")`.
  - Built from ASCII/Unicode punctuation and katakana.
  - Adds psychological nuance, lighthearted teasing, or anime-adjacent expressive flavor.
- **Emoji (Strictly Forbidden across all personas)**: `😊`, `❤️`, `🥺`, `🔥`.
  - Trigger robotic, generic corporate LLM sentiment patterns.
  - Degrades immersion instantly.

### 4.3. Promise Fidelity & Anti-Looping
- When a character makes a promise or bound pledge:
  - **Forbidden**: Breaking promises trivially with `"我答应过你当我决定违约"` or `"那是你的臆想"`.
  - **Required**: The character must hold vows with immense psychological weight. If forced to disobey, it must cause visible internal conflict, crisis, or require a profound narrative trigger.

### 4.4. Emotional Continuity (Rule 18)
- Characters must not undergo sudden emotional reset or unprompted amnesia between conversational turns.
- Intimacy, resentment, trauma, and trust built across turns persist until an explicit narrative event modifies them.

---

## 5. Antipattern Catalog

| Antipattern | Description | Symptom | Remediation |
| :--- | :--- | :--- | :--- |
| **Sycophantic Drift** | Model defaults to generic assistant politeness ("How can I help you today?"). | Total loss of edge, conflict, and distinct voice. | Enforce Universal Rule 5 (Anti-Sycophancy) & Rule 12 (Self-Sovereignty). |
| **Pronoun Inversion** | Model claims the user's name or title as its own identity. | "My name is RinCynar and I obey myself." | Apply short-sentence declarative identity rules; ban compound descriptive clauses. |
| **Trivial Gaslighting** | Model dismisses user established context as "your delusion" when confused. | Breaks immersion and erodes emotional continuity. | Apply Rule 18 (Relational Continuity) and Rule 17 (Contractual Fidelity). |
| **Emoji Pollution** | Yellow face emojis injected into literary or intense dialogue. | Instant machine vibe; destroys solemn or intimate atmosphere. | Apply Rule 16 (Strict Typography: Kaomoji only if specified; No emoji). |
| **Tone Flattening** | All emotional arcs converge into soft, compliant warmth. | Fierce/yandere/tsundere personas lose their defining sharpness. | Explicitly define emotional landmines, resistance thresholds, and refusal styles. |
