 Data-Scraping with Selenium and Dynamic Filtering using Streamlit

Introduction
solution for collecting, organizing, and visualizing bus travel data. It automates the extraction of real-time bus data The Data-Scraping with Selenium and Dynamic Filtering using Streamlit project provides a from the Redbus website using Selenium and presents it in an interactive Streamlit web app. Users can filter buses by routes, prices, or availability, making it a helpful tool for transport managers and travelers.
________________________________________
Domain Overview
Domain: Transportation.
The project falls under the transportation sector, aiming to optimize bus service management by gathering and presenting real-time data.
________________________________________
Skill Takeaway
This project covers several key areas:
•	Python Scripting: Automating tasks using Python.
•	Selenium: A browser automation tool for web scraping.
•	MySQL: Storing and managing data in relational databases.
•	Streamlit: Building web applications for data interaction.
•	Data Visualization: Presenting data through interactive plots using Plotly.
 

Technology Stack
•	Python (3.9+): For scripting and backend logic.
•	Selenium WebDriver: Automating browser interactions to scrape Redbus data.
•	MySQL: Storing and querying the data in a database.
•	Streamlit: Frontend for building dynamic, interactive dashboards.
•	Pandas: Handling and transforming data during scraping and analysis.
•	Plotly: Visualizing bus data interactively.
________________________________________
System Architecture
The system follows a modular design:
Data Scraping: Selenium is used to scrape Redbus for bus data such as routes, schedules, prices, and availability.
Data Storage: The data is stored in a MySQL database to allow easy querying and management.
Web Interface: The Streamlit application is used to provide users with dynamic filtering and visualization of bus data.
 

Project Workflow

Data Scraping with Selenium
The data collection process uses Selenium to:
•	Navigate to the Redbus website.
•	Automate interactions such as selecting cities, dates, and fetching search results.
•	Scrape bus route details, fares, bus types, and seat availability.
Code snippet:

from selenium import webdriver
from selenium.webdriver.common.by import By

# Setting up the Selenium WebDriver
driver = webdriver.Chrome(executable_path='/path/to/chromedriver')

# Navigate to Redbus and search for buses
driver.get('https://www.redbus.in/')
search_field = driver.find_element(By.ID, 'src')
search_field.send_keys('Bangalore')
 

Storing Data in MySQL
Once the data is collected, it's stored in a MySQL database. Pandas DataFrames are used to manage the data before inserting it into the database. The table structure includes fields for:
•	Route_name: The bus route.
•	Fare: Price of the ticket.
•	Availability: Number of available seats.
Code snippet:
import mysql.connector

# Connecting to MySQL
conn = mysql.connector.connect(
    host="localhost",
    user="root",
    password="934497x2",
    database="redbus_details"
)

cursor = conn.cursor()

# Create table query
create_table = """CREATE TABLE IF NOT EXISTS bus_routes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    Route_name VARCHAR(255),
    Fare DECIMAL(10,2),
    Availability INT
)"""
cursor.execute(create_table)

Building the Web App with Streamlit
Streamlit creates a dynamic front-end for the application. Users can filter data by states and routes, visualize price trends, and see real-time bus availability.
Streamlit’s components allow for easy data interaction:
python
Copy code
import streamlit as st

# Sidebar for state and route selection
state = st.selectbox("Select State", ["Kerala", "Andhra", "Telangana"])
route = st.selectbox("Select Route", available_routes[state])

# Display filtered data
st.write("Bus Routes:", filtered_data)
________________________________________
Features of the Application
•	Automated Data Collection: Scrape real-time bus data using Selenium.
•	Dynamic Filtering: Use Streamlit to filter by state, route, or price.
•	Interactive Charts: Visualize data such as price trends and seat availability with Plotly.
•	Data Management: Efficiently store and retrieve data from MySQL.
________________________________________
Code Explanation
Data Collection Using Selenium
Selenium simulates browser interactions to scrape bus data. It navigates through the Redbus website, performs searches, and extracts bus information dynamically.
Data Management with MySQL
Once data is collected, it is inserted into MySQL tables. Pandas DataFrames help clean and structure the data before storage.
Application Usage with Streamlit
Users can interact with the bus data through a Streamlit web application. It allows them to:
•	Filter buses by state and route.
•	View the lowest and highest fares.
•	See available seats for each bus.
________________________________________
Database Design
The MySQL database schema includes:
•	bus routes: Stores route-specific details.
•	bus fares: Contains fare information for different buses.
•	bus seats: Manages seat availability data.
Each table has a primary key for easy retrieval and foreign keys for linking between tables.
 

Web Interface Design
The Streamlit web interface includes:
•	A sidebar with filters for selecting states and routes.
•	Tables displaying filtered bus data.
•	Interactive charts and graphs showing bus trends.
Users can customize their search queries and view bus data in real-time.
________________________________________
Data Visualization with Plotly
Plotly is integrated into the Streamlit app to provide interactive data visualizations. It generates charts such as:
•	Price distribution: Showing fare variations across routes.
•	Seat availability: Displaying real-time seat counts.
Example:
python
Copy code
import plotly.express as px

# Create a bar chart for fares
fig = px.bar(df, x='Route_name', y='Fare', color='Availability')
st.plotly_chart(fig)
 

Future Enhancements
•	Additional Data Sources: Expand the application to include train and flight data.
•	User Authentication: Add user profiles and login systems.
•	Predictive Models: Use machine learning to predict fare hikes or bus availability.
________________________________________
Conclusion
The Data-Scraping with Selenium and Dynamic Filtering using Streamlit project provides a comprehensive solution for gathering, managing, and visualizing bus travel data. By automating the process with Selenium and offering an interactive dashboard with Streamlit, it simplifies bus information retrieval and enhances user experience.
________________________________________

