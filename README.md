# Zillow_API_Housing_Estimates_In_Disaster
Using the Zillow API, this project allows organizations like FEMA to estimate potential property damage caused by a natural disaster by using house value statistics.

Zillow-Disaster-Estimates:

During a disaster, it is important to model and estimate the potential or forecasted effect of the event, including the projected/forecasted damage. Estimates for other factors exist, this project seeks to add an additional indicator, up-to-date estimates for property value in the area of effect. The tool will allow for quick return on property statistics of an affected area or zipcode.

Addressing the Problem - Zipcode Value Estimate:

The first function 'The Damage Estimator' references our address dictionary from Openaddress.io. After a few cleaning steps to allow for seamless integration into the API, one can quickly and efficiently produce ZEstimates for any given zipcode. The Function takes an initial zip code input, used as the reference for the dictionary, that returns all of the values from the dictionary within the given zipcode. Once this is done, each row of the dictionary is referenced into the URL ('number' = street number, 'name' = street name, 'city' = city, 'state' = state and 'postcode' = zipcode (also the input)). This would produce a string in the proper format, -i.e. 123 Ex St., Example, State-. With the string inputs established the function loops through the dictionary for each row and returns only those which return values from Zillow and appends them to a list. Statistics are printed based on the values obtained from Zillow and a histogram of the valuations.

Beyond the Deliverable - Area based Value Estimate:

After running several queries of zipcode we found that zipcode was not as dynamic as we were hoping. If a disaster were to occur it could possible span multiple zipcodes and potentially only damage select houses within a given zipcode. After discovering this, we found that the zipcode selector would be too general in the instance of a large/small scale disaster. Our next function allows for customizable selection areas that return the same statistics as above. The function was called 'The Circle Selector' because the original code includes a circle generator with inputs for latitude/longitude centerpoint and kilometer radius, this name is somewhat misleading as the function is able to take ANY polygon shape (totally customizable by the user) with perimeter points in LatLong. Once the polygon is generated or imported, the user must generate GeoPandas points for the area given LatLong. Once these points are generated, they are appended into a list and used as the reference for the Polygon contains in function. All points that are within the polygon return as a list, and their index numbers are used to reference the greater address database. Once these addresses are selected, they are run through the previous function and return the same statistics and plots.

Future Developments:

- We were able to generate points on a map using GeoPandas but this has not been totally integrated into the functions. This would allow for easy visualization of an affected area.
- Polygon generation with Bokeh was also considered but not yet implemented, allowing for easy drawing implementation to select a disaster area.
- An interactive map of zipcodes which could return values based on any givn zipcodes was considered but not yet implemented, due primarily to Zillow's API ToS which does not allow for downloading their Zestimate data.

Known Issues:

- Computational Inefficiency: Many of the processes take substantial computational power, this cause result in long run times over larger areas.
- Missing Zestimates: Zillow is not comprehensive, this results in a substantial amount of missing data in the returns. Averaging around 10% returned estimates for all addresses given.

-There are a variety of important librarys that were used in the code which can be seen at the beginning of each code segment.-

This project was developed by:

Allison Ragan https://www.linkedin.com/in/allison-ragan/ allison.n.ragan@gmail.com

Erik Green https://www.linkedin.com/in/erikgreenj/ erikgreenj@gmail.com

Suzanne McGann https://www.linkedin.com/in/suzanne-mcgann-79052b83/ suzannemcgann2@gmail.com

Melanie Welcome https://www.linkedin.com/in/melanie-welcome/ mwelcome21@gmail.com

Thomas Bacas https://www.linkedin.com/in/thomas-bacas/ thomasbacas@gmail.com
