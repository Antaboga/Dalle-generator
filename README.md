---

# DALL-E Style Image Generator

This repository contains a web-based image generator that utilizes the DALL-E API to generate images based on user-provided prompts. Users can enter a prompt, and the app will display four AI-generated images in a stylish grid format with a glowing "glassmorphism" effect.

## Features

- **Prompt-based Image Generation**: Allows users to enter custom prompts to generate unique images.
- **Stylish UI**: The interface features a dark theme with "glow in the dark" elements and a glassmorphism style for a modern, futuristic look.
- **Image Grid Display**: Displays four generated images in a responsive 2x2 grid layout.

## Tech Stack

- **HTML, CSS**: For structuring and styling the user interface.
- **JavaScript (async/await)**: To handle the image generation requests to the DALL-E API.
- **DALL-E API**: Provides the image generation functionality based on user prompts.

## Preview

![Preview](link-to-screenshot-or-demo.gif)  
*(Add a screenshot or demo link here)*

## Setup and Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/your-username/dalle-style-image-generator.git
   cd dalle-style-image-generator
   ```

2. Open the `index.html` file in a web browser to test it locally.

3. Make sure to have an internet connection to reach the DALL-E API endpoint.

## How It Works

1. Enter a prompt in the input box describing the image you want.
2. Click the **Generate Images** button.
3. The application sends a request to the DALL-E API with the provided prompt.
4. Four generated images are displayed in a 2x2 grid.

## Customization

- **Styling**: You can modify the CSS for a different visual appearance.
- **API Endpoint**: Change the API endpoint if you're using a different image generation service.

## Code Snippets

Here's the core JavaScript function that makes the API call and handles multiple image generation:

```javascript
async function generateImages() {
    const prompt = document.getElementById("prompt").value;
    const output = document.getElementById("output");

    if (!prompt) {
        alert("Please enter a prompt to generate images.");
        return;
    }

    output.innerHTML = "Generating images...";

    try {
        output.innerHTML = "";
        for (let i = 0; i < 4; i++) {
            const response = await fetch(`https://aemt.uk.to/dalle?text=${encodeURIComponent(prompt)}`);
            if (response.ok) {
                const blob = await response.blob();
                const imageUrl = URL.createObjectURL(blob);
                const img = document.createElement("img");
                img.src = imageUrl;
                output.appendChild(img);
            }
        }
    } catch (error) {
        console.error("Error:", error);
        output.innerHTML = "Error generating images. Please try again.";
    }
}
```

## License

This project is open-source and available under the [MIT License](LICENSE).

## Acknowledgements

- [DALL-E API](https://openai.com/dall-e) for image generation capabilities.
- UI inspired by modern, minimalist designs with glassmorphism and neon glow effects.

---
