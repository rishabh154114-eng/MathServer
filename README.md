# Ex.04 Design a Website for Server Side Processing

## Date:

28-05-2026

---

# AIM:

To create a web page to calculate total bill amount with GST from price and GST percentage using server-side scripts.

---

# FORMULA:

Bill = P + (P * GST / 100)

P → Price (in Rupees)
GST → GST Percentage
Bill → Total Bill Amount

---

# DESIGN STEPS:

### Step 1:

Clone the repository from GitHub.

### Step 2:

Create Django Admin project.

### Step 3:

Create a New App under the Django Admin project.

### Step 4:

Create a HTML file to implement form based input and output.

### Step 5:

Create python programs for views and urls to perform server side processing.

### Step 6:

Receive input values from the form using request.POST.get().

### Step 7:

Calculate the total bill amount including GST.

### Step 8:

Display the calculated result in the server console.

### Step 9:

Render the result to the HTML template.

### Step 10:

Publish the website in localhost.

---

# PROGRAM:

## mathexp_4.html

```html
<html>

<head>

    <title>GST Bill Calculator</title>

    <style>

        body
        {
            font-family: Arial, sans-serif;

            background-color: purple;

            color: white;

            display: flex;

            justify-content: center;

            align-items: center;

            height: 100vh;
        }

        .table
        {
            width: 500px;

            background-color: crimson;

            border: 5px solid cyan;

            padding: 40px;

            text-align: center;

            border-radius: 15px;
        }

        input
        {
            padding: 8px;

            width: 200px;
        }

        button
        {
            padding: 10px 20px;

            background-color: cyan;

            border: none;

            font-weight: bold;

            cursor: pointer;
        }

    </style>

</head>

<body>

    <div class="table">

        <h1>GST Bill Calculator</h1>

        <h3>T. Rishabh Srivastav [21224113001]</h3>

        <form method="POST">

            {% csrf_token %}

            <label>Price :</label>

            <input type="number" name="price" value="{{ p }}">

            <br><br>

            <label>GST % :</label>

            <input type="number" name="gst" value="{{ gst }}">

            <br><br>

            <button type="submit">
                Calculate
            </button>

            <br><br>

            <label>Total Bill :</label>

            <input type="text" value="{{ bill }}" readonly>

        </form>

    </div>

</body>

</html>
```

---

## views.py

```python
from django.shortcuts import render

def bill(request):

    p = 0
    gst = 0
    bill = 0

    if request.method == 'POST':

        p = int(request.POST.get('price', 0))

        gst = int(request.POST.get('gst', 0))

        bill = p + (p * gst / 100)

    print("Price =", p)
    print("GST =", gst)
    print("Total Bill =", bill)

    return render(
        request,
        'mathserverapp/mathexp_4.html',
        {
            'p': p,
            'gst': gst,
            'bill': bill
        }
    )
```

---

## urls.py

```python
from django.contrib import admin
from django.urls import path
from mathserverapp import views

urlpatterns = [

    path('', views.bill, name='bill'),

]
```

---

# OUTPUT - SERVER SIDE:

<img width="1141" height="649" alt="Screenshot 2026-05-28 195942" src="https://github.com/user-attachments/assets/0f2f0d3c-9eac-43c0-a61b-1c9ef5457dcb" />


# OUTPUT - WEBPAGE:

<img width="1897" height="956" alt="Screenshot 2026-05-28 195407" src="https://github.com/user-attachments/assets/1a0f6115-8f58-40b8-ab09-b19dff53a3f9" />


---

# RESULT:

The web page to calculate total bill amount with GST using server-side scripts was created successfully.
