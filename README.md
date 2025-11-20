# Medium Newsletter Trading Digest Automation
<img width="677" height="807" alt="Screenshot 2025-11-19 at 9 20 59 PM" src="https://github.com/user-attachments/assets/2a3d40be-d3e9-46af-bd59-e417d9f4f154" />

This Python automation tool streamlines the process of turning your Medium (and Beehiiv) newsletter into actionable trading insights. It integrates directly with Gmail, downloads your most recent newsletter emails, extracts article links, fetches the full article content, summarizes the material using an AI summarizer, and stores the results locally for easy recall.

## Key Features

- **Automated Gmail Fetching:**  
  Uses the Gmail API to securely access your inbox and retrieve the latest Medium or Beehiiv newsletters.

- **Article Extraction and Processing:**  
  Parses newsletter HTML to identify article links, then downloads and cleans the full text from each article.

- **AI-Powered Summarization:**  
  Summarizes each article into concise, trading-focused insights using Anthropic's Claude language model (via LangChain).

- **Local Database Storage:**  
  Saves summaries, links, and full content to a SQLite database for efficient caching and future reference.

- **Customizable Workflow:**  
  Designed for easy extension to support different newsletter sources or summary formats.

## Use Case

Traders and analysts can quickly digest daily trading advice from Medium or Beehiiv newsletters without manually opening every email or reading full articles. The summarized content is ready for strategy building, market research, or portfolio adjustments.

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/medium-newsletter-digest.git
cd medium-newsletter-digest
```

### 2. Install Dependencies

Install Python packages (preferably in a virtual environment):

```bash
pip install -r requirements.txt
```

Required Python packages include:
- `langchain`
- `langchain-anthropic`
- `google-auth`, `google-auth-oauthlib`, `google-api-python-client`
- `python-dotenv`
- `requests`
- `beautifulsoup4`
- `sqlite3` (standard library)

### 3. API Keys and Credentials

- **Claude API Key:**  
  Place your Anthropic Claude API key in a `.env` file:
  ```
  CLAUDE_API_KEY=your_claude_api_key_here
  ```

- **Google Credentials:**  
  Put your Gmail OAuth client credentials in `credentials.json` (see [Google Docs](https://developers.google.com/gmail/api/quickstart/python) for setup).

- **Token File:**  
  The first run will prompt you to log in to Gmail and will cache your token as `token.json`.

### 4. Run the Pipeline

```bash
python main.py
```

This will:
- Fetch your latest Medium/Beehiiv newsletter emails
- Extract article links from each newsletter
- Download and clean the text of each article
- Summarize each article using Claude
- Store all data in `digests.db`

### 5. Query Your Summaries

Use the interactive query tool:

```bash
python query_interface.py
```

Ask questions like:
- `"Show me summaries for today"`
- `"List all articles about options trading"`

## File Overview

- `digest_logic.py` — Core logic for fetching emails, extracting articles, summarizing, and database storage.
- `main.py` — Entry point for running the full pipeline.
- `query_interface.py` — Interactive CLI for querying your summaries.
- `credentials.json` — Google OAuth client credentials.
- `token.json` — Cached Gmail access token.
- `digests.db` — SQLite database storing articles and summaries.
- `list_models.py` — Utility to list available Anthropic models.

## Extending

- Add new newsletter sources by updating the Gmail query and link extraction logic.
- Customize the summarization prompt or summary style in `digest_logic.py`.
- Integrate with other LLMs or databases as needed.

## License

MIT License. See `LICENSE` file for details.

---

## Acknowledgements

- [LangChain](https://github.com/langchain-ai/langchain)
- [Anthropic Claude](https://www.anthropic.com/)
- [Google Gmail API](https://developers.google.com/gmail/api)

---

**Questions or issues?**  
Open an issue in this repository or contact the maintainer!
