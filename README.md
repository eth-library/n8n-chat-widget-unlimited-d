# n8n Chat Widget for Unlimited D

This is a lightweight, embeddable chat widget that connects to an `n8n` chat webhook endpoint. It has been customized by ETH Library for integration into internal services such as **Unlimited D** (Confluence-based). The code is based on https://github.com/WayneSimpson/n8n-chatbot-template and is an alternative to the official n8n widget (https://www.npmjs.com/package/@n8n/chat). Thanks to Wayne Simpson!

## 🚀 Features

- 📩 Connects to `n8n` via webhook (custom route)
- 💬 Fully client-side rendered widget UI
- 🎨 Custom branding and theming support
- 📎 Supports Markdown-formatted responses
- 🔗 Renders clickable links (`target="_blank"`) from Markdown or HTML
- ⚙️ Easily embeddable in any website via HTML snippet

## 📦 Repository Contents

- `chat-widget.js` – Main JavaScript for rendering the chat UI and connecting to n8n
- `chat-widget.css` – Optional: custom styling (can be embedded or external)
- `index.html` – Example usage with configuration
- `README.md` – You're reading it

## ✨ Customizations
This widget includes the following ETH Library-specific customizations:

Uses marked.js to parse Markdown in bot responses

- Automatically adds target="_blank" and rel="noopener noreferrer" to all links
- Optional fallback that ensures HTML-based links are also modified correctly
- All links open in a new browser tab

## 🌐 Integration

To use this widget on a website:

### 1. Include Required Script (place it just before the </body> tag.

```html
<!-- Widget Configuration -->
<script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
<script>
  window.ChatWidgetConfig = {
    webhook: {
      url: 'https://n8n.library.ethz.ch/webhook/01148f91-7a21-4f2c-b9fb-f9fdcaca0c1c/chat',
      route: 'general'
    },
    branding: {
      logo: 'https://avatars.githubusercontent.com/u/101881644',
      name: 'SLSP Manuals', // Your company name
      welcomeText: 'Hallo 👋, ich bin der Assistenzbot für den Confluence-Bereich SLSP Manuals.', //Welcome message
      responseTimeText: 'Dieser Bot kann Fehler machen. <a href="https://library.ethz.ch/footer/datenschutz.html" target="_blank">Datenschutz</a>' //Response time message
    },
    style: {
      primaryColor: '#00596D', //Primary color
      secondaryColor: '#007894', //Secondary color
      position: 'right', //Position of the widget (left or right)
      backgroundColor: '#ffffff', //Background color of the chat widget
      fontColor: '#333333' //Text color for messages and interface
    }
  };
</script>
<script src="https://cdn.jsdelivr.net/gh/eth-library/n8n-chat-widget-unlimited-d/chat-widget.js"></script>
<!-- Widget Script --> 
```
### 2. Configure the Widget
In your HTML page, configure/change webhook URL, branding and style settings.

### 3. Done!
Once embedded, the chat widget will connect to your configured n8n webhook and respond with formatted messages.

### Notes

- This widget is designed to be served as a static asset (e.g. GitHub Pages, ETH web hosting, etc.)
- No backend required – logic is delegated to n8n workflows
- Works best when paired with Markdown-formatted responses from n8n

