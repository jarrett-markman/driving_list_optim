# Optimizing driving lists for the SU club tennis team

For the Syracuse University Club tennis team, we organize driving lists for all practices and matches. In the past, we've manually assigned driving lists attempting to minimize the total distance traveled to practice. As one of the Captains during the 2024-2025 year, making driving lists is one of my many responsibilities. With the power of programming, this is something that we can calculate and optimize solely with driver start locations, passenger locations, and an end location (Drumlins Tennis Club). 

With csv's for drivers that consists of: Name/Address/Spots (available spots in the car for passengers), and passengers that consists of: Name/Address, using the GeoPy library we can find the latitude and longitude coordinates of each possible pickup location for each possible combination of passengers. 

The .ipynb script requires 2 inputs: driver_names, and passenger_names, which are then used to subset those specific drivers and passengers from the drivers and passengers csv's, which are ultimately used in the find_best_routes function as "practice_drivers" and "practice_passengers", which finds all the possible driver/passenger pairings, and minimizes the total distance traveled for all drivers. 

The calculate_route_distance function calculates the distance from the drivers start location -> passenger 1 location -> ... -> passenger n location + end_location (it is calculated as the distance in a straight line as if you could just travel from point A to point B). Next, the generate_valid_assignments finds all possible route combinations for passengers that would reach the maximum capacity of car, and ensures that every passenger gets placed in a car. All the possible passenger combinations created from generate_valid_assignments is then applied to find_best_route, which applies each unique combination, which applies the calculate_route_distance function to calculate the distance for each driver's possible sequence of pickups, and finally returns the best_assignment and best_total_distance, which returns the unique passenger combination that requires the least total amount of travel for all the drivers combined. 
