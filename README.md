
# Pizza Ordering Application with Gradio

This project is a simple pizza ordering application built using Gradio. The application allows users to select the size of their pizza and add up to three toppings. It then calculates and displays the total cost, including tax.

## Getting Started

### 1. Install Dependencies

To start, you'll need to install Gradio in your Google Colab environment:

```bash
!pip install gradio
```

### 2. Import Gradio and Define the Application

After installing Gradio, import it and define the function for calculating the pizza price based on user inputs:

```python
import gradio as gr

# Define the pizza order function
def pizza_order(size, topping_1, topping_2, topping_3):
    if size.lower() == "large":
        size_price = 19.99
    elif size.lower() == "medium":
        size_price = 14.99
    elif size.lower() == "small":
        size_price = 9.99

    topping_price = 0
    if topping_1:
        topping_price += 1.99
    if topping_2:
        topping_price += 1.99
    if topping_3:
        topping_price += 1.99

    pizza_price = size_price + topping_price + (size_price + topping_price) * 0.07
    return f"Your pizza costs ${pizza_price:.2f}, including tax."
```

### 3. Create the Gradio Interface

Create a Gradio interface for the pizza ordering function:

```python
app = gr.Interface(fn=pizza_order,
                   inputs=["text", "text", "text", "text"],
                   outputs="text")

app.launch()
```

### 4. Launch the Application

Finally, launch the application to start using the pizza ordering system:

```python
app.launch()
```

### Example Usage

Once the application is running, users can input their desired pizza size and up to three toppings. The application will return the total cost of the pizza, including tax.

## UI Improvements for Future Iterations

Here are some suggestions for improving the UI in future versions of this application:

1. **Dropdown Menus for Pizza Size and Toppings**: 
   - Instead of using text inputs for pizza size and toppings, you could use dropdown menus. This would ensure that users select valid options and prevent errors from incorrect text input.
   
   ```python
   inputs = [
       gr.inputs.Dropdown(["Large", "Medium", "Small"], label="Pizza Size"),
       gr.inputs.Checkbox(label="Topping 1"),
       gr.inputs.Checkbox(label="Topping 2"),
       gr.inputs.Checkbox(label="Topping 3")
   ]
   ```

2. **Checkboxes for Toppings**: 
   - Use checkboxes for the toppings to make it more intuitive for users to select multiple options.

3. **Add Images**:
   - Adding images of different pizza sizes and toppings can enhance the visual appeal of the application and make it more engaging.

4. **Improved Error Handling**:
   - Implement better error handling to guide users when they input invalid data (e.g., entering text in a field where only numbers are expected).

5. **Customize Output Format**:
   - Enhance the output to display a more detailed receipt-like format, showing the breakdown of costs, toppings selected, and total price.

6. **Responsive Design**:
   - Ensure that the interface is mobile-friendly and adjusts well to different screen sizes for a better user experience on various devices.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

Special thanks to the Gradio team for providing an easy-to-use interface for machine learning applications.
```
