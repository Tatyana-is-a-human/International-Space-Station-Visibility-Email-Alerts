# International-Space-Station-Visibility-Email-Alerts
Emails users with low-security inboxes when the International Space Station is visible overhead

Using http://api.open-notify.org/iss-now.json, this program pulls the latitude and longtitude of the ISS and sends an email to the user every minute when the ISS is within 5 lat and long points of them, while it is nighttime. The emails are currently set up to go from tatyana.automated@yahoo.com to tatyana.automated@gmail.com and the location is set as Hamilton, Canada.  https://api.sunrise-sunset.org/json is used to determine when sunrise and sunset are at that location. Location and emails are easy to change from within the program. 

Receptor emails must have their security set to low in order for this to work. It's not hard to see why any decent email server would mistake this for  spam.

This project is day 33 of the 100 days to python mastery course on Udemy.com

Enjoy!
