# Troubleshooting and FAQ

This page addresses frequently asked questions (FAQ) and provides troubleshooting steps for common issues encountered while using Agent Zero.

## Frequently Asked Questions

**1. How do I set up and activate a Python virtual environment?**

Use the `venv` module (recommended for Python) or `conda`.

* **`venv`:**
    ```bash
    python -m venv .venv  # Create the environment
    source .venv/bin/activate  # Activate (Linux/macOS)
    .venv\Scripts\activate  # Activate (Windows)
    ```
* **`conda`:**
    ```bash
    conda create -n agent-zero python=3.12  # Create
    conda activate agent-zero  # Activate
    ```

**2. How do I resolve `ModuleNotFoundError` errors (e.g., for `ansio`, `pyflakes`, `Flask`)?**

Ensure your virtual environment is activated *before* installing requirements:

```bash
pip install -r requirements.txt
```

**3. How do I integrate models like `ollama` or `llama` with Agent Zero?**

Refer to the [Choosing your LLMs](./architecture.md#customization) section of the documentation for detailed instructions and examples for configuring different LLMs in `initialize.py`. (This assumes you'll have a dedicated documentation page for model integration).

**5. How can I make Agent Zero retain memory between sessions?**

Auto memory automatically saves and loads solutions and informations from previous sessions.

**6. Where can I find more documentation or tutorials?**

*   Check the official Agent Zero documentation (link to main documentation site).
*   Join the Agent Zero Discord community for support and discussions (provide link).

**7. How do I fix JSON formatting errors when using tools or models?**

*   Ensure that the output from your tools strictly adheres to valid JSON format. Use a JSON validator if needed.
*   Check the specific tool's documentation or prompt for expected output formats.
*   If using custom tools, double-check your Python code for correct JSON serialization.

**8. Can I run Agent Zero without API keys or for free?**

You can experiment with locally hosted open-source LLMs like Llama.  Refer to the Model Integration documentation for configuration instructions.  Using API-based LLMs like those from OpenAI, Google, etc., requires API keys and might incur costs.

**9. How do I adjust API rate limits?**

Modify the `rate_limit_seconds` and `rate_limit_requests` parameters in the `AgentConfig` class within `initialize.py`.

**10. Can Agent Zero interact with external APIs or services (e.g., WhatsApp)?**

Extending Agent Zero to interact with external APIs is possible by creating custom tools or solutions. Refer to the documentation on creating them. 

## Troubleshooting

**(Installation)**

* **Dependency Conflicts:** If encountering version conflicts during installation, try creating a fresh virtual environment and reinstalling the requirements.
* **Docker Issues:** If Docker containers fail to start or Agent Zero can't connect to Docker, consult the Docker documentation and verify your Docker installation and configuration.  On macOS, ensure you've granted Docker access to your project files in Docker Desktop's settings as described in the Installation guide.

**(Usage)**

* **"Nothing happens" when sending a message:** This often indicates a tool execution issue, an API connection problem, or rate limiting. Check your API keys, internet connection, and ensure any required services (like Docker) are running.  Examine the logs for more details.

* **Terminal commands not executing:** If using Docker for code execution, ensure the Docker container is running and properly configured.  Check SSH settings if applicable.

* **Error Messages:** Pay close attention to the error messages displayed in the Web UI or terminal.  They often provide valuable clues for diagnosing the issue. Refer to the specific error message in online searches or community forums for potential solutions.

* **Performance Issues:** If Agent Zero is slow or unresponsive, it might be due to resource limitations, network latency, or the complexity of your prompts and tasks.