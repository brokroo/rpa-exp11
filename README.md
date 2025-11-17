# Exp 11:API Integration and Data Processing
# UiPath: Weather API to Excel Automation

This UiPath project demonstrates a fundamental automation workflow:
1.  Fetching data from a live REST API (a Weather API).
2.  Parsing the JSON response.
3.  Extracting specific data points (e.g., humidity, temperature, description).
4.  Writing that data into a structured Excel file.

---

## ⚙️ Technologies & Dependencies

This project relies on the following UiPath activity packages:

* **UiPath.WebAPI.Activities:** Used for the `HTTP Request` and `Deserialize JSON` activities.
* **UiPath.Excel.Activities:** Used for the `Write Range Workbook` activity.
* **UiPath.System.Activities:** Used for core logic like `Assign`, `Build Data Table`, and `Add Data Row`.

---

## 🚀 How It Works: Project Workflow

The `Main.xaml` file executes the following steps in order:

1.  **Build Data Table:** An in-memory `DataTable` variable (e.g., `weatherTable`) is created. This table is structured with columns to hold the weather data (e.g., "City", "Temperature", "Humidity", "Description").

2.  **HTTP Request:** The robot makes a call to the specified weather API endpoint. The raw API response (a long string of text in JSON format) is saved to a String variable (e.g., `apiResponseString`).

3.  **Deserialize JSON:** The `apiResponseString` is converted from plain text into a `JObject` (e.g., `weatherJson`). This "JSON Object" allows us to easily find and extract data using keys.

4.  **Assign Data:** The robot uses `Assign` activities to pull specific values from the `weatherJson` object and save them into local variables. For example:
    * `humidity = weatherJson("main")("humidity").ToString`
    * `description = weatherJson("weather")(0)("description").ToString`

5.  **Add Data Row:** The variables (humidity, description, etc.) are compiled into an array and added as a new row to the in-memory `weatherTable`.

6.  **Write Range Workbook:** Finally, the robot takes the complete `weatherTable` and writes all its contents into an Excel file (e.g., `Downloads\chennai.xlsx`).

---

## 📋 How to Set Up and Run

1.  **Download:** Download or clone this project.
2.  **Open:** Open the `Main.xaml` file in UiPath Studio.
3.  **Restore Dependencies:** UiPath should prompt you to restore the required activity packages. Click "Restore."
4.  **Configure API (Important):**
    * Open the `HTTP Request` activity.
    * Update the `Endpoint` URL with your correct API endpoint.
    * If your API requires an **API Key**, add it in the `Headers` or `Parameters` section as required by your API provider.
5.  **Configure Output:**
    * Open the `Write Range Workbook` activity.
    * Update the file path to where you want the Excel file to be saved on your computer.
6.  **Run:**
    * Click **Debug (F5)** to run the process and see the execution step-by-step.
    * Click **Run (Ctrl+F6)** to run the process from start to finish.

## WORKFLOW AND OUTPUT:

<img width="1919" height="1079" alt="workflow 1" src="https://github.com/user-attachments/assets/9b7a32b6-195d-4fba-9c96-b4e0a4c34218" />
<img width="1919" height="1079" alt="workflow 2" src="https://github.com/user-attachments/assets/faa96a0e-92a1-4c4a-8ff6-21ae1545a24c" />
<img width="1919" height="1079" alt="workflow 3" src="https://github.com/user-attachments/assets/4c441f23-93a9-4ab8-8c19-f2f06188199c" />
<img width="389" height="138" alt="Output" src="https://github.com/user-attachments/assets/7b4efb77-d1ce-4299-bc8e-7ac6f3acc001" />

