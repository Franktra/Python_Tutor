# Basic Architecture Code for Problem Generation

🏗️ This code snippet demonstrates a simplified example of the basic architecture for generating a coding problem using Flask as the backend framework and React as the frontend framework. It showcases how a backend endpoint can be used to generate a problem and a React component to fetch and display the generated problem.

## Backend Endpoint (Flask)

```python
from flask import Flask, jsonify
import openai

openai.api_key = 'your-api-key'
app = Flask(__name__)

@app.route('/generate-problem', methods=['GET'])
def generate_problem():
    prompt = "Generate a Python coding problem for beginners."
    response = openai.Completion.create(
        engine="text-davinci-002",
        prompt=prompt,
        max_tokens=100
    )
    problem = response.choices[0].text.strip()
    return jsonify({'problem': problem})

if __name__ == '__main__':
    app.run(debug=True)
```

In this Flask application, we define a `/generate-problem` endpoint that uses the OpenAI API to generate a Python coding problem for beginners. The generated problem is returned as a JSON response.

## React Component

```jsx
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function ProblemGenerator() {
    const [problem, setProblem] = useState('');

    useEffect(() => {
        axios.get('/generate-problem')
            .then(response => setProblem(response.data.problem));
    }, []);

    return (
        <div>
            <p>{problem}</p>
            {/* other components for user interaction */}
        </div>
    );
}

export default ProblemGenerator;
```

In this React component, we use the `useState` and `useEffect` hooks to fetch the generated problem from the `/generate-problem` endpoint and update the `problem` state. The fetched problem is then displayed within a `<p>` tag.

---
