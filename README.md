# Chatbot
This code implements a Flask application that serves as a chatbot capable of answering user queries from any documents. It uses Langchain, an AI language model, for generating responses to user queries. Additionally, when a user requests the chatbot to call them, a conversational form is presented to collect the user's name, phone number, and email address.

Here's a breakdown of the code:

Setting up Flask and Environment:

The Flask framework is imported to create the web application.
Necessary libraries are imported, including VectorStoreIndex from llama_index.core for document indexing and OpenAI for using the Langchain language model.
The OpenAI API key is set using the os.environ function to enable access to the Langchain API.
Constructing the Index:

The construct_index function reads text documents from a specified directory path and constructs an index using VectorStoreIndex. This index is used to retrieve relevant information when the user asks queries.
Initializing Langchain:

The Langchain instance is created to interact with the OpenAI language model.
Collecting User Information:

The collect_user_info function is responsible for gathering user information through a form. It validates the provided information (name, phone number, and email) using regular expressions.
Calling the User:

The call_user function uses Twilio to initiate a call to the user. It sets up the Twilio client using the account SID and authentication token. The function then creates a call using Twilio's client.calls.create method, specifying the recipient's phone number, the Twilio phone number as the caller ID, and a URL containing instructions for the call (in this case, a TwiML document).
Routing and Request Handling:

The / route renders the main page (home.html), where the user can interact with the chatbot.
The /query route handles user queries submitted through a form. If the user requests a call, it renders the user information form (user_info.html).
The /call route is triggered when the user submits the user information form. It invokes the collect_user_info function to gather the user's information and initiate the call using Twilio.
Running the Application:

The app.run() method starts the Flask application in debug mode.
This code fulfills the requirements of building a chatbot capable of answering user queries from documents and incorporating a conversational form to collect user information for initiating calls. It leverages Langchain for natural language processing and Twilio for making phone calls.





