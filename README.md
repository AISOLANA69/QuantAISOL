AI Quant App (based on AI Getting Started template)
CA:

![Your Quantitative AI Analyst (1)](https://github.com/user-attachments/assets/fb7cf129-428d-47d4-8013-d0de112ecf3d)

This is a tutorial stack to create and host AI quants that you can interact with through a browser or SMS. The app lets you define the personality and backstory of your quant and leverages a vector database with similarity search to enhance conversational depth. It includes conversational memory by queuing interactions and integrating them into prompts.

The app currently hosts quants on both ChatGPT and Vicuna, running on Replicate.

Use Cases for AI Quants
AI quants are versatile tools that can serve various purposes, including:

Financial analysis and modeling: Providing insights, forecasts, and explaining complex concepts.
Note: Any advice or insights provided by the AI quant should be considered non-financial advice and used for educational or exploratory purposes only. Always consult a certified financial advisor for professional guidance.

Coaching: Tailored advice in trading or investing strategies.
Education: Teaching quantitative concepts or market dynamics.
Entertainment: Simulating financial decision-making.
You can adapt the quant to your specific needs by customizing its backstory and selecting the language model that powers it.

Overview
💻 Stack
🧠 Quickstart
🚀 How does this work?
👤 Adding/modifying quants
👩‍💻 How to contribute
🐍 Python support
💽 Exporting your quant to Character.ai
Stack Components
The app is built on the AI Getting Started Stack:

Auth: Clerk
App logic: Next.js
VectorDB: Pinecone / Supabase pgvector
LLM orchestration: Langchain.js
Text model: OpenAI, Replicate (Vicuna13b)
Text streaming: AI SDK
Conversation history: Upstash
Deployment: Fly.io
Text interactions: Twilio
Quickstart Guide
Get started with a local deployment of AI quants by following these steps:

1. Fork and Clone Repo
Fork the repository to your GitHub account, then run:

bash
Copy code
git clone git@github.com:[YOUR_GITHUB_ACCOUNT_NAME]/quant-app.git
Alternatively, use GitHub Codespaces for quicker setup:

Click "Code" → "Codespaces" → "+".
2. Install Dependencies
bash
Copy code
cd quant-app
npm install
3. Fill Out Secrets
Copy the example environment file and configure it:

bash
Copy code
cp .env.local.example .env.local
Add API keys for Clerk, OpenAI, Replicate, Pinecone, or Supabase (optional).
4. Generate Embeddings
Prepare your quant for interaction by generating embeddings:

bash
Copy code
npm run generate-embeddings-pinecone # if using Pinecone
npm run generate-embeddings-supabase # if using Supabase
5. Run the App Locally
bash
Copy code
npm run dev
Access the app in your browser at http://localhost:3000.

6. Deploy the App
Deploy your quant to Fly.io with:

bash
Copy code
fly launch
fly scale memory 512
fly deploy --ha=false
Adding/Modifying Quants
To customize or create new AI quants:

Add a JSON entry in quants.json.
Define the quant’s description and backstory in a .txt file under the quants/ directory.
Each quant includes:

A preamble with core details.
Seed chat to establish its conversational tone.
Optional extended backstory for richer interactions.
Export to Character.ai
Easily migrate your AI quant to Character.ai:

bash
Copy code
npm run export-to-character [QUANT_NAME] [MODEL_NAME] [USER_ID]
This generates configuration files for Character.ai.

Shortcomings
Some current limitations:

No persistent UI for chat history.
Vicuna’s cold start issue causes delays.
Minimal error reporting for backend issues.
Manual clearing of Upstash message history is required.
Contributions
Contribute by opening pull requests or issues, or explore the Python implementation for command-line quant interactions.
