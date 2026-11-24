# 📊 Guesstimation Agent

### Interactive Market Sizing & Business Opportunity Estimation

An AI skill that helps users break down ambiguous estimation problems, develop logical assumptions, and calculate market opportunities through a structured, transparent approach.

Designed for **Product Managers, founders, consultants, and business strategists** who need to make informed decisions when reliable market data is limited.

## 🎯 What It Does

The Guesstimation Agent guides users through the estimation process rather than simply generating an answer.

Key capabilities include:

- **Interactive Discovery:** Asks users to describe their problem and share any known assumptions.
- **Market Sizing:** Estimates Total Addressable Market (TAM), Serviceable Addressable Market (SAM), and Serviceable Obtainable Market (SOM).
- **Flexible Methodologies:** Supports bottom-up, top-down, demand-side, and supply-side estimation.
- **Assumption Management:** Differentiates user-provided inputs, sourced facts, and estimated values.
- **Scenario Analysis:** Builds conservative, base, and optimistic scenarios.
- **Sensitivity Analysis:** Identifies the assumptions that most influence the final estimate.
- **Strategic Insights:** Translates calculated results into product and business implications.

## 🧠 How It Works

The skill follows a structured estimation workflow:

**Define the problem → Gather assumptions → Build the model → Calculate → Validate → Interpret**

### Step 1: Understand the Problem

The user enters a market-sizing or general guesstimation question.

### Step 2: Gather Known Assumptions

The agent asks a small number of relevant questions to understand the geography, target market, business model, and available numerical inputs.

### Step 3: Develop the Estimation Model

Depending on the problem, the agent uses bottom-up, top-down, funnel-based, or capacity-based estimation.

### Step 4: Calculate and Validate

The agent presents formulas, intermediate calculations, and final estimates while checking for numerical and logical consistency.

### Step 5: Analyze Scenarios

The agent explores how different assumptions affect the result, identifies major uncertainties, and recommends ways to validate them.

## 💡 Example Use Cases

| Use Case | Example Question |
|---|---|
| Consumer App | What is the TAM for an AI-powered personal finance app in India? |
| SaaS Product | How large is the Indian SME market for an AI customer-support platform? |
| E-commerce | What is the potential market for educational flashcards in India? |
| Agentic Commerce | What is the market opportunity for AI shopping assistants? |
| General Guesstimation | How many cups of coffee are consumed in Bengaluru every day? |

## 📈 Understanding TAM, SAM & SOM

- **TAM:** The total relevant market opportunity.
- **SAM:** The portion of that market the product or business can serve.
- **SOM:** The portion the business can realistically capture within a defined period.

The agent calculates these using explicit assumptions instead of arbitrary market-share percentages.

For non-commercial estimation problems, it produces a direct quantitative estimate without forcing a TAM/SAM/SOM framework.

## 🚀 How to Use

The skill instructions are defined in [SKILL.md](SKILL.md).

Place this skill in a supported Agent Skills directory and use it with a compatible AI agent.

Start with a prompt such as:

> Help me estimate the TAM, SAM, and SOM for an AI-powered personal finance application in India. Ask me for the assumptions I already know and help estimate the missing inputs.

The agent should guide the conversation, explain its assumptions, and construct the estimate step by step.

## 🧪 Evaluation Status

**Status:** Initial version — testing pending.

Planned evaluations:

1. Consumer application market sizing.
2. B2B SaaS opportunity estimation.
3. General non-commercial guesstimation.
4. Sensitivity testing with revised assumptions.
5. Validation of calculations, units, and scenario consistency.

Evaluation inputs, outputs, and findings will be documented in the repository.

## ⚠️ Limitations

- Results depend on the quality of input assumptions.
- Estimates are not substitutes for independently verified market research.
- Market figures should not be presented as sourced facts unless verified.
- Scenario estimates are not statistical confidence intervals.
- TAM, SAM, and SOM definitions depend on consistent market boundaries, units, and time horizons.

## 👤 Author

**Renganathan Sekar**

Senior Product Manager | AI Products & Agentic Systems

[GitHub](https://github.com/SRenganathan) · 
[LinkedIn](https://www.linkedin.com/in/renganathansekar/)