![Screenshot 2024-12-13 204956](https://github.com/user-attachments/assets/efb73dd6-18cb-4542-8dfc-06776dc20d2d)# Ex.05 Design a Website for Server Side Processing
# Date:22/11/2024
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
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lamp Power Calculator</title>
</head>
<body>
    <h1>Lamp Filament Power Calculator</h1>
    <form method="POST">
        {% csrf_token %}
        {{ form.as_p }}
        <button type="submit">Calculate Power</button>
    </form>

    {% if power is not None %}
        <h2>Calculated Power: {{ power }} Watts</h2>
    {% endif %}
</body>
</html>

<div class="edge">
<div class="box">
<h1>Power of a Light Filament</h1>
<form method="POST">
{% csrf_token %}
<div class="formelt">
intensity : <input type="text" name="intensity" value="{{i}}"></input>(in Wm
</div>
<div class="formelt">
resistance : <input type="text" name="resistance" value="{{r}}"></input>(in
</div>
<div class="formelt">
<input type="submit" value="Calculate"></input><br/>
</div>
<div class="formelt">
Power : <input type="text" name="power" value="{{power}}"></input>(in W)<br/
</div>
</form>
</div>
</div>
</body>
</html>
views.py
from django.shortcuts import render
def power_calculator(request):
power = None
intensity = None
resistance = None
if request.method == 'POST':
print("POST method is used")
intensity = request.POST.get('intensity','0')
resistance = request.POST.get('resistance','0')
if intensity and resistance:
try:
I = float(intensity)
R = float(resistance)
power = I**2 * R
print('request=',request)
print('intensity=',I)
print('resistance=',R)
print('power=',power)
except ValueError:
power = "Invalid input. Please enter numerical values."
return render(request, 'mathapp/mathserver.html', {'power': power, 'inte
urls.py
from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
path('admin/', admin.site.urls),
path('', views.power_calculator, name='power_calculator'),
]
```
# SERVER SIDE PROCESSING:
![Screenshot 2024-12-13 204956](https://github.com/user-attachments/assets/cd37be01-4d21-4873-bfcf-7ce5150919b8)

# HOMEPAGE:
![Screenshot 2024-12-13 205015](https://github.com/user-attachments/assets/301e52e9-454e-4c88-a27d-5365ebdeffa4)

# RESULT:
The program for performing server side processing is completed successfully.
