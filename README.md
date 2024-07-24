[17/11/2023, 10:31 pm] Harshit Paaji Clsmmate: <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BMI Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 20px;
        }
        form {
            display: inline-block;
            text-align: left;
        }
    </style>
</head>
<body>

    <h1>BMI Calculator</h1>

    <form id="bmiForm">
        <label for="weight">Weight (kg):</label>
        <input type="number" id="weight" required step="any">
        <br>

        <label for="height">Height (m):</label>
        <input type="number" id="height" required step="any">
        <br>

        <button type="button" onclick="calculateBMI()">Calculate BMI</button>
    </form>

    <h2 id="result"></h2>

    <script>
        function calculateBMI() {
            // Get input values
            var weight = document.getElementById("weight").value;
            var height = document.getElementById("height").value;

            // Calculate BMI
            var bmi = weight / (height * height);

            // Output result
            var resultElement = document.getElementById("result");
            if (bmi >= 30) {
                resultElement.textContent = "BMI: " + bmi.toFixed(2) + " (Obese)";
            } else {
                resultElement.textContent = "BMI: " + bmi.toFixed(2) + " (Fit)";
            }
        }
    </script>

</body>
</html>
[17/11/2023, 10:46 pm] Harshit Paaji Clsmmate: # BMI Calculator Program

def calculate_bmi(height, weight):
    # BMI formula: weight (kg) / (height (m) * height (m))
    height_in_meters = height / 100  # Convert height from cm to meters
    bmi = weight / (height_in_meters ** 2)
    return bmi

def assess_fitness(bmi):
    if bmi < 18.5:
        return "Underweight"
    elif 18.5 <= bmi < 25:
        return "Normal Weight"
    elif 25 <= bmi < 30:
        return "Overweight"
    else:
        return "Obese"

# Input from the user
height = float(input("Enter your height in centimeters: "))
weight = float(input("Enter your weight in kilograms: "))

# Calculate BMI
bmi = calculate_bmi(height, weight)

# Assess fitness based on BMI
fitness_result = assess_fitness(bmi)

# Print the results
print(f"Your BMI is: {bmi:.2f}")
print(f"Fitness Assessment: {fitness_result}")

# HTML Code for Front-End
html_code = f"""
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BMI Calculator</title>
    <style>
        body {{
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            padding: 50px;
        }}
        h2 {{
            color: #333;
        }}
    </style>
</head>
<body>
    <h2>BMI Calculator and Fitness Assessment</h2>
    <form action="">
        <label for="height">Enter your height in centimeters:</label>
        <input type="number" id="height" name="height" required><br>
        <label for="weight">Enter your weight in kilograms:</label>
        <input type="number" id="weight" name="weight" required><br><br>
        <button type="button" onclick="calculateBMI()">Calculate BMI</button><br><br>
        <p id="bmiResult"></p>
        <p id="fitnessResult"></p>
    </form>
    <script>
        function calculateBMI() {{
            var height = document.getElementById('height').value;
            var weight = document.getElementById('weight').value;
            var bmi = (weight / ((height / 100) ** 2)).toFixed(2);
            var fitnessResult = '';

            if (bmi < 18.5) {{
                fitnessResult = 'Underweight';
            }} else if (bmi < 25) {{
                fitnessResult = 'Normal Weight';
            }} else if (bmi < 30) {{
                fitnessResult = 'Overweight';
            }} else {{
                fitnessResult = 'Obese';
            }}

            document.getElementById('bmiResult').innerHTML = 'Your BMI is: ' + bmi;
            document.getElementById('fitnessResult').innerHTML = 'Fitness Assessment: ' + fitnessResult;
        }}
    </script>
</body>
</html>
"""

# Save HTML code to a file
with open("bmi_calculator.html", "w") as html_file:
    html_file.write(html_code)
