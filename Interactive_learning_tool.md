```python
import openai

openai.api_key = 'your-api-key'

def generate_quiz(question):
    """
    🎯 **Generate Quiz**

    This function takes a question as input and uses OpenAI's text completion API to generate a multiple-choice quiz question.

    :param question: The question for which a quiz question needs to be generated.
    :type question: str
    :return: The generated multiple-choice quiz question.
    :rtype: str
    """

    prompt = f"""
    {question}
    """
    response = openai.Completion.create(
        engine="text-davinci-002",
        prompt=prompt,
        max_tokens=100
    )

    return response.choices[0].text.strip()

# Test the function with a sample question
quiz_question = "Create a multiple-choice question about the basics of Python."
print(generate_quiz(quiz_question))
```

📝 **Description:**

The code snippet above demonstrates the usage of the OpenAI API to generate a multiple-choice quiz question based on a given input question. The `generate_quiz` function takes a question as input and utilizes OpenAI's text completion API to generate a multiple-choice quiz question. The function sends the input question as a prompt to the API and receives a completion as the response. The generated quiz question is then returned.

🔑 **API Key:**

Before using the code, make sure to replace `'your-api-key'` with your actual OpenAI API key. This key is required to authenticate your requests to the OpenAI API.

⚙️ **Function Usage:**

To use the `generate_quiz` function, simply call it with a question as the argument. The function will return a string representing the generated multiple-choice quiz question. You can customize the function and modify the prompt or API parameters to suit your specific requirements.

✅ **Example Output:**

When the code is executed with the provided sample question, it generates a multiple-choice quiz question about the basics of Python.

🔗 **Additional Resources:**

- [OpenAI API Documentation](https://docs.openai.com/)
- [OpenAI Python Library](https://github.com/openai/openai-python)
- [OpenAI Playground](https://play.openai.com/)
