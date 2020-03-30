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
