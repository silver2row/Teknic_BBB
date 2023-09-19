# TekTips-BeagleBone-Examples

# ** I will be trying to set up some docs. **

` These docs. will be in relation to BeagleBone Black Rev. C `

# 1. Adding the correct documentation...

Here along w/ the correct bunch of hardware and a motor, one can see the port opened!

```
HelloWorld
======================

This example program will initiate communication with up to three ports.
The port number is automaticaly detected when using the USB connection on the SC4-Hub board.
```

and...

```

//Required include files
#include <stdio.h>
#include <iostream>
#include "pubSysCls.h"

using namespace sFnd;

// Send message and wait for newline
void msgUser(const char *msg) {
        std::cout << msg;
        getchar();
}

/*****************************************************************************
*       Description:    This program is the bare minimum to open a port and identify the number of nodes
*               on the port.
*
*
*               Return:         0 if the system was initialized properly.
*                                       -1 if there was a problem accessing the port.
*****************************************************************************/

int main(int argc, char* argv[]){
        size_t portCount = 0;
        std::vector<std::string> comHubPorts;

        msgUser("Hello World Example starting. Press Enter to continue.");

        //Create the SysManager object. This object will coordinate actions among various ports
        // and within nodes. In this example we use this object to setup and open our port.
        SysManager myMgr;                                                       //Create System Manager myMgr

        printf("Hello World, I am SysManager\n");       //Print to console

        //This will try to open the port. If there is an error/exception during the port opening,
        //the code will jump to the catch loop where detailed information regarding the error will be displayed;
        //otherwise the catch loop is skipped over
        try
        {

                SysManager::FindComHubPorts(comHubPorts);
                printf("Found %d SC Hubs\n", comHubPorts.size());

                for (portCount = 0; portCount < comHubPorts.size() && portCount < NET_CONTROLLER_MAX; portCount++) {

                        myMgr.ComHubPort(portCount, comHubPorts[portCount].c_str());    //define the first SC Hub port (port 0) to be associated
                                                                                        // with COM portnum (as seen in device manager)
                }

                if (portCount > 0) {
                        //printf("\n I will now open port \t%i \n \n", portnum);
                        myMgr.PortsOpen(portCount);                             //Open the port

                        for (size_t i = 0; i < portCount; i++) {
                                IPort &myPort = myMgr.Ports(i);

                                printf(" Port[%d]: state=%d, nodes=%d\n",
                                        myPort.NetNumber(), myPort.OpenState(), myPort.NodeCount());
                        }
                        // Close down the ports
                        myMgr.PortsClose();
                }
                else {
                        printf("Unable to locate SC hub port\n");

                        msgUser("Press any key to continue."); //pause so the user can see the error message; waits for user to press a key

                        return -1;  //This terminates the main program
                }
        }
        catch(mnErr& theErr)    //This catch statement will intercept any error from the Class library
        {
                printf("Port Failed to open, Check to ensure correct Port number and that ClearView is not using the Port\n");
                //This statement will print the address of the error, the error code (defined by the mnErr class),
                //as well as the corresponding error message.
                printf("Caught error: addr=%d, err=0x%08x\nmsg=%s\n", theErr.TheAddr, theErr.ErrorCode, theErr.ErrorMsg);

                msgUser("Press any key to continue."); //pause so the user can see the error message; waits for user to press a key

                return -1;  //This terminates the main program
        }

        msgUser("Press any key to continue."); //pause so the user can see the error message; waits for user to press a key

        return 0;                       //End program
}
//

```

As of now, there has been an update by the Co. that produced the motors,
the SDK, and the templates.

Also, most of what has happened in the past with the Cross-Compilation is
now an error in context. So, an easier approach would be to understand
your system, what C++ library is on your BBB or BBBW, and then use a 
Makefile with ` make ` to install the required lib. onto the BBB or other
Single Board Computer with the am335x...

So, sign in to the Teknic website at https://teknic.com/ and then scroll the
above options in the headers to Downloads and then to Clearpath and then to 
Software. The software, their SDK in question, can be found in this option.

It is in the form of .tar.gz.

Simply tar the file by calling ` tar -xvf <TheFile.tar.gz> ` to decompress it.

Then, going into the dir. to make the SDK is next. 

...

# 2. Getting the correct hardware to run the servos...

So, as most of everyone knows already, running heavy loads on fantastic motors
does not come at a cheap price. So, if you are looking to add a high-end 
motor to your BBB with a SDKs involved, I recommend these products.

For back up of power failure on specific hardware during running routes and edges,
one might also get a Power Hub from their company. They have drives, motors,
cables, and other hardware to get you up and running with ease.

Look into their website if this is what should entail in your life.

# 3. Making the USB Driver available on the BBB for working with their Hub...

The USB Driver is for Windows OS support for altering, homing, and doing other
tasks on the Motor in question for Teknic.

There is also another type of hardware piece to get if working with their SDK and
motors, i.e. the Software Controlled ClearPath Servos. They are fully integrated.

The SC Hub is what I am talking about currently. You can run four motors off one hub.
You can also, if needed, attach the power hub with ease to the SC Hub in case
one is worried about power failure and/or issues with too much current.

** I will be making a short demo and I encourage you to provide your build as well **

Seth

P.S. If by chance you are working with these SC-Servos from Teknic and have used the SDK
from them, please add on and stay collective. 

` Here is a video of the BBB with such a servo! `

https://youtu.be/R7bgAo0EINI 

and...

This is as far as I have gotten w/ the BBB and the teknic.com hardware/software...

I know ` boring ` but it is not over! https://youtube.com/shorts/KTfUQBa_BQI?feature=share
