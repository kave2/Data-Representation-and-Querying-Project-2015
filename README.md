
##**Data Representation and Querying Project 2015**
###**Mario Szombati(G00316944)**

##Introduction
This project provides the design and documentation for the dataset "Parks in Galway City".

##About the data
Dataset is available at https://data.gov.ie/dataset/parks-in-galway-city as .csv(Comma Separated Values) file. It contains 29 rows, the first one being the object id of the actual park. It then contains another 13 values.

###*Description of each value and validation type values*

ObjectID: unique value of each park, type integer<br>
Number: number of park, type integer<br>
Name: name of the park, type String
Location: location of the park, type String<br>
AreaOfCity: area where the park is located, type String<br>
OpeningHours: opening hours of park, type integer<br>
Facilities: type of facilities in the park, type String<br>
Descr: short description of park, type String<br>
Lat: point of position from North to South, type Integer<br>
Long: point of position from East to West, type Integer<br>
EastITM: Irish Transverse Mercator co-ordinations, type Integer<br>
NorthITM: Irish Transverse Mercator co-ordinations, type Integer<br>
EastIG:  Irish grid reference system co-ordinations, type Integer<br>
NorthIG:  Irish grid reference system co-ordinations, type Integer<br>

Csv file converted to .json can be downloaded from
https://www.dropbox.com/s/83vu4o0t5m2orxo/data.json?dl=0.


----------


###*Explanation of GET, POST, DELETE, PUT*
####*GET*
The GET method requests a representation of the specified resource. Requests using GET should only retrieve data and should have no other effect

####*POST*
POST request method requests that a web server accepts and stores the data enclosed in the body of the request message. Used when uploading a file or submitting a completed web form.

####*DELETE*
The DELETE method deletes the specified resource

####*PUT*
The PUT method requests that the enclosed entity be stored under the supplied URI.  if the URI does not point to an existing resource, then the server can create the resource with that URI


----------


####Sample  JSON data
 

    {
        "OBJECTID": 1,
        "NUMBER": 1,
        "NAME": "Corrib Park",
        "LOCATION": "Newcastle, Galway",
        "AREAOFCITY": "City- West",
        "OPENINGHRs": "No restricted opening hours",
        "FACILITIES": "Passive Recreational Walkways, 3G Artificial Surface Pitch, Multi- Use Games Area(MUGA), Planting areas with flowers, sh",
        "DESCR": "Local Neighbourhood Park",
        "Lat": 53.279,
        "Long": -9.075,
        "EastITM": 528328.238,
        "NorthITM": 725961.154,
        "EastIG": 128361.999,
        "NorthIG": 225932.124
      }

  
 

     {
        "OBJECTID": 2,
        "NUMBER": 2,
        "NAME": "Shantalla Park",
        "LOCATION": "Seamus Quirke Road, Shantalla",
        "AREAOFCITY": "City- West",
        "OPENINGHRs": "No restricted opening hours",
        "FACILITIES": "1 Soccer/ Gaa Playing Pitch, Planting area with flowers, shrubs and trees.",
        "DESCR": "Local Neighbourhood Park",
        "Lat": 53.278,
        "Long": -9.068,
        "EastITM": 528739.965,
        "NorthITM": 725816.312,
        "EastIG": 128773.815,
        "NorthIG": 225787.254
      }

  


----------

###*Get Method*
####*Silent get request:*
http://tld/park

    GET /park HTTP/1.1
    Host: kave.info
    Cache-Control: no-cache

####*Get request with parameters:*
http://TLD/park?OBJECTID=1

    GET /park?OBJECTID=1 HTTP/1.1
    Host: kave.info
    Cache-Control: no-cache
  
####*Response to GET request with parameters:*

