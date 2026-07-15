Multimodal means?




Machine learning has three primary learning approaches: supervised, unsupervised, and reinforcement learning, each with its own data requirements.
Supervised models rely on labeled data.
    Goal is to feed input and expected output enough number of times so that model should predict the output for given input.
    eg. label images with cat, dog, etc and train model to recognize the animals.
Unsupervised models work with unlabeled data
    Dont label the data, rather let model learn from chaotic data and learn to find the patterns. It can bring insights you might have never imagined.\
    e.g. feed order history and let model predict the products frequently bought together
Reinforcement learning learns through interaction and feedback.
    Imagine a robot learning to navigate a maze. It starts with no knowledge of the maze's layout.
    As it explores and interacts with the maze, it collects data—bumping into walls (negative feedback) or finding shortcuts (positive feedback).
    Through this process of trial and error, the algorithm learns which actions lead to the best outcomes.
    You reward good behavior and discourage bad behavior.
    e.g. model learning to play chess by looking at other chase games/playing with other player
    Another example is to teach model how to drive car in different scenarios
    This is how we humans learn in real world, by the way.



Deep Learning
    its subset of ML
    uses artificial neural networks with many layers (hence the word “deep”) to learn patterns from large amounts of data

    For example, if you want a computer to recognize cats in photos:
    * With traditional programming, you’d have to define features like ears, whiskers, and tails.
    * With deep learning, you provide thousands or millions of labeled cat images. The model learns simple features (edges and shapes) in early layers,
    more complex features (eyes and ears) in middle layers, and finally recognizes a cat in the deepest layers.

Foundational models
    An intelligent model often based on foundational model. A foundational model is like a student who has read everything in an entire library,
    absorbing knowledge from countless books, articles, and websites. He is good at almost everything.
    We often then augment foundational model with specific data.

    They heavily use deep learning to make all-rounder smart model.

    Types of foundational models
    LLM : generate text and code
    Diffusion models : generate images, audio, videos

    sidenote: what is meant by diffusion? ask AI


Models have some serious limitations like hallucinations, bias, fairness, knowledge cutoff etc.
Techniques to overcome -
    Grounding :
        It's like giving AI a reality check.
        By providing the model with access to specific data sources, we tether its output to real-world information, reducing the risk of invented content.

    Retrieval-augmented generation (RAG) :
        One of the way to ground the model is RAG.
        Retrieval - uses a search engine to find relevant information related to given prompt.
        Augmentation - The retrieved information is then added to the prompt given to the AI. This is the augmentation phase.
        Generation - The AI then uses this augmented prompt, along with its existing knowledge, to generate a response. This is referred to as the generation phase.

    Prompt engineering:
        This involves crafting precise prompts to guide the model towards desired outputs.
        It refines results by understanding the factors that influence a model's responses.
        However, prompting is limited by the model's existing knowledge; it can't conjure information it hasn't learned.

    Fine-tuning model :
        Tuning involves further training a pre-trained or foundation model on a new dataset specific to your task.
        This process adjusts the model's parameters, making it more specialized for your needs. Agent Platform provides tooling to facilitate tuning.
        e.g. fine-tuning model to write code in volvo specific DDD style.

    Humans in the loop : yes



What is AI agent?
In typical application, there are many facets. For example, in. travel booking app, we need flight booking, activity suggestion,
itinerary planning etc.
These are specific tasks that can be independently performed.
Comes Ai agent.
We can create agent that is specialized in performing these narrow scoped acitvities really well. Agent can work autonomously and collaborate with each other to complete task.
Agent works using a reasoning loop to deliver results. see @Agent Reasoning Loop.png.

Types of agents?
conversational agents:  they interact with users to answer questions and engage in dialogue.
workflow agents:  they automate complex, multi-step tasks like log analysis, anomaly detection etc


What is tool?
Agent works using a reasoning loop to deliver results. see @Agent Reasoning Loop.png.
During any phase of reasoning(observe, interpret, plan, Act) if agent needs any more information it can call a tool.
e.g. While booking a flight autonomously, booking agent might need a check weather info of the destination. It can call a weather tool to make informed decision.




Prompting Techniques
Zero-shot prompting :  is like asking a foundation model to complete a task with no prior examples, relying solely on its existing knowledge.
One-shot prompting : involves showing the foundation model just one example, allowing it to learn and apply that knowledge to similar situations.
Few-shot prompting :  provides the foundation model with multiple examples to learn from, which helps it better understand the task and improve its performance.

