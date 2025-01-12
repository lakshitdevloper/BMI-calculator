# BMI-calculator
This software will be calculate your BMI this is made by python
import tkinter as tk
from tkinter import messagebox

# Function to calculate BMI
def calculate_bmi():
    try:
        # Get user input
        weight = float(weight_entry.get())
        height = float(height_entry.get())

        # Calculate BMI
        bmi = weight / (height ** 2)

        # Interpret BMI
        if bmi < 18.5:
            category = "Underweight"
        elif 18.5 <= bmi < 24.9:
            category = "Normal weight"
        elif 25 <= bmi < 29.9:
            category = "Overweight"
        else:
            category = "Obesity"

        # Display result
        result_label.config(text=f"BMI: {bmi:.2f}\nCategory: {category}")
    
    except ValueError:
        # Show error message if inputs are invalid
        messagebox.showerror("Invalid Input", "Please enter valid numeric values for weight and height.")

# Create the main window
window = tk.Tk()
window.title("BMI Calculator")
window.geometry("400x300")
window.resizable(False, False)
window.config(bg="#f4f4f4")

# Add title label
title_label = tk.Label(window, text="BMI Calculator", font=("Helvetica", 18, "bold"), bg="#f4f4f4", fg="#333")
title_label.pack(pady=10)

# Create input frame
input_frame = tk.Frame(window, bg="#f4f4f4")
input_frame.pack(pady=10)

# Weight input
weight_label = tk.Label(input_frame, text="Weight (kg):", font=("Helvetica", 12), bg="#f4f4f4")
weight_label.grid(row=0, column=0, padx=5, pady=5, sticky="e")
weight_entry = tk.Entry(input_frame, font=("Helvetica", 12), width=10)
weight_entry.grid(row=0, column=1, padx=5, pady=5)

# Height input
height_label = tk.Label(input_frame, text="Height (m):", font=("Helvetica", 12), bg="#f4f4f4")
height_label.grid(row=1, column=0, padx=5, pady=5, sticky="e")
height_entry = tk.Entry(input_frame, font=("Helvetica", 12), width=10)
height_entry.grid(row=1, column=1, padx=5, pady=5)

# Calculate button
calculate_button = tk.Button(window, text="Calculate", font=("Helvetica", 12, "bold"), bg="#007acc", fg="white",
                             command=calculate_bmi)
calculate_button.pack(pady=10)

# Result label
result_label = tk.Label(window, text="", font=("Helvetica", 14), bg="#f4f4f4", fg="#007acc")
result_label.pack(pady=10)

# Run the application
window.mainloop()
