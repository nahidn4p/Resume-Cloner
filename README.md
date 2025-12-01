# ATS Resume Cloner

An intelligent resume transformation tool that converts any resume (PDF, DOCX, or TXT) into a perfectly formatted ATS-friendly resume using your custom template. Powered by Groq's LLM API for accurate data extraction.

## Features

- 📄 **Multi-format Support**: Accepts PDF, DOCX, and TXT resume files
- 🤖 **AI-Powered Extraction**: Uses Groq's Llama models to extract structured data from resumes
- 🎨 **Template-Based Formatting**: Applies your custom resume template with consistent styling
- 🌐 **Web Interface**: User-friendly Gradio UI for easy interaction
- 🔄 **Automatic Formatting**: Preserves your template's exact formatting (fonts, colors, spacing, bullets)

## Prerequisites

- Python 3.8 or higher
- A Groq API key ([Get one here](https://console.groq.com/))
- Your resume template file (`main_resume.docx`) [Put the file in Same Folder]

## Installation

1. **Clone or download this repository**

2. **Create a virtual environment** (recommended):
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

## Setup

1. **Get your Groq API Key**:
   - Sign up at [Groq Console](https://console.groq.com/)
   - Navigate to API Keys section
   - Create a new API key

2. **Create a `.env` file** in the project root:
   ```bash
   touch .env  # On Windows: type nul > .env
   ```

3. **Add your Groq API key to `.env`**:
   ```env
   GROQ_API_KEY=your_groq_api_key_here
   ```

   Optionally, you can also specify a custom model:
   ```env
   GROQ_API_KEY=your_groq_api_key_here
   GROQ_MODEL=llama-3.1-8b-instant
   ```

4. **Ensure your template file is present**:
   - Make sure `main_resume.docx` is in the project root directory
   - This is your base template that will be used for formatting

## Usage

1. **Start the application**:
   ```bash
   python main.py
   ```

2. **Access the web interface**:
   - The terminal will display a local URL (e.g., `http://127.0.0.1:7860`)
   - A public shareable URL will also be generated (if `share=True` is set)
   - Open either URL in your web browser

3. **Use the interface**:
   - Upload a candidate's resume (PDF, DOCX, or TXT format)
   - Click "Generate My ATS-Style Resume"
   - Download the generated resume and review the extracted JSON data

## Project Structure

```
resume-cloner/
├── main.py                 # Main application code
├── requirements.txt        # Python dependencies
├── main_resume.docx       # Your resume template (required)
├── .env                   # Environment variables (create this)
└── README.md             # This file
```

## How It Works

1. **File Reading**: The tool reads the uploaded resume (supports PDF, DOCX, TXT)
2. **Data Extraction**: Groq's LLM extracts structured information (name, contact, experience, education, skills, etc.)
3. **Template Application**: The extracted data is inserted into your `main_resume.docx` template
4. **Formatting Preservation**: Your template's exact styling (fonts, colors, bullets, spacing) is maintained
5. **Output**: A new formatted resume is generated and made available for download

## Configuration

### Changing the Model

By default, the tool uses `llama-3.1-8b-instant`. To use a different model, add to your `.env`:

```env
GROQ_MODEL=llama-3.1-70b-versatile
```

Check [Groq's documentation](https://console.groq.com/docs/models) for available models.

### Customizing the Template

Edit `main_resume.docx` to match your preferred resume style. The tool will:
- Replace the name and contact information
- Update the portfolio/links section
- Fill in the summary
- Populate the skills matrix
- Add education entries
- Insert work experience with proper formatting

## Troubleshooting

### "GROQ_API_KEY not found"
- Ensure your `.env` file exists in the project root
- Verify the API key is correctly set: `GROQ_API_KEY=your_key_here`
- Make sure `python-dotenv` is installed

### "Model decommissioned" error
- Update `GROQ_MODEL` in your `.env` to a currently supported model
- Check [Groq's deprecation notices](https://console.groq.com/docs/deprecations)

### Template file not found
- Ensure `main_resume.docx` is in the same directory as `main.py`
- Check the file name matches exactly (case-sensitive)

### Port already in use
- If port 7860 is busy, Gradio will automatically use another port
- Check the terminal output for the actual URL

## Dependencies

- `gradio` - Web interface framework
- `python-docx` - Word document manipulation
- `pymupdf` - PDF reading (fitz)
- `groq` - Groq API client
- `python-dotenv` - Environment variable management

## License

This project is provided as-is for personal or commercial use.

## Support

For issues related to:
- **Groq API**: Check [Groq Documentation](https://console.groq.com/docs)
- **This tool**: Review the code comments in `main.py` or open an issue

---

**Note**: Make sure to keep your `.env` file private and never commit it to version control. The `.gitignore` file should already exclude it.

