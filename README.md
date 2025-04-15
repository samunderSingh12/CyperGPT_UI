# Basic Single-File ChatGPT Web Interface (v1.3 - Responsive)

This repository contains a single HTML file that creates a basic, responsive web interface for interacting with OpenAI's Chat Completion API models (like GPT-3.5 Turbo, GPT-4, GPT-4o). It features a cyberpunk-inspired theme and supports streaming responses, conversation history, parameter adjustments, Markdown rendering, and more.

**This is primarily intended as a demonstration or personal tool due to inherent security limitations regarding API key handling.**

![Screenshot Placeholder - Replace with an actual screenshot of the UI](screenshot.png)
*(Replace `screenshot.png` with an actual image file in your repo)*

## Features

*   **Single File Operation:** Entire UI and logic contained within one `.html` file.
*   **Direct OpenAI API Interaction:** Connects to the `v1/chat/completions` endpoint.
*   **Model Selection:** Dropdown to choose compatible OpenAI models (GPT-3.5, GPT-4, GPT-4o, etc.).
*   **Parameter Control:** Adjust Temperature, Top P, and Max Tokens for generation.
*   **System Prompt:** Define a system message to guide the AI's behavior throughout the conversation.
*   **Conversation Memory:** Remembers previous turns (with a configurable message limit to manage context length).
*   **Streaming Responses:** Displays AI responses token-by-token as they arrive for a real-time feel.
*   **Stop Generation:** Button to interrupt the AI response stream if needed.
*   **Markdown Rendering:** Formats responses containing Markdown (code blocks, lists, bold, italics) using `marked.js`.
*   **Copy Code Button:** Easily copy the text content of assistant messages to the clipboard.
*   **Settings Persistence:** Saves API key, model, parameters, and system prompt to browser `localStorage` for convenience (see Security Warning).
*   **Responsive Design:** Adapts layout for desktop, tablet, and mobile devices using CSS media queries.
*   **Cyberpunk Theme:** Dark, neon-infused visual style using CSS variables.
*   **Accessibility:** Includes `aria-live` region for chat history updates.

## How to Use

1.  **Download:** Download the `chatgpt_ui_enhanced.html` (or the latest version file, likely named `chatgpt_ui_responsive.html` based on our last step) from this repository.
2.  **Open:** Open the downloaded `.html` file directly in your modern web browser (e.g., Chrome, Firefox, Edge, Safari). No web server is required.
3.  **Enter API Key:** Paste your OpenAI API key into the "// Access Key:" field.
4.  **(Optional) Configure:**
    *   Set a System Prompt if desired.
    *   Choose your preferred AI Model.
    *   Adjust Temperature, Top P, and Max Tokens.
    *   *(Your settings, including the API key, will be saved in your browser's local storage for the next session unless cleared).*
5.  **Chat:** Type your message in the "// Input Command:" box and press Enter or click the "> Transmit" button.
6.  **Interact:** View the streaming response. Use the "STOP" button to interrupt, "X Clear Log" to start fresh, or the "Copy" button on messages.

## Configuration

*   **API Key:** Your secret key from OpenAI (required).
*   **System Prompt:** An optional instruction to set the AI's context or persona (e.g., "You are a helpful assistant specialized in Python.").
*   **Model:** Select the desired OpenAI chat model compatible with the Chat Completions API.
*   **Temperature, Top P, Max Tokens:** Standard OpenAI generation parameters.
*   **History Limit:** The `MAX_HISTORY_MESSAGES` constant (e.g., `const MAX_HISTORY_MESSAGES = 60;`) within the `<script>` tag controls how many *messages* (user + assistant turns) are sent back to the API as context. Adjust this value directly in the code if needed, considering your chosen model's context window and typical usage (e.g., coding needs more history).
*   **Local Storage:** Settings are saved automatically. Use the "Clear Saved Settings" button within the UI's warning box to remove all saved data from your browser.

## 🚨 CRITICAL SECURITY WARNING 🚨

*   **Client-Side API Key:** This application handles your OpenAI API key **entirely within the client-side JavaScript**.
*   **HIGH RISK:** This means your API key is **exposed in your browser** and can be easily accessed by anyone inspecting the page source or using browser developer tools. If someone obtains your key, they can make API calls billed to your account.
*   **DO NOT** use this setup in a production environment, host it publicly where others might enter their keys, or share it with untrusted users.
*   **DEMONSTRATION ONLY:** This tool is intended solely for **personal, local use or demonstration purposes** where you fully understand and accept the security risk.
*   **Local Storage Insecurity:** Saving the API key to `localStorage` adds convenience for personal use but **does not fix the fundamental security issue**. The key is still stored unencrypted on your machine and accessible via the browser.
*   **RECOMMENDATION:** For any application involving multiple users or deployment beyond local use, **always handle API keys on a secure backend server**. The backend should act as a proxy, receiving requests from the frontend, adding the API key securely, and then forwarding the request to the OpenAI API.

## Dependencies

*   Relies on the `marked.js` library (v~4.x or compatible) loaded via CDN for Markdown rendering. An internet connection is required for this feature.
*   Uses modern browser features like `fetch`, `ReadableStream`, `AbortController`, and `localStorage`.

## Limitations & Potential Improvements

*   **Security:** The client-side API key handling is the primary and most critical limitation.
*   **History Management:** Uses a simple message count limit, not precise token counting. Long messages could still potentially exceed the model's context window limit.
*   **Markdown:** Provides basic rendering. Does not include syntax highlighting for code blocks.
*   **No Edit/Regenerate:** Lacks built-in features to easily edit a previous prompt or regenerate the last AI response.
*   **Error Handling:** Covers common cases but could be made more robust against edge-case API responses or stream interruptions.
*   **Scalability:** The single-file approach limits complexity and maintainability for significant feature growth.

## License

This project is released under the [MIT License](LICENSE). (Consider adding a LICENSE file with the MIT license text to your repository).

---

Feel free to fork, modify, and experiment, but always be mindful of the API key security implications!
