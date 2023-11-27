# TITTLE:

INDOOR AIR QUALITY MODELING BASED ON IOT 

## ABSTRACT:

The Internet of Things refers to connecting things and people through the internet,
it has imposed itself as the new business practice in different sectors. In regulating
indoor air quality, the existing control system the indoor air quality regulation is
based on only filtering the indoor air and cannot control the flow of indoor air to
control the fresh charge. In this work, a novel method is implemented using
sensor fusion to make a quick and efficient response in air quality control using
inlet flow control of air through a filtered channel. A real-time model is created
to monitor and control the indoor air quality key parameters like oxygen, carbondi-oxide, nitrogen dioxide, carbon monoxide, and particulate matter are
considered in the modeling. Data collected under various segments of day,
season, area, residential, and semi-residential are fed to train the intelligent
algorithm (ANN). The model is validated using K-fold cross-validation to check
the performance, and the results found after validation are within the standard
limits. The system developed is found to be rugged at various test conditions, and
the accuracy limits are within the standard limits

## INTRODUCTION:

Indoor air quality (IAQ) plays a crucial role in the over all well-being and health of
individuals. Most of the people spend 80% to 90% of their time, whether in
residential, commercial, or public spaces, it is imperative to ensure that the air they
breathe is clean and free from pollutants. Thus, it is necessary to take immediate
steps to improve the quality of indoor air. Poor IAQ can arise from factors such as
inadequate ventilation, the presence of pollutants, high humidity levels, and
temperature fluctuations. Adverse health effects caused by poor IAQ can range from
discomfort and allergies to more severe respiratory problems and reduced cognitive
function.
Recognizing the importance of maintaining optimal indoor air quality, there is a
growing interest in leveraging technology to monitor, model, and manage IAQ
effectively. The Internet of Things (IoT) presents a promising solution by enabling the
integration of various sensing devices, data collection mechanisms, and analytics tools
to create smart environments. By employing IoT-based systems, it becomes possible
to gather real-time data on key IAQ parameters and utilize advanced algorithms to
model and assess the air quality in indoor spaces accurately.
By implementing an IoT-based system for IAQ modeling, building owners, facility
managers, and occupants can gain real-time visibility into the air quality conditions.
This knowledge can empower them to make informed decisions, take proactive
measures to address any IAQ issues, and create healthier indoor environments.
Additionally, the insights derived from the project can help in developing IAQ
guidelines, standards, and policies for the future. 
## LITERATURE REVIEW:

With the ongoing improvements in quality of life, breathing
environment has become an essential area of concern for humans in the
twenty-first century. Many studies confirm that indoor air is more deadly
then outdoor air. Constant exposure to indoor air pollution (IAP) due to the
combustion of solid fuels is the common cause of several harmful diseases
in developing countries. The list includes chronic obstructive pulmonary
disease (COPD), otitis media, acute respiratory infections, tuberculosis,
asthma, lung cancer, cancer of larynx and nasopharynx, low birth rate,
perinatal conditions and severe eye diseases that can even cause blindness.
In developed countries, modernization has shifted indoor fire and
heating systems from biomass fuels to electricity-based appliances.
However, in developing Asia, it is projected that 1.3 billion people will still
rely on biomass for cooking by 2030. The use of coal and solid biomass
leads to 2.8 million premature deaths annually. Poverty is the main obstacle
to adopting advanced and cleaner fuels. To achieve the goal, the annual
growth rate needs to increase from 0.5% to 3% between 2016 and 2030.
However, based on current statistics, it is likely that around 2.3 billion
people globally will still lack direct access to clean cooking by 2030. This
means that health impacts from indoor air pollution (IAP) will continue,
particularly in areas without proper ventilation arrangements.
Ventilation plays a crucial role in improving indoor air quality by
ensuring proper air circulation and reducing the concentration of pollutants.
It helps remove or dilute indoor pollutants emitted from various sources,
such as cooking, cleaning chemicals, and indoor activities. Additionally,
 ventilation aids in moisture control, preventing mold and mildew growth. By
eliminating unpleasant odors and reducing the presence of allergens like dust
and pet dander, ventilation creates a healthier indoor environment. It also
contributes to temperature regulation, keeping spaces comfortable. Moreover,
proper ventilation has been associated with improved respiratory health,
reduced risk of airborne infections, and enhanced cognitive function. Overall,
ventilation is essential for maintaining clean and fresh indoor air, promoting a
healthier and more pleasant living or working environment. Most of the people
spend 80% to 90% of their time indoors either at home, classrooms or in the
offices. Thus, it is necessary to take immediate steps to improve the quality of
indoor air. The idea is to create some healthy solutions that can contribute to a
comfortable living environment while reducing the chances of the occurrence of
severe diseases. Modernization has also heightened the focus on indoor air
quality monitoring by providing advanced technologies, increasing health
consciousness, emphasizing energy efficiency and building design, influencing
indoor lifestyles, and establishing regulations and standards. These factors
collectively contribute to a greater understanding of the importance of
monitoring and maintaining clean and healthy indoor air. 

## PROPOSED METHODLOGY:

