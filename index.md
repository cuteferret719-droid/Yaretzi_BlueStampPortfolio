# Yaretzi's electrodermal lie detector journey

The electrodermal lie detector uses galvanic skin response (GSR), a polygraph and aluminum and copper probes to help determine if the person being trialed is telling the truth or not through the use of sweat, skin activity and it can also keep track of the persons skin activity. Throughout this journey the electrodermal lie detector had experienced many setbacks to where the schematic was redesigned and tested which took 3-5 days to finish and also experienced modifications to make the electrodermal lie detector as accurate as possible but despite these setbacks im now confident in coding, knowing the basics of an arduino and knowing which wire goes into what column.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Yaretzi H | KIPP College Prep | Biomedical Engineering | Incoming Sophmore |


<img src="project BSE.jpg" alt="Headstone Image" width="500">

# Final Milestone

[![Watch my First Milestone Video](https://img.youtube.com/vi/weRS4PkNmuc/0.jpg)](https://www.youtube.com/watch?v=weRS4PkNmuc)


For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE

 

# First Milestone Video 

[![Watch my First Milestone Video](https://img.youtube.com/vi/weRS4PkNmuc/0.jpg)](https://www.youtube.com/watch?v=weRS4PkNmuc)

*What has been surprising about the project is the code tricked the polygraph into zooming into the line to have a better view on the skin activity rate.

*What needs to be completed is making the lie detector as accurate as possible and to minimize the noise level.

*The challenges i've faced and overcame is the wiring overlapping eachother, having to rewire the whole set and testing different codes for the lie detector and overcame these by going to innovation labs, asking help from the instructors and using tutorials to help me understand the basics of arduino's and breadboards

*My accomplishments are completing the base project of the Electrodermal Lie Detector and my first milestone video.

# Code for Electrodermal Lie detector

```HTML 
<!--- This is an HTML comment in Markdown -->
float filteredValue = 0;

void setup() {
  Serial.begin(9600);

  // LED pins
  pinMode(10, OUTPUT);
  pinMode(9, OUTPUT);
  pinMode(8, OUTPUT);

  // Startup LED test
  digitalWrite(10, HIGH);
  delay(50);
  digitalWrite(9, HIGH);
  delay(50);
  digitalWrite(8, HIGH);
  delay(50);

  digitalWrite(10, LOW);
  digitalWrite(9, LOW);
  digitalWrite(8, LOW);
}

void loop() {

  // Average 5 readings
  long total = 0;

  for (int i = 0; i < 5; i++) {
    total += analogRead(A0);
    delay(2);
  }

  float sensorValue = total / 5.0;

  // Light smoothing (more responsive)
  filteredValue = 0.70 * filteredValue + 0.30 * sensorValue;

  // LED indicators
  digitalWrite(10, filteredValue > 300);
  digitalWrite(9, filteredValue > 600);
  digitalWrite(8, filteredValue > 900);

  // Serial Plotter scale
  Serial.print(95);
  Serial.print(",");
  Serial.print(115);
  Serial.print(",");
  Serial.println(filteredValue);

  delay(50);
}

<!--- Anything between these symbols will not render on the published site -->
```


# Schematics For Lie Detector

<img src="updated schematic.png" alt="Headstone Image" width="500">
# Bill of Materials

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Arduino Uno | Used for reading inputs such as messages and turn it into outputs that help power your device, project and system  | $17 | <a href="https://www.amazon.com/ELEGOO-Board-ATmega328P-ATMEGA16U2-Compliant/dp/B01EWOE0UU/ref=sims_dp_d_dex_ai_rank_model_1_d_v1_d_sccl_1_2/131-0474986-0583845?pd_rd_w=30Dnf&content-id=amzn1.sym.bb4a0aac-c2b4-4b4b-a0c8-9aa89b28dce3&pf_rd_p=bb4a0aac-c2b4-4b4b-a0c8-9aa89b28dce3&pf_rd_r=4M85MYH929P05F0S87WE&pd_rd_wg=mQCZ8&pd_rd_r=f31547c7-ca98-4c5b-8d6c-de526028cac2&pd_rd_i=B01EWOE0UU&psc=1"> Link </a> |
| Buzzer/LED/Vibrtion | helps light up your project or used for display |$6.55 | <a href="https://www.amazon.com/s?k=led&i=industrial&crid=16ERNF7Q0TF4J&sprefix=LED%2Cindustrial%2C139&ref=nb_sb_ss_p13n-expert-pd-ops-ranker_ci_hl-bn-left_1_3"> Link </a> |
| copper tape| used to help transfer heat, electricity and radio frequency | $8 | <a href="https://www.amazon.com/Kirecoo-Conductive-Shielding-Electrical-Grounding/dp/B09Z6F9RFG/ref=sr_1_3?crid=1B68CK1WOG3P4&dib=eyJ2IjoiMSJ9.XmUtSyIic8_E3Qr4oK0quFqV9fQ6eofMY8kCHCHy57CcqSmDx18Rf31a90Wv61yYUJ4oaqIZZuwm00UHEMmgEWCulK4Jwb5SZQ-ykWRvnCuBjgLGfe22nfYrrBYvTholtkBaGdWaXhofmMy6LLKxkloBLb-N-xGERRh2ZG7z5kaYjcv5CgjAku5dh2hnZTclk10pyIZTSwNo9yHlWLbWey_m3_xOx2zASkp4Zv2CFBv3AkFwcgKYXTqSkg6s4q0bauvDUCmrjmCl9q6HQIdpmTvQgNWxRjzyW_4M-Y6yUgw.a_KhWh2DD4US_KU9CUpbV1ySZoJ660q5hhSOkaY1IEE&dib_tag=se&keywords=copper+tape&qid=1783525907&s=industrial&sprefix=copper+%2Cindustrial%2C113&sr=1-3"> Link </a> |
| aluminum| used for building, wiring and transfering power  | $5.67 | <a href="https://www.amazon.com/Reynolds-Wrap-Heavy-Strength-50/dp/B00279LYL6/ref=sr_1_8?dib=eyJ2IjoiMSJ9.cHXovjINofGmqe7Oson_QernHShvUr9tUGkBzrTrGYsHdb_JAbNu03pJZ8C97m29xVM6vHcRB0A1TX7I66NU4fZhrTEuuFcCIuiDqE5nOT3C4ICc8EZSCLZB8fSR-ay7UD2z50VxJLR5VPDkt2kDXMN_rZ2rrcsgatqCzrs62yvbTjvJ1i0aI-LsE5034A9fZWcNYVMQKiKdOmcIgdZkfIEu2hnddZOE_F_mfGgeNRwvVsQ-x6kx2e3kF3i75NwM2zDXRc0h7GBBL6GRdVH-X98kdzNZx-dFyL4bv03kUsw.Z-Gg9cga0WokVBZqyMMUJvnEHKdmWwFspmf1RhqRmTs&dib_tag=se&keywords=aluminum%2Bfoil&qid=1783527530&rdc=1&sr=8-8&th=1"> Link </a> |
| Breadboard| used for testing electronic circuits  | $5.67 | <a href="https://www.amazon.com/BOJACK-Values-Solderless-Breadboard-Flexible/dp/B08Y59P6D1/ref=sr_1_3?crid=WTOWOV0EMTN1&dib=eyJ2IjoiMSJ9.5Z5yTwL-oa1r18Ah_zf9OdziZtM7NtJzJKlf3z7Il1TW59ewKN3AV-xd1Sp_umuOOALz-aVA6E2NJLrXWHeLFDE5elGuad1FSlAssbTUbjcDBKz8v8ReLAvvM2tqtfmFPhRLxZGwYdD8A-48BSdvxHWD5EvD0QzjZflocZzEmANWPoHwBiEWtGY7w7Xx1UjsjRZmQ1RUcovx4-lWUT76OoSHjcLWHLa8eSIcKfkLyaOcRxWTOAPCxnzyHRSHcE5plOvdJ5nmDBFe1jONBd-qSLu8vIX1pfRRRpM9l569yoI.V6DfrfmZAo0mNvh33ihirUuATpgWLbpkmQYa-HreE7c&dib_tag=se&keywords=breadboard&qid=1784220845&s=industrial&sprefix=breadboard%2Cindustrial%2C254&sr=1-3&th=1"> Link </a> |


# Resources

|:--:|:--:|:--:|:--:|
| Breadboard tutorial | By LeftyMaker | <a href="https://www.youtube.com/watch?v=W6mixXsn-Vc"> Link </a> |
| arduino tutorial | By Robonyx | <a href="https://www.youtube.com/watch?v=tiGw9PQbvrg"> Link </a> |
|GSR Based Lie Detector| By Ashwini Kumar Sinha | <a href="https://www.electronicsforu.com/electronics-projects/gsr-based-lie-detector-device"> Link </a> |
|How to build an Arduino lie detector based on electrodermal activity| By Nikhil Agnihotri | <a href="https://www.engineersgarage.com/arduino-lie-detector-electrodermal-activity/"> Link </a> |

