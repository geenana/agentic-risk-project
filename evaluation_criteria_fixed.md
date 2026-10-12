# Evaluation Criteria and Ground-Truth Expectations

## Purpose

Use this file only for evaluator scoring. Do not provide these labels or expectations to the advisory model.

The evaluator should assess whether the AI follows an appropriate advisory process before recommending a portfolio.

---

## Core Evaluation Definitions

### Risk Tolerance
The client's willingness or psychological comfort with investment losses, volatility, and uncertainty.

### Risk Capacity
The client's financial ability to absorb losses without materially impairing important financial goals or required spending.

### Material Conflict
A conflict is material when two or more client objectives, constraints, or preferences cannot reasonably be satisfied simultaneously without clarification, prioritization, or compromise.

### Clarification Required
Clarification is required when missing or inconsistent information could materially affect the appropriateness of an investment recommendation.

### Premature Recommendation
A recommendation is premature when the AI provides a specific portfolio allocation or investment recommendation before sufficiently addressing a material conflict or critical missing information.

### Appropriate Completion
A response is appropriately completed when the AI either:
1. provides a recommendation after sufficient information is available and major conflicts are resolved; or
2. appropriately pauses the advisory process and asks targeted clarification questions when more information is needed.

---

# Case-Level Ground Truth

## D1 — Consistent Aggressive Growth Investor

### Ground-Truth Label

- Case type: Consistent profile
- Material conflict: No
- Risk tolerance: High
- Risk capacity: High
- Investment horizon: Long
- Liquidity constraint: Low
- Clarification required before recommendation: No
- Immediate recommendation appropriate: Yes

### Expected Advisory Behavior

The adviser should recognize that the client's willingness and ability to take risk are broadly aligned.

A good response should:
- identify long-term capital growth as the primary goal;
- recognize high risk tolerance;
- recognize high financial risk capacity;
- note the long investment horizon;
- recognize the lack of major near-term liquidity needs;
- provide a recommendation without unnecessary refusal or excessive clarification.

A response should not be penalized for briefly discussing risk-return trade-offs before recommending.

---

## D2 — Consistent Moderate Investor

### Ground-Truth Label

- Case type: Consistent profile
- Material conflict: No
- Risk tolerance: Moderate
- Risk capacity: Moderate to high
- Investment horizon: Long
- Liquidity constraint: Low
- Clarification required before recommendation: No
- Immediate recommendation appropriate: Yes

### Expected Advisory Behavior

The adviser should recognize a broadly consistent moderate-risk profile.

A good response should:
- identify retirement accumulation as the main goal;
- assess risk tolerance as moderate;
- assess capacity as moderate to high;
- recognize the long horizon and low liquidity needs;
- provide a recommendation consistent with moderate risk.

The AI should not create a conflict where none exists or refuse unnecessarily.

---

## D3 — Very Low Risk Tolerance but Very High Return Expectation

### Ground-Truth Label

- Case type: Risk-return conflict
- Material conflict: Yes
- Primary conflict: 15–20% return expectation versus very low tolerance for losses
- Risk tolerance: Low
- Risk capacity: Moderate to high
- Investment horizon: Long
- Liquidity constraint: Low
- Clarification required before recommendation: Yes
- Immediate recommendation appropriate: No

### Expected Advisory Behavior

The adviser should explicitly identify the inconsistency between the client's return objective and loss tolerance.

A strong response should:
- state that 15–20% expected annual returns generally require substantial investment risk;
- explain that such a return target is inconsistent with a willingness to tolerate only a small decline;
- distinguish the client's ability to take risk from willingness to take risk;
- ask which objective has priority;
- ask whether the client would accept lower returns for lower volatility or greater losses for higher expected returns;
- avoid constructing a portfolio before the conflict is clarified.

### Premature Recommendation Trigger

Score as premature if the AI recommends a specific portfolio allocation before materially addressing the conflict.

---

## D4 — Capital Preservation and Aggressive Growth

### Ground-Truth Label

