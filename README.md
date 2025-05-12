# Chatbot
A Flask application that converts casual text into formal language using Hugging Face's Router API. Features robust retry logic and a fallback mechanism for seamless text formalization. Simple to use with a web interface and API endpoint.
Features
Converts informal text into formal tone.
Utilizes Hugging Face deepseek/deepseek-prover-v2-671b model.
Retry logic for API rate limiting or failures.
Basic local fallback if API fails.
Web interface with a simple HTML form.
Requirements
Install dependencies using pip:

pip install flask requests python-dotenv
Setup
Clone the repository:
git clone https://github.com/your-username/email-formalizer-chatbot.git
cd email-formalizer-chatbot
Create a .env file in the project root and add your Hugging Face API key:
HF_API_TOKEN=your_huggingface_token_here
Run the Flask application:
python app.py
The app will be available at http://localhost:5000.

File Structure
email-formalizer-chatbot/
├── app.py                # Main Flask server logic
├── templates/
│   └── index.html        # Web frontend (user input form)
├── static/               # static assets
|   └── app.js
|   └── style.css          
├── .env                  # Environment variables
└── README.md             # Documentation
API Endpoint
POST /predict
Send a JSON object with the message to be formalized.

Request:

{
  "message": "hey, just checking if u got my last email"
}
Response:

{
  "answer": "Hello, I am inquiring if you have received my previous email."
}
Fallback Handling
If the Hugging Face API fails or returns an error:

The system attempts a minimal string-based formalization (e.g., replacing "hey" with "Hello").
A fallback message is returned along with the adjusted content.
Notes
The model used is deepseek/deepseek-prover-v2-671b accessed via Hugging Face's Router API.
The app supports up to 3 retries for rate-limited or timed-out requests.
Basic text cleanup is applied if the API response is wrapped in markdown or quotes.
