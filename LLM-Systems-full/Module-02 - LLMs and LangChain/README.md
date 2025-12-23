# Module 2: LLMs and LangChain

## Overview
This module provides a comprehensive introduction to Large Language Models (LLMs) and how to use them with LangChain for building intelligent applications.

## Course Information
- **Course**: LangChain and Vector Databases in Production
- **Instructor**: ActiveLoop
- **Module**: 2 - LLMs and LangChain

## Contents

### Intro_to_LLMs.ipynb
A complete Jupyter notebook covering:

#### Theory
1. **What are Large Language Models** - Fundamental concepts
2. **How LLMs Work** - Tokenization, embedding, and prediction
3. **Common Use Cases** - Real-world applications
4. **Limitations** - Important constraints to understand

#### Practical Examples
1. **Direct LLM Invocation** - Basic text generation
2. **Token Counting** - Understanding token usage
3. **Prompt Templates** - Reusable prompt patterns
4. **Few-shot Prompting** - Teaching by example
5. **Chaining** - Combining prompts with LLMs
6. **Sequential Chains** - Multi-step workflows
7. **Text Summarization** - Condensing long texts
8. **Text Translation** - Multi-language support
9. **Question Answering** - Context-aware responses
10. **Temperature Control** - Managing output randomness
11. **Output Parsing** - Structured output extraction
12. **Chat Prompts** - Conversation interfaces
13. **Conversation Memory** - Maintaining context

## Setup Requirements

### Prerequisites
- Python 3.8 or higher
- Ollama installed locally ([Download](https://ollama.ai))
- qwen3:4b model pulled in Ollama

### Install Ollama Model
```bash
ollama pull qwen3:4b
ollama serve
```

### Install Python Dependencies
```bash
pip install langchain langchain-community langchain-core python-dotenv tiktoken
```

### Environment Setup
Create a `.env` file in the project root:
```
OLLAMA_HOST=http://localhost:11434
```

## Why Ollama Instead of OpenAI?

✓ **Free** - No API costs
✓ **Local** - All processing happens on your machine
✓ **Private** - Your data never leaves your computer
✓ **Fast** - Optimized for local inference
✓ **Open Source** - Full control and transparency

## Running the Notebook

1. Ensure Ollama is running:
   ```bash
   ollama serve
   ```

2. Open the notebook in Jupyter:
   ```bash
   jupyter notebook Intro_to_LLMs.ipynb
   ```

3. Run cells sequentially to understand each concept

## Key Concepts

### Large Language Models (LLMs)
- Neural networks with billions of parameters
- Trained on massive text datasets
- Predict next token based on context
- Can perform multiple tasks without retraining

### Tokens
- Basic units of text (words or word parts)
- LLMs process text as sequences of tokens
- Token counting helps estimate resource usage
- Important for understanding model capacity

### Prompts
- Instructions or questions for the LLM
- Quality of prompts directly affects output quality
- Templates allow reusable prompt patterns
- Few-shot examples improve performance

### Chains
- Combinations of prompts and LLMs
- Enable complex multi-step workflows
- Can be sequential or parallel
- Support memory and state management

### Temperature
- Controls randomness of output (0.0 to 1.0+)
- Lower (0.1-0.3): Deterministic, factual
- Medium (0.5-0.7): Balanced responses
- Higher (0.8-1.0): Creative, varied

## Common Patterns

### 1. Simple Generation
```python
response = llm.invoke("Your prompt here")
```

### 2. With Prompt Template
```python
prompt = PromptTemplate(template="...", input_variables=[...])
chain = prompt | llm
response = chain.invoke({...})
```

### 3. With Output Parsing
```python
chain = prompt | llm | output_parser
result = chain.invoke({...})
```

### 4. Sequential Processing
```python
chain = (
    prompt1 | llm | parser1 | 
    prompt2 | llm | parser2
)
result = chain.invoke({...})
```

## Best Practices

1. **Start Simple**: Master basic patterns before complex workflows
2. **Test Prompts**: Experiment with different phrasings
3. **Monitor Output**: Always validate LLM responses
4. **Use Templates**: Reuse prompts for consistency
5. **Error Handling**: Implement fallbacks for failures
6. **Token Management**: Monitor usage, especially for long texts
7. **Temperature Tuning**: Adjust based on task requirements

## Troubleshooting

### Connection Error
- Ensure Ollama is running: `ollama serve`
- Check OLLAMA_HOST environment variable
- Verify localhost:11434 is accessible

### Model Not Found
- Pull the model: `ollama pull qwen3:4b`
- Verify model is in Ollama: `ollama list`

### Slow Responses
- Check system resources (CPU/RAM)
- Reduce temperature for faster responses
- Use shorter prompts when possible

### Memory Issues
- Restart Ollama service
- Clear conversation memory between sessions
- Process large texts in batches

## Further Learning

### Related Topics
- Vector Databases (Module 3)
- Embeddings and Semantic Search
- RAG (Retrieval Augmented Generation)
- Agents and Tool Use
- Fine-tuning and Prompt Engineering

### Resources
- [LangChain Documentation](https://python.langchain.com/)
- [Ollama Documentation](https://ollama.ai/)
- [Hugging Face Hub](https://huggingface.co/)
- [ActiveLoop Docs](https://docs.activeloop.ai/)

## Notes

- All code examples use Ollama qwen3:4b locally
- No API keys are required
- Internet connection is optional (after model download)
- Responses may vary due to temperature and randomness
- Model is quantized at 4B parameters for efficiency

---

**Last Updated**: December 2024
**Status**: Complete and Ready to Use ✓
