# Holiday-Cost-Calculator
'''
This is a program that calculates a user’s total holiday cost, incluing the cost of plane, hotel, and car-rental.
It allows the user to choose from a list of pre-defined destinations, input the number of nights 
and rental days, and calculates the total cost based on their choices.
'''

# Estimate cost of hotel accommodation, assuming daily rate is $80
def hotel_cost(num_nights):
    rate_per_night = 80  
    return num_nights * rate_per_night

# Dictionary to store flight costs for different cities
def plane_cost(city_flight):
    flight_costs = {
    "Edinburgh": 500,
    "London": 700,
    "Manchester": 800,
    "Bristol": 400,
    "Newcastle": 900
  }
   
 # Check if the selected city is in the dictionary, otherwise return an error message
    if city_flight in flight_costs:
        return flight_costs[city_flight]
    else:
        raise ValueError ("Invalid selection!")
    

# Estimate cost of car rental, assuming daily car rental cost is $60
def car_rental(rental_days):
    daily_rental_cost = 60
    return rental_days * daily_rental_cost

def holiday_cost(city_flight, num_nights, rental_days):
  hotel_price = hotel_cost(num_nights)
  plane_price = plane_cost(city_flight)
  car_price = car_rental(rental_days)
  total_cost = hotel_price + plane_price + car_price
  return total_cost

available_cities = ["Edinburgh", "London", "Manchester", "Bristol", "Newcastle"]
while True:
    city_flight = input("Choose your destination city (from " + ", ".join(available_cities) + "): ").title()
    if city_flight in available_cities:
        break
    else:
        print ("Invalid Selection!")
num_nights = int(input("Enter the number of nights you will stay: "))
rental_days = int(input("Enter the number of days you will rent a car: "))

# Calculate total holiday cost
total_price = holiday_cost(city_flight, num_nights, rental_days)

#Output user's holiday information
print(f"\nYour holiday details:")
print(f"City: {city_flight}")
print(f"Number of nights: {num_nights}")
print(f"Rental days: {rental_days}")
print(f"Hotel cost: ${hotel_cost(num_nights)}")
print(f"Plane cost: ${plane_cost(city_flight)}")
print(f"Car rental cost: ${car_rental(rental_days)}")
print(f"Total cost: ${total_price}")
