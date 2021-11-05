# Capstone_Rabi_Realtime_Sign_Language
## Tensorflow Sign Detection Walkthrough
<p>This set of Notebooks provides a complete set of code to be able to train and leverage your own custom sign detection model using the Tensorflow Object Detection API.
  
## Steps
<br />
<b>Step 1.</b> Clone this repository and go to TFOD folder.
<br/><br/>
<b>Step 2.</b> Create a new virtual environment inside tfod folder.
<pre>
python -m venv tfod
</pre> 
<br/>
<b>Step 3.</b> Activate your virtual environment
<pre>
source tfod/bin/activate # Linux
.\tfod\Scripts\activate # Windows 
</pre>
<br/>
<b>Step 4.</b> Install dependencies and add virtual environment to the Python Kernel
<pre>
python -m pip install --upgrade pip
pip install ipykernel
python -m ipykernel install --user --name=tfodj
</pre>
<br/>
<b>Step 5.</b> Collect images using the Notebook Image Collection.ipynb.
<br/><br/>
<b>Step 6.</b> Manually divide collected images into two folders train and test. So now all folders and annotations should be split between the following two folders. <br/>
Tensorflow\workspace\images\train<br />
Tensorflow\workspace\images\test
<br/><br/>
<b>Step 7.</b> Begin training process by opening Training and Detection.ipynb, this notebook will walk you through installing Tensorflow Sign Detection, making detections, saving and exporting your model. 
<br /><br/>
<b>Step 8.</b> During this process the Notebook will install Tensorflow Sign Detection. You should ideally receive a notification indicating that the API has installed successfully at Step 8 with the last line stating OK.  
If not, resolve installation errors by referring to the Error Guide.md in this folder.
<br /> <br/>
<b>Step 9.</b> Once you get to step 6. Train the model, inside of the notebook, you may choose to train the model from within the notebook. I have noticed however that training inside of a separate terminal on a Windows machine you're able to display live loss metrics.  
<br /> <br/>
<b>Step 10.</b> You can optionally evaluate your model inside of Tensorboard. Once the model has been trained and you have run the evaluation command under Step 7. Navigate to the evaluation folder for your trained model e.g. 
<pre> cd Tensorlfow/workspace/models/my_ssd_mobnet/eval</pre> 
and open Tensorboard with the following command
<pre>tensorboard --logdir=. </pre>
Tensorboard will be accessible through your browser and you will be able to see metrics including mAP - mean Average Precision, and Recall.
<br />


## Demo React Application for the project
<p>This app can be used for real time sign detection by leveraging the Tensorflow Object Detection API, React and Tensorflow JS. After complete above training task download model json file.
  
## Steps
<br />
<b>Step 1.</b> In this repo go to TFODApp folder.
<br/><br/>
<b>Step 2.</b> Install Node https://nodejs.org/en/
<br/><br/>
<b>Step 3.</b> Install App Depdendencies 
<pre>npm install</pre>
<br/>
<b>Step 4.</b> Create a new free object storage repository on IBM Cloud <a href="https://cloud.ibm.com/objectstorage/create">Create Cloud Object Storage Bucket</a> 
<br/><br/>
<b>Step 5.</b> Create a new bucket and store model.json and .bin files into the bucket.</a> 
<br/><br/>
<b>Step 6.</b> Enable public access policy.</a> 
<br/><br/>
<b>Step 7.</b> Download and install the Cloud Object Store plugin.</a> 
<br/><br/>
<b>Step 8.</b> Login to the IBM Cloud CLI, target the right region and run the following command from inside of the TFODApp folder.</a> 
<pre>ibmcloud cos bucket-cors-put --bucket livelong --cors-configuration file://corsconfig.json</pre>
<br/>
<b>Step 9.</b> Update the following line with the link to your model.json file inside of the cloud bucket.</a> 
<pre>
const net = await tf.loadGraphModel('YOUR MODEL.json file here')
// e.g. const net = await tf.loadGraphModel('link to your model or local system')
</pre>
This URI is available from your bucket. Select the model.json file then choose object details and the link will be made available. 
<br/><br/>
<b>Step 10.</b> Update the labelmap inside of utilities.js with your labels.</a> 
<br/><br/>
<b>Step 11.</b> Start the app by running npm start.</a> 
<pre>npm start</pre>
<br/><br/>




