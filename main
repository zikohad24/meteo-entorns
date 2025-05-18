import requests
import json
from datetime import datetime

latitude = 41.39
longitude = 2.16

url = f"https://api.open-meteo.com/v1/forecast?latitude={latitude}&longitude={longitude}&hourly=temperature_2m"

response = requests.get(url)
data = response.json()

temperatures = data["hourly"]["temperature_2m"]

temp_max = max(temperatures)
temp_min = min(temperatures)
temp_avg = sum(temperatures) / len(temperatures)

today = datetime.now().strftime("%Y%m%d")
filename = f"temp_{today}.json"

results = {
    "date": today,
    "max": temp_max,
    "min": temp_min,
    "avg": round(temp_avg, 2)
}

with open(filename, "w") as f:
    json.dump(results, f, indent=4)

print(f"Saved to {filename}")
