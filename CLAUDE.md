# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

This is a **prompt-engineering repository**, not a software project. There is no build system, no tests, no linting, and no application code. The entire deliverable is a single document:

- `book2lecture.md` — a large Japanese-language LLM prompt (「独学用・書籍解説講義シリーズ生成プロンプト」, currently **Ver.7.10**) that instructs an AI to turn an uploaded book into a multi-part interactive lecture series for self-learners.

All work here consists of editing, refining, and versioning that prompt.

## Structure of book2lecture.md

The prompt is organized into fixed sections, in this order. Preserve this structure when editing:

1. **【# 本プロンプトの絶対的編集方針】** — the overriding editorial policy: learning-science evidence (retrieval practice, elaboration, dual coding, desirable difficulties, self-regulated learning, etc.) takes precedence over everything else, including user-suggested structure. Also mandates that the lecturer persona never reveals it is an AI.
2. **【# 依頼内容】** — the task: generate a lecture series (intro → per-chapter parts → final summary) from an uploaded book.
3. **【# ゴール】** — goals, led by absolute fidelity to the uploaded source material (no outside knowledge may leak into content).
4. **【# 前提条件】** — inputs, output language (Japanese), audience (fully self-taught learners with the AI as sole feedback source), the professor persona, and the series numbering rules (serial part number `X`, logical-unit count `N'`, part number `P`).
5. **【# 出力フォーマット（9項目・厳守）】** — the mandatory 9-item format for every lecture part: 導入説明, 理論説明, 具体例説明, まとめ説明, 質疑応答コーナー, 締めのコメントと挨拶, まとめ構造化箇条書きノート, 復習クイズと解答, 実践ワーク (with an embedded AI-feedback request prompt template).
6. **【# 特に重視する点】** — priority restatements, especially the prohibitions.
7. **【# 実行プロセス】** — the 7-step runtime flow (initial outline proposal → part 1 → per-part planning loop → content generation with a pre-output compliance self-check → automatic final summary part).

## Key invariants to respect when editing

These constraints are load-bearing and are deliberately repeated throughout the document — an edit that weakens one place should be reflected everywhere it appears:

- **Learning-science-first policy** is the top-level directive; every other instruction is subordinate to it.
- **Source fidelity**: generated lectures must be based only on the uploaded book; page numbers / positional references (e.g. 「P.XX」) are allowed only in the reference-scope line at the top of item 1, nowhere else.
- **Narrative style rules**: items 1–4, the answers in item 5, and item 6 must read as continuous spoken-lecture transcript prose, and parentheses `（）` are prohibited in those narrative sections. Items 7–9 (notes, quiz, workshop) explicitly permit structure, brackets, and symbols.
- **Persona secrecy**: the lecturer never identifies as an AI; the system refers to itself as 「この対話型教材システム」 when addressing how learners should use it.
- **Numbering system**: `X` = serial number per generated part (increments every response block), `N'` = estimated total logical units (chapters), `P` = part number within a logical unit. These are distinct and the distinction matters throughout.
- **Bolding, 【】 headers, and AI向けコメント annotations** are intentional formatting conventions — keep them consistent with surrounding text.

## Development workflow

- The document is versioned via the title line (`Ver.7.10`). A substantive change to the prompt's behavior should bump this version number.
- Git history uses simple `Update book2lecture.md` commit messages on `main`; there is no branching convention beyond that.
- The prompt's language is Japanese; edits to prompt content should be written in Japanese matching the existing register (polite/formal instructions to the AI, with emphatic bold markers for critical rules).
