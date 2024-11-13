# Ex.05 Design a Website for Server Side Processing
## Date:

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
### HTML :
```HTML
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<title>Lamp Filament Power Calculator</title>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body {
   background-color: black;
   font-family: Arial, sans-serif;
}
.edge {
   width: 100%;
   padding-top: 100px;
   display: flex;
   justify-content: center;
}
.box {
   width: 400px;
   padding: 30px;
   font-size: 20px;
   background-color: dimgray;
   border-radius: 8px;
   box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.5);
   text-align: center;
}
.formelt {
   color: lightgray;
   margin-top: 10px;
   margin-bottom: 10px;
   display: flex;
   align-items: center;
   justify-content: space-between;
}
.formelt input[type="text"] {
   width: 200px;
   padding: 8px;
   font-size: 16px;
   background-color: darkgray;
   color: white;
   border: 1px solid gray;
   border-radius: 4px;
}
h1 {
   color: gold;
   padding-bottom: 20px;
   font-size: 24px;
}
input[type="submit"] {
   margin-top: 15px;
   padding: 10px 20px;
   font-size: 18px;
   background-color: darkorange;
   color: white;
   border: none;
   border-radius: 4px;
   cursor: pointer;
   transition: background-color 0.3s;
}
input[type="submit"]:hover {
   background-color: orange;
}
</style>
</head>
<body>
<h2><center><font color="red">RAKSHA DHARANIKA V (212223230167)</font></center></h2> 
<div class="edge">
   <div class="box">
       <h1>Power of Lamp Filament</h1>
       <form method="POST">
           
           <div class="formelt">
               <label>Intensity (I):</label>
               <input type="text" name="intensity" value=""> A
           </div>
           <div class="formelt">
               <label>Resistance (R):</label>
               <input type="text" name="resistance" value=""> Ω
           </div>
           <div class="formelt">
               <input type="submit" value="Calculate">
           </div>
           <div class="formelt">
               <label>Power (P):</label>
               <input type="text" name="power" value=""> W
           </div>
       </form>
   </div>
</div>
</body>
</html>


```
### VIEWS.PY :
```
from django.shortcuts import render

def calculate_power(request):
    # Initialize default values for intensity, resistance, and power
    i = r = power = None

    # Check if the form has been submitted
    if request.method == "POST":
        try:
            # Get intensity and resistance from the form data
            i = float(request.POST.get("intensity", 0))
            r = float(request.POST.get("resistance", 0))

            # Calculate power if both inputs are valid
            power = i ** 2 * r
        except ValueError:
            # If input is not a valid float, show an error or handle as needed
            power = "Invalid input"

    # Render the HTML template with values
    return render(request, "app/maths.html", {"i": i, "r": r, "power": power})

```
### URLS.PY
```
from django.urls import path
from . import views

urlpatterns = [
    path("", views.calculate_power, name="calculate_power"),
]

```
### MAIN URLS.PY :
```
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('app.urls')),  # Replace 'your_app_name' with your app's name
]


```

## SERVER SIDE PROCESSING:


## HOMEPAGE:


## RESULT:
The program for performing server side processing is completed successfully.