Role Prompting : Assigning a persona to the AI to push it to generate more relatable answers.

Prompt chaining : Instead of giving one set of instructions, you let AI build context by gradually explaining the task
you want to accomplish.
prompt1 - I want to grow muscles and reduce body weight
prompt2 - my age, weight, height, lifestyle etc are this and this
prompt3 - You are expert nutritionist and health coach
prompt4 - here are my limitations
Here you gradually refined the context and AI responds in more accurate and relatable manner.


Saved info vs Gems
    If you want your AI to always craft reponses for perticular style then you can save it and AI will always respect it.
    e.g. I am 36 year old software engineer working in sweden.
    With this saved info, AI will write language suitable for a young software professional. It will refine results for Swedish demographic.
    If you ask, "what are movies running today?", it wont look in bookmyshow but filmstaden.
    Remember, the saved info is shared across chats.

    On the other hand, gems is a mutually exclusive context independent chat with AI. The gem is specialised version of
    the AI model/agent.
    e.g. You can create a gem using codeing agent and customise it to write code only in java, DDD style with your own coding preferences. It becomes Apollo gem.
    Each new conversation with a gem is brand-new conversation without any memory, unlike saved info.



Temperature vs top-k vs top-p
https://chatgpt.com/share/6a4ccea1-28f8-83eb-8487-8200fb30553a

Remember, AI agents works in tokens and they choose the next token based on probability.
There can many next tokens to select from to complete given task.
This is where  these setting knobs comes into play to define how the AI model will behave.
see - https://youtu.be/9uTasuThkNs?si=qxXxsnvyJWs4PHjB



Reinforcement learning?
agent learns by interacting with an environment, receiving rewards or penalties based on its actions.
Instead of being told the correct answer for every situation, the agent figures out which actions lead to the highest long-term reward through trial and error.
e.g we all humans do RL all our life. For some decisions we get rewards while other teaches us to follow right path.

Supervised learning?
It's like teaching AI agent what is correct, poking him in right directions all the time. It can be done by giving the labelled datasets, structured curated information etc.
e.g. Give a list of spam emails so AI can learn how spam looks like.

Unsupervised learning?
The model is given unlabeled data and must discover patterns, relationships, or structures on its own
Unlike supervised learning, there are no correct answers provided during training.

Imagine you have a basket of mixed fruits, but none are labeled.
* In supervised learning, someone tells you which ones are apples, oranges, and bananas.
* In unsupervised learning, you’re simply asked to organize the fruits based on similarities like color, size, and shape. You discover the groups yourself.



Sampling Parameters and Settings
    Token count :
        Controls conversation length. A token is != word. AI can keep only certain number of tokens in memory.
        Every AI model has a context window, which is the maximum number of tokens it can keep “in mind” during a conversation.
        Larger the token count, better is AI's ability to respond in conversations.
    Temperature
        controls how random or predictable the model’s next token selection is.
        it gives creativity and randomness to model.
        When generating each token, the model doesn’t usually think “there is only one correct next word.” Instead, it assigns probabilities.
        e.g. capital of france is ?
        In this example, if we keep higher temperature(higher creativity) model might pick answer as "banana".
        That is the reason, tasks like coding, math needs lower temperature(lower randomness) while creative writing needs higher temperature.
    top-k
        controls how many tokens will be available for selection of "next token"
        If you ask "I drink my coffee with?" and set top-k to 2 then AI will consider only 2 tokens to select next token from.
    top-p
        Restricts sampling to the set of tokens whose cumulative probability reaches p.
        e.g.I drink my coffee with.....
        The tokens wih probability are
        milk 50%, sugar 30%, cream 10%, ice 5%
        If I set top-p to 90% then available tokens for selection are those that make 90%(milk, sugar, cream)
    Output length
        Filters harmful or inappropriate content
    Safety settings
        Defines maximum generated text length.


top-k vs top-p?
    Imagine you’re ordering food:
    * Top-k: “Only show me the top 5 dishes.”
    * Top-p: “Show me enough dishes to cover 90% of what people usually order.”
    * Temperature: “Be conservative and pick the most popular dish” (low) vs. “Be adventurous and try something unusual” (high).

