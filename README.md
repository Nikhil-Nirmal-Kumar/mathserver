# Ex.05 Design a Website for Server Side Processing
# Date:
27.11.2025
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
    <title>Server Side Processing - Lamp Power</title>
    <style>
        /* Basic Reset */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(to right, #74ebd5, #ACB6E5);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .container {
            background: #ffffff;
            padding: 40px 50px;
            border-radius: 15px;
            box-shadow: 0 15px 25px rgba(0,0,0,0.2);
            width: 350px;
            text-align: center;
            transition: transform 0.3s;
        }

        .container:hover {
            transform: translateY(-5px);
        }

        h2 {
            color: #333;
            margin-bottom: 30px;
        }

        label {
            display: block;
            text-align: left;
            margin-bottom: 8px;
            font-weight: bold;
            color: #555;
        }

        input[type="number"] {
            width: 100%;
            padding: 10px;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 8px;
            outline: none;
            transition: border 0.3s;
        }

        input[type="number"]:focus {
            border-color: #6C63FF;
        }

        button {
            background: #6C63FF;
            color: #fff;
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            transition: background 0.3s;
        }

        button:hover {
            background: #574fd6;
        }

        .result {
            margin-top: 25px;
            padding: 15px;
            background: #f1f1f1;
            border-radius: 10px;
            font-weight: bold;
            color: #333;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Power of Lamp Filament</h2>

        <form method="POST">
            {% csrf_token %}
            <label for="current">Intensity (I in Amps):</label>
            <input type="number" step="any" name="current" id="current" required>

            <label for="resistance">Resistance (R in Ohms):</label>
            <input type="number" step="any" name="resistance" id="resistance" required>

            <button type="submit">Calculate</button>
        </form>

        {% if power is not None %}
            <div class="result">
                Power = <b>{{ power }} Watts</b>
            </div>
        {% endif %}
    </div>
</body>
</html>

views.py

from django.shortcuts import render

def math(request):
    power = None

    if request.method == "POST":
        I = float(request.POST.get("current"))
        R = float(request.POST.get("resistance"))
        power = (I ** 2) * R   # P = I²R

    return render(request, "myapp/math.html", {"power": power})

myproject/urls.py

from django.shortcuts import render

def math(request):
    power = None

    if request.method == "POST":
        I = float(request.POST.get("current"))
        R = float(request.POST.get("resistance"))
        power = (I ** 2) * R   # P = I²R

    return render(request, "myapp/math.html", {"power": power})

myapp/urls.py

from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('myapp.urls')),
]
```
# SERVER SIDE PROCESSING:
<img width="1920" height="1080" alt="Screenshot (54)" src="https://github.com/user-attachments/assets/b330fa3c-d086-40e7-a83e-3b6afaf606e0" />
<img width="1920" height="1080" alt="Screenshot (53)" src="https://github.com/user-attachments/assets/86e7d1e8-fbd0-4344-84c5-a6552293b85e" />

# HOMEPAGE:
<img width="1920" height="1080" alt="Screenshot (56)" src="https://github.com/user-attachments/assets/235c0e69-7bd0-477d-81bd-776e034c3bb1" />

# RESULT:
The program for performing server side processing is completed successfully.
