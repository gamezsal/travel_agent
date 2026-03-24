# README: Travel Agent

This project is an AI-powered travel planning assistant built using the **Agent Development Kit (ADK)**. The agent is designed to help users plan complete trips by searching for flights and hotels and calculating comprehensive budgets.

## Project Overview
The agent, named **travel_agent**, acts as a helpful travel specialist. It uses a multi-tool workflow to provide users with a seamless planning experience:
1.  **Search Flights:** Finds available flight options based on destination and date.
2.  **Search Hotels:** Locates accommodations in the target city.
3.  **Calculate Budget:** Synthesizes flight and hotel data to provide a total trip estimate.

## Prerequisites
*   **Python 3.11 or higher**
*   **pip** (Python package installer)
*   An **API Key** from Google AI Studio (Gemini API)

## Installation & Setup

1.  **Create a Workspace Directory:**
    ```bash
    mkdir adk-projects
    cd adk-projects
    ```

2.  **Set Up a Virtual Environment:**
    *   **Mac/Linux:**
        ```bash
        python3 -m venv .venv
        source .venv/bin/activate
        ```
    *   **Windows:**
        ```bash
        python -m venv .venv
        .venv\Scripts\activate
        ```

3.  **Install the ADK Framework:**
    ```bash
    pip install google-adk
    ```

4.  **Create the Project:**
    ```bash
    adk create travel_agent
    cd travel_agent
    ```

## Configuration

Open the **`.env`** file in your project directory and add your credentials. **Note: Do not share or commit this file**.

```text
GOOGLE_GENAI_USE_VERTEXAI=0
GOOGLE_API_KEY=your-actual-api-key-here
```

To prevent your keys from being uploaded to GitHub, ensure your **`.gitignore`** file includes `.env`, `__pycache__/`, and `.venv/`.

## Agent Features

### 1. Structured Instructions
The agent follows professional instruction patterns including **Identity**, **Mission**, **Methodology**, and **Boundaries**. This ensures it remains friendly and educational while strictly adhering to its role as a travel planner.

### 2. Custom Function Tools
The project includes three integrated Python functions that ADK automatically wraps as tools for the agent:
*   **`search_flights`**: Searches for available flights to destinations like Paris or Tokyo.
*   **`search_hotels`**: Finds available hotels and their ratings.
*   **`calculate_trip_budget`**: Provides a detailed breakdown of flight and accommodation costs.

### 3. Automatic Orchestration
The agent can intelligently sequence its tools. For a full trip estimate, it will call both search tools, extract the necessary pricing data, and pass it to the budget tool to provide a final response.

### 4. Error Handling
The agent is instructed to handle errors gracefully. If a user requests a destination not supported by the tools, the agent will apologize and suggest available options (such as Paris or Tokyo) rather than hallucinating data.

## How to Run

To test the travel agent in a visual chat interface, run:

```bash
adk web
```

This starts a local server at **`http://localhost:8000`**.

## Project Structure
*   **`agent.py`**: The core file containing the `root_agent` and the three custom tools.
*   **`__init__.py`**: Enables ADK to discover the agent.
*   **`.env`**: Stores sensitive API keys securely.
