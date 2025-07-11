# Gumloop Unified Model Context Protocol (guMCP)

guMCP is an open-source collection of Model Context Protocol (MCP) servers that can be run both remotely and locally. The project aims to create the largest collection of MCP servers with a unified backend, fostering a community around AI integrations and the future of AGI.

## Overview

While many MCP server providers are closed source, and open-source alternatives typically only support local hosting through stdio, guMCP provides:

- A comprehensive collection of MCP servers that work both locally and remotely
- Support for both stdio and SSE (Server-Sent Events) transports
- A unified backend architecture for consistent implementation
- Full open-source access to encourage community contributions

## Getting Started

> **🎬 RECOMMENDED: Watch our quick setup video before getting started!** 
> 
> This under 5-minute walkthrough will save you time and help you understand the key concepts.
> 
> [![Watch the guMCP Getting Started Video](https://www.gumloop.com/_next/image?url=%2Fimages%2Fmcp%2FGuideVideo.png&w=1920&q=75)](https://vimeo.com/1070438737/8dea56e6a1)

### Prerequisites

- Python 3.11
- Git
- For Windows users: A bash-compatible shell is recommended (Git Bash, WSL, etc.)

### Installation

1. **Clone the repository**:

   ```bash
   git clone https://github.com/gumloop/guMCP.git
   cd guMCP
   ```

2. **Set up a virtual environment**:

   This isolates the project dependencies from your system Python installation.

   ```bash
   # Create the virtual environment
   python -m venv venv
   
   # Activate it (choose the appropriate command for your OS)
   # On Unix/macOS:
   source venv/bin/activate
   
   # On Windows (Command Prompt):
   venv\Scripts\activate
   
   # On Windows (PowerShell):
   .\venv\Scripts\Activate.ps1
   
   # On Windows (Git Bash):
   source venv/Scripts/activate
   ```
   
   You'll know your virtual environment is active when you see `(venv)` at the beginning of your command prompt.

3. **Install dependencies**:

   ```bash
   # Install core dependencies
   pip install -r requirements.txt
   
   # Install development dependencies (for contributing)
   pip install -r requirements-dev.txt
   ```

4. **Configure environment variables**:

   ```bash
   # Create a local environment file from the template
   cp .env.example .env
   
   # Open the .env file in your preferred text editor and update values as needed
   # If you're using VS Code:
   code .env
   ```
   
   The `.env` file contains configuration for:
   - API keys for service integrations
   - Authentication settings
   - Server configuration options
   - Development environment settings


## Usage

### Running SSE Servers

An SSE server can be run locally. This will provide a single URL and host every server available.

To start the SSE development server, run:

```bash
./start_sse_dev_server.sh
```

For convenience, we also provide a lightweight MCP Client to connect to SSE servers. Usage:

```bash
python tests/clients/RemoteMCPTestClient.py --endpoint=http://localhost:8000/simple-tools-server/local
```

### Running Stdio Servers

```bash
python src/servers/local.py --server=simple-tools-server
```

For convenience, we also provide a lightweight MCP Client to start and connect to stdio servers. Usage:

```bash
 python tests/clients/LocalMCPTestClient.py --server=simple-tools-server
```

## Supported Servers and Authentication Methods

The following table provides an overview of the current servers implemented in guMCP, their authentication requirements, and relative ease of use with different authentication methods:

| Server | Auth Type | Remote Auth<br>(e.g., Cursor) | Local Auth<br>(e.g., Claude Desktop) | Documentation |
|--------|-----------|-------------------------------|--------------------------------------|---------------|



## Contributing

We welcome contributions! Please see our [CONTRIBUTING.md](CONTRIBUTING.MD) for guidelines.

Key areas for contribution:

- New server implementations
- Transport improvements
- Documentation
- Test coverage
- Bug fixes

## License

This project is licensed under the GNU General Public License v3.0 (GPL-3.0) - see the [LICENSE](LICENSE) file for details.

## Security

Security is the single highest priority for us.

That's why [Gumloop is SOC 2 Type II, GDPR, and HIPAA compliant](https://trust.gumloop.com/), and why for this OSS repo, we're actively rewarding those who responsibly disclose serious vulnerabilities and exploits to security@gumloop.com.

## Community

- GitHub Issues: Bug reports and feature requests
- GitHub Discussions: General questions and discussions
- [Forum](https://forum.gumloop.com/): Community discussions and support

## Acknowledgments

This project builds on the Model Context Protocol (MCP) specification and is inspired by the work of various MCP implementations in the community, especially those at Anthropic.

Thank you to all the contributors that have provided feedback, advice, and early servers for the repository.
