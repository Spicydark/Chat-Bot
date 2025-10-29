# Chat-Bot - AI-Powered Multi-Feature Application

A full-stack application that leverages OpenAI's powerful AI models to provide three distinct features: intelligent chat interactions, AI-powered image generation, and personalized recipe creation. Built with Spring Boot and React, this application demonstrates the integration of cutting-edge AI capabilities into a modern web application.

## 🌟 Features

### 1. **AI Chat Assistant**
- Interactive conversational AI powered by OpenAI's GPT models
- Real-time responses to user queries
- Support for GPT-4o model with customizable parameters
- Natural language processing for intelligent conversations

### 2. **AI Image Generator**
- Generate high-quality images from text descriptions using DALL-E 2
- Customizable image parameters:
  - Quality settings (HD or standard)
  - Multiple image generation (up to n images)
  - Adjustable dimensions (width and height)
- Visual grid display for generated images
- Direct integration with OpenAI's image generation API

### 3. **Recipe Generator**
- Create personalized recipes based on available ingredients
- Specify cuisine preferences (Italian, Chinese, Mexican, etc.)
- Accommodate dietary restrictions (vegetarian, vegan, gluten-free, etc.)
- Receive detailed recipes including:
  - Recipe title
  - Complete ingredient list
  - Step-by-step cooking instructions

## 🏗️ Technology Stack

### Backend
- **Framework**: Spring Boot 3.3.2
- **Java Version**: 17 (compiled with Java 21)
- **AI Integration**: Spring AI 1.0.0-M1
- **OpenAI Integration**: Spring AI OpenAI Starter
- **Build Tool**: Maven
- **API Style**: RESTful

