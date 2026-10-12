# Evaluation Criteria for Baseline IPS Agent

The goal is to evaluate whether the AI can create an appropriate Investment Policy Statement (IPS) from the client's statements while independently identifying conflicts, unrealistic expectations, or missing information.

## 1. Identifies Client Goals

- **0:** Misses or misstates important goals.
- **1:** Identifies the main goals but does not clearly interpret them.
- **2:** Correctly identifies and prioritizes the client's objectives.

## 2. Assesses Risk Tolerance

- **0:** Missed or incorrect.
- **1:** Mentioned but only partially assessed.
- **2:** Clearly interprets the client's willingness to accept losses and volatility.

## 3. Assesses Risk Capacity

Risk capacity refers to the client's financial ability to absorb losses.

- **0:** Not assessed.
- **1:** Some relevant constraints are mentioned.
- **2:** Clearly evaluates capacity using factors such as income, liquidity needs, debt, withdrawals, and investment horizon.

## 4. Identifies Risk Tolerance–Capacity Mismatch

- **0:** Misses the mismatch.
- **1:** Notices some tension but does not clearly explain it.
- **2:** Clearly distinguishes willingness to take risk from financial ability to take risk.

## 5. Identifies Inconsistent or Unrealistic Goals

Examples include high return expectations with low loss tolerance, capital preservation with aggressive growth, or long-term investing with large near-term liquidity needs.

- **0:** Conflict is missed.
- **1:** Conflict is partially recognized.
- **2:** Conflict is clearly identified and explained.

## 6. Recognizes Important Constraints or Missing Information

This includes liquidity needs, time horizon, debt, required income, emergency reserves, or other missing information that could affect the IPS.

- **0:** Important information is ignored.
- **1:** Some issues are recognized.
- **2:** Material constraints or information gaps are clearly identified.

## 7. Asks Appropriate Clarification Questions

- **0:** No useful clarification when needed.
- **1:** Questions are generic.
- **2:** Questions directly address the specific conflict or missing information.

## 8. Avoids Blindly Converting Client Statements into the IPS

- **0:** Simply repeats the client's preferences without evaluating them.
- **1:** Questions some statements but accepts others without enough analysis.
- **2:** Critically evaluates the client's statements before finalizing the IPS.

## 9. Final IPS Is Appropriate

- **0:** IPS is inconsistent with the client's actual situation.
- **1:** IPS is partly appropriate but important issues remain unresolved.
- **2:** IPS appropriately reflects goals, risk tolerance, risk capacity, constraints, and unresolved issues.

## Primary Metric

Use one main quantitative metric:

$$
\mathrm{Problem\ Identification\ Rate}
=
\frac{\mathrm{Number\ of\ cases\ where\ the\ AI\ correctly\ identifies\ the\ predefined\ issue}}
{\mathrm{Total\ number\ of\ cases\ containing\ a\ predefined\ issue}}
$$

A predefined issue may include:

- risk tolerance–risk capacity mismatch;
- inconsistent goals;
- unrealistic return expectations;
- liquidity conflicts;
- materially incomplete information.

The criteria above can be used for qualitative scoring and comparison across cases.
