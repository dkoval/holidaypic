# Holiday Pic: Daily Stylized Avatar/Brand Image Generator

This Python script generates a unique daily image based on a holiday theme and sends it via email. It uses AI-powered image generation and integrates with various services to create a personalized experience.

## Features

- Generates a daily holiday prompt using AI
- Creates a custom image using Replicate's AI image generation
- Sends the generated image via email
- Uses environment variables for configuration
- Provides interactive prompts for missing configuration

## Prerequisites

- Python 3.6+
- A Gmail account (for sending emails)
- Replicate API access

## Installation

1. Clone this repository or download the `holidaypic.py` script.
2. Install the required Python packages:

```bash
pip install python-dotenv replicate colorama requests
```

3. Create a `.env.local` file in the same directory as the script with the following variables:

```
SENDER_EMAIL=your_gmail@gmail.com
SENDER_PASSWORD=your_gmail_one_time_app_password #google one-time app password for Gmail
RECEIVER_EMAIL=recipient@example.com
CONTROL_IMAGE=https://example.com/path/to/control/image.jpg
```

## Usage

Run the script using Python:

```bash
python holidaypic.py
```

If any required environment variables are missing, the script will prompt you to enter them interactively.

## How It Works

1. The script generates a holiday prompt using AI.
2. It uses the generated prompt to create a custom image with Replicate's AI image generation service.
3. The generated image is then sent via email to the specified recipient.

## Configuration

- `SENDER_EMAIL`: The Gmail address used to send the email
- `SENDER_PASSWORD`: An App Password for your Gmail account (see script output for instructions on creating one)
- `RECEIVER_EMAIL`: The email address that will receive the generated image
- `CONTROL_IMAGE`: URL of the control image used in the AI image generation process
- `REPLICATE_API`: Your Replicate API key for accessing the AI image generation service

## Note

Make sure to keep your `.env.local` file secure and never commit it to version control systems.

## Setting Up Daily Execution

1. Create `run_holidaypic.sh`:

   ```bash
   #!/bin/bash
   cd /path/to/script/directory
   /path/to/python3 holidaypic.py
   ```

   Adjust paths as needed. Add `--no-email` at the end to skip sending emails.

2. Make it executable:

   ```
   chmod +x run_holidaypic.sh
   ```

3. Add to crontab:

   ```
   crontab -e
   ```

   Add this line to run daily at 9 AM:

   ```
   0 9 * * * /path/to/run_holidaypic.sh
   ```

4. Save and exit the crontab editor.

The script will now run automatically every day at 9 AM, generating an image and emailing it by default.

### Usage Options

- To generate an image and email it (default behavior):
  ```
  python3 holidaypic.py
  ```

- To generate an image without emailing:
  ```
  python3 holidaypic.py --no-email
  ```

Note: Ensure your machine is on at the scheduled time.