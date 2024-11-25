Project Name: Web based cloud detection system
---------------------------------------------------------

Requirements:

	*Hardware: Computer / laptop, stable internet connection, usb camera or built in camera
	*Software: Visual Studio code, Internet browser

Structure:

	index.php - homepage / default page
	getImageInference.php - request image inference 
	Views - HTML files
	Script - Javascript files
	Images - Images for website use
	CSS - Webpages styling sheets

How to use:

	*Assuming there is no re-training of object detection model:

		Launching of product:
			1.Download and install Visual Studio Code.
			2.Install PHP extension. If there are additional extension is needed to run the application, the IDE will ask permission before installing it.
			3.Open index.php.
			4.Click ctrl + f5 to enable debugging mode.
			5.Select "Launch built-in server".
			6.The default Internet browser will launch the web application.

		Product Usage:
			Live video detection:
				1. From the index page, press "get started" button to be redirected to the desired page.
				2. Upon opening the page, a prompt will be shown to request user's permission for camera access.
				3. Click allow and await the model status indicator from red turns to green colour.
				4. A video frame will appear below with the live detection.
				5. Users are able to tune the treshold score as higher score will result in lesser prediction but with higher accuracy.
			Upload image for inference:
				1. Load index page, scroll all the way to the bottom of the page
				2. There is an input file button
				3. Click the button and upload an image file
				4. The image file will be shown to the user alongside with the results from object detection model.
			Cloud learning:
				1. Load index page, press on learning center image.
				2. The page will be loaded and a list of clouds and their description will be shown.
				3. Users are allowed  to filter them based on their categories such as high, medium and low clouds by pressing the button.
			Weather forecasting data:
				1. Load index page, press on weather forecase image.
				2. The page will be loaded with an empty table by default.
				3. Click on a state button and the table will be filled with forecast data retrived via API call.

	*Assuming there is re-training of object detection model:
		
		Training of model:
			1. Search in the internet for roboflow universe
			2. Open the page and create an account
			3. Upon successfull creation, log into the account
			4. Create a new project
			5. Name the a project a name, Annotation Group fill in "clouds", and select "object detection" under project type
			6. Upon creation, upload the clouds dataset into the project by clicking upload data.
			7. Upload all three image file that are train, test and valid. 
			8. Upon successfull upload, apply augmentation for model training
			9. Augmentation parameters:
				Ouputs per training example - 3 
				90 degree rotation - clockwise, counter-clockwise, upside down
				Crop - 0% minimum zoom, 19% maximum zoom
				Grayscale - apply to 20% of image
				Exposure - -14% and +14%
			10. Train model using roboflow object detection 3.0 (fast) model
		
		Assigning model to project:
			1. Retrieve model name, model version, and publishable_key from project samples.
			2. Project samples can be found in Deploy/Deployments.
			3. Under "Hosted image inference", click view code.
			4. Model name, model version and publishable_key can be obtained from there.
			5. After obtaining, insert the new values into every html views that has declared those variables. 
			6. The variables can be found in the "script" section
			7. Open getImageInference.php and replace the existing attibute value with the newly retrived value.
			8. The application can be tested.
			
		
