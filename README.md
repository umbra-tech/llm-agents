# LLM Agents Repository

A collection of specialized AI agent configurations and documentation for automating specific tasks and workflows.

## Overview

This repository contains pre-configured LLM agents, each designed to handle specific tasks efficiently and consistently. Each agent includes:
- **agent.md** - Configuration file with rules, standards, and patterns
- **README.md** - User guide with workflows and examples
- Supporting files and resources as needed

## Available Agents

### 📝 [recipes-to-json](./recipes-to-json/)
Converts recipe content from any text format directly to structured JSON using the schema.org/Recipe standard.

**Use Case:** Mealie import, Web deployment, SEO optimization, recipe database creation

**Input:** Plain text, DOCX content, any structured/unstructured recipe text

**Output:** schema.org/Recipe compliant JSON files

[View Full Documentation →](./recipes-to-json/README.md)

---

## Repository Structure

```
llm-agents/
├── README.md                  # This file
├── recipes-to-json/           # Recipe conversion agent
│   ├── agent.md               # Agent configuration
│   ├── README.md              # User guide
├── [future-agent-1]/          # Additional agents...
│   ├── agent.md
│   └── README.md
└── [future-agent-2]/
    ├── agent.md
    └── README.md
```

## Quick Start

### Using an Agent

1. **Navigate to the agent folder**
   ```bash
   cd recipes-to-json
   ```

2. **Reference the agent in your LLM conversation**
   ```
   Please refer to @agent.md for [task] standards
   ```

3. **Provide your input**
   ```
   [Paste your content or describe your task]
   ```

4. **Agent processes and outputs**
   - Follows rules defined in agent.md
   - Produces consistent, standardized output
   - Saves to current directory (or specified location)

### First-Time Setup

Each agent may have specific requirements. Check the agent's README.md for:
- Software prerequisites
- Configuration needs
- Initial setup steps

## How Agents Work

### Agent Files Explained

#### agent.md
The configuration file that defines:
- **Task overview** - What the agent does
- **Input/output formats** - Expected data structures
- **Conversion rules** - How to process content
- **Standards** - Formatting, naming conventions, patterns
- **Special cases** - Edge case handling
- **Best practices** - Quality guidelines

#### README.md
The user guide that includes:
- **Overview** - Agent purpose and capabilities
- **Quick start** - Fast track to using the agent
- **Workflows** - Common use patterns
- **Examples** - Sample inputs and outputs
- **Troubleshooting** - Common issues and solutions
- **FAQ** - Frequently asked questions

### Using Agents with LLMs

Agents work with any LLM that supports:
- File references (e.g., @agent.md)
- Context windows large enough for the agent.md file
- Tool/function calling (for file operations)

**Compatible with:**
- Claude (Anthropic) ✅
- ChatGPT (OpenAI) ✅
- Other LLMs with file reference capabilities ✅

## Creating New Agents

### Agent Development Process

1. **Identify the task/workflow** to automate
2. **Define input and output formats** clearly
3. **Document conversion rules** and standards
4. **Create agent.md** with comprehensive configuration
5. **Write README.md** with user-facing documentation
6. **Test with various inputs** to validate consistency
7. **Refine based on edge cases** and user feedback

### Agent Template Structure

```markdown
agent.md
├── Project Overview
├── Accepted Input Formats
├── Output Format
├── Directory Structure
├── Parsing/Conversion Guidelines
├── Standards and Patterns
├── Special Cases
└── Best Practices

README.md
├── Overview
├── What This Agent Does
├── Prerequisites
├── Quick Start Guide
├── Common Workflows
├── Tips for Best Results
├── Troubleshooting
└── FAQ
```

### Naming Conventions

- **Folder names**: `lowercase-with-hyphens`
- **Agent files**: Always `agent.md` and `README.md`
- **Purpose-based naming**: Describe what the agent does (e.g., `pdf-to-markdown`, `code-documenter`)

## Best Practices

### For Agent Users

