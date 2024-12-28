# Gurubase Widget

A lightweight, customizable chat widget that can be easily integrated into any website. It connects your webpage to Gurubase, an AI-powered chat interface that can answer any question regarding your product.

## Features

- 🚀 Easy integration

- 💬 Real-time streaming responses

- 🎨 Customizable appearance

- 📱 Responsive design

- 🔒 Secure API integration

- 📊 Trust score indicators

- 🔗 Reference link support

- ⌨️ Markdown support

- 🎯 Code syntax highlighting

## Installation

### Pure Javascript

Add the widget to your website by including these scripts in your HTML:

```html
<!-- Gurubase Widget -->
<script async src="/path/to/widget.js" 
    data-widget-id="FhdIYUJfuAs3g_Zmm_U6UarG6GJFSVSUzf4NHYltu1g"
    data-text="Ask AI"
    data-margins='{"bottom": "20px", "right": "20px"}'
    data-bg-color="#F5A51D"
    data-icon-url="https://avatars.githubusercontent.com/u/75415501?s=200&v=4"
    data-name="Anteon"
    data-light-mode="true"
    id="guru-widget-id">
</script>
```

### React

1. Add the widget.js in your project. 
2. Create this component:

```jsx
"use client";

import { useEffect } from 'react';

function GurubaseWidget({
  widgetId,
  text = "Ask AI",
  margins = { bottom: "20px", right: "20px" },
  bgColor = null,
  iconUrl = null,
  name = null,
  lightMode = true
}) {
  useEffect(() => {
    // Check if the widget is already initialized
    if (window.chatWidget) {
      return;
    }

    const script = document.createElement('script');
    script.src = '/path/to/widget.js';
    script.async = true;

    // Set data attributes
    script.setAttribute('data-widget-id', widgetId);
    if (text) {
    script.setAttribute('data-text', text);
    }
    if (margins) {
    script.setAttribute('data-margins', JSON.stringify(margins));
    }
    if (bgColor) {
    script.setAttribute('data-bg-color', bgColor);
    }
    if (iconUrl) {
    script.setAttribute('data-icon-url', iconUrl);
    }
    if (name) {
    script.setAttribute('data-name', name);
    }
    if (lightMode) {
    script.setAttribute('data-light-mode', lightMode);
    }

    script.setAttribute('id', 'guru-widget-id');

    document.body.appendChild(script);

    // Cleanup when component unmounts
    return () => {
      const widgetScript = document.querySelector('script[src="/widget.js"]');
      if (widgetScript) {
        document.body.removeChild(widgetScript);
      }
      const widgetContainer = document.querySelector('.chat-widget');
      if (widgetContainer) {
        widgetContainer.remove();
      }
    };
  }, [widgetId, text, margins, bgColor, iconUrl, name, lightMode]);

  return null;
}

export default GurubaseWidget;
```

3. Use the component in your app.

```jsx
<GurubaseWidget 
  widgetId="b_GSd67b_KVColq6d0YFygTkTkT-aaAOhonhP4JsWgP5k"
  text="Ask AI"
  margins={{ bottom: "20px", right: "20px" }}
  lightMode={false}
  bgColor="#F5A51D"
  iconUrl="https://avatars.githubusercontent.com/u/75415501?s=200&v=4"
  name="Anteon"
/>
```

## Usage

### Configuration Options

| Option | Type | Description | Default |
|--------|------|-------------|---------|
| data-widget-id | string | Your widget ID (Click [here](https://gurubase.io) to get one) | Required |
| data-text | string | Text displayed on the chat button | "Ask AI" |
| data-margins | object | Button positioning margins | { bottom: "20px", right: "20px" } |
| data-bg-color | string | Primary color for the widget | Fetched from the backend |
| data-icon-url | string | URL to your company logo | Fetched from the backend |
| data-name | string | Your company/product name | Fetched from the backend |
| data-light-mode | boolean | Whether to use light mode | true |

## Customization

### Styling

The widget automatically fetches the following configuration options from the backend:

- `data-bg-color`
- `data-icon-url`
- `data-name` 

> You can override these values by passing them as given in the Installation section.

The widget can be customized through the following configuration options:

- `data-bg-color`: Change the primary color of the widget.
- `data-icon-url`: Change the logo displayed in the widget.
- `data-name`: Change the name displayed in the widget.
- `data-text`: Change the text displayed on the chat button.
- `data-margins`: Change the margins of the chat button.
- `data-light-mode`: Change the mode of the widget.

#### Examples

# TODO: Add screenshots

## Demos

Currently there are two demos:

- [React App](examples/react_app/index.html)
    
    You can view this by the following commands
    ```bash
    cd examples/react_app
    npm install
    npm run dev
    ```
- [Pure JS](examples/pure_js/index.html)
    
    You can view this simply by opening the file in your browser.

## License
MIT License - see the LICENSE file for details.

## Support

For any issues or support requests, please contact us at [support@gurubase.com](mailto:support@gurubase.com).
