# Claude MCP Job Assistant

<p align="center">
  <img src="https://raw.githubusercontent.com/eric623/Claude-MCP-Job-Assistant/main/job-flow.svg"
       alt="Claude MCP Job Assistant Workflow"
       width="1000"/>
  <br>
  <em>Figure 1 - MCP Job Assistant architecture illustrating the interaction between Claude Desktop, MCP Server, Tools, Resources, and Prompts.</em>
</p>

## Overview

Claude MCP Job Assistant is a production-ready MCP (Model Context Protocol) server designed to demonstrate how Tools, Resources, and Prompts can be orchestrated to build an intelligent job search assistant.

The project uses **Claude Desktop** as the MCP Host/Client and exposes a complete ecosystem for:

- Searching job opportunities.
- Saving interesting positions.
- Performing labor market analysis.
- Receiving personalized recommendations based on a resume.
- Generating matching reports between a resume and saved jobs.

This project provides a practical introduction to the Model Context Protocol and illustrates how modern AI assistants can leverage MCP capabilities to deliver contextual and personalized experiences.

---

## Features

- MCP-compliant server implementation.
- Integration with Claude Desktop.
- Intelligent job search.
- Job bookmarking and persistence.
- Resume-based recommendations.
- Labor market analysis.
- Matching reports generation.
- Modular architecture using MCP Tools, Resources, and Prompts.
- Production-ready setup with `uv`.

---

## Architecture

The MCP server is organized around the three core MCP primitives:

### Tools

| Tool | Description |
|------|------|
| `search_jobs()` | Retrieves job offers using an external API. |
| `save_job()` | Saves selected jobs in a structured format. |

---

### Resources

| Resource | Description |
|------|------|
| `resume://default` | Loads the user's resume. |
| `jobs://saved` | Loads previously saved jobs. |

---

### Prompts

| Prompt | Description |
|------|------|
| `analyze_job_market()` | Analyzes labor market trends. |
| `personalized_job_recommender()` | Suggests jobs, skills, and companies based on the user's resume. |
| `create_match_report()` | Generates a report comparing saved jobs with the user's resume. |

---

## Workflow

```text
User
 ↓
Claude Desktop (MCP Host)
 ↓
MCP Job Assistant Server
 ├── Tools
 │   ├── search_jobs()
 │   └── save_job()
 │
 ├── Resources
 │   ├── resume://default
 │   └── jobs://saved
 │
 └── Prompts
     ├── analyze_job_market()
     ├── personalized_job_recommender()
     └── create_match_report()

 ↓
Generated Response
```

---

## Technologies Used

- Python
- Model Context Protocol (MCP)
- Claude Desktop
- UV
- External Job APIs
- PDF Processing

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/eric623/Claude-MCP-Job-Assistant.git

cd Claude-MCP-Job-Assistant
```

---

### 2. Install Dependencies

This project uses `uv` for dependency management.

```bash
uv sync
```

At this stage, the MCP server is ready to be launched by Claude Desktop.

---

## Claude Desktop Configuration

### Step 1: Install Claude Desktop

Download and install Claude Desktop from Anthropic.

---

### Step 2: Open Developer Settings

Navigate to:

```text
Settings → Developer → Edit Config
```

This opens the `claude_desktop_config.json` file.

---

### Step 3: Add the MCP Server

Add the following configuration:

```json
{
  "mcpServers": {
    "mcp_job": {
      "command": "uv",
      "args": [
        "--directory",
        "PATH_TO_PROJECT_DIRECTORY",
        "run",
        "server.py"
      ]
    }
  }
}
```

> Replace `PATH_TO_PROJECT_DIRECTORY` with the absolute path to your local project folder.

---

## Adding Your Resume

Place your CV inside the `resume` directory.

The file must be named exactly:

```text
resume.pdf
```

Example:

```text
Claude-MCP-Job-Assistant/
│
└── resume/
    └── resume.pdf
```

> **Important:** Resume-based recommendations and matching reports require this file.

---

## Launching the MCP Server

After saving the configuration:

1. Completely close Claude Desktop.
2. Reopen Claude Desktop.

You should now see:

```text
mcp_job (Running)
```

in the Developer panel.

---

## MCP Concepts Demonstrated

- MCP Tools
- MCP Resources
- MCP Prompts
- Claude Desktop Integration
- Context-Aware AI Systems
- Intelligent Job Search
- External API Consumption
- Personalized Recommendations
- Modular MCP Server Design

---

## Why This Project?

This project was built to explore and demonstrate the capabilities of the **Model Context Protocol (MCP)** by implementing a realistic use case centered around job exploration and career assistance.

It highlights how MCP enables:

- Context-aware assistants.
- Modular architectures.
- Tool orchestration.
- Resource management.
- Prompt engineering.
- Intelligent interactions between users and AI systems.

---

## Author

**AKAKPO Koffi Moïse**

- Interested in Agentic AI, Multi-Agent Systems, and Applied Artificial Intelligence.
  
---

> Claude MCP Job Assistant demonstrates how the Model Context Protocol can be leveraged to build intelligent, modular, and extensible assistants through the coordinated use of Tools, Resources, and Prompts.
