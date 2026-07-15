# Prompt Engineering Techniques

## 📌 Quick Navigation

- [Basic Techniques](#basic-techniques)
- [Advanced Techniques](#advanced-techniques)
- [Tool Utilization](#tool-utilization)
- [Meta Prompting](#meta-prompting)
- [Personalization](#personalization)

---

## Basic Techniques

### Zero-Shot Prompting

**Definition:** Asking a foundation model to complete a task with no prior examples, relying solely on its existing knowledge.

**When to use:** When you have confidence in the model's existing knowledge about the domain.

### One-Shot Prompting

**Definition:** Showing the foundation model just one example, allowing it to learn and apply that knowledge to similar situations.

**When to use:** When a single example can clarify the expected format or style.

### Few-Shot Prompting

**Definition:** Providing the foundation model with multiple examples to learn from, which helps it better understand the task and improve its performance.

**When to use:** When you need consistent, high-quality outputs and can provide representative examples.

### Role Prompting

**Definition:** Assigning a persona to the AI to push it to generate more relatable answers.

**Example:**
```
"You are an expert nutritionist and health coach..."
```

**When to use:** When you want responses tailored to a specific expertise or perspective.

---

## Advanced Techniques

### Prompt Chaining

**Definition:** Instead of giving one set of instructions, let AI build context by gradually explaining the task you want to accomplish.

**Process:**

| Step | Description |
|------|-------------|
| **Prompt 1** | Define the general goal: "I want to grow muscles and reduce body weight" |
| **Prompt 2** | Provide specific context: "My age, weight, height, lifestyle, etc. are..." |
| **Prompt 3** | Assign expertise: "You are expert nutritionist and health coach" |
| **Prompt 4** | Add constraints: "Here are my limitations" |

**Result:** AI gradually refines context and responds in a more accurate and relatable manner.

**Why it works:**
- Builds conversational history
- Allows for iterative refinement
- More natural interaction flow
- Better handling of complex tasks

### Chain of Thought Prompting

**Definition:** Making AI think like humans—approaching problems step by step.

**Core Concept:** Guide AI to solve intricate problems one thing at a time, gradually building context as you chat more.

**Key Difference from Prompt Chaining:**
- Focuses on **reasoning steps** within a single prompt
- AI explains its thinking process
- Helps catch and correct logical errors

**Example Use Case:** Building an ERP (Enterprise Resource Planning) app for a company

**Benefits:**
- Improves accuracy on complex tasks
- Makes reasoning transparent and verifiable
- Easier to identify where the model went wrong

### ReAct Prompting (Reasoning + Acting)

**Definition:** AI model uses a reasoning loop of **Think → Plan → Act → Observe** until the solution is achieved.

**The Loop:**

```
Observe → Interpret → Plan → Act → (Back to Observe if needed)
```

**Real-world Example: Restaurant Recommendation**

Prompt: "Recommend me a good restaurant"

AI Reasoning Process:
1. **Observe:** User wants a restaurant recommendation
2. **Think:** Let me check the user's current location and find restaurants within 10km radius
3. **Plan:** Filter by rating, then pick top dishes
4. **Act:** Search for restaurants
5. **Observe:** Here are some delicious dishes
6. **Think:** Oh, but user likes Italian food—let me refine my search
7. **Plan:** Find restaurants that serve Italian food
8. **Act:** Search Italian restaurants
9. **Observe:** Restaurant 1 has great pasta, Restaurant 2 has excellent pizza
10. **Curate:** Present 2 best recommendations to user

**Why it works:**
- Mimics human reasoning
- Iterative refinement leads to better results
- Can adapt based on new information
- Ideal for complex, multi-step tasks

---

## Tool Utilization

### Tool Calling

**Definition:** Tools are external capabilities that an AI model can use to perform actions or access information beyond its built-in knowledge.

**The Relationship:**

```
┌─────────────────┐
│   AI Model      │  (The "Brain")
│ Understands &   │  Generates language
│ Generates Text  │
└────────┬────────┘
         │ Uses
         ↓
┌─────────────────┐
│  Tools/Helpers  │  Function, Database, API,
│ Access External │  CLI, Model, Google Search,
│    Information  │  Application, etc.
└─────────────────┘
```

**Real-world Example:**

Question: "What's the weather in Tokyo right now?"

- **Without Tools:** AI can't answer accurately (knowledge cutoff)
- **With Weather Tool:** AI fetches live data and provides accurate information

### What is a Function?

**Definition:** A function is a specialized tool within the agent's toolbox.

**How it works:**
- Agent knows about available functions
- Agent can use them whenever it determines a function is needed
- Used during the reasoning process

**Example: Coding Agent**

- Has a **compiler function**
- During reasoning, when writing code, it can decide to use the compiler
- Purpose: Verify the written code works correctly

### Can an Agent be a Tool for Another Agent?

**Answer:** Yes!

**Example:**

```
Customer Service Agent
        ↓
   Uses (as a tool)
        ↓
Sentiment Analysis Agent
        ↓
   Purpose: Gauge user satisfaction during interaction
```

**Benefits:**
- Specialization and modularity
- Agents focus on their core competency
- Reusability across multiple systems

### Types of Tools

Tools can be:

- ✅ Functions
- ✅ Databases
- ✅ APIs
- ✅ Command-line programs
- ✅ Other AI models
- ✅ Google Search
- ✅ Application invocations

---

## Meta Prompting

**Definition:** Using AI to create instructions for other AI.

**Use Case Example:**

```
Your Task:
"Create instructions for an AI agent that my customers 
will chat with. Here is my company's information..."

AI Output:
→ Detailed instructions for a customer-service agent
→ Customized for your company's needs
→ Ready to feed to another AI model
```

**When to Use:**
- Creating prompt templates for your team
- Building reusable AI agent instructions
- Standardizing AI behavior across multiple use cases
- Rapidly iterating on agent behavior

**Benefits:**
- **Scalability:** Create instructions for many scenarios quickly
- **Consistency:** Ensures uniform AI behavior
- **Efficiency:** Reduces manual prompt engineering effort
- **Iteration:** Easily refine and improve instructions

---

## Personalization

### Saved Info

**Purpose:** If you want your AI to always craft responses in a particular style

**How it works:**
- Persistent profile information
- AI uses this for every interaction

**Example:**
```
Saved Info: "I am a 36-year-old software engineer working in Sweden"

AI Behavior:
- Writes language suitable for a young software professional
- Refines results for Swedish demographics
- When asked "What movies are running today?", 
  searches Filmstaden (Swedish service) not BookMyShow (Indian service)
```

**Key Characteristic:**
- ✅ Shared across all chats
- ✅ Persistent profile
- ✅ Global personalization

### Gems

**Definition:** A mutually exclusive, context-independent chat with AI. A specialized version of the AI model/agent.

**Example: "Apollo Gem"**

```
Base Agent: Coding Agent

Customization:
  - Language: Java only
  - Style: Domain-Driven Design (DDD)
  - Preferences: Your coding style
  
Result: Apollo Gem
```

**Key Characteristics:**
- ✅ Specialized version of a model/agent
- ✅ Each conversation is brand new (no memory)
- ✅ Context-independent
- ✅ Not shared across chats
- ❌ Unlike saved info

### Saved Info vs. Gems Comparison

| Feature | Saved Info | Gems |
|---------|-----------|------|
| **Scope** | Global, shared across chats | Isolated conversation |
| **Memory** | Persistent across sessions | Fresh start each conversation |
| **Use Case** | Personal/demographic info | Specialized agent versions |
| **Customization Level** | Profile-based | Agent-based |
| **Example** | Your age, location, profession | Java-only coding agent |

---

## 🎯 Prompt Engineering Decision Tree

```
      Start
        ↓
   Do you have examples?
      ↙      ↘
    No        Yes
    ↓          ↓
  Zero-     One or Few?
  Shot      ↙      ↘
           One     Few
           ↓       ↓
        One-Shot Few-Shot
           ↓       ↓
       [Choose based on task complexity]
            ↓
    Need step-by-step reasoning?
        ↙       ↘
      Yes        No
      ↓          ↓
  Chain of     Role
  Thought    Prompting
             or
          ReAct Prompting
             ↓
    Need external tools?
        ↙       ↘
      Yes        No
      ↓          ↓
  Tool Calling  [Done]
      ↓
    [Use appropriate tool]
```

---

## 💡 Quick Tips

1. **Start Simple:** Begin with zero-shot, escalate complexity as needed
2. **Provide Context:** More context usually leads to better responses
3. **Be Specific:** Clear instructions produce better results
4. **Iterate:** Refine prompts based on results
5. **Use Examples:** When possible, provide examples of desired output
6. **Role Assignment:** Sometimes assigning a persona significantly improves responses
7. **Break It Down:** Complex tasks work better when broken into steps
8. **Tool Awareness:** Know what tools are available to your AI agent

---

**Last Updated:** 2026-07-15