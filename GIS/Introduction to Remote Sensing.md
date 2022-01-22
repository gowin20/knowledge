#remote-sensing 

---
use cisco vpn

---
- What is RS?
- RS vs GIS
- Modern Remote Sensing

# Intro to Remote Sensing (RS)
**The art and science of obtaining information about an object without coming into direct contact with the object**
It's so useful because:
- global coverage due to sattelite imagery (analyzing spatial patterns)
- able to view data over time, different temporal scales (change detection)
- allows us to analyze spectrums the human eye can't see (infrared + thermal)
- not intrusive, to the environment or people

Useful for natural analysis and cultural analysis

### Limitations
- People hype it up too much
- Sensors are delicate and need careful calibration
- It's super expensive!


## RS vs GIS
**ALL REMOTE SENSING IS [[Raster Data]]**
(as opposed to vector data)
GIS is generally more concerned with vector data, but RS is raster
Raster is faster (to update)



## History of RS
Term was initially used in the 1950s, but the actual history began with Sputnik, the space race. 
We started to send sattelites into orbit which returned images to us, initially primarily about weather.
Weather channels, all weather predictions, are pretty much ALL remote sensing now.


# Sattelites
The sattelite we're using: LANDSAT (a series of sattelites), existing since the 70s
Landsat 4 and Landsat 5 both have 30 meter pixel resolutions. There are now a lot more than 5 and the resolution is still really good / better!

- High Resolution Imagery
- Water Flow Patterns
- 3d modeling to mimic landscape


Nowadays things are evolving RAPIDLY!!!

DRONES are a primary component of remote sensing now. We'll be using the UCLA Drone Lab if we go in-person


# Fundamental Mechanic: Reflection and Absorption
Objects are the color of the bandwith of light they REFLECT
![[Pasted image 20220110101725.png]]
- Plant reflect green light so they're green. 
- Banana reflect yellow light so they're yellow
- White reflects all colors
- Black absorbs all colors


Basically, this is how we get ALL of the image analysis data for RS. It's pretty much just **color analysis of pixels**
As a basic application, we can see how snow coverage varies year to year or seasonally:
![[Pasted image 20220110101844.png]]

Weather, hurricanes are an important issue
Another important issue: drought and fire
![[Pasted image 20220110101935.png]]
In the above image, the red pixels are geographic units which have increased over 300 degrees Farenheight. We can use thermal imaging to analyze that and plot location of fires!