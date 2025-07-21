# Teams Bot UI

A comprehensive Python library for creating rich Microsoft Teams bot cards with Adaptive Cards support. Build interactive, visually appealing bot experiences with minimal code.

## 🚀 Features

- **Rich Card Library**: Pre-built cards for welcome messages, responses, feedback, charts, and more
- **Data Visualization**: Built-in chart support with Chart.js integration
- **Bot Management**: Multi-assistant support with easy switching capabilities
- **File Processing**: Cards for displaying file analysis and content previews
- **Feedback System**: Integrated user feedback collection with detailed forms
- **Session Management**: Track and manage conversation sessions
- **Responsive Design**: Mobile-friendly adaptive cards with modern styling
- **Backward Compatibility**: Smooth migration path with legacy function support

## 📦 Installation

```bash
pip install teams-bot-ui
```

## 🔧 Requirements

- Python 3.8+
- botbuilder-core>=4.14.0

## 🎯 Quick Start

```python
from teams_bot_ui.cards import create_welcome_adaptive_card, create_text_response_card

# Create a welcome card
welcome_card = create_welcome_adaptive_card(
    user_name="John Doe",
    bot_info={
        "name": "My Assistant",
        "logo": "https://example.com/logo.png"
    }
)

# Create a response card
response_card = create_text_response_card(
    response_text="Hello! How can I help you today?",
    bot_info={
        "name": "My Assistant",
        "logo": "https://example.com/logo.png"
    },
    suggested_actions=[
        {"title": "Ask a Question", "value": "I have a question"},
        {"title": "Get Help", "value": "I need help"}
    ]
)
```

## 📚 Card Types

### Welcome Cards
Create engaging welcome experiences for new users:

```python
from teams_bot_ui.cards import create_enhanced_welcome_adaptive_card

card = create_enhanced_welcome_adaptive_card(
    user_name="Alice",
    bot_info={
        "name": "Support Bot",
        "logo": "https://example.com/bot-logo.png"
    }
)
```

### Response Cards
Display bot responses with optional actions:

```python
from teams_bot_ui.cards import create_text_response_card

card = create_text_response_card(
    response_text="Here's the information you requested...",
    suggested_actions=[
        {"title": "More Details", "value": "tell me more"},
        {"title": "Next Steps", "value": "what's next"}
    ]
)
```

### Chart Cards
Visualize data with interactive charts:

```python
from teams_bot_ui.cards import create_chart_card

chart_data = {
    "labels": ["Jan", "Feb", "Mar", "Apr"],
    "datasets": [{
        "label": "Sales",
        "data": [12, 19, 3, 5],
        "backgroundColor": ["#FF6384", "#36A2EB", "#FFCE56", "#4BC0C0"]
    }]
}

card = create_chart_card(
    title="Monthly Sales Report",
    chart_data=chart_data,
    chart_type="bar"
)
```

### Feedback Cards
Collect user feedback:

```python
from teams_bot_ui.cards import create_feedback_card

card = create_feedback_card(
    message_id="msg_123",
    bot_code="ASSISTANT_01",
    session_id="session_456"
)
```

### Bot Management Cards
List and manage available assistants:

```python
from teams_bot_ui.cards import create_bot_list_card

bots = [
    {
        "code": "SUPPORT_BOT",
        "name": "Support Assistant",
        "description": "Help with technical support questions",
        "logo": "https://example.com/support-logo.png"
    },
    {
        "code": "SALES_BOT", 
        "name": "Sales Assistant",
        "description": "Assistance with sales inquiries",
        "logo": "https://example.com/sales-logo.png"
    }
]

card = create_bot_list_card(bots)
```

### File Processing Cards
Display file analysis results:

```python
from teams_bot_ui.cards import create_file_analysis_card

card = create_file_analysis_card(
    processing_results=file_results,
    bot_info={"name": "Document Analyzer"}
)
```

### Capabilities Cards
Showcase bot features:

```python
from teams_bot_ui.cards import create_capabilities_card

features = [
    {
        "title": "Answer Questions",
        "description": "Get detailed answers to your questions",
        "icon": "https://example.com/question-icon.png"
    },
    {
        "title": "Data Analysis", 
        "description": "Analyze and visualize your data",
        "icon": "https://example.com/chart-icon.png"
    }
]

card = create_capabilities_card(
    bot_info={"name": "AI Assistant"},
    features=features
)
```

