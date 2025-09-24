Cricketer Image Recognition App
A web application that identifies famous cricketers from an uploaded image. This project leverages a pre-trained deep learning model to perform feature extraction and comparison, all served through a simple and user-friendly interface built with Flask.

🚀 Features
Image Upload: Simple interface to upload a JPG or PNG image.

AI-Powered Recognition: Uses the VGG16 deep learning model to identify the cricketer.

Confidence Score: Displays the similarity score to show how confident the model is in its prediction.

Customizable Library: Easily add or update the library of recognizable cricketers by adding their images.

Responsive UI: A clean and simple front-end that works on different screen sizes.

🛠️ Tech Stack
Backend: Python, Flask

Machine Learning: TensorFlow, Keras, Scikit-learn

Image Processing: Pillow, NumPy

Frontend: HTML5, Tailwind CSS (via CDN)

⚙️ Setup and Installation
Follow these steps to get the application running on your local machine.

1. Prerequisites
Make sure you have Python 3.9 or newer installed on your system.

2. Clone the Repository
git clone [https://github.com/your-username/cricketer-recognition-app.git](https://github.com/your-username/cricketer-recognition-app.git)
cd cricketer-recognition-app

3. Create a Virtual Environment
It's highly recommended to use a virtual environment to manage project dependencies.

On Windows:

python -m venv venv
venv\Scripts\activate

On macOS & Linux:

python3 -m venv venv
source venv/bin/activate

4. Install Dependencies
Install all the required Python packages using the requirements.txt file.

pip install -r requirements.txt

(This may take a few minutes as TensorFlow is a large library.)

5. Add Reference Images (Crucial Step)
The model needs a library of images to compare against. You must create sub-folders inside the cricketer_images directory for each cricketer you want to recognize.

The folder structure should look like this:

/cricketer_images
    |-- /Virat_Kohli
    |   |-- image1.jpg
    |   |-- image2.png
    |   |-- ...
    |-- /MS_Dhoni
    |   |-- dhoni_pic1.jpg
    |   |-- another_photo.jpeg
    |   |-- ...

The application will use the folder name (e.g., "Virat_Kohli") as the cricketer's name in the prediction.

6. Run the Application
Once the setup is complete, you can start the Flask server.

flask run

Open your web browser and navigate to http://127.0.0.1:5000 to use the app.

🤖 How It Works
The recognition process is broken down into a few key steps:

Model Loading: The application loads the VGG16 model, pre-trained on the ImageNet dataset, without its final classification layer. We use the output of the fc1 layer as a high-level feature extractor.

Reference Feature Extraction: On startup, the app scans the cricketer_images directory. For each cricketer's sub-folder, it processes all images, extracts their feature vectors using the VGG16 model, and calculates an average feature vector for that cricketer. This creates a robust digital signature for each person.

User Upload & Feature Extraction: When a user uploads an image, it is pre-processed to the required size (224x224) and its feature vector is extracted using the same model.

Similarity Comparison: The feature vector of the uploaded image is compared against the pre-computed average vectors of all known cricketers using Cosine Similarity. This mathematical function measures the cosine of the angle between two vectors, providing a score of how similar they are.

Prediction: The cricketer with the highest similarity score is presented as the prediction, as long as the score is above a set confidence threshold.

📂 Project Structure
├── app.py                  
├── requirements.txt          
├── templates/
│   └── index.html          
├── static/
│   └── uploads/            
└── cricketer_images/        


![Screenshot_24-9-2025_211010_127 0 0 1](https://github.com/user-attachments/assets/2e1403f7-66c4-4b8f-b40a-78fe7c386cdb)


