# 🚀 ABBYY Document AI API MCP Server

[![Context7 MCP Server](https://img.shields.io/badge/Context7-MCP%20Server-blue)](https://context7.com/sarvottam-bhagat/abbyy-documentation)
[![ABBYY Document AI](https://img.shields.io/badge/ABBYY-Document%20AI-orange)](https://docs.abbyy.com/)

> **Transform any IDE into a powerful Document AI development environment with intelligent context-aware assistance**

This repository contains comprehensive ABBYY Document AI API documentation that has been converted into a **Model Context Protocol (MCP) Server** via [Context7](https://context7.com). Now developers can access the complete ABBYY Document AI knowledge base directly within their IDE, enabling AI-powered assistance for building document processing applications.

## 🎯 What is This?

This MCP server provides **instant access** to the complete ABBYY Document AI API documentation, examples, and best practices directly in your development environment. Whether you're a technical expert or just getting started with document AI, this server acts as your intelligent coding assistant.

### 🔥 Key Features

- **📚 Complete API Documentation**: Access to all ABBYY Document AI endpoints and models
- **💡 Intelligent Code Assistance**: Context-aware suggestions and code generation
- **🔧 Ready-to-Use Examples**: Pre-built code snippets for all document types
- **🌐 Multi-Language Support**: Python SDK examples and implementations
- **⚡ Real-time Help**: Instant answers to Document AI questions
- **🎨 IDE Integration**: Works with Cursor, VS Code, Claude Desktop, and more

## 📋 Supported Document Types & Models

The ABBYY Document AI API supports a comprehensive range of document processing capabilities:

### 🧾 **Financial Documents**
- **Invoices** - Extract vendor details, amounts, line items, tax information
- **Receipts** - Process retail receipts, expense reports
- **Utility Bills** - Parse electricity, gas, water, telecom bills
- **Hotel Invoices** - Extract stay details, room charges, additional services
- **Taxi Receipts** - Process transportation expense receipts

### 🚚 **Logistics & Shipping**
- **Air Waybills** - Extract flight details, cargo information
- **Bill of Lading** - Process shipping manifests and cargo details
- **Sea Waybills** - Maritime shipping documentation
- **Delivery Notes** - Proof of delivery and shipment tracking
- **Arrival Notices** - Import/export notifications
- **Dangerous Goods Declarations** - Hazardous material documentation

### 💰 **Accounts Payable**
- **Remittance Advice** - Payment notifications and details
- **Purchase Orders** - Procurement document processing
- **Credit Notes** - Return and refund documentation

### 🔧 **Core Processing Features**
- **Document Conversion** - Convert between PDF, images, and other formats
- **Image to Text (OCR)** - Extract text from scanned documents and images
- **Handwriting Recognition** - Process handwritten text
- **Multi-language Support** - Process documents in multiple languages
- **Document Management** - Upload, list, delete, and organize documents

## 🚀 Quick Start

### Step 1: Connect to Your IDE

Choose your preferred development environment and add the MCP server configuration:

#### 🎯 **Cursor IDE**
Add to your Cursor settings:
```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

#### 💻 **VS Code**
Add to your VS Code settings:
```json
"mcp": {
  "servers": {
    "context7": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

#### 🤖 **Claude Desktop**
Add to your `claude_desktop_config.json`:
```json
{
  "mcpServers": {
    "Context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

#### 🌊 **Windsurf**
Add to your Windsurf configuration:
```json
"mcp": {
  "servers": {
    "context7": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

#### 🔧 **Cline**
1. Open Cline
2. Click the hamburger menu (☰) → MCP Servers
3. Search for "Context7" in the Marketplace
4. Click Install

#### ☁️ **Claude Code (Remote)**
```bash
# HTTP transport
claude mcp add --transport http context7 https://mcp.context7.com/mcp

# SSE transport
claude mcp add --transport sse context7 https://mcp.context7.com/sse

# Local server
claude mcp add context7 -- npx -y @upstash/context7-mcp
```

### Step 2: Start Building

Once connected, you can immediately start asking questions and building with ABBYY Document AI:

**Example Prompts:**
- *"How do I extract data from an invoice using ABBYY Document AI?"*
- *"Show me how to process a receipt and get the total amount"*
- *"Create a Python script to convert PDF to text using ABBYY"*
- *"What fields can I extract from a hotel invoice?"*
- *"Help me build a document processing pipeline"*

## 🤖 AI-Powered Development with Zero Hallucinations

### **The Problem with Traditional AI Coding Assistants**
Most AI coding assistants suffer from **hallucination** - they generate code based on outdated information, incorrect API endpoints, or non-existent methods. This leads to:
- ❌ Broken code that doesn't work
- ❌ Deprecated API calls
- ❌ Incorrect parameter names
- ❌ Hours of debugging and frustration

### **The Solution: Context-Aware AI Development**
Our MCP server provides **real-time access** to the complete, up-to-date ABBYY Document AI documentation. This means:
- ✅ **100% Accurate Code**: AI generates code using current API specifications
- ✅ **No Hallucinations**: All responses are grounded in actual documentation
- ✅ **Latest Features**: Access to newest API endpoints and capabilities
- ✅ **Error-Free Development**: Correct parameter names, types, and usage patterns

### **🚀 Build Complex Applications with Simple Prompts**

Just tell the AI what you want to build, and it will create a complete, working solution using accurate ABBYY Document AI context:

#### **Example: RAG Application**
```
"Build me a RAG app powered by ABBYY Document AI API. For context, please use the Context7 MCP server and get all information from ABBYY documentation about the API and code."
```

**Result**: A fully functional RAG application with:
- Correct ABBYY API integration
- Proper authentication handling
- Document processing workflows
- Vector database integration
- Query processing logic

#### **Example: Invoice Processing System**
```
"Create an enterprise invoice processing system that extracts data from invoices, validates the information, and exports to CSV. Use ABBYY Document AI for extraction."
```

**Result**: Complete system with:
- File upload handling
- ABBYY API integration for invoice processing
- Data validation logic
- CSV export functionality
- Error handling and logging

#### **Example: Multi-Document Workflow**
```
"Build a document classification and processing pipeline that can handle invoices, receipts, and shipping documents using ABBYY Document AI."
```

**Result**: Sophisticated pipeline with:
- Document type detection
- Appropriate ABBYY model selection
- Parallel processing capabilities
- Results aggregation and reporting

### **🎯 Why This Approach Works**

1. **Grounded Responses**: Every AI response is backed by actual ABBYY documentation
2. **Current Information**: No outdated or deprecated code examples
3. **Complete Context**: AI understands the full API ecosystem and relationships
4. **Best Practices**: Follows official ABBYY implementation patterns
5. **Rapid Prototyping**: Go from idea to working code in minutes, not hours

## 💻 Code Examples

### Basic Invoice Processing
```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    # Start invoice processing
    res = document_ai.models.invoice.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/invoice.pdf",
        },
    })

    doc_id = res.documents[0].id

    # Wait for processing to complete
    processed = False
    while not processed:
        time.sleep(3)
        result = document_ai.models.invoice.get_extracted_fields(
            document_id=doc_id
        )
        processed = result.invoice.meta.status == "Processed"

    # Access extracted data
    print(f"Invoice Number: {result.invoice.fields.invoice_number}")
    print(f"Total Amount: {result.invoice.fields.total_amount}")
    print(f"Vendor: {result.invoice.fields.vendor_name}")
```

### Document Conversion
```python
import abbyy_document_ai
from abbyy_document_ai import DocumentAi

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.document_conversion.begin_conversion(request={
        "input_source": {
            "url": "https://example.com/document.png",
        },
        "options": {
            "format_": abbyy_document_ai.DocumentConversionOutputFormat.PDF,
        },
    })

    print(f"Conversion started for document: {res.documents[0].id}")
```

### OCR Text Extraction
```python
from abbyy_document_ai import DocumentAi

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.image_to_text.begin_text_extraction(request={
        "input_source": {
            "url": "https://example.com/scanned_document.jpg",
        },
        "options": {
            "languages": "en",
            "handwriting": True,
        },
    })

    print(f"Text extraction started: {res.documents[0].id}")
```

## 🛠️ Installation & Setup

### Prerequisites
- Python 3.9 or higher
- ABBYY Document AI API key
- Node.js (for MCP server)

### Get Your API Key
1. Sign up at [ABBYY Document AI](https://www.abbyy.com/document-ai/)
2. Navigate to your dashboard
3. Generate an API key
4. Set it as an environment variable: `DOCUMENTAI_API_KEY_AUTH`

### Install Python SDK
```bash
# Using pip
pip install abbyy-document-ai

# Using poetry
poetry add abbyy-document-ai

# Using uv (for scripts)
uvx --from abbyy-document-ai python
```

## 🎯 Use Cases

### 📊 **Business Process Automation**
- Automate invoice processing and AP workflows
- Extract data from expense reports and receipts
- Process shipping and logistics documents
- Handle regulatory compliance documents

### 🏢 **Enterprise Integration**
- Integrate with ERP systems (SAP, Oracle, etc.)
- Connect to accounting software (QuickBooks, Xero)
- Build document management systems
- Create automated data entry solutions

### 🔬 **Data Analytics**
- Extract structured data from unstructured documents
- Build document classification systems
- Create data pipelines for business intelligence
- Analyze document patterns and trends

### 🚀 **Application Development**
- Build mobile apps with document scanning
- Create web applications with file upload processing
- Develop API integrations for document workflows
- Build AI-powered document assistants

## 🌟 Why Use This MCP Server?

### ✅ **For Technical Users**
- **Faster Development**: Skip documentation browsing, get instant code examples
- **Best Practices**: Learn optimal implementation patterns
- **Error Prevention**: Get guidance on common pitfalls and solutions
- **API Mastery**: Understand all available endpoints and parameters
- **Zero Debugging**: Code works on first try with accurate API calls

### ✅ **For Non-Technical Users**
- **No Coding Required**: Ask questions in plain English
- **Guided Learning**: Step-by-step assistance for building solutions
- **Concept Explanation**: Understand document AI capabilities and use cases
- **Implementation Planning**: Get help designing document processing workflows
- **Instant Prototypes**: Get working applications without technical knowledge

### ✅ **For Teams**
- **Consistent Standards**: Ensure all team members follow best practices
- **Knowledge Sharing**: Centralized access to ABBYY expertise
- **Faster Onboarding**: New team members get instant access to comprehensive knowledge
- **Reduced Support Tickets**: Self-service answers to common questions
- **Reliable Code Generation**: No more broken code from AI hallucinations

## 🎯 Real-World Application Examples

### **📊 Enterprise Document Processing Hub**
**Prompt**: *"Create a web application that processes multiple document types (invoices, receipts, shipping docs) and provides a dashboard with extracted data analytics."*

**AI Will Build**:
- Multi-file upload interface
- Document type auto-detection
- ABBYY API integration for each document type
- Real-time processing status
- Data visualization dashboard
- Export capabilities (JSON, CSV, Excel)

### **🔄 Automated Accounts Payable System**
**Prompt**: *"Build an AP automation system that processes invoices, validates against purchase orders, and integrates with QuickBooks."*

**AI Will Build**:
- Invoice upload and processing pipeline
- ABBYY invoice extraction integration
- PO matching logic
- Approval workflow system
- QuickBooks API integration
- Exception handling and notifications

### **📱 Mobile Document Scanner App**
**Prompt**: *"Create a mobile app that scans receipts and extracts expense data for business travelers."*

**AI Will Build**:
- Camera integration for document capture
- Image preprocessing and optimization
- ABBYY receipt processing API calls
- Expense categorization logic
- Cloud storage integration
- Expense report generation

### **🏢 Multi-Tenant SaaS Platform**
**Prompt**: *"Build a SaaS platform where businesses can upload documents and get structured data extraction with custom field mapping."*

**AI Will Build**:
- Multi-tenant architecture
- User authentication and authorization
- Custom field mapping interface
- ABBYY API integration with rate limiting
- Webhook notifications
- Usage analytics and billing integration

## 🔗 Links & Resources

- **🌐 MCP Server**: [https://context7.com/sarvottam-bhagat/abbyy-documentation](https://context7.com/sarvottam-bhagat/abbyy-documentation)
- **📖 ABBYY Document AI**: [Official Documentation](https://docs.abbyy.com/)
- **🔧 Context7**: [MCP Platform](https://context7.com)
- **📋 Model Context Protocol**: [Official Specification](https://modelcontextprotocol.io/)

## 🤝 Contributing

This repository contains the source documentation used to create the MCP server. To contribute:

1. Fork this repository
2. Make your improvements to the documentation
3. Submit a pull request
4. The MCP server will be automatically updated via Context7

## 📄 License

This project contains documentation and examples for the ABBYY Document AI API. Please refer to ABBYY's terms of service for API usage guidelines.

## 🆘 Support

- **MCP Server Issues**: Open an issue in this repository
- **ABBYY API Support**: Contact ABBYY support
- **Context7 Platform**: Visit [Context7 documentation](https://context7.com/docs)

---

**🚀 Ready to transform your document processing workflow? Connect the MCP server to your IDE and start building with ABBYY Document AI today!**
