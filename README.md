
## PORTFOLIO
### :white_check_mark: [CHECKLIST][identifier] 
### :memo: [TEST CASES][identifier] 
### :technologist: [API TESTING][identifier] 
You can download this Postman collection [here](https://github.com/kari-pr/kari-pr/blob/main/Booking.postman_test_run.json)
1. CreateToken - Creates a new auth token to use for access to the PUT and DELETE /booking
```
https://restful-booker.herokuapp.com/auth
```
Request body:
 ```JSON
{
    "username": "admin",
    "password": "password123"
}
```
Response:
```JSON
{
    "token": "169c1144c985ca5"
}
```
![image](https://github.com/kari-pr/kari-pr/assets/147839924/3e6f3aac-0271-4b11-802e-ae55199e66de)

2. CreateBooking - Creates a new booking in the API
```
https://restful-booker.herokuapp.com/booking
```
Request body:
 ```JSON
{
    "firstname" : "Jim",
    "lastname" : "Brown",
    "totalprice" : 111,
    "depositpaid" : true,
    "bookingdates" : {
        "checkin" : "2023-12-01",
        "checkout" : "2024-01-01"
    },
    "additionalneeds" : "Breakfast"
}
```
Response:
```JSON
{
    "bookingid": 4500,
    "booking": {
        "firstname": "Jim",
        "lastname": "Brown",
        "totalprice": 111,
        "depositpaid": true,
        "bookingdates": {
            "checkin": "2023-12-01",
            "checkout": "2024-01-01"
        },
        "additionalneeds": "Breakfast"
    }
}
```
![image](https://github.com/kari-pr/kari-pr/assets/147839924/93721993-3df6-48dd-9f3d-24aa94445d5b)

3. UpdateBooking - Updates a current booking
```
https://restful-booker.herokuapp.com/booking/{{id}}
```
Request body:
 ```JSON
{
    "firstname": "James",
    "lastname": "Brown",
    "totalprice": 131,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2023-12-01",
        "checkout": "2024-01-15"
    },
    "additionalneeds": "Breakfast"
}
```
Response:
```JSON
{
    "firstname": "James",
    "lastname": "Brown",
    "totalprice": 131,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2023-12-01",
        "checkout": "2024-01-15"
    },
    "additionalneeds": "Breakfast"
}
```
![image](https://github.com/kari-pr/kari-pr/assets/147839924/7456e011-dc98-4734-9424-9e3eade94fa6)

4. GetBooking - Returns a specific booking based upon the booking id provided
```
https://restful-booker.herokuapp.com/booking/{{id}}
```
Response:
```JSON
{
    "firstname": "James",
    "lastname": "Brown",
    "totalprice": 131,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2023-12-01",
        "checkout": "2024-01-15"
    },
    "additionalneeds": "Breakfast"
}
```
![image](https://github.com/kari-pr/kari-pr/assets/147839924/c051f584-ba70-4bba-aebc-a56a625f2d46)

5. PartialUpdateBooking - Updates a current booking with a partial payload
```
https://restful-booker.herokuapp.com/booking/{{id}}
```
Request body:
 ```JSON
{
    "additionalneeds": "Supper"
}
```
Response:
```JSON
{
    "firstname": "James",
    "lastname": "Brown",
    "totalprice": 131,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2023-12-01",
        "checkout": "2024-01-15"
    },
    "additionalneeds": "Supper"
}
```
![image](https://github.com/kari-pr/kari-pr/assets/147839924/121d3902-c100-4a55-8fb1-4ffe7593d5f9)

6. DeleteBooking - Delete a booking with that id.
```
https://restful-booker.herokuapp.com/booking/{{id}}
```
Response:
```JSON
{
    201
}
```
![image](https://github.com/kari-pr/kari-pr/assets/147839924/d7032d5a-066c-420b-8929-e9b1292eb7f0)

### :technologist: [SELENIUM][identifier] 

Creating simple positive login test on testspracticetestautomation.com
![image](https://github.com/kari-pr/kari-pr/assets/147839924/e07e1514-da4b-4093-9fbb-6f14f6609190)
```python
from selenium import webdriver
from selenium.webdriver.chrome.service import Service as ChromeService
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.common.by import By
import time


driver = webdriver.Chrome(service=ChromeService(ChromeDriverManager().install()))
driver.get("https://practicetestautomation.com/practice-test-login/")

email = driver.find_element(by=By.ID, value="username")
password = driver.find_element(by=By.ID, value="password")
submit_button = driver.find_element(by=By.ID, value="submit")
successful_login_text = "Logged In Successfully"

email.send_keys("student")
password.send_keys("Password123")
submit_button.click()
get_source = driver.page_source

print(successful_login_text in get_source)

time.sleep(5)
driver.close()
driver.quit()
```
