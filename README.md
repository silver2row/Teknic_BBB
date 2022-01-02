# TekTips-BeagleBone-Examples

** I will be trying to set up some docs. **

` These docs. will be in relation to BeagleBone Black Rev. C `

# 1. Adding the correct documentation...

As of now, there has been an update by the Co. that produced the motors,
the SDK, and the templates.

Also, most of what has happened in the past with the Cross-Compilation is
now an error in context. So, an easier approach would be to understand
your system, what C++ library is on your BBB or BBBW, and then use a 
Makefile with ` make ` to install the required lib. onto the BBB or other
Single Board Computer with the am335x...

So, sign in to the Teknic website at https://teknic.com/ and then scross the
above options in the headers to Downloads and then to Clearpath and then to 
Software. The software, their SDK in question, can be found in this option.

It is in the form of .tar.gz.

Simply tar the file by calling ` tar -xvf <TheFile.tar.gz> ` to decompress it.

Then, going into the dir. to make the SDK is next. 

...

# 2. Getting the correct hardware to run the servos...

So, as most of everyone knows already, running heavy loads on fantastic motors
does not come at a cheap price. So, if you are looking to add a high-end 
motor to your BBB with SDKs involved, I recommend this product.

For back up of power failure on specific hardware during running routes and edges,
one might also get a Power Hub from their company. They have drives, motors,
cables, and other hardware to get you up and running with ease.

Look into their website if this is what should entail in your life.

# 3. Making the USB Driver available on the BBB for working with their Hub...

There is also another type of hardware piece to get if working with their SDK and
motors, i.e. the Software Controlled ClearPath Servos. They are fully integrated.

The SC Hub is what I am talking about currently. You can run four motors off one hub.
You can also, if needed, attach the power hub with ease to the SC Hub in case
one is worried about power failure and/or issues with too much current.

** I will be making a short demo and I encourage you to provide your build as well **

Seth

P.S. If by chance you are working with these SC-Servos from Teknic and have used the SDK
from them, please add on and stay collective. 
