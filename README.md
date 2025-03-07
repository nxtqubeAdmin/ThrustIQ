# ThrustIQ
ThrustIQ is an AI-powered edge computing module designed for real-time propeller health assessment. Utilizing computer vision and deep learning, the system captures top-down images of drone propellers, analyzes their condition, and detects potential anomalies.


Key Features

Automotive-Grade Camera Integration: Captures high-resolution images in low-light environments inside the docking station.

Edge AI Processing: Runs inference on Raspberry Pi with optimized AI models.

Global Shutter Support: Reduces motion blur for accurate propeller diagnostics.

Scalable Architecture: Can be extended for multiple drone types and configurations.

Secure & Efficient Data Handling: Optimized for on-device inference with optional cloud sync.

Repository Structure

ThrustIQ/
│-- backend/                 # AI inference and API services
│-- models/                  # Pre-trained AI models for propeller analysis
│-- hardware/                # Raspberry Pi and camera interface code
│-- docs/                    # Documentation and setup guides
│-- scripts/                 # Utility scripts for data processing
│-- tests/                   # Unit and integration tests
│-- README.md                # Project documentation (this file)

Getting Started

Prerequisites

Hardware Requirements:

Raspberry Pi 4 or Jetson Nano

Selected automotive-grade camera (Sony IMX390 / Arducam IMX519)

Adequate storage (≥32GB microSD)

Software Requirements:

Python 3.8+

TensorFlow / PyTorch (optimized for edge AI)

OpenCV for image processing

Raspberry Pi OS (or Ubuntu 20.04 for Jetson)

Installation

Clone the Repository:

git clone https://github.com/QubeNetwork/ThrustIQ.git
cd ThrustIQ

Install Dependencies:

pip install -r requirements.txt

Set Up Camera Driver (For Raspberry Pi):

sudo raspi-config  # Enable CSI Camera

Run the AI Module:

python3 main.py

Usage

Capture Propeller Image

The system automatically captures images when a drone lands.

Supports manual image capture for debugging:

python3 capture.py --output test_image.jpg

Run AI-Based Propeller Analysis

python3 analyze.py --image test_image.jpg

View Results

The AI model outputs a health score (0-100) and highlights anomalies.

Logs are stored in logs/propeller_analysis.log.

API Endpoints

ThrustIQ provides a REST API for integrating with external services.

Endpoint

Method

Description

/analyze

POST

Uploads an image and returns health score

/status

GET

Returns system health & camera status

/logs

GET

Retrieves recent analysis logs

Example API Call:

curl -X POST -F "file=@test_image.jpg" http://localhost:5000/analyze

Testing

Run unit and integration tests before deployment:

pytest tests/

Deployment

For production deployment, use Docker:

docker build -t thrustiq-ai .
docker run -d -p 5000:5000 thrustiq-ai

Contributing

Fork the repository and create a feature branch.

Follow the code style guidelines (PEP8 for Python).

Submit a pull request with a detailed description.

License

This project is licensed under the MIT License. See LICENSE for details.

Contact

For support, contact the ThrustIQ Development Team at support@nxtqube.com.
