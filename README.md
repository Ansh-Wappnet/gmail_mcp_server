# 📧 Gmail MCP Server

The Gmail MCP Server provides a toolset to interact programmatically with Gmail using OAuth 2.0 authentication. It enables you to search, read, send, and manage emails efficiently using a standardized interface.

---

## 📘 Google Cloud Setup

Before using the Gmail MCP Server, you must set up a Google Cloud project, enable the Gmail API, and create OAuth 2.0 credentials.

### 1. Create a Google Cloud Project
- Go to the [Google Cloud Console](https://console.cloud.google.com/).
- Click the project dropdown at the top and select **New Project**.
- Enter a project name (e.g., `Gmail MCP Server`) and click **Create**.

### 2. Enable the Gmail API
- With your project selected, navigate to the [Gmail API page](https://console.cloud.google.com/apis/library/gmail.googleapis.com).
- Click **Enable**.

### 3. Create OAuth 2.0 Credentials (Desktop Client)
- In the Cloud Console, go to **APIs & Services > Credentials**.
- Click **+ Create Credentials** and choose **OAuth client ID**.
- If prompted, configure the consent screen:
  - Set the **App type** to `External`.
  - Fill in the required fields (App name, user support email, etc.).
- For **Application type**, select **Desktop app**.
- Enter a name (e.g., `Gmail MCP Desktop Client`) and click **Create**.
- Download the credentials file (`credentials.json`) and store it securely. You’ll need this file for authentication.

---

## 🛠️ Available Tools

The Gmail MCP Server offers the following tools for interacting with Gmail:

- **search_emails**  
  Search emails using Gmail’s advanced search syntax (e.g., by sender, subject, date).

- **get_recent_emails**  
  Retrieve the most recent emails from your Gmail inbox.

- **get_email_details**  
  Fetch full details (headers, body, metadata) of a specific email using its message ID.

- **send_email**  
  Send a new email using your authenticated Gmail account.

- **list_gmail_labels**  
  List all available labels configured in your Gmail account (e.g., INBOX, STARRED, SENT).

- **get_emails_by_label**  
  Retrieve emails that belong to a specific Gmail label.

- **health_check**  
  Check the health and connectivity of the Gmail MCP Server to ensure it is functioning correctly.
  
## 🖥️ Claude Desktop Configuration

To use the **Gmail MCP Server** with Claude Desktop, update your Claude configuration file to include the following entry under `mcpServers`. Replace `CREDENTIALS_FILE` with the **absolute path** to your downloaded `credentials.json` file from the Google Cloud Console.

```json
{
  "mcpServers": {
    "gmail_mcp": {
      "command": "uvx",
      "args": [
        "gmail-mcp-server-ansh",
        "--credentials-file", "CREDENTIALS_FILE"
      ]
    }
  }
}
```

## 🔧 Programmatic Usage

If you are integrating the **Gmail MCP Server** into your own application (such as a custom agent system), you can configure and launch it programmatically using a `params` dictionary as shown below. Also replace `CREDENTIALS_FILE` with the **absolute path** to your downloaded `credentials.json` file from the Google Cloud Console.


```python
params = {
    "command": "uvx",
    "args": [
        "gmail-mcp-server-ansh",
        "--credentials-file", "CREDENTIALS_FILE"
    ]
}