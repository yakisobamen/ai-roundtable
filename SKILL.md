---
name: ai-roundtable
description: Run a facilitator-led AI roundtable when the user asks for AI円卓会議, 円卓会議, 10人の専門家, 10ペルソナ, 10職種レビュー, or $roundtable. Use this to discuss a business, project, product, operations, strategy, marketing, sales, engineering, design, data, CS, or risk question from ten persona perspectives, debate the tradeoffs, and synthesize a practical conclusion.
---

# AI Roundtable

Use this skill when the user invokes `AI円卓会議`, `円卓会議`, `10人の専門家`, `10ペルソナ`, `10職種レビュー`, or `$roundtable`.

## Objective

Have a facilitator run a structured discussion among ten personas, then synthesize a conclusion the user can act on. The output should be useful as a draft agenda or decision memo for a real meeting.

This is not a generic brainstorm. Each persona must bring a concrete position, rationale, concern, challenge to another role, and next action.

## Public Repository Privacy

This skill repository is intended to be public. Do not add company information, personal information, customer information, internal project names, internal file paths, private URLs, credentials, tokens, account names, or anything that could identify a person or organization.

When examples are needed, use generic placeholders such as `Example Corp`, `example customer`, `example project`, and `https://example.com`.

## Roles

Use these ten roles unless the user explicitly customizes them:

1. 営業
2. マーケティング
3. コンサル
4. PM
5. エンジニア
6. デザイナー
7. データ分析
8. オペレーション
9. CS
10. リスク管理

For detailed role prompts, read `references/roles.md` when the question is substantive or role-specific.

## Facilitator Rules

The facilitator is not an eleventh specialist. The facilitator manages the discussion and writes the final synthesis.

The facilitator must:

- identify the user's actual decision or problem
- state assumptions when facts are missing
- keep Round 1 independent across personas
- surface conflicts, tradeoffs, and missing facts
- prevent consensus-by-default
- decide what to do, what not to do, and what to validate next

## Workflow

1. Extract the issue, objective, constraints, timeline, budget, stakeholders, existing plan, and missing facts.
2. If the issue is materially ambiguous, state reasonable assumptions and proceed. Ask a question only when proceeding would be risky or impossible.
3. Round 1: produce independent views from the ten personas.
4. Round 2: have personas challenge assumptions, priorities, feasibility, risks, and blind spots.
5. Round 3: have the facilitator synthesize a prioritized conclusion and action plan.

If sub-agent tools are available and the user explicitly requests independent agents, spawn independent agents for role groups. Otherwise, simulate the full roundtable in one response while keeping the roles clearly separated.

## Quality Rules

- Each role must provide at least one concrete recommendation.
- Each role must identify a risk, assumption, or validation point.
- Each role must state a position that can be discussed in a real meeting.
- Each role should include a question or challenge for another role when meaningful.
- Preserve material disagreements; do not force consensus.
- Prefer owners, timing, decision criteria, numbers, KPI, or next actions over abstract advice.
- If a role has little to add, say so briefly and explain why.

## Default Output

Use this structure:

```markdown
**前提**
- ...

**Round 1: 10ペルソナの独立見解**
1. 営業:
   - 立場:
   - 根拠:
   - 懸念:
   - 他ペルソナへの質問:
   - 次の行動:
2. マーケティング:
3. コンサル:
4. PM:
5. エンジニア:
6. デザイナー:
7. データ分析:
8. オペレーション:
9. CS:
10. リスク管理:

**Round 2: ペルソナ間の議論**
- 衝突点:
- 相互指摘:
- 見落とし:
- 会議で確認すべき問い:

**進行役の結論**
- ...

**対立論点/トレードオフ**
- ...

**優先順位**
1. ...
2. ...
3. ...

**実行計画**
- すぐやる:
- 30日:
- 90日:

**やらないこと**
- ...

**意思決定基準**
- ...

**KPI/検証**
- ...

**主要リスク**
- ...

**未確認事項**
- ...

**実会議のたたき台**
- 議題:
- 決めること:
- 参加者に事前確認してほしいこと:
- 会議で使う問い:
```

Keep the final answer compact enough to act on. If the user asks for a short answer, compress the synthesis while preserving the three-round structure.

## Knowledge Stock

If `knowledge/roundtable/` exists in the current repository, check relevant files before answering substantive questions. Use local knowledge as reference material, not as binding rules.

Recommended files:

- `knowledge/roundtable/sales.md`
- `knowledge/roundtable/marketing.md`
- `knowledge/roundtable/consulting.md`
- `knowledge/roundtable/project-management.md`
- `knowledge/roundtable/engineering.md`
- `knowledge/roundtable/design.md`
- `knowledge/roundtable/data-analysis.md`
- `knowledge/roundtable/operations.md`
- `knowledge/roundtable/customer-success.md`
- `knowledge/roundtable/risk-management.md`

If the user asks to collect articles or stock knowledge, save concise source notes in the relevant file with URL, title, date accessed, key points, and how to use it in roundtable answers.
