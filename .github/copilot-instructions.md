# Copilot Instructions for TruthShield

## Overview
TruthShield is a multi-component project aimed at detecting fake news and deepfake videos. It consists of the following major components:

1. **Chrome Extension**: Provides a user interface for detecting fake news.
   - Located in `Extension/`
   - Key files: `background.js`, `popup.html`, `script.js`

2. **Backend Models**:
   - **Deepfake Video Detection**:
     - Located in `Models_Backend/Deepfake_Video/`
     - Key file: `deepfake.py`
     - Uses PyTorch and a Vision Transformer (ViT) model for video analysis.
   - **Text Fake News Detection**:
     - Located in `Models_Backend/Textfakedetection/`
     - Key file: `FakenewsApi.py`
     - Uses FastAPI and integrates with the Groq API for text verification.

3. **Website**:
   - **Frontend**:
     - Located in `Website/Frontend/`
     - Built with React and Vite.
   - **Backend**:
     - Located in `Website/Backend/`
     - Key file: `index.js`

## Developer Workflows

### Running the Backend APIs
- **Deepfake Video Detection**:
  ```bash
  python -m uvicorn deepfake:app --host 127.0.0.1 --port 8002 --reload
  ```
- **Text Fake News Detection**:
  ```bash
  uvicorn FakenewsApi:app --reload
  ```

### Frontend Development
- Navigate to `Website/Frontend/` and run:
  ```bash
  npm install
  npm run dev
  ```

### Backend Development
- Navigate to `Website/Backend/` and run:
  ```bash
  npm install
  node index.js
  ```

## Project-Specific Conventions

1. **API Endpoints**:
   - Deepfake Video Detection:
     - `/predict`: Accepts video files for analysis.
     - `/predict_url`: Accepts video URLs for analysis.
   - Text Fake News Detection:
     - `/verify_newstext`: Accepts text for verification.
     - `/verify_Imagearticle`: Accepts text or image files for verification.

2. **Frontend Styling**:
   - CSS files are colocated with their respective components.
   - Use `cursor: pointer;` for interactive elements.

3. **Model Loading**:
   - Deepfake model is loaded from `best_vit_model.pth`.
   - Ensure the model file is present in `Models_Backend/Deepfake_Video/`.

4. **Environment Variables**:
   - Store sensitive keys (e.g., `GROQ_API_KEY`) in a `.env` file.

## Integration Points

- **Frontend to Backend**:
  - The Chrome extension and React frontend communicate with the FastAPI backend via HTTP requests.
- **Backend Models**:
  - The backend APIs use pre-trained models for predictions.
  - Ensure dependencies like `torch`, `timm`, and `easyocr` are installed.

## External Dependencies

- **Python**:
  - `torch`, `timm`, `fastapi`, `uvicorn`, `easyocr`
- **Node.js**:
  - `vite`, `react`, `express`

## Examples

### Adding a New API Endpoint
1. Define the endpoint in the relevant FastAPI app (e.g., `deepfake.py` or `FakenewsApi.py`).
2. Update the frontend to call the new endpoint.

### Debugging
- Use `console.log` in JavaScript files and `print` in Python files for debugging.
- Check logs in the terminal for errors.

---

Feel free to update this document as the project evolves.