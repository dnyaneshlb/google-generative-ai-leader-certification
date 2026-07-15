# Google Generative AI Leader Certification - Study Notes

## 📚 Overview

Comprehensive study notes for Google Generative AI Leader Certification, organized into easy-to-follow sections.

---

## 📑 Contents

- [Machine Learning Fundamentals](#machine-learning-fundamentals)
- [Deep Learning](#deep-learning)
- [Foundational Models](#foundational-models)
- [Model Limitations & Solutions](#model-limitations--solutions)
- [AI Agents](#ai-agents)
- [Prompting Techniques](#prompting-techniques)
- [Sampling Parameters & Settings](#sampling-parameters--settings)
- [Google Cloud GenAI Capabilities](#google-cloud-genai-capabilities)

---

## Machine Learning Fundamentals

### Three Primary Learning Approaches

Machine learning has three primary learning approaches, each with its own data requirements:

#### 1. **Supervised Learning**

- **Relies on:** Labeled data
- **Goal:** Feed input and expected output enough times so the model can predict outputs for new inputs
- **Example:** Label images as "cat" or "dog" and train the model to recognize animals

#### 2. **Unsupervised Learning**

- **Relies on:** Unlabeled data
- **Goal:** Let the model learn patterns from chaotic data without guidance
- **Insight:** Can reveal unexpected patterns you might never have imagined
- **Example:** Feed order history and let the model predict which products are frequently bought together

#### 3. **Reinforcement Learning**

- **Relies on:** Interaction and feedback
- **Goal:** Agent learns through trial and error, receiving rewards for good behavior and penalties for bad
- **Key Difference:** Instead of being told the correct answer, the agent figures out which actions lead to the highest long-term reward
- **Examples:**
  - Robot learning to navigate a maze (bumping into walls = negative feedback, finding shortcuts = positive feedback)
  - Model learning to play chess by observing other games or playing against other players
  - Teaching a model how to drive in different scenarios
  - **Real-world analogy:** How humans learn in the real world!

---

## Deep Learning

**Definition:** A subset of machine learning that uses artificial neural networks with many layers (hence the word "deep") to learn patterns from large amounts of data.

### How It Works

**Traditional Programming vs. Deep Learning:**

| Aspect | Traditional Programming | Deep Learning |
|--------|------------------------|----------------|
| **Task:** Recognize cats in photos | Define features manually (ears, whiskers, tails) | Provide thousands/millions of labeled cat images |
| **Learning Process** | Hard-coded rules | Automatic feature discovery |
| **Layer 1** | N/A | Simple features (edges, shapes) |
| **Layer 2** | N/A | Complex features (eyes, ears) |
| **Output** | Limited accuracy | Recognizes cats with high accuracy |

---

## Foundational Models

### What is a Foundational Model?

**Analogy:** A foundational model is like a student who has read everything in an entire library—absorbing knowledge from countless books, articles, and websites. This student is good at almost everything!

**Key Characteristics:**
- Heavily use deep learning
- Create all-rounder smart models
- Often augmented with specific data for specialized tasks

### Types of Foundational Models

1. **LLM (Large Language Models)**
   - Generate text and code

2. **Diffusion Models**
   - Generate images, audio, and videos

---

## Model Limitations & Solutions

### Common Limitations

Models have serious limitations:
- **Hallucinations:** Making up false information
- **Bias:** Systematic prejudices
- **Fairness:** Unequal treatment
- **Knowledge Cutoff:** Limited to training data date

### Solutions

#### 1. **Grounding**

**Definition:** Giving AI a "reality check"

**How it works:** Provide the model with access to specific data sources to tether its output to real-world information, reducing the risk of invented content.

#### 2. **Retrieval-Augmented Generation (RAG)**

**Three Phases:**

1. **Retrieval Phase**
   - Use a search engine to find relevant information related to the given prompt

2. **Augmentation Phase**
   - Add the retrieved information to the original prompt

3. **Generation Phase**
   - The AI uses this augmented prompt along with its existing knowledge to generate a response

#### 3. **Prompt Engineering**

**Definition:** Crafting precise prompts to guide the model towards desired outputs

**Characteristics:**
- Refines results by understanding factors that influence model responses
- **Limitation:** Can't conjure information the model hasn't learned

#### 4. **Fine-Tuning Model**

**Definition:** Further training a pre-trained or foundational model on a new dataset specific to your task

**Process:**
- Adjusts the model's parameters
- Makes it more specialized for your needs
- Agent Platform provides tooling to facilitate tuning

**Example:** Fine-tuning a model to write code in Volvo-specific DDD (Domain-Driven Design) style

#### 5. **Humans in the Loop**

**Concept:** Involve humans in the decision-making process for critical tasks

---

## AI Agents

### What is an AI Agent?

**Context:** In typical applications, there are many facets. For example, in a travel booking app:
- Flight booking
- Activity suggestions
- Itinerary planning

These are specific tasks that can be independently performed.

**Solution:** AI Agents

**Definition:** Create agents specialized in performing narrow-scoped activities really well. Agents can work autonomously and collaborate with each other to complete tasks.

**How it works:** Agents use a reasoning loop to deliver results (see Agent Reasoning Loop diagram)

### Types of Agents

#### 1. **Conversational Agents**

- Interact with users to answer questions and engage in dialogue

#### 2. **Workflow Agents**

- Automate complex, multi-step tasks
- **Examples:** Log analysis, anomaly detection

### What is a Tool?

**Definition:** During any phase of reasoning (observe, interpret, plan, act), if an agent needs additional information, it can call a tool.

**Example:** While booking a flight autonomously, a booking agent might need to check the weather at the destination. It can call a weather tool to make an informed decision.

**Tool Characteristics:**
- Can be a function, database, API, command-line program, another model, Google search, or application invocation
- Agents know about their available tools and use them when needed
- **Example:** A coding agent has a compiler function it can use during the reasoning process to verify written code

**Can agents be tools?** **Yes!** A customer service agent can use a sentiment analysis agent as a tool to gauge user satisfaction during an interaction.

---

## Prompting Techniques

### Zero-Shot Prompting

**Definition:** Asking a foundation model to complete a task with no prior examples, relying solely on its existing knowledge.

### One-Shot Prompting

**Definition:** Showing the foundation model just one example, allowing it to learn and apply that knowledge to similar situations.

### Few-Shot Prompting

**Definition:** Providing the foundation model with multiple examples to learn from, which helps it better understand the task and improve its performance.

### Role Prompting

**Definition:** Assigning a persona to the AI to push it to generate more relatable answers.

### Prompt Chaining

**Definition:** Instead of giving one set of instructions, let AI build context by gradually explaining the task you want to accomplish.

**Example:**
```
Prompt 1: "I want to grow muscles and reduce body weight"
Prompt 2: "My age, weight, height, lifestyle, etc. are [specific details]"
Prompt 3: "You are an expert nutritionist and health coach"
Prompt 4: "Here are my limitations"
```

**Result:** AI gradually refines context and responds in a more accurate and relatable manner.

### ReAct Prompting

**Definition:** AI model uses a reasoning loop of "Think → Plan → Act → Observe" until the solution is achieved.

**Example: Recommend a good restaurant**

AI Thoughts:
1. Let me check the user's current location and find restaurants within 10km radius
2. Let me filter by rating
3. Let me pick the top dishes
4. Here are some delicious dishes
5. Oh, but the user likes Italian food—let me find Italian recommendations
6. Let me search restaurants that serve Italian food
7. This pasta in Restaurant 1 looks yummy, this pizza in Restaurant 2 looks scrumptious
8. Curating 2 recommendations and sending to user

### Chain of Thought Prompting

**Definition:** Making AI think like humans—approaching problems step by step.

**Concept:** Guide AI to solve intricate problems one thing at a time, gradually building context as you chat more.

**Example:** Building an ERP app for a specific company

### Tool Calling

**Definition:** Tools are external capabilities that an AI model can use to perform actions or access information beyond its built-in knowledge.

**Analogy:**
- **AI model** = the "brain" that understands and generates language
- **Tool** = a "helper" that lets the AI do specific tasks

**Example:** "What's the weather in Tokyo right now?"
- A language model alone doesn't know the current weather
- It can use a weather tool to fetch live data and then explain it to you

**Types of Tools:**
- Functions
- Databases
- APIs
- Command-line programs
- Other models
- Google Search
- Application invocation

### Meta Prompting

**Definition:** Using AI to create instructions for other AI.

**Example:** Create instructions for an AI agent that your customers will chat with, based on your company details. The AI will create detailed instructions to be fed to another AI.

### Saved Info vs. Gems

#### **Saved Info**

**Purpose:** If you want your AI to always craft responses in a particular style

**Example:** "I am a 36-year-old software engineer working in Sweden"

**Behavior:**
- AI writes language suitable for a young software professional
- Refines results for Swedish demographics
- When asked "What are movies running today?", it won't look in BookMyShow but Filmstaden
- **Shared across chats**

#### **Gems**

**Definition:** A mutually exclusive, context-independent chat with AI. A specialized version of the AI model/agent.

**Example:** Create a gem using a coding agent customized to:
- Write code only in Java
- Follow DDD (Domain-Driven Design) style
- Apply your own coding preferences
- Named "Apollo gem"

**Behavior:**
- Each new conversation is brand new (no memory)
- Unlike saved info

---

## Sampling Parameters & Settings

### Token Count

**Definition:** Controls conversation length

**Key Concepts:**
- A token ≠ a word
- AI can keep only a certain number of tokens in memory
- Every AI model has a **context window** (maximum tokens it can keep "in mind" during a conversation)
- **Rule:** Larger token count = better AI's ability to respond in conversations

### Temperature

**Definition:** Controls how random or predictable the model's next token selection is

**Effect:** Gives creativity and randomness to the model

**How it works:**
- When generating each token, the model assigns probabilities to possible next tokens
- Higher temperature = more randomness = more creative
- Lower temperature = more predictable = more consistent

**Example:** "Capital of France is?"
- With **higher temperature** (higher creativity): Model might pick "banana" instead of "Paris"
- This is why tasks like coding and math need **lower temperature** while creative writing needs **higher temperature**

### Top-K

**Definition:** Controls how many tokens are available for selection of the "next token"

**Example:** If you ask "I drink my coffee with?" and set top-k to 2, the AI will consider only the 2 most likely tokens to select from.

### Top-P (Nucleus Sampling)

**Definition:** Restricts sampling to the set of tokens whose cumulative probability reaches p

**Example:** "I drink my coffee with..."

Tokens with probabilities:
- Milk: 50%
- Sugar: 30%
- Cream: 10%
- Ice: 5%

If you set top-p to 90%, available tokens for selection are those that make up 90% (milk, sugar, cream)

### Output Length

**Definition:** Defines maximum generated text length

### Safety Settings

**Definition:** Filters harmful or inappropriate content

### Comparison: Temperature vs. Top-K vs. Top-P

**Analogy: Ordering Food**

- **Top-K:** "Only show me the top 5 dishes"
- **Top-P:** "Show me enough dishes to cover 90% of what people usually order"
- **Temperature:** "Be conservative and pick the most popular dish" (low) vs. "Be adventurous and try something unusual" (high)

---

## Google Cloud GenAI Capabilities

### **Gemma**
Lightweight, open models for local deployments and specialized AI applications

### **Imagen**
Text-to-image generation

### **Veo**
Video generation using text/image prompts

### **Gemini Products**

- **Gemini Enterprise:** Enterprise-grade Gemini
- **Gemini for Google Workspace:** Integration with Google Workspace
- **Gemini Enterprise Agent Platform:** Build and deploy AI agents at scale
- **Gemini Nano:** Google's most efficient and compact AI model, specifically designed to run on devices

### **NotebookLM**
AI-powered notebook for research and learning

### **Google Cloud Contact Center as a Service**
Contact center solutions with AI capabilities

### **Google AI Studio vs. Vertex AI Studio**

| Feature | Google AI Studio | Vertex AI Studio |
|---------|------------------|------------------|
| **Cost** | Free | Paid |
| **Use Case** | Quick AI prototyping | Production-ready AI applications at scale |
| **Target** | Individuals, rapid experimentation | Enterprises, production deployments |

### **Model Garden**
[To be explored]

### **Grounding with Google Search**
Ground AI models using Google Search for real-time, accurate information

---

## 🎯 Key Takeaways

✅ Understand the three learning approaches and when to use each  
✅ Grasp how foundational models work and their limitations  
✅ Know the techniques to overcome model limitations (RAG, grounding, fine-tuning)  
✅ Master prompting techniques for better AI outputs  
✅ Understand sampling parameters to control AI behavior  
✅ Familiarize yourself with Google Cloud GenAI capabilities  

---

## 🔗 Useful References

- [Temperature vs Top-K vs Top-P Explanation](https://chatgpt.com/share/6a4ccea1-28f8-83eb-8487-8200fb30553a)
- [Sampling Parameters Video](https://youtu.be/9uTasuThkNs?si=qxXxsnvyJWs4PHjB)
- Agent Reasoning Loop (see diagram in repository)

---

**Last Updated:** 2026-07-15