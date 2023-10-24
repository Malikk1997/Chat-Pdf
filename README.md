# Chat-With-Pdf
Upload a Pdf and get answers from it like Chat GPT works.

How I Did this project and a brief summary to understand things better.

1. **Import Statements**: The code begins by importing several Python libraries and modules, including `streamlit` for building the web application's user interface, `dotenv` for loading environment variables from a `.env` file, `pickle` for serializing and deserializing Python objects, `PyPDF2` for working with PDF files, and various modules from the "langchain" and "streamlit_extras" libraries for natural language processing and Streamlit utilities.

2. **Sidebar Contents**: Within the Streamlit app, there's a sidebar section where information about the app is displayed. This includes a title, a brief description of the app and its components, and attribution to the creator.

3. **Function Definitions**: The code defines a Python function named `main()`, which serves as the main logic of the Streamlit app. This function is responsible for handling the user interface, PDF file processing, text splitting, embeddings, question answering, and displaying the results.

4. **`load_dotenv()`**: This function loads environment variables from a `.env` file. It's used to securely store sensitive information like API keys.

5. **User Interface**:
   - The Streamlit app includes a header that displays "Chat with PDF" as the title.
   - It allows users to upload a PDF file using the `st.file_uploader` function.
   - If a PDF file is uploaded, the code extracts the text content from the PDF pages and splits it into smaller chunks. These chunks are used for subsequent processing.

6. **Embeddings and Vector Store**:
   - The code initializes an embeddings object using OpenAI's model.
   - It creates a "VectorStore" using the chunks of text obtained from the PDF. A "VectorStore" is a data structure used for efficient similarity searching.

7. **Embeddings Persistence**:
   - The code checks if embeddings and the vector store have already been saved to disk (as a binary file) with a name corresponding to the PDF file. If so, they are loaded from the disk. This is a performance optimization to avoid recomputing embeddings if they've been processed before.
   - If the embeddings and vector store don't exist on disk, the code computes embeddings using OpenAI and creates a new vector store.

8. **User Input and Question Answering**:
   - The app allows users to enter questions or queries about the PDF content using `st.text_input`.
   - When a user submits a query, the code performs similarity searches on the vector store to find relevant documents.
   - It then uses OpenAI's model to generate responses to the user's queries based on the relevant documents.
   - The responses are displayed on the Streamlit app using `st.write`.

9. **`if __name__ == '__main__':`**: This is the standard way to check if the script is being run as the main program. If so, it calls the `main()` function, which starts the Streamlit app.

The code is a complex Streamlit application that combines various libraries and services to allow users to interact with PDF documents using natural language queries. It involves PDF text extraction, text splitting, embeddings, and question answering powered by OpenAI. The chatbot-like functionality responds to user questions about the PDF content.

Please note that this code assumes the presence of certain Python libraries, environment variables, and additional functionality provided by external libraries (e.g., "langchain"). Additionally, API keys and other sensitive information are expected to be provided in the environment variables for security purposes.