####If the value of ObjectId is added as 1 it will bring all the relevant information about park with object id value 1, data pulled from server would look as .json file example above.
     {
        "OBJECTID": 1,
        "NUMBER": 1,
        "NAME": "Corrib Park",
        "LOCATION": "Newcastle, Galway",
        "AREAOFCITY": "City- West",
        "OPENINGHRs": "No restricted opening hours",
        "FACILITIES": "Passive Recreational Walkways, 3G Artificial Surface Pitch, Multi- Use Games Area(MUGA), Planting areas with flowers, sh",
        "DESCR": "Local Neighbourhood Park",
        "Lat": 53.279,
        "Long": -9.075,
        "EastITM": 528328.238,
        "NorthITM": 725961.154,
        "EastIG": 128361.999,
        "NorthIG": 225932.124
      },

####If the value of AreaOfCity is added as City-West the response would be all the parks from City-West.
http://tld/park?AreaOfCity=City-West

    GET /park?AreaOfCity=City- West HTTP/1.1
    Host: kave.info
    Cache-Control: no-cache

####If the value of Location is changed as Shantalla, Galway the response would be all the parks from Shantalla, Galway.
http://tld/park?Location=Shantalla,Galway

    GET /park?Location=Shantalla, Galway HTTP/1.1
    Host: kave.info
    Cache-Control: no-cache




###*POST Method*

http://tld.com/park[/ID]

    POST /park HTTP/1.1
    Host: kave.info
    Cache-Control: no-cache
    Content-Type: multipart/form-data;

    Content-Disposition: form-data; name="OBJECTID";value="1"
    Content-Disposition: form-data; name="NUMBER";value="1"
    Content-Disposition: form-data; name="NAME";value="Corrib park"
    Content-Disposition: form-data; name="LOCATION";value="Newcastle, Galway"
    Content-Disposition: form-data; name="AREAOFCITY";value="City- West"
    Content-Disposition: form-data; name="OPENINGHRs";value="No restricted opening hours"
    Content-Disposition: form-data; name="FACILITIES";value="Passive Recreational Walkways, 3G Artificial Surface Pitch, Multi- Use Games Area(MUGA), Planting areas with flowers, sh"
    Content-Disposition: form-data; name="DESCR";value="Local Neighbourhood Park"
    Content-Disposition: form-data; name="Lat";value="53.279"
    Content-Disposition: form-data; name="Long";value="-9.075"
    Content-Disposition: form-data; name="EastITM";value="528328.238"
    Content-Disposition: form-data; name="NorthITM";value="725961.154"
    Content-Disposition: form-data; name="EastIG";value="128361.999"
    Content-Disposition: form-data; name="NorthIG";value="225932.124"


###Actual JSON object being send by POST request
    {
        "OBJECTID": 1,
        "NUMBER": 1,
        "NAME": "Corrib Park",
        "LOCATION": "Newcastle, Galway",
        "AREAOFCITY": "City- West",
        "OPENINGHRs": "No restricted opening hours",
        "FACILITIES": "Passive Recreational Walkways, 3G Artificial Surface Pitch, Multi- Use Games Area(MUGA), Planting areas with flowers, sh",
        "DESCR": "Local Neighbourhood Park",
        "Lat": 53.279,
        "Long": -9.075,
        "EastITM": 528328.238,
        "NorthITM": 725961.154,
        "EastIG": 128361.999,
        "NorthIG": 225932.124
      }


###*DELETE Method*



    DELETE /park?OBJECTID=1 HTTP/1.1
    Host: kave.info
    Cache-Control: no-cache

####This call would delete the record of ObjectId = 1 from web server.

###*PUT Method*


    PUT /park?OBJECTID=1&NUMBER=1&NAME=Briarhill Park HTTP/1.1
    Host: kave.info
    Cache-Control: no-cache
    
####This call would update the .json file and its attribute name from Corrib Park to Briarhill Park on the web server.
####Before:

    {
        "NAME": "Corrib Park",
    }
 
####After:
    {
        "NAME": "Briarhill Park",
    }

