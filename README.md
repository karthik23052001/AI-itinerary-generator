# Travel Itinerary Generator

A web application that helps users plan their trips by generating a travel itinerary based on a destination. It fetches and displays weather information for the location and allows users to download the itinerary as a PDF.

## Features

* **Dynamic Itinerary Generation:** Creates a travel plan based on user input (e.g., destination, duration - *details of input depend on your application's specific form*).
* **Weather Information:** Displays current and forecasted weather conditions for the chosen destination.
* **Markdown Itinerary:** Presents the travel plan in a clean, readable format using Markdown.
* **PDF Download:** Allows users to download the complete itinerary, including weather information, as a PDF document.
* **Responsive Design:** Built with Bootstrap for a good experience on various devices.
* **Custom 404 Page:** Provides a user-friendly "Not Found" page.

## Technologies Used

* **Backend:** Python, Flask (for generating content dynamically)
* **Frontend:** HTML, CSS, JavaScript
* **Templating Engine:** Jinja2
* **Styling:** Bootstrap 5
* **Markdown Rendering (Client-Side):** `markdown-it.js`
* **PDF Generation (Client-Side):** `html2pdf.js`

## Project Structure

```
Travel-Itinerary-Generator-main/
├── app.py                  # Main Flask application logic (Python backend)
├── requirements.txt        # Python dependencies for the Flask app
├── static/                 # Static assets (images, CSS, client-side JS)
│   ├── background.png      # Background image for the dashboard
│   └── logo.svg            # Favicon/logo
├── templates/              # HTML templates (rendered by Flask)
│   ├── dashboard.html      # Displays the weather and itinerary
│   ├── headers.html        # Common header, including navigation and PDF download button
│   └── 404.html            # Custom 404 error page
└── README.md               # This file
```

## Setup and Local Development (Running the Flask App)

To run this project locally (for development or to generate static files):

1. **Clone the repository:**

   ```bash
   git clone https://github.com/karthik23052002/Travel-Itinerary-Generator-main.git
   cd Travel-Itinerary-Generator-main
   ```
2. **Create and activate a virtual environment (recommended):**

   ```bash
   python -m venv venv
   ```

   * On macOS/Linux: `source venv/bin/activate`
   * On Windows: `venv\Scripts\activate`
3. **Install dependencies:**
   Create a `requirements.txt` file in your project root with the necessary Python packages. For a typical Flask app like this, it might include:

   ```txt
   Flask
   python-dotenv  # If you use .env files for API keys
   requests       # If you make external API calls from Python
   # Add other specific Python libraries your app.py uses
   ```

   Then install them:

   ```bash
   pip install -r requirements.txt
   ```
4. **Set up Environment Variables (if applicable):**
   If your `app.py` uses API keys (e.g., for a weather service or an AI model for itinerary generation), create a `.env` file in the project root:

   ```
   OPENAI_API_KEY=your_openai_api_key_here
   WEATHER_API_KEY=your_weather_api_key_here
   ```

   Ensure your `app.py` is configured to load these (e.g., using `python-dotenv`).
5. **Run the Flask application:**

   ```bash
   flask run
   ```

   (Or `python app.py` if you have `app.run(debug=True)` in your script).
6. Open your browser and navigate to `http://127.0.0.1:5000/` (or the port your app runs on).

## Deployment to GitHub Pages (Static Site)

GitHub Pages hosts **static** websites. Since this is a Flask (Python) application, you cannot run the Python backend directly on GitHub Pages. To deploy, you need to:

1. **Generate Static HTML Files:**

   * Run your Flask application locally (as described above).
   * Navigate to the page(s) you want to publish (e.g., the dashboard page after an itinerary has been generated).
   * Save the fully rendered HTML page from your browser (usually "File > Save Page As..." or "View Source" and save the content).
     * The `dashboard.html` (once rendered with data) should ideally be saved as `index.html` to serve as the main page of your GitHub Pages site.
     * Ensure all Jinja2 template tags (`{{ ... }}`, `{% ... %}`) are replaced with actual content in these saved files.
   * Your `404.html` is already static and can be used directly.
2. **Organize Files for Deployment:**
   Your repository for GitHub Pages should look something like this:

   ```
   your-repository-name/
   ├── index.html          # (The statically generated dashboard.html)
   ├── 404.html            # Your custom 404 page
   ├── static/             # Folder for assets
   │   ├── background.png
   │   └── logo.svg
   └── README.md           # (Optional for the live site, but good for the repo)
   ```
3. **Commit and Push to GitHub:**
   Add these static files to your Git repository and push them to GitHub.
4. **Enable GitHub Pages:**

   * Go to your repository on GitHub.com.
   * Click on **"Settings"** > **"Pages"** (in the left sidebar).
   * Under "Build and deployment":
     * For **"Source"**, select **"Deploy from a branch"**.
     * Choose the **branch** (e.g., `main`).
     * Choose the **folder** (`/ (root)` if your `index.html` is at the root, or `/docs` if it's in a `docs` folder).
     * Click **"Save"**.
   * Your site will be available at `https://your-username.github.io/your-repository-name/`.

## How to Use (Generated Site on GitHub Pages)

Once deployed as a static site:

1. Navigate to your GitHub Pages URL.
2. The `index.html` (which was your `dashboard.html` with pre-filled data) will display the itinerary and weather information.
3. The "Download PDF" button (likely in the header, as defined in `headers.html` and included in your static `index.html`) can be used to download the displayed itinerary.

*Note: Since it's a static site, the itinerary and weather data will be fixed based on what you generated and saved. To update it, you'd need to re-generate the static HTML and push the changes.*

## Contributing

Contributions are welcome! If you have suggestions or improvements:

1. Fork the Project.
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the Branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

## License

Distributed under the MIT License. See `LICENSE.txt` for more information.
*(You'll need to add a `LICENSE.txt` file with the MIT License text if you choose this license).*
