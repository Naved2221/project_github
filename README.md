# project_github
#a ambiguous random project

import requests







def get_weather(city):
    api_key = 'YOUR_API_KEY'  # Replace with your OpenWeatherMap API key
    base_url = 'http://api.openweathermap.org/data/2.5/weather'
    
    params = {
        'q': city,
        'appid': api_key,
        'units': 'metric'  # Set the units to metric for Celsius temperature
    }
    
    try:
        response = requests.get(base_url, params=params)
        data = response.json()
        
        if response.status_code == 200:
            temperature = data['main']['temp']
            humidity = data['main']['humidity']
            description = data['weather'][0]['description']
            
            print(f"Weather in {city}:")
            print(f"Temperature: {temperature}°C")
            print(f"Humidity: {humidity}%")
            print(f"Description: {description}")
        else:
            print(f"Error: {data['message']}")
    
    except requests.exceptions.RequestException as e:
        print(f"Error: {e}")

# Example usage
city_name = input("Enter city name: ")
get_weather(city_name)
