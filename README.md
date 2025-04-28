# Ex02 Django ORM Web Application
## Date: 28.04.2025

## AIM
To develop a Django application to store and retrieve data from a Movies Database using Object Relational Mapping(ORM).

## FORMULA
P = I2R P --> Power (in watts)
I --> Intensity
R --> Resistance



## DESIGN STEPS

### STEP 1:
Clone the problem from GitHub

### STEP 2:
Create a new app in Django project

### STEP 3:
Enter the code for admin.py and models.py

### STEP 4:
Execute Django admin and create details for 10 books

## PROGRAM
```
math.html
<!DOCTYPE html>
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Power Calculation (P = I²R)</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body {
    background-color:  #66eddf;
}
.edge {
    width: 100%;
    padding-top: 250px;
    text-align: center;
}
.box {
    display: inline-block;
    border: thick double rgb(97, 4, 18);
    width: 500px;
    min-height: 300px;
    font-size: 20px;
    background-color: #fefbd8;
}
.formelt {
    color: black;
    text-align: center;
    margin-top: 7px;
    margin-bottom: 6px;
}
h1 {
    color: black;
    padding-top: 20px;
}
</style>
</head>
<body>
<div class="edge">
    <div class="box">
        <h1>Power Calculation</h1>
        <h3>Keerthana (212224100031)</h3>
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Current (I): <input type="text" name="current" value="{{current}}"> A<br/>
            </div>
            <div class="formelt">
                Resistance (R): <input type="text" name="resistance" value="{{resistance}}"> Ω<br/>
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate"><br/>
            </div>
            <div class="formelt">
                Power (P): <input type="text" name="power" value="{{power}}"> W<br/>
            </div>
        </form>
    </div>
</div>
</body>
</html>
```
``` 
views.py
from django.shortcuts import render

def power(request):
    context = {}
    context['power'] = "0"
    context['current'] = "0"
    context['resistance'] = "0"

    if request.method == 'POST':
        print("POST method is used")
        print('request.POST:', request.POST)
        
        current = request.POST.get('current', '0') 
        resistance = request.POST.get('resistance', '0') 
        print('current(I) =', current)
        print('Resistance(R) =', resistance)
        
        try:
            # Convert inputs to floats for calculation
            current = float(current)
            resistance = float(resistance)
            
            # Power calculation: P = I²R
            power = current ** 2 * resistance
            context['power'] = power
            
        except ValueError:
            # Handle invalid input
            context['error'] = "Please enter valid numeric values for current and resistance."
            context['power'] = "0"
        
        context['current'] = current
        context['resistance'] = resistance
        print('Power(P) =', context['power'])

    return render(request, 'mathapp/math.html', context)
```
```
urls.py
from django.contrib import admin
from django.urls import path
from mathapp import views  # Updated to match the new app name (mathapp)

urlpatterns = [
    path('admin/', admin.site.urls),
    path('powercalculation/', views.power, name="powercalculation"),  # Updated URL for power calculation
    path('', views.power, name="powercalculationroot")  # Root URL redirects to power calculation
]
```

## OUTPUT

SERVER SIDE PROCESSING:

![WhatsApp Image 2025-04-28 at 20 37 00_56aae6a6](https://github.com/user-attachments/assets/b2bbd659-247d-4543-bb9c-24e19a1c6c6b)

HOMEPAGE:

![WhatsApp Image 2025-04-28 at 20 37 20_d6d0ab96](https://github.com/user-attachments/assets/500e57fe-83ba-4386-a6fc-859122f1e3a5)

## RESULT
Thus the program for creating movies database using ORM hass been executed successfully