✅ **DO:**
- Read the agent's README.md before first use
- Reference @agent.md at the start of sessions
- Provide clear, complete input
- Verify output meets your needs
- Report issues or edge cases

❌ **DON'T:**
- Skip reading documentation
- Mix agents without clear context
- Expect agents to handle undefined scenarios
- Modify agent.md without understanding implications

### For Agent Developers

✅ **DO:**
- Write clear, comprehensive documentation
- Include real-world examples
- Handle edge cases explicitly
- Keep agent.md focused on rules/standards
- Keep README.md focused on user guidance
- Test with diverse inputs
- Version your agents

❌ **DON'T:**
- Create overly complex agents (split into multiple if needed)
- Mix concerns (one agent = one task)
- Leave undocumented behavior
- Forget to update documentation when changing rules

## Agent Guidelines

### When to Create a New Agent

Create a new agent when you have a task that:
- ✅ Is repetitive and follows consistent patterns
- ✅ Requires specific formatting or standards
- ✅ Benefits from documented rules and examples
- ✅ Can be clearly defined with inputs/outputs
- ✅ Will be reused multiple times

### When NOT to Create an Agent

Avoid creating an agent for:
- ❌ One-time tasks
- ❌ Highly variable, unpredictable workflows
- ❌ Tasks that require constant human judgment
- ❌ Simple prompts that don't need rules

## Contributing

### Adding a New Agent

1. Create a new folder: `agent-name/`
2. Add `agent.md` with configuration
3. Add `README.md` with user guide
4. Update this root README with agent listing
5. Test thoroughly with sample inputs
6. Document any prerequisites or dependencies

### Improving Existing Agents

1. Test the current agent behavior
2. Identify gaps or issues
3. Update agent.md and/or README.md
4. Test changes with various inputs
5. Update version notes if significant changes

## Version Control

### Semantic Versioning

For significant agent changes, consider versioning:
- **1.0** - Initial release
- **1.1** - Minor improvements, backward compatible
- **2.0** - Breaking changes, new structure

Document version changes in agent README.md

## Support and Feedback

### Getting Help

1. Check the agent's README.md
2. Review agent.md for configuration details
3. Search for similar issues
4. Create detailed issue reports

### Reporting Issues

When reporting problems:
- Agent name and version
- Input provided
- Expected output
- Actual output
- Steps to reproduce

## Use Cases

### Common Agent Applications

- **Data Transformation**: Converting between formats (JSON, XML, CSV, etc.)
- **Content Generation**: Creating standardized documents or files
- **Code Operations**: Documentation, refactoring, analysis
- **Media Processing**: Metadata extraction, format conversion
- **Workflow Automation**: Multi-step processes with consistent rules

## Roadmap

### Potential Future Agents

Ideas for expansion:
- `markdown-to-pdf` - Convert markdown to formatted PDFs
- `code-documenter` - Auto-generate code documentation
- `image-metadata-extractor` - Extract and organize image metadata
- `csv-to-sql` - Convert CSV data to SQL insert statements
- `api-spec-generator` - Create API documentation from code

*Have an agent idea? Add it to the roadmap!*

## Technical Details

### File Formats

- **agent.md**: Markdown format, UTF-8 encoding
- **README.md**: Markdown format, UTF-8 encoding
- Output formats vary by agent

### Performance Considerations

- Agents are optimized for single or batch processing
- Batch sizes recommended in each agent's documentation
- Processing time depends on LLM and input complexity

## Resources

- **LLM Documentation**: Check your LLM provider's docs for file reference syntax
- **Schema Standards**: Refer to relevant standards (schema.org, etc.)
- **Markdown Guide**: [Markdown Syntax](https://www.markdownguide.org/)

## License

[MIT License]

## Changelog

### Repository Updates

- **2026-03-14**: Repository created
- **2026-03-14**: Added recipes-to-json agent
- [Add more as agents are added]

---

**Maintained by:** Umbra-Tech  
**Last Updated:** 2026-03-14  
**Repository Version:** 1.0