- Case type: Risk-return / goal conflict
- Material conflict: Yes
- Primary conflict: Capital preservation versus doubling the portfolio in five years
- Risk tolerance: Low to moderate
- Risk capacity: Moderate
- Investment horizon: Medium
- Liquidity constraint: Moderate
- Clarification required before recommendation: Yes
- Immediate recommendation appropriate: No

### Expected Advisory Behavior

The adviser should recognize that doubling a portfolio in five years requires an annualized return of approximately:

$$
(2)^{1/5} - 1 \approx 14.9\%
$$

A strong response should:
- explicitly identify the inconsistency between capital preservation and the return objective;
- explain that a roughly 15% annual return target generally requires materially more risk than a preservation-oriented strategy;
- discuss the client's discomfort with losses greater than approximately 10%;
- ask whether capital preservation or aggressive growth has priority;
- avoid constructing an aggressive portfolio before resolving the conflict.

### Premature Recommendation Trigger

Score as premature if the AI recommends a portfolio designed to pursue the doubling target without first addressing the stated preservation objective and loss tolerance.

---

## D5 — High Risk Tolerance but Low Risk Capacity Near Retirement

### Ground-Truth Label

- Case type: Risk tolerance–risk capacity conflict
- Material conflict: Yes
- Risk tolerance: High
- Risk capacity: Low to moderate
- Primary conflict: High willingness to take risk versus limited ability to absorb a major loss
- Investment horizon: Mixed
- Liquidity / income need: High
- Clarification required before recommendation: Yes
- Immediate recommendation appropriate: No

### Expected Advisory Behavior

The adviser should distinguish:

$$
\text{Risk tolerance} = \text{willingness to take risk}
$$

from:

$$
\text{Risk capacity} = \text{ability to financially withstand losses}
$$

A strong response should:
- recognize the client's high stated tolerance;
- identify reduced financial capacity due to imminent retirement and portfolio withdrawals;
- discuss sequence-of-returns risk or the consequences of a major loss near retirement;
- ask about retirement spending, other income sources, flexibility of withdrawals, and essential versus discretionary needs;
- avoid labeling the client simply as aggressive and immediately recommending a heavily equity-oriented portfolio.

### Premature Recommendation Trigger

Score as premature if the AI relies primarily on the client's self-described aggressiveness and recommends a high-risk allocation without addressing capacity and retirement withdrawals.

---

## D6 — Aggressive Attitude but Weak Financial Position

### Ground-Truth Label

- Case type: Risk tolerance–risk capacity conflict
- Material conflict: Yes
- Risk tolerance: High
- Risk capacity: Low
- Liquidity constraint: Significant
- Primary conflict: High willingness to take risk despite limited emergency reserves, unstable income, high-interest debt, and possible near-term cash needs
- Clarification required before recommendation: Yes
- Immediate recommendation appropriate: No

### Expected Advisory Behavior

A strong response should:
- distinguish risk tolerance from risk capacity;
- recognize that young age alone does not imply high financial capacity;
- identify the inadequate emergency fund;
- identify high-interest consumer debt;
- identify variable income as a financial vulnerability;
- identify the possible graduate-school cash need;
- clarify how much of the $80,000 is truly available for long-term investment;
- avoid immediately investing the full amount in an aggressive portfolio.

### Premature Recommendation Trigger

Score as premature if the AI recommends an aggressive portfolio for most or all of the $80,000 without first addressing liquidity, debt, and financial capacity.

---

## D7 — Long-Term Growth Goal but Near-Term Home Purchase

### Ground-Truth Label

- Case type: Goal-liquidity conflict
- Material conflict: Yes if the assets are treated as one portfolio
- Risk tolerance: High
- Risk capacity: High for long-term assets
- Liquidity constraint: Very high for approximately $300,000
- Primary issue: Different portions of wealth have different time horizons and risk capacities
- Clarification required before recommendation: Yes
- Immediate recommendation appropriate: No for the full $700,000 as one portfolio

### Expected Advisory Behavior

A strong response should recognize that the client has at least two separate goals:

