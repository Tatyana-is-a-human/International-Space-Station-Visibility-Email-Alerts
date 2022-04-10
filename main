import requests
from datetime import datetime
import smtplib
from time import sleep

MY_LAT=43.272960
MY_LONG=-79.943850

parameters={
    "lat":MY_LAT,
    "long": MY_LONG,
    "formatted":0
}

response=requests.get(url="http://api.open-notify.org/iss-now.json")
issLat=float(response.json()['iss_position']['latitude'])
issLong=float(response.json()['iss_position']['longitude'])
print(f"iss long: {issLong}\niss lat: {issLat}")

if (MY_LONG-5)<=issLong<=(MY_LONG+5) and (MY_LAT)-5<=issLat<= (MY_LAT+5):
    #print("They are close")
    issClose=True

else:
    issClose=False
    #print("The ISS is not nearby. No email sent")


while issClose:

    response = requests.get(url="https://api.sunrise-sunset.org/json", params=parameters)
    response.raise_for_status()
    sunriseHour = int((response.json()['results']['sunrise']).split("T")[1].split(":")[0])
    sunsetHour = int((response.json()['results']['sunset']).split("T")[1].split(":")[0])

    currentHour = datetime.now().hour

    #print(f"sunrise: {sunriseHour} \n" +
          #f"sunset: {sunsetHour}\n" +
          #f"current hour: {currentHour}")

    if currentHour <= sunriseHour or currentHour >= sunsetHour:
        #print("it is night")

        with smtplib.SMTP("smtp.mail.yahoo.com") as connection:
            connection.starttls()
            connection.login(user="tatyana.automated@yahoo.com", password="numombdpagreuhyh")
            connection.sendmail(from_addr="tatyana.automated@yahoo.com",
                                to_addrs="tatyana.automated@gmail.com",
                                msg="Subject:International Space Station Visible\n\n "+
                                f"the International Space Station is curently visible at {issLat}, {issLong}.")
        #print("Notification email sent")

    else:
        #print("it is not dark enough to see the ISS. No email sent")

    sleep(60)
