# Tutorial about How to Use the Google API 

## Get your API KEY
To begin with, you need to have a Google API, and for that is a requierment to have a an account and to debit/credit card.
1. Enter to [Google Cloud Console](https://www.googleadservices.com/pagead/aclk?sa=L&ai=DChcSEwj5mb3ntPbkAhUQboYKHeh3DBoYABAAGgJ2dQ&ohost=www.google.com&cid=CAESEeD2a-isKx0bOlEmqvWSj8nQ&sig=AOD64_1Q1jDJoR8xP0O3PioSJdZWOb--BA&q=&ved=2ahUKEwjo17XntPbkAhXSuFkKHW8JB1sQ0Qx6BAgLEAE&adurl=)
2. You'll see a bar that says "select a project" in which you'll press where it says "create".
3. Write the name of your project and the ubication.
4. On the left, there is a column with various names, in which you'll press APIs & Services an then Credentials.
5. There is going to abe a blue box with "create credentials", then to "API Key".
6. It will display a box with your API Key, you should copy and save it.
7. Now, restrict the API key before using it.

## Decide what you would like to do
Google gives you a library with all the the APIs of their own. Depending on what you'd like to do you should choose.
e.g. Places API, Gmail API, Google Drive API, Youtube Analytics API, etc.
In this tutorial we'll use the Places API.
 * On the same column where you pressed APIs & Services, you'll see the library
 * When you chose the API that you'll use, click on the "enable" bottom.
 * The go to [Developers](https://developers.google.com/)
 * Homepage > products > Google Maps Platform >Documentation > Places API > Guides
 * There it will explain the requeried and optional parameterz for whatever it is that you would like to do.
 
 ## Example with the API KEY
 ```
 def search_nearby_places(latitude, longitude, radius, types, key):
    """
    Function to search naer places 
    according to the parameters.

    Parameters:
    latitude: float (latitude from the places we are searching by)
    longitude: float (longitude from the places we are searching by)
    radius: float (distance in meters within which to return place results)
    types: the kind of place we are lookinf for (e.g. restaurant)
    key: the API key
    
    Returns:
    A json
    """
    url = 'https://maps.googleapis.com/maps/api/place/nearbysearch/json?location={},{}&radius={}&types={}&key={}'.format(latitude, longitude, radius, types, key)
    res = requests.get(url) #Do the request of the data and getting it 
    results = json.loads(res.content) #Reading the object into readable dictionary
    return results 
  ```
 * In here, we used the [Nearby Seach Method](https://developers.google.com/places/web-service/search#PlaceSearchRequests)
 * You will read that the requiered parameters are location: (latitude, longitude), the radius, type, and your API key.
 * With the based url: https://maps.googleapis.com/maps/api/place/nearbysearch/output?parameters
 * You'll choose your output (can be json or a xml) after that a "?" is required to start to put the parameters
 * To separte each parameter you'll use "&"
 * Also, when you write the name of the paramter remember to use ={}, e.g. radius={}, and if it has two entries, location={},{}
 * We use the .format to add the parameters 
 
```
UPY_restaurants = search_nearby_places(20.988459, -89.736768, 2000, 'restaurant', key)
```
* For example, here we call the function and put the arguments, on the key you should put yours.

## Example with GoogleMaps Library

First, you'll need to install:
```
$ pip install -U googlemaps
```
* [Here](https://googlemaps.github.io/google-maps-services-python/docs/#module-googlemaps) you can find the documentation.
* In there, explains the parameters and what will return.
```
search_nearby_places():
  """
   This function uses python googlemaps library and gets nearby searches of the UPY type restaurant
    
   Parameters:
      None
      
   Returns:
    A json 
    """
    UPY_restaurants_google = gmaps.places_nearby(location = '20.988459, -89.736768', radius = 2000, type = 'restaurant')
    return UPY_restaurants_google
```
* In the documentation exaplains that you should declare a variable:
```
gmaps = googlemaps.Client(key='YOUR KEY')
```
* With that you'll do the rest of your functions, in the one we chose the .places_nearby and only write the arguments. Just like in the 
previous function.

In conclusion, both ways are good, and do the same thing. In our opinion, maybe you should learn how to use the API, so that you know
how internaly works and to further works.

## Documentation and Resources 

[Get an API Key](https://developers.google.com/places/web-service/get-api-key)

[Places API](https://developers.google.com/places/web-service/search#FindPlaceRequests)

[Google Maps Services Github](https://github.com/googlemaps/google-maps-services-python#api-keys)

[Overview Place API](https://developers.google.com/places/web-service/intro)

[Python Client for Google Maps Services Documentation](https://googlemaps.github.io/google-maps-services-python/docs/#module-googlemaps)


## Authors and acknowledgment
Author account:

[Samuel Venegas](https://github.com/Sam9Ves3)


