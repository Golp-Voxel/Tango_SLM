# SLM - Tango Device Server 
This repository contains the driver to control a SLM with the Tango Control.





## Comands that are aviable 
After installing the Tango Device server, you can display a LaguerreGauss or a CylindricalLens or even a CustomImage by calling the corresponding function:

```python 
LaguerreGauss()
```

```python 
CylindricalLens()
```

```python 
CustomImage(User_Image)
```
In the case of the CustomImage it is recuired to send a 2D array of 1280 by 1024 (`User_Image`).

To stop the display of the SLM you need to call the following function:

```
kill_theard()
```

## Exemple of Tango Client code to send a LaguerreGauss to be displayed
```python
import tango
import time
SLM = tango.DeviceProxy(<SLM_Tango_location_on_the_database>)
print(SLM.state())
# Change this time out if need
SLM.set_timeout_millis(9000) 

# This function returns a list with all the command aviable on the device server
SLM.get_command_list()
#['CylindricalLens', 'CustomImage', 'LaguerreGauss', 'kill_theard']

SLM.LaguerreGauss()
time.sleep(10)
SLM.kill_theard()
```