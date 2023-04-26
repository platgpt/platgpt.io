# Prompt Engineering

**Prompts** - Instructions and context passed to a language model to achieve a desired task.

**Prompt engineering - P**ractice of developing and optimizing prompts to efficiently use language models(LMs). It is a useful skill for developer productivity.

## Elements of a Prompt

- Instruction - a specific task or instruction you want the model to perform
- Context - can involve external information or additional context that can steer the model to better responses
- Input Data - is the input or question that we are interested to find a response for
- Output Indicator - indicates the type or format of the output.

## ****LLM**** settings

- **Temperature** - Entropy (proxy for creativity, lack of predictability), increasing the weights of the other possible tokens. Temp of 0 means same response every time. Lower the temperature (ex: fact-based QA) the more deterministic the results. Increasing temperature (ex: poem generation) could lead to more randomness encouraging more diverse or creative outputs. We are essentially increasing the weights of the other possible tokens.
    
    ```jsx
    [temperature=0.8]
    ```
    
    The default values for ChatGPT is 1.0.
    
- **Top_p** - Similarly with Temperature. Distribution of probably of common tokens. 1.0 means "use all tokens in the vocabulary" while 0.5 means "use only the 50% most common tokens.
    
    ```jsx
    [top_p=0.9]
    ```
    
    The default values for ChatGPT is 0.9.
    

The general recommendation is to alter one, not both. 

## Prompting tasks

- Text Summarization
- Question Answering
- Text Classification
- Role Playing
- Code Generation
- Reasoning

## Advanced prompting techniques

Designed to improve performance on complex tasks:

- Few-shot prompts - Provide exemplars in prompts to steer the model towards better performance.
- Chain-of-thought (CoT) prompting - Combine reasoning in exemplars for better results.
- Self-Consistency - Reduce bias, increase the accuracy and consistency of the model.
- Knowledge Generation Prompting
    - Generate a summary of a specific article by providing it with a prompt that focuses on a particular aspect of the article.
- ReAct
    - Customer service chatbots - ReAct could be used to automate the process of answering customer inquiries through a chatbot. The LLMs would analyze the customer's question and generate a sequence of actions that the chatbot could take to respond to the customer.

## Zero-Shot CoT

- Add "Let's think step by step" to the original prompt

## Program-aided Language Model (PAL)

Sometimes CoT (Chain-of-thought) is not enough as it depends only on the generated text from the model:

- Use LLM to generate programs as intermediate step

## **Data-Augmented Generation**

- Fetching relevant data
- Augmenting prompts with the retrieved data as context

## Model Safety

****Adversarial Prompting****

- Prompt Injection - Hijack an LM’s output
- Prompt Leaking - Leak secrets, PII
- Jailbreaking - Bypass moderation

**Defense Tactics**

- Add Defense in the Instruction
- Parameterizing Prompt Components - Instructions separated from inputs
- Quotes and Additional Formatting - Using JSON encoding plus Markdown headings for instructions.
- Adversarial Prompt Detector

**Summary**: Don’t use instruction-tuned models in production on untrusted input. Either write k-shot prompt for a non-instruct model, or create  own fine-tune one. ChatGPT has already some guardrails in place, which also prevents certain behaviors that are desired but not possible given the constraints.

## Reference

[https://www.promptingguide.ai](https://www.promptingguide.ai/)

[https://www.youtube.com/watch?v=dOxUroR57xs](https://www.youtube.com/watch?v=dOxUroR57xs)