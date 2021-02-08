# Working
As of March 30th, the lisence plate, and color is working fully with a high accuracy. The symbol code is also there but it doesn't have a high enough accuracy so there is a change it can't use it. Code takes around ~5 seconds to run one frame. Still working on combining the code, with the multiple frames and line detection. 
 
## Lisence Plate Google API
Using a google API connected to the email - (kunalapiprogram@gmail.com)

 1. Lowers, the quality of the picture 
 2. Run it through the Google API (make sure you have the key.json file)
	 1. returns [Text Detected,  4 Vertices of the Text detected]
 3. Using the Vertices, it find the area of the text detected.
 4. Since the API Detects all of the text, (inluding extra text like "Georgia") code runs through a series of cleaning, to get the final lisence plate
	 5. Cleaning includes, area, state, county, and length properties of the text
 5.  return FINAL_LISENCE_PLATE_DETECTED
## COLOR
 1. Using scipy, it detects the top 5 colors detected, and returns the top one
 2. Returns the RGB Value and the HEX value of the color
 3. Using that, it returns the name of the color
 4. Will furter compare it will the database of colors
## SYMBOL
1. Detects the symbol of the car
2. Code is there for all cars it can detect. 
3. Not the most accurate code. 
```python
cars = ['Alfa Romeo', 'Audi', 'BMW', 'Chevrolet', 'Citroen', 'Dacia', 'Daewoo', 'Dodge','Ferrari', 'Fiat', 'Ford', 'Honda', 'Hyundai', 'Jaguar', 'Jeep', 'Kia', 'Lada','Lancia', 'Land Rover', 'Lexus', 'Maserati', 'Mazda', 'Mercedes', 'Mitsubishi','Nissan', 'Opel', 'Peugeot', 'Porsche', 'Renault', 'Rover', 'Saab', 'Seat','Skoda', 'Subaru', 'Suzuki', 'Tata', 'Tesla', 'Toyota', 'Volkswagen', 'Volvo']
```

# Future Plan
- First Build own detection for lisence plate
- Using the cleaning methods, and see the changes


# CarRecognition
-   Color
	- Using Numpy Array, I will take the color of the pixel and using average get the color of the car
-   Logo
	-   I will have to look into a dataset but that will be simple
-   License plate
	- [https://github.com/Dharun/Tensorflow-License-Plate-Detection](https://github.com/Dharun/Tensorflow-License-Plate-Detection)
	-  [License Plate Recognition API](https://app.platerecognizer.com/accounts/login/?next=/) (API)
	- Using tesseract to detect text on the license plate
-   Make, Model, Year of Car
	- Using the Stanford dataset I will be able to detect this



## Inspiration
Every building requires a parking lot, many of which are regulated meaning only a specific amount of people can park there. Some even have designated slots for each car. In order to maintain this order, the building administration needs to check if each car is in its correct parking lot position. This is an extreme waste of time and money. 

A robot installed with a camera recording each parking lot and its car, it will be able to recognize each car in seconds. And then return any data to administration, for example a car parking in spot 300 when they are assigned spot 200. 

## What it does

The robot records a video of the entire row of the parking lot. Using AI, it processes this data to extract key criteria
- Lisence Plate
	- State
	- Number
- Car Color
- Car logo

From manually inputing the starting position, the robot can number each parking lot position and create a list of the cars in that lot. This can then be compared to a true value list to detect any anomalies.  

## How we built it
As it is hard to build a robot in a limited time frame we hand recorded video of different cars in the parking lot. We then split the code into 3 sections for each criteria. We used the GCP Vision API for the label detection and logo detection and with prelimenary tests we are running with a **96%** accuracy for both of them. 

These are the following steps we used to built it
1. Split the video into different frames to process each frame and then combine the data
2. Connect to GCP key
3. Detect objects in frame
4. Get image data (size, type)
5. Run Logo Detection
6. Detect which colors are in frame
7. Detect Lisence plate
8. Use OCR to get lisence plate number
9. Combine all data into Excel spreadsheet
10.Compare to real sheet
  

## Challenges we ran into
There was a lot of reflection in sunny **weather conditions** on some of the cars which changed the color of the image. 
**Compression** of the image changed different ways to save and use the images
Some lisence plates are temporary which affect the **OCR** model
## Accomplishments that we're proud of
Creating a visual of the Image Array using a highlight on top of the logo on the car
Using selenium to get the specific English color name from the HEX value.
## What we learned
In order to process long videos of robot running through long car parking lots, we need to create each frame accuratly becuase processing every frame takes too long and every 2nd frame could increase speed without lowering accuracy.
## What's next for Car Recognition and checking
We belive this can be deployed at highschools where the parking lot is numbered and assigned to a pre-defined student and its car data is already given. This can be deployed very easily and futher move on


