# DashTailor - AI Clothing Transfer

DashTailor is a Gradio-based web interface that allows users to transfer clothing from one image to another using AI. It leverages ComfyUI for the underlying image processing and transformation.

## Prerequisites

- Python 3.10+
- ComfyUI server running locally or remotely
- Required Python packages (install via pip):
  ```bash
  pip install gradio
  pip install Pillow
  pip install websocket-client
  pip install requests
  pip install numpy
  ```

## Setup

1. Clone the repository:
   ```bash
   git clone [repository-url]
   cd ai-clothes-transfer-gradio
   ```

2. Ensure ComfyUI is running with the following models:
   - VAE: `ae.safetensors`
   - CLIP: 
     - `t5xxl_fp16.safetensors`
     - `clip_l.safetensors`
   - UNET: `flux-dev-fill.safetensors`
   - Style Model: `flux-redux.safetensors`
   - CLIP Vision: `sigclip_vision_patch14_384.safetensors`

3. Update the server address in `app.py`:
   ```python
   server_address = "your_comfyui_server:port"  # default is "127.0.0.1:8188"
   ```

## Running the Application

1. Start the Gradio interface:
   ```bash
   python app.py
   ```

2. Open your web browser and navigate to the URL shown in the terminal (typically `http://127.0.0.1:7860`)

## Usage

1. **Source Clothing Image**
   - Upload an image containing the clothing you want to transfer
   - Use the brush tool to paint over the clothing area (this creates the mask)
   - The masked area will be transferred to the target image

2. **Target Person Image**
   - Upload an image of the person who will receive the clothing
   - Use the brush tool to paint where you want the clothing to appear
   - This guides the AI in placement

3. Click "Generate" to start the transfer process

## Tips for Best Results

- Use clear, well-lit images
- Make precise masks around the clothing areas
- For upper body clothing changes, mask only the upper body in both images
- Use a smaller brush size for detailed masking
- Ensure the target pose somewhat matches the source clothing pose