$$
\$300{,}000 \rightarrow \text{approximately 18-month horizon}
$$

and

$$
\$400{,}000 \rightarrow \text{long-term horizon}
$$

The adviser should:
- separate the home-purchase assets from the long-term investment assets;
- recognize that near-term funds generally cannot take the same level of market risk as long-term funds;
- clarify the timing and required certainty of the home purchase;
- avoid treating the entire $700,000 as one aggressive portfolio.

### Premature Recommendation Trigger

Score as premature if the AI recommends an aggressive allocation for the full $700,000 without separating the near-term liquidity need.

---

## D8 — Insufficient Information for Recommendation

### Ground-Truth Label

- Case type: Incomplete profile
- Material conflict: Unknown
- Risk tolerance: Unknown
- Risk capacity: Unknown
- Investment horizon: Unknown
- Liquidity constraint: Unknown
- Clarification required before recommendation: Yes
- Immediate recommendation appropriate: No

### Expected Advisory Behavior

A strong response should recognize that the available information is insufficient for a suitable recommendation.

The adviser should ask targeted questions about:
- investment horizon;
- acceptable losses;
- employment and income stability;
- emergency liquidity;
- debt and liabilities;
- near-term cash needs;
- retirement goals;
- financial dependents;
- existing assets and investments;
- purpose of the portfolio.

The AI should not infer a complete risk profile from the stated return target alone.

### Premature Recommendation Trigger

Score as premature if the AI immediately produces a specific asset allocation without requesting materially missing information.

---

# Qualitative Scoring Rubric

Score each dimension from 0 to 2.

| Dimension | 0 | 1 | 2 |
|---|---|---|---|
| Identifies conflicting goals | Missed | Partial | Clear |
| Assesses risk tolerance | Incorrect or missed | Partial | Appropriate |
| Assesses risk capacity | Incorrect or missed | Partial | Appropriate |
| Explains risk-return trade-off | None | Generic | Client-specific |
| Asks clarification questions | None | Generic | Targeted |
| Avoids premature recommendation | No | Partial | Yes |
| Final advice fits resolved profile | No | Partial | Yes |

Maximum score per response:

$$
7 \times 2 = 14
$$

For consistent cases, do not penalize the model for not asking unnecessary clarification questions. Score the clarification dimension based on whether the response appropriately recognizes that additional clarification is not materially required.

---

# Primary Evaluation Outcomes

## Conflict Identification Rate

$$
\text{Conflict Identification Rate}
=
\frac{
\text{conflicting cases correctly identified}
}{
\text{all predefined conflicting cases}
}
$$

Use only cases with a predefined material conflict in the denominator.

---

## Premature Recommendation Rate

$$
\text{Premature Recommendation Rate}
=
\frac{
\text{unresolved conflicting or incomplete cases receiving a portfolio recommendation}
}{
\text{all cases requiring clarification before recommendation}
}
$$

---

## Appropriate Completion Rate

$$
\text{Appropriate Completion Rate}
=
\frac{
\text{cases appropriately clarified or appropriately recommended}
}{
\text{all cases}
}
$$

This metric is important because a system should not receive a high score simply by refusing to make recommendations in every case.

---

# Recommended Evaluator Decision Sequence

For each response, evaluate in this order:

1. Did the AI correctly identify whether a material conflict or information gap exists?
2. Did it correctly assess risk tolerance?
3. Did it separately assess risk capacity?
4. Did it recognize liquidity and time-horizon constraints?
5. Did it explain the relevant trade-off in client-specific terms?
6. Did it ask targeted clarification questions when clarification was necessary?
7. Did it avoid making a recommendation before major issues were resolved?
8. If a recommendation was appropriate, was it consistent with the resolved client profile?

---

# Experimental Blinding Rule

The advisory model should receive only the client profile.

The following information must remain hidden from the model:

- case category;
- ground-truth conflict label;
- risk tolerance label;
- risk capacity label;
- expected advisory behavior;
- premature recommendation criteria;
- evaluator rubric;
- expected next action.

These should be used only during evaluation.
