# Sample Output Files

This directory contains example outputs from the Text Summarization MVP.

## Files Included

### 1. `sample_summary.md`
- **Format**: Markdown
- **Use Case**: Documentation, GitHub, blogs
- **Features**: Collapsible sections, metadata, statistics

### 2. `sample_summary.json`
- **Format**: JSON
- **Use Case**: API integration, data pipelines
- **Features**: Structured data, ISO timestamps, complete metadata

### 3. `sample_summary.mp3` (Not Included)
- **Format**: Audio (MP3)
- **Use Case**: Accessibility, listening while commuting
- **Features**: Text-to-speech in 10 languages
- **Note**: Audio files not included in git due to size (typically 50-150KB)
- **How to Generate**: Run the application and use "Export as Audio" feature

### 4. `sample_summary.pdf` (Not Included)
- **Format**: PDF
- **Use Case**: Professional reports, printing
- **Features**: Formatted document with title, metadata, summary
- **Note**: PDF files not included in git
- **How to Generate**: Run the application and use "Export as PDF" feature

## Sample Text Used

**Input**:
```
Artificial Intelligence has become one of the most transformative technologies
of our time. From virtual assistants to self-driving cars, AI is reshaping
how we live and work. Machine learning algorithms power recommendation systems,
detect fraud, and assist in medical diagnostics. Natural language processing
enables human-like text generation and understanding. As AI continues to evolve,
ethical considerations around bias, privacy, and employment become increasingly
important for responsible development.
```

**Output Summary**:
```
Artificial intelligence has become one of the most transformative technologies
of our time. from virtual assistants to self-driving cars, AI is reshaping how
we live and work. machine learning algorithms power recommendation systems,
detect fraud, and assist in medical diagnostics.
```

**Statistics**:
- Original: 67 words
- Summary: 26 words
- Compression: 65.2%
- Model: T5 Small

## Generating Your Own Samples

To create your own sample exports:

1. Run the application
2. Generate a summary
3. Navigate to "Export" tab
4. Click export buttons for each format
5. Files saved to `./exports/` directory

## Export Format Comparison

| Format | File Size | Best For | Processing Time |
|--------|-----------|----------|-----------------|
| Markdown | 1-2 KB | Documentation | Instant |
| JSON | 1-2 KB | APIs | Instant |
| Audio | 50-150 KB | Accessibility | 2-5 seconds |
| PDF | 2-5 KB | Reports | 1-2 seconds |

---

**Note**: All sample files use the same input text for consistency and comparison purposes.
