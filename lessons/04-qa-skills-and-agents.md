# Agentic AI Testing with Claude Skills & QA Agents

Now we will create test cases for feature – Transfer Funds in Parabank

But rather than plainly creating test cases – basic

We will give domain knowledge to it first – Specific and Advanced

First create 3 folders inside claude folder – skills, commands, agents

Create a skill - name: banking-qa-knowledge

description: Apply banking QA knowledge – risk categories, boundary values, and test case format for ParaBank features

agent read only name and description and decides if it needs to refer the particular skill.

Explain all the risks there and also test cases format.

Create an agent: qa-analyst-agent.md

It will be the agent for above dedicated skill

The fourth point is instructing the system (or user) to **analyze the given feature** and then **produce a complete output** according to the structure or rules defined by the agent.

In simpler terms, it means:

“Take the feature you’re working on, examine it thoroughly, and generate the full result following the agent’s defined process and parameters (the $ARGUMENTS).”

Essentially, it’s the execution step — where all prior setup (loading instructions, skills, and context) culminates in performing the actual analysis and delivering the final output.

$ARGUMENTS is essentially a **placeholder variable**. It means:

-   When the agent is invoked, you pass in specific inputs (arguments) that describe what feature or task needs to be analyzed.
-   The $ARGUMENTS token will be replaced at runtime with those actual inputs.

For example: If you run the agent with $ARGUMENTS = "Funds Transfer Feature", then step 4 becomes:

“Analyze the Funds Transfer Feature and deliver the complete output as defined by the agent.”

So $ARGUMENTS isn’t literal text — it’s a slot where the **real feature name or parameters** go, telling the agent what to analyze.

So now you will see the different between basic and these test cases both in format and quality.

It is considering different types of risks as well.
