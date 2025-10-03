# Ex.05 Design a Website for Server Side Processing
# Date:3.10.2025
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
math.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>mathserver</title>
</head>
<style>
    form{
        text-align: center;
        color:blue;

    }
    h1{
        text-align: center;
    }
    h3{
        text-align: center;
    
    }
    body{
        border:black solid;
        border-style: dotted;
    }
</style>
<body bgcolor="yellow">
    <h1>MATH SERVER</h1>
    <br>
    <br>
    <form method="POST"> 
        {% csrf_token %}
        <label for="resistance">RESISTANCE(ohm) :</label>
        <input type="text" name="resistance">
        <br>
        <br>
        <br>
        <br>
        <label for="intensity"> INTENSITY(W/m**2):</label>
        <input type="text" name="intensity">
        <br>
        <br>
        <br>
        <br>
        <button type="submit">POWER</button>


    </form>
    <h3>POWER: {{ power }}</h3>


    
</body>
</html>

views.py
from django.shortcuts import render

def calculate(request):
    power = None 

    if request.method == "POST":
        resistance_str = request.POST.get("resistance")
        intensity_str = request.POST.get("intensity")
        if resistance_str and intensity_str:
            resistance = float(resistance_str)
            intensity = float(intensity_str)
            power = (intensity ** 2) * resistance
            print(f"INTENSITY: {intensity} W/m**2, RESISTANCE: {resistance} ohm, POWER: {power:.2f}")
        else:
            power = "Please enter both resistance and intensity."

    return render(request, 'math.html', {'power': power})


urls.py
from django.contrib import admin
from django.urls import path
from calapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('',views.calculate),
]




```
# SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-10-03 113451.png>)
# HOMEPAGE:
![alt text](<Screenshot 2025-10-03 113143.png>)
# RESULT:
The program for performing server side processing is completed successfully.