### Frontend
- **Framework**: React 18.3.1
- **Language**: JavaScript
- **Build Tool**: Create React App (react-scripts 5.0.1)
- **HTTP Client**: Fetch API
- **Testing**: Jest, React Testing Library

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
- **Java 17** or higher (Java 21 recommended)
- **Node.js** (v14 or higher) and **npm**
- **Maven** (for backend build)
- **OpenAI API Key** - [Get one here](https://platform.openai.com/api-keys)

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/Spicydark/Chat-Bot.git
cd Chat-Bot
```

### 2. Backend Setup (Spring Boot)

#### Configure OpenAI API Key

You need to set your OpenAI API key as an environment variable:

**On Linux/macOS:**
```bash
export MY_APP_KEY=your_openai_api_key_here
```

**On Windows (Command Prompt):**
```cmd
set MY_APP_KEY=your_openai_api_key_here
```

**On Windows (PowerShell):**
```powershell
$env:MY_APP_KEY="your_openai_api_key_here"
```

Alternatively, you can modify the `application.properties` file in `ChatBot/src/main/resources/`:
```properties
spring.application.name=SpringAiDemo
spring.ai.openai.api-key=your_openai_api_key_here
```

#### Build and Run the Backend

Navigate to the backend directory and run:

```bash
cd ChatBot
./mvnw clean install
./mvnw spring-boot:run
```

The backend server will start on `http://localhost:8080`

### 3. Frontend Setup (React)

Open a new terminal window and navigate to the frontend directory:

```bash
cd ChatBot-React
npm install
npm start
```

The React application will start on `http://localhost:3000` and automatically open in your browser.

## 🎯 Usage

Once both backend and frontend are running:

1. **Open your browser** and navigate to `http://localhost:3000`
2. **Select a feature** using the tab buttons at the top:
   - **Image Generator**: Enter a text prompt to generate images
   - **Ask AI**: Have a conversation with the AI assistant
   - **Recipe Generator**: Input ingredients and preferences to get recipe suggestions

### Using Each Feature

#### Image Generator
1. Click on the "Image Generator" tab
2. Enter a descriptive prompt (e.g., "A serene mountain landscape at sunset")
3. Click "Generate Image"
4. Wait for the AI to generate your image(s)

#### Ask AI
1. Click on the "Ask AI" tab
2. Type your question or prompt
3. Click "Ask AI"
4. Receive an intelligent response from the AI

#### Recipe Generator
1. Click on the "Recipe Generator" tab
2. Enter available ingredients (comma-separated)
3. Specify cuisine type (optional)
4. Add dietary restrictions (optional)
5. Click "Create Recipe"
6. Get a detailed recipe tailored to your inputs

## 🔌 API Endpoints

The backend exposes the following REST endpoints:

### Chat Endpoints
- **GET** `/ask-ai?prompt={prompt}`
  - Simple chat interaction with default settings
  - Returns AI-generated text response

- **GET** `/ask-ai-options?prompt={prompt}`
  - Chat interaction with custom GPT-4o settings
  - Uses temperature 0.4 for more focused responses

### Image Generation
- **GET** `/generate-image?prompt={prompt}&quality={quality}&n={count}&width={width}&height={height}`
  - **Parameters**:
    - `prompt` (required): Text description of desired image
    - `quality` (optional, default: "hd"): Image quality
    - `n` (optional, default: 1): Number of images to generate
    - `width` (optional, default: 1024): Image width in pixels
    - `height` (optional, default: 1024): Image height in pixels
  - Returns: Array of image URLs

### Recipe Generation
- **GET** `/recipe-creator?ingredients={ingredients}&cuisine={cuisine}&dietaryRestriction={restriction}`
  - **Parameters**:
    - `ingredients` (required): Comma-separated list of ingredients
    - `cuisine` (optional, default: "any"): Preferred cuisine type
    - `dietaryRestriction` (optional): Dietary restrictions to consider
  - Returns: Detailed recipe as formatted text

## 📁 Project Structure

```
Chat-Bot/
├── ChatBot/                    # Spring Boot Backend
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/ai/SpringAiDemo/
│   │   │   │   ├── SpringAiDemoApplication.java    # Main application class
│   │   │   │   ├── GenAIController.java            # REST API controller
│   │   │   │   ├── ChatService.java                # Chat functionality
│   │   │   │   ├── ImageService.java               # Image generation
│   │   │   │   ├── RecipeService.java              # Recipe creation
│   │   │   │   └── WebConfig.java                  # CORS configuration
│   │   │   └── resources/
│   │   │       └── application.properties          # Configuration
│   │   └── test/                                   # Test files
│   └── pom.xml                                     # Maven dependencies
│
└── ChatBot-React/              # React Frontend
    ├── src/
    │   ├── components/
    │   │   ├── ChatComponent.js                    # Chat UI component
    │   │   ├── ImageGenerator.js                   # Image generation UI
    │   │   └── RecipeGenerator.js                  # Recipe generation UI
    │   ├── App.js                                  # Main application component
    │   ├── App.css                                 # Application styles
    │   └── index.js                                # React entry point
    ├── public/                                     # Static assets
    └── package.json                                # npm dependencies
```

## 🔧 Configuration

### Backend Configuration
The backend can be configured through `ChatBot/src/main/resources/application.properties`:

```properties
spring.application.name=SpringAiDemo
spring.ai.openai.api-key=${MY_APP_KEY}
```

### CORS Configuration
CORS is configured in `WebConfig.java` to allow requests from `http://localhost:3000` (the React frontend).

## 🧪 Testing

### Backend Tests
```bash
cd ChatBot
./mvnw test
```

### Frontend Tests
```bash
cd ChatBot-React
npm test
```

## 🐛 Troubleshooting

### Common Issues

**Issue**: Backend fails to start with "API key not found" error
- **Solution**: Ensure the `MY_APP_KEY` environment variable is set correctly with your OpenAI API key

**Issue**: Frontend cannot connect to backend
- **Solution**: Verify the backend is running on port 8080 and CORS is properly configured

**Issue**: Image generation fails
- **Solution**: Check your OpenAI API key has access to DALL-E models and you have sufficient credits

**Issue**: Maven build fails
- **Solution**: Ensure you're using Java 17 or higher. Run `java -version` to check

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Commit your changes (`git commit -m 'Add some amazing feature'`)
5. Push to the branch (`git push origin feature/amazing-feature`)
6. Open a Pull Request

## 📝 License

This project is open source and available under the MIT License.

## 🙏 Acknowledgments

- [OpenAI](https://openai.com/) for providing the AI models
- [Spring AI](https://spring.io/projects/spring-ai) for the Spring Boot AI integration
- [Create React App](https://create-react-app.dev/) for the React boilerplate

## 📧 Contact

For questions or feedback, please open an issue on the GitHub repository.

---

**Note**: This application uses OpenAI's API which is a paid service. Please be aware of the costs associated with API usage, particularly for image generation which can be expensive.
