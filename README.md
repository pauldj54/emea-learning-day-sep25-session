# Azure AI Search Document-Level Access Control Demo

This notebook demonstrates how to create and use Azure AI Search indexes with document-level access control using group-based permissions.

## Prerequisites

- Azure AI Search service with RBAC enabled
- Azure CLI installed and logged in (`az login`)
- Python 3.8+ with required packages installed

## Setup

1. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

2. **Configure Environment**
   - Update `.env` with your Azure AI Search endpoint
   - Ensure you're authenticated via Azure CLI

3. **Required Azure Permissions**
   - Search Service Contributor
   - Search Index Data Contributor
   - Search Index Data Reader

## Notebook Structure

The notebook contains 8 cells that execute in sequence:

1. **Introduction** - Overview of the demo
2. **Import Libraries** - Load required Azure SDK and Python packages
3. **Load Environment** - Configure connection settings from `.env`
4. **Create Search Client** - Initialize Azure AI Search client with DefaultAzureCredential
5. **List Existing Indexes** - Display current indexes in the search service
6. **Create Index** - Create new index with document-level access control fields
7. **Define Document Permissions** - Map PDF files to group permissions
8. **Process & Upload Documents** - Extract text from PDFs and upload with access controls

## Usage

1. Place PDF files in the `/docs` folder
2. Update the `document_permissions` list in cell 7 with appropriate group IDs
3. Run all cells sequentially
4. The notebook will:
   - Extract text from PDF files using PyPDF2
   - Create documents with group-based access control
   - Upload documents to Azure AI Search with permission metadata

## Features

- **Secure Authentication**: Uses DefaultAzureCredential (no API keys)
- **Document-Level Security**: Group-based access control for search results
- **PDF Processing**: Automatic text extraction from PDF documents
- **Error Handling**: Comprehensive error reporting and status updates

## Files

- `azure_search_test.ipynb` - Main notebook
- `.env` - Azure AI Search configuration
- `requirements.txt` - Python dependencies
- `/docs/` - PDF documents to process

## Notes

- The preview version of Azure AI Search SDK is required for document-level access control
- Group IDs should be valid Azure AD group identifiers for production use
- Documents are indexed with base64-encoded path as the unique document ID