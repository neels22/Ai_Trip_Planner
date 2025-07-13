# 🌍 GetSetGO-ai: AI-Powered Travel Planner

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-green.svg)](https://fastapi.tiangolo.com/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.28+-red.svg)](https://streamlit.io/)
[![LangGraph](https://img.shields.io/badge/LangChain-0.3.26+-orange.svg)](https://langchain.com/)




> **Your intelligent travel companion that creates comprehensive, personalized trip plans with real-time data and cost analysis.**

## 🎬 Demo

https://github.com/neels22/Ai_Trip_Planner/blob/main/Demo-video.mov

*Watch how GetSetGO-ai creates comprehensive travel plans with real-time data, weather forecasts, and detailed cost breakdowns.*

## 🚀 What is GetSetGO-ai?

GetSetGO-ai is an advanced AI-powered travel planning application that leverages cutting-edge language models and real-time data to create detailed, personalized travel itineraries. Built with a modern agentic workflow architecture, it provides comprehensive trip planning including attractions, accommodations, dining, activities, transportation, weather forecasts, and detailed cost breakdowns.

### ✨ Key Features

- **🤖 Intelligent AI Agent**: Powered by Groq LLM with agentic workflow for complex reasoning
- **🌤️ Real-time Weather Data**: Current weather and forecasts for any destination
- **🏨 Comprehensive Place Search**: Find attractions, restaurants, activities, and transportation options
- **💰 Smart Expense Calculator**: Detailed cost breakdowns and budget planning
- **💱 Currency Conversion**: Real-time currency conversion for international trips
- **📊 Visual Workflow**: Mermaid graph visualization of the planning process
- **🌐 Dual Interface**: Both FastAPI backend and Streamlit frontend
- **📱 Modern UI**: Beautiful, responsive web interface

## 🏗️ Architecture

The application uses a sophisticated **agentic workflow** built with LangGraph:

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   User Query    │───▶│  AI Agent       │───▶│  Tool Execution │
│   (Streamlit)   │    │  (Groq LLM)     │    │  (Weather,      │
└─────────────────┘    └─────────────────┘    │  Places, etc.)  │
                                              └─────────────────┘
                                                       │
                                                       ▼
                                              ┌─────────────────┐
                                              │  Comprehensive  │
                                              │  Travel Plan    │
                                              └─────────────────┘
```

### Core Components

- **Agent Module**: Orchestrates the planning workflow using LangGraph
- **Tools Module**: Specialized tools for weather, places, calculations, and currency
- **Utils Module**: Helper functions for data processing and API integrations
- **Web Interface**: FastAPI backend + Streamlit frontend

## 🛠️ Available Tools

### 🌤️ Weather Information
- **Current Weather**: Real-time temperature, conditions, and descriptions
- **Weather Forecast**: 5-day weather predictions for trip planning

### 🏛️ Place Search & Discovery
- **Attractions**: Find popular tourist spots and hidden gems
- **Restaurants**: Discover dining options with price ranges
- **Activities**: Adventure sports, cultural experiences, and entertainment
- **Transportation**: Public transport, car rentals, and travel options

### 💰 Financial Planning
- **Expense Calculator**: Total trip cost calculations
- **Hotel Cost Estimator**: Per-night and total accommodation costs
- **Daily Budget Calculator**: Per-day expense planning
- **Currency Converter**: Real-time exchange rates for international trips

## 🚀 Quick Start

### Prerequisites

- Python 3.10 or higher
- API keys for external services (see Configuration section)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/Ai_Trip_Planner-github.git
   cd Ai_Trip_Planner-github
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your API keys
   ```

### Configuration

Create a `.env` file with the following API keys:

```env
# Required for weather data
OPENWEATHERMAP_API_KEY=your_openweathermap_key

# Required for place search (Google Places API)
GPLACES_API_KEY=your_google_places_key

# Required for currency conversion
EXCHANGE_RATE_API_KEY=your_exchange_rate_key

# Required for AI model (Groq)
GROQ_API_KEY=your_groq_key

# Optional: Tavily API for fallback search
TAVILY_API_KEY=your_tavily_key
```

### Running the Application

#### Option 1: Streamlit Interface (Recommended)

```bash
# Start the backend server
python main.py

# In another terminal, start the Streamlit frontend
streamlit run streamlit_app.py
```

Visit `http://localhost:8501` to access the web interface.

#### Option 2: API Only

```bash
python main.py
```

The FastAPI server will be available at `http://localhost:8000`

## 📖 Usage Examples

### Example 1: Beach Vacation Planning
```
"Plan a 7-day trip to Bali, Indonesia with a budget of $2000"
```

**Response includes:**
- Day-by-day itinerary with popular and off-beat locations
- Hotel recommendations with pricing
- Restaurant suggestions with price ranges
- Transportation options and costs
- Weather forecast for the travel dates
- Detailed cost breakdown
- Currency conversion to Indonesian Rupiah

### Example 2: City Exploration
```
"Plan a 3-day weekend trip to Paris, France focusing on art and culture"
```

**Response includes:**
- Museum and gallery recommendations
- Cultural activities and events
- Traditional French restaurants
- Metro and walking routes
- Weather-appropriate activities
- Budget-friendly and luxury options

## 🔧 API Endpoints

### POST `/query`
Submit a travel planning request.

**Request:**
```json
{
  "question": "Plan a 5-day trip to Tokyo, Japan"
}
```

**Response:**
```json
{
  "answer": "Comprehensive travel plan in markdown format..."
}
```

## 🏗️ Project Structure

```
Ai_Trip_Planner-github/
├── agent/                    # Agentic workflow implementation
│   ├── agentic_workflow.py  # Main graph builder
│   └── __init__.py
├── tools/                    # Specialized planning tools
│   ├── weather_info_tool.py      # Weather data
│   ├── place_search_tool.py     # Places and attractions
│   ├── expense_calculator_tool.py # Cost calculations
│   ├── currency_conversion_tool.py # Currency conversion
│   └── arthamatic_op_tool.py    # Mathematical operations
├── utils/                   # Helper utilities
│   ├── model_loader.py      # LLM configuration
│   ├── weather_info.py      # Weather API integration
│   ├── place_info_search.py # Google Places & Tavily
│   ├── expense_calculator.py # Financial calculations
│   ├── currency_converter.py # Exchange rate API
│   └── save_to_document.py  # Document generation
├── prompt_library/          # AI prompts
│   └── prompt.py           # System prompts
├── config/                  # Configuration files
│   └── config.yaml
├── exception/               # Error handling
│   └── exceptiohandling.py
├── logger/                  # Logging utilities
│   └── logging.py
├── main.py                  # FastAPI backend
├── streamlit_app.py         # Streamlit frontend
└── requirements.txt         # Dependencies
```

## 🛠️ Development

### Adding New Tools

1. Create a new tool class in the `tools/` directory
2. Implement the tool methods with proper error handling
3. Add the tool to the `GraphBuilder` class in `agent/agentic_workflow.py`
4. Update the system prompt if needed

### Extending the Agent

The agentic workflow can be extended by:
- Adding new nodes to the LangGraph
- Implementing custom conditions
- Integrating additional data sources
- Enhancing the reasoning capabilities

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

### Development Setup

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **LangChain**: For the powerful LLM framework
- **LangGraph**: For the agentic workflow capabilities
- **Groq**: For the fast and efficient LLM inference
- **Streamlit**: For the beautiful web interface
- **FastAPI**: For the robust backend API

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/yourusername/Ai_Trip_Planner-github/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/Ai_Trip_Planner-github/discussions)
- **Email**: your-email@example.com

---

**Made with ❤️ by the GetSetGO-ai team**

*Transform your travel dreams into detailed, actionable plans with the power of AI!*