In this project, following are the methodology we used:
1. Sensor Data Collection: Install and configure the sensor kit consisting of the
PM2.5 dust smoke sensor, MQ7 sensor (for carbon monoxide), DHT11 sensor (for
temperature and humidity), and Arduino node. The sensors collect real-time data
on PM2.5 levels, carbon monoxide levels, temperature, and humidity in the indoor
environment.
2. Data Transmission to Thingspeak: Connect the Arduino node to the internet and
transmit the sensor data to the Thingspeak IoT platform. Thingspeak acts as a data
repository and provides a web API for data retrieval and analysis.
3. Dataset Creation and Preprocessing: Retrieve the sensor data from Thingspeak
and create a dataset for IAQ prediction. Preprocess the dataset by handling missing
values, outliers, and performing data normalization if required. Additionally,
engineer relevant features that could potentially improve prediction accuracy.
4. Model Selection, Training & Evaluation: Choose a hybrid model for IAQ
prediction that combines Random Forest and Logistic Regression. The Random
Forest algorithm can handle non-linear relationships and capture complex
interactions, while Logistic Regression can provide interpretability and handle
binary classification tasks. Split the pre-processed dataset into training and testing
sets. Train the hybrid model using the training set. Evaluate the performance of the
trained hybrid model using the testing set.
5. Prediction and Labelling: Deploy the trained hybrid model to make predictions
on new, unseen data. Input the real-time sensor values (PM2.5, carbon monoxide,
temperature, humidity) into the model, and obtain the predicted IAQ label (good,
bad, moderate). These labels can indicate the quality of the indoor air at a given
time.
6. Continuous Monitoring and Feedback: Continuously monitor the IAQ
predictions and compare them with actual measurements. Collect feedback on the
accuracy and reliability of the predictions and incorporate it into the system. This
feedback loop helps to refine and improve the hybrid model over time.


## CIRCUIT DIAGRAM:



![iot mini](https://github.com/Thenmozhi-Palanisamy/Simulation-project/assets/95198708/9a0681ad-3bc6-47b3-b52e-273d39dc726f)


## PROGRAM:
`````
#include <ESP8266WiFi.h>
#include <SPI.h>
#include <Wire.h>
#include "MQ135.h"
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>
 
#define SCREEN_WIDTH 128    // OLED display width, in pixels
#define SCREEN_HEIGHT 64    // OLED display height, in pixels
#define OLED_RESET -1       // Reset pin # (or -1 if sharing Arduino reset pin)
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);
 
String apiKey = "14K8UL2QEK8BTHN6"; // Enter your Write API key from ThingSpeak
const char *ssid = "Alexahome";     // replace with your wifi ssid and wpa2 key
const char *pass = "12345678";
const char* server = "api.thingspeak.com";
 
WiFiClient client;
 
 
void setup()
{
  Serial.begin(115200);
  display.begin(SSD1306_SWITCHCAPVCC, 0x3C); //initialize with the I2C addr 0x3C (128x64)
  display.clearDisplay();
  delay(10);
 
  Serial.println("Connecting to ");
  Serial.println(ssid);
  
  display.clearDisplay();
  display.setCursor(0,0);  
  display.setTextSize(1);
  display.setTextColor(WHITE);
  display.println("Connecting to ");
  display.setTextSize(2);
  display.print(ssid);
  display.display();
  
  WiFi.begin(ssid, pass);
 
  while (WiFi.status() != WL_CONNECTED)
  {
    delay(500);
    Serial.print(".");
  }
    Serial.println("");
    Serial.println("WiFi connected");
    
    display.clearDisplay();
    display.setCursor(0,0);  
    display.setTextSize(1);
    display.setTextColor(WHITE);
    display.print("WiFi connected");
    display.display();
    delay(4000);
}
 
 
  void loop()
  {
    MQ135 gasSensor = MQ135(A0);
    float air_quality = gasSensor.getPPM();
    Serial.print("Air Quality: ");  
    Serial.print(air_quality);
    Serial.println("  PPM");   
    Serial.println();
 
    display.clearDisplay();
    display.setCursor(0,0);  //oled display
    display.setTextSize(1);
    display.setTextColor(WHITE);
    display.println("Air Quality Index");
    
  
    display.setCursor(0,20);  //oled display
    display.setTextSize(2);
    display.setTextColor(WHITE);
    display.print(air_quality);
    display.setTextSize(1);
    display.setTextColor(WHITE);
    display.println(" PPM");
    display.display();
 
 
    if (client.connect(server, 80)) // "184.106.153.149" or api.thingspeak.com
  {
    String postStr = apiKey;
    postStr += "&field1=";
    postStr += String(air_quality);
    postStr += "r\n";
    
    client.print("POST /update HTTP/1.1\n");
    client.print("Host: api.thingspeak.com\n");
    client.print("Connection: close\n");
    client.print("X-THINGSPEAKAPIKEY: " + apiKey + "\n");
    client.print("Content-Type: application/x-www-form-urlencoded\n");
    client.print("Content-Length: ");
    client.print(postStr.length());
    client.print("\n\n");
    client.print(postStr);
    
    Serial.println("Data Send to Thingspeak");
  }
    client.stop();
    Serial.println("Waiting...");
 
    delay(2000);      // thingspeak needs minimum 15 sec delay between updates.
}
``````
## RESULTS:


![mini 2](https://github.com/Thenmozhi-Palanisamy/Simulation-project/assets/95198708/0155a3bb-2303-46a6-88e3-2a7047d486fc)



![mini 1](https://github.com/Thenmozhi-Palanisamy/Simulation-project/assets/95198708/a3cb4e30-610b-4b38-915e-407f07cc9180)


## REFERENCE:

Tang, Y., & Chen, Y. (2018). Forecasting indoor air quality in HVAC systems
based on long short-term memory recurrent neural networks. Energy and
Buildings, 171, 204-213.

Long, S., & Yao, L. (2018). Indoor air quality prediction with a novel hybrid
model combining long short-term memory and extreme learning machine.
Building and Environment, 144, 167-178.

Wang, C., Du, X., Ma, Z., & Li, Y. (2020). An indoor air quality prediction
method based on hybrid model. Environmental Science and Pollution
Research, 27(36), 45362-45375.

Zhao, D., Wu, J., & Chen, Z. (2018). Indoor air quality prediction using deep
belief network and support vector regression. Building Simulation, 11(2), 351-
359

