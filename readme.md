# Radiology Report Generator

## Overview
This application uses fine-tuned Large Language Models to generate detailed radiology reports from chest X-ray images. It provides a user-friendly interface for healthcare professionals to upload X-ray images and receive professionally formatted radiology reports with findings and impressions.

<a href="https://www.youtube.com/embed/xtSYHhKyc9g?si=nMN_Ug-8PItGYT6F" target="_blank">
 <img src="https://i.ytimg.com/vi/xtSYHhKyc9g/hqdefault.jpg?sqp=-oaymwEnCNACELwBSFryq4qpAxkIARUAAIhCGAHYAQHiAQoIGBACGAY4AUAB&rs=AOn4CLAyedofLJSiRBJJGHdp40w7ziavfQ" alt="Watch the video" width="320" height="240" border="10" />
</a>


## Features
- **Multiple Model Support**: Choose from different fine-tuned LLMs (Llama, Qwen, Phi, GPT, Zephyr)
- **Professional Report Format**: Automatically structures reports with FINDINGS and IMPRESSION sections
- **User-Friendly Interface**: Clean, intuitive Streamlit web interface
- **Report Download**: Download generated reports as text files
- **Debug Mode**: Optional debug features for development and troubleshooting

## Technology Stack
- **Frontend**: Streamlit
- **Backend**: PyTorch, Transformers, Lightning
- **Models**:
  - Vision Transformer (Swin Tiny) for image encoding
  - Various LLMs for text generation (Llama-3.2-3B, Qwen2-1.5B, Phi-2, Cerebras-GPT-1.3B, StableLM-Zephyr-3B)
- **Deployment**: Ngrok for tunneling

## Requirements
Requirements are listed in `requirements.txt`. The main dependencies include:
- streamlit
- torch
- transformers
- lightning
- pyngrok
- matplotlib
- pillow

## Setup and Installation

### Local Installation
1. download the file
   ```bash
   download project_user_interface.ipynb
   ```

2. Install dependencies
   ```bash
   pip install -r requirements.txt
   ```

3. Run the application
   ```bash
   streamlit run app.py
   ```

### Google Colab Installation
1. Upload the notebook to Google Colab
2. Run the cells to install dependencies
3. Set up Hugging Face access token if needed
4. Run the Streamlit app with Ngrok for public access

## Model Structure
The application uses a two-stage approach:
1. **Image Encoding**: X-ray images are processed through a vision transformer to extract visual features
2. **Report Generation**: The visual features are fed into a fine-tuned LLM with a specialized prompt to generate the radiology report

The `R2GenGPT` class integrates these components, providing a seamless pipeline from image to report.

## Directory Structure
```
radiology-report-generator/
├── app.py                    # Main Streamlit application
├── models/                   # Directory for model checkpoints
│   ├── llama-3.2-3b/
│   ├── qwen2-1.5b/
│   ├── phi-2/
│   ├── gpt-1.3b/
│   └── stablelm-zephyr-3b/
├── requirements.txt          # Python dependencies
└── README.md                 # Project documentation
```

## Usage
1. Start the application
2. Select a model from the dropdown menu
3. Upload a chest X-ray image (JPG, JPEG, or PNG)
4. Click "Generate Report"
5. View the generated report in the right panel
6. Download the report as a text file if needed

## Development
The application includes a debug mode that provides additional information for development:
- Raw model output
- Processed report text
- Tokenizer information
- Error logs

Enable debug mode by checking the "Debug Mode" checkbox in the sidebar.

## Fallback Mechanisms
The application includes multiple fallback mechanisms to ensure reliability:
- Alternative generation parameters if the primary approach fails
- Post-processing to ensure proper report formatting
- Default report templates for error cases

## License
MIT License 1.0

## Citation
If you use this project in your research, please cite:
```
@software{radiology_report_generator,
  author = {Amirparsa Rouhi},
  title = {Radiology Report Generator},
  year = {2025},
  url = {https://github.com/ai-art-dev99/xray-report-generation}
}
```

## Acknowledgments
- Hugging Face for model repositories
- PyTorch and Lightning for deep learning frameworks
- Streamlit for the web interface
