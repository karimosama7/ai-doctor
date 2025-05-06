# AI-Doctor: Medical Chatbot with Image Analysis

<div align="center">
  <img src="https://via.placeholder.com/150" alt="AI-Doctor Logo" width="200"/>
  <h3>An AI-powered medical image analysis application</h3>
</div>

## 📋 Overview

AI-Doctor is a web application that allows users to upload medical images and ask questions about them. The system leverages advanced AI models through Groq's API to analyze the images and provide informative responses. The application compares outputs from two different large language models, offering users multiple perspectives on their medical image queries.

> **Note**: This application is for educational purposes only and is not intended to replace professional medical advice.

## ✨ Features

- 📤 Simple image upload interface
- 💬 Natural language question input about medical images
- 🤖 Dual AI model analysis for comparison (using LLaMA models)
- 📱 Responsive design for desktop and mobile use
- 🔒 Image validation and error handling

## 🖼️ Screenshots

<div align="center">
  <img src="https://via.placeholder.com/800x400" alt="AI-Doctor Interface" width="800"/>
</div>

## 🛠️ Technology Stack

- **Frontend**: HTML, JavaScript, Tailwind CSS
- **Backend**: Python, FastAPI
- **AI Models**: LLaMA models via Groq API
- **Image Processing**: PIL/Pillow
- **Deployment**: Uvicorn ASGI server

## 📊 Architecture

The application follows a client-server architecture:

1. **Frontend Layer**: Handles user interactions, image uploads, and displays responses
2. **API Layer**: Processes requests, validates images, and communicates with AI services
3. **AI Integration Layer**: Formats data for and communicates with Groq's AI services

<div align="center">
  <img src="https://via.placeholder.com/600x300" alt="Architecture Diagram" width="600"/>
</div>

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- Groq API key

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/karimosama7/ai-doctor.git
   cd ai-doctor
   ```

2. Create and activate a virtual environment:

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.env` file in the root directory with your Groq API key:
   ```
   GROQ_API_KEY=your_api_key_here
   ```

### Running the Application

1. Start the FastAPI server:

   ```bash
   uvicorn app:app --reload
   ```

2. Open your browser and navigate to:
   ```
   http://localhost:8000
   ```

## 📁 Project Structure

```
ai-doctor/
├── app.py            # FastAPI application
├── templates/
│   └── index.html    # Frontend interface
├── .env              # Environment variables (create this)
└── requirements.txt  # Python dependencies
```

## 🧠 How It Works

1. **User Interface**: Users upload a medical image and enter a question about it
2. **Image Processing**: The backend validates and encodes the image
3. **AI Processing**:
   - The application sends the query and image to two different LLaMA models
   - Models analyze the image and generate responses to the query
4. **Response Display**: Both AI responses are displayed side by side for comparison

## 🔄 API Endpoints

| Endpoint            | Method | Description                                               |
| ------------------- | ------ | --------------------------------------------------------- |
| `/`                 | GET    | Serves the main application interface                     |
| `/upload_and_query` | POST   | Processes image uploads and queries, returns AI responses |

## 🧪 Technical Details

### AI Models Used

The application uses the following models through Groq's API:

#### In FastAPI Version:

- `meta-llama/llama-4-scout-17b-16e-instruct`
- `meta-llama/llama-4-maverick-17b-128e-instruct`

### Request Format

The application constructs multimodal requests with both text and image data:

```json
{
  "model": "model_name",
  "messages": [
    {
      "role": "user",
      "content": [
        { "type": "text", "text": "user_query" },
        { "type": "image_url", "image_url": { "url": "base64_encoded_image" } }
      ]
    }
  ],
  "max_tokens": 1000
}
```

## 🔒 Security Considerations

- The application validates uploaded images to prevent malicious file uploads
- API keys are stored in environment variables, not in the code
- Input validation is performed on all user inputs

## 🚧 Future Improvements

- Add user authentication
- Implement result caching for faster responses on similar queries
- Support for more specialized medical imaging formats (DICOM, etc.)
- Integration with additional AI models
- Add detailed medical reference information

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👥 Contributors

- [karim_osama]

## 🙏 Acknowledgments

- [Groq](https://groq.com/) for providing the API access to LLaMA models
- [FastAPI](https://fastapi.tiangolo.com/) for the efficient API framework
- [Tailwind CSS](https://tailwindcss.com/) for the styling framework
