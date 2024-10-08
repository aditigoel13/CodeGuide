<!-- PROJECT LOGO -->
<br />
<div align="center">
  


  <h3 align="center">CodeGuide</h3>

  <p align="center">
    An RAG based LLM app to help with your competitive programming queries 
    <br />
   
    
   
  </p>
</div>




<!-- ABOUT THE PROJECT -->
## About The Project

CodeGuide is an AI-driven assistant aimed at transforming the competitive programming experience. Built on Pathway's advanced LLMApp framework, it integrates seamlessly with Codeforces to provide personalized advice and insights based on users' coding history and current problem sets.


### Built With

The tools used for building this app are:

* [Pathway's LLM App](https://pathway.com/developers/showcases/llm-app-pathway)

* [Streamlit](https://streamlit.io/)

* [Codeforces API](https://codeforces.com/api/)


### UI and API Layer
- **CodeGuide UI:** The user interface where users interact with the system. Users submit queries through this interface.
- **Pathway Restful API:** Acts as the bridge between the UI and the backend services. It processes incoming requests and interacts with various internal components to fetch and return the necessary information.

### Data Collection and Processing
- **Codeforces Handle and API:** The system uses the user's Codeforces handle to fetch historical data of user submissions via the Codeforces API.
- **Cron Job:** A scheduled task that periodically fetches the latest problems from Codeforces to ensure the system has up-to-date information.
- **Document Processing Pipeline:** Fetched documents are split into smaller chunks for efficient processing. These chunks are then processed through the OpenAI Embedding API to generate vector embeddings, which are numerical representations of the text that capture semantic meaning.

### Query Handling and Response Generation
- **User Query:** When a user submits a query, it is processed to generate a vector embedding using the OpenAI Embedding API.
- **KNN Similarity Search:** A K-Nearest Neighbors (KNN) search is performed using the generated embedding to find the most similar documents from the previously stored vector embeddings.
- **Context and Prompt Generation:** The system builds context for the user's query by integrating relevant information from the similarity search and the user's preferred programming language. A prompt is generated using this context, which is then fed into a Large Language Model (LLM) to produce a coherent and relevant response.
- **Output:** The final response, generated by the LLM, is tailored to the user's query and programming preferences and is sent back to the user through the CodeGuide UI.


## Project Impact and Key Aspects

### End-user and Impacted Industry
**End-User:** Competitive programmers, coding enthusiasts, and students seeking to enhance their problem-solving and coding skills.

**Impacted Industry:** Education and Skill Development.

### Key Features
- **Codeforces Integration:** Users can input their Codeforces handle, allowing CodeGuide to retrieve their past submissions and performance data, tailoring the assistance to their specific strengths and areas for improvement.
- **Personalized Coding Assistance:** CodeGuide leverages the user's Codeforces data and the latest Codeforces problem sets as contextual information to provide personalized guidance, explanations, and code examples, addressing the user's specific coding queries.
- **Interactive Experience:** With its conversational interface, CodeGuide offers an engaging and interactive coding experience, allowing users to ask follow-up questions and receive real-time feedback.


<!-- GETTING STARTED -->

## Installation

### Run with Docker

### Prerequisites

Ensure you have Docker and docker compose both latest version installed on your system before proceeding. Docker compose  will be used to build and run the application in a containerized environment. For installation please refer the offcial documneation of docker [Docker Installation Guide](https://docs.docker.com/compose/install/linux/)

- **OpenAI API Key**:
    - To access the OpenAI API, you will need to create an API Key. You can do this by logging into the [OpenAI] (https://openai.com/product) website and navigating to the API Key management page.


### 1. Environment Setup

1. Create a `.env` file in the root directory of your project.
2. Add the following lines to the `.env` file, replacing `{YOUR_OPENAI_KEY}` with your actual OpenAI API key:

   ```env
    OPENAI_API_TOKEN={YOUR_OPENAI_KEY}
    HOST=0.0.0.0
    PORT=8080
    EMBEDDER_LOCATOR=text-embedding-ada-002
    EMBEDDING_DIMENSION=1536
    MODEL_LOCATOR=gpt-4o
    MAX_TOKENS=400
    TEMPERATURE=0.2
   ```

This file will be used by Docker to set the environment variables inside the container.

### 2. Build and Run the Docker Image

With the environment variables set up, you can now build the Docker and run the image for the project.

- Open a terminal or command prompt.
- Navigate to the root directory of your project.
- Execute the following command to build and run the docker:

  ```sh
  docker compose up
  ```

This step compiles your application and its dependencies into a Docker image.


### 3. Access the Application

- Open your web browser.
- Navigate to `localhost:8501` to access the application.

You should see the application's interface if the setup was successful. This confirms that your Docker container is running and the application is accessible.

### 4. Troubleshooting

If you encounter any issues during the setup or execution process, please check the following:

- Ensure Docker is running on your system.
- Verify that the `.env` file contains the correct API key and settings.
- Make sure the Docker image was built successfully without errors.
- Check if the Docker container is running and the ports are correctly mapped.

For further assistance, consult the Docker documentation or seek help from Docker community forums.



<!-- USAGE -->
## Usage



- **Programming Language Preference:** Enhance your learning experience by specifying your preferred programming language. The chatbot will provide code solutions and explanations tailored to your chosen language, facilitating a more effective understanding.



- **Enter your Codeforces Handle:** Unlock insights into your competitive programming journey by entering your Codeforces handle. The chatbot will retrieve your past submissions and performance data, allowing it to provide personalized guidance and recommendations based on your historical progress.


- **Ask your queries:** Engage in a conversational coding experience with our AI-powered chatbot. Ask your coding queries, and the chatbot will analyze your questions, leverage its extensive knowledge base, and provide tailored guidance, explanations, and code examples to help you deepen your understanding of programming concepts and overcome learning challenges.