## 🔄 Session Management

Track conversation sessions:

```python
from teams_bot_ui.cards import create_session_info_card

card = create_session_info_card(
    bot_code="ASSISTANT_01",
    bot_name="My Assistant",
    session_id="session_123",
    message_count=15,
    start_time="2024-01-15 09:30:00"
)
```

## 🎨 UI Components

Build custom cards with reusable components:

```python
from teams_bot_ui.components import create_submit_button, create_fact_set
from teams_bot_ui.templates import base_adaptive_card, add_text_block

# Create custom card
card = base_adaptive_card()
add_text_block(card, "Custom Information", is_heading=True)

facts = create_fact_set([
    {"title": "Status", "value": "Active"},
    {"title": "Type", "value": "Premium"}
])

card["body"].append(facts)
```

## 📊 Chart Types

Support for multiple chart visualizations:

- **Bar Charts**: `chart_type="bar"`
- **Line Charts**: `chart_type="line"`  
- **Pie Charts**: `chart_type="pie"`

```python
# Line chart example
chart_data = {
    "labels": ["Week 1", "Week 2", "Week 3", "Week 4"],
    "datasets": [{
        "label": "Performance",
        "data": [65, 59, 80, 81],
        "borderColor": "#36A2EB",
        "backgroundColor": "rgba(54, 162, 235, 0.2)"
    }]
}

card = create_chart_card(
    title="Weekly Performance",
    chart_data=chart_data,
    chart_type="line"
)
```

## 🔧 Advanced Usage

### Custom Bot Information
Standardize bot branding across all cards:

```python
bot_info = {
    "name": "Enterprise Assistant",
    "logo": "https://company.com/logo.png"
}

# Use across multiple cards
welcome = create_welcome_adaptive_card(bot_info=bot_info)
response = create_text_response_card("Hello!", bot_info=bot_info)
```

### Error Handling
Display user-friendly error messages:

```python
from teams_bot_ui.cards import create_error_card

error_card = create_error_card(
    error_message="Sorry, I couldn't process your request. Please try again."
)
```

### Carousel Cards
Display multiple items in a carousel:

```python
from teams_bot_ui.cards import create_carousel_activity

items = [
    {
        "title": "Product A",
        "subtitle": "$99.99",
        "text": "Premium quality product",
        "image": "https://example.com/product-a.jpg",
        "buttons": [
            {"title": "Learn More", "value": "product_a_details"}
        ]
    },
    {
        "title": "Product B", 
        "subtitle": "$149.99",
        "text": "Professional grade solution",
        "image": "https://example.com/product-b.jpg",
        "buttons": [
            {"title": "Learn More", "value": "product_b_details"}
        ]
    }
]

carousel = create_carousel_activity(items)
```

## 🔄 Migration from Legacy Code

The library maintains backward compatibility with legacy "copilot" terminology:

```python
# Legacy functions still work
from teams_bot_ui.cards import create_copilot_response_card

# Automatically maps to create_text_response_card
card = create_copilot_response_card(
    response_text="Hello!",
    copilot_info={"name": "Assistant"}
)
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues, feature requests, or pull requests.

### Development Setup

```bash
# Clone the repository
git clone https://github.com/shubhamshinde7995/teams-bot-ui.git
cd teams-bot-ui

# Install development dependencies
pip install -e ".[dev]"

# Run tests
pytest

# Format code
black teams_bot_ui/
```

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🔗 Links

- **GitHub**: https://github.com/shubhamshinde7995/teams-bot-ui
- **PyPI**: https://pypi.org/project/teams-bot-ui/
- **Issues**: https://github.com/shubhamshinde7995/teams-bot-ui/issues
- **Documentation**: https://github.com/shubhamshinde7995/teams-bot-ui#readme

## 📞 Support

- **Email**: shubhamshinde7995@gmail.com
- **GitHub Issues**: For bug reports and feature requests

## 🏷️ Keywords

`microsoft teams`, `bot`, `adaptive cards`, `ui`, `chatbot`, `assistant`, `conversation`, `bot framework`, `teams bot`, `cards`, `interactive`

---

Made with ❤️ for the Microsoft Teams development community