### Benchmark

* [Phoronix](https://askubuntu.com/questions/198978/is-there-a-benchmark-tool-for-ubuntu): Test Suite: `phoronix-test-suite list-tests` 

### Docker
* Labs: http://104.236.186.62/#/labs/setup-development-environment
  
### Notes on IoT from the labs

As we build our Internet of Things system, we will need to define the objects and events that we want to track on our edge network.

For this edge network, we will define five types that we will track in the database.

**Sensor** - this data describes an edge device that publishes data to the Intel® IoT Gateway. Examples of sensors include the sensors included in your Intel IoT Developer Kit. For a complete list of supported sensors see the libUPM project.  

**Actuator** - this data describes an edge device that performs an action and can be triggered by the Intel® IoT Gateway. For example, an LCD screen can have text sent to it to be displayed, a servo motor can be told to rotate a certain number of degrees, or a buzzer may be told to activate. Any device that performs an action is considered an actuator. Note that actuators usually do not publish sensor data to the network but they may be queried for the current status.

**Data** - the data contained within a single reading from a sensor

**Trigger** - Triggers have a four important aspects: a name, a sensor that it watches, a condition function (a predicate) that returns TRUE or FALSE and a trigger function that performs an action when the predicate function is true. This will be used more in the Automation Lab. It will watch data coming from a temperature sensor. Its predicate function will evaluate if the temperature is greater than 27 degrees, and its action function will send an alert, log a system error and send text to the LCD screen.

**Error** - a text string and a timestamp describing the errors on the edge network.
Our database will store five types: sensors, actuators, data, trigger and error. We've prepared the MongooseJS schemas that you will need to complete this lab. Install the NPM package below and then you will be able to import the schemas.

### Issues and resolution

* Downloaded mongodb & installed npm and node 
  - `curl -sL https://deb.nodesource.com/setup_7.x | sudo -E bash -`
  - `sudo apt install nodejs` ; `sudo apt install npm`
  - In the mongodb/bin folder: `sudo ./mongod --dbpath=/data/db` # ensure the db folder exists
* Create the [server.js](monitord/server.js) file
  - `mkdir ~/monitord && cd ~/monitord`
  - `npm init` -> creates a file `package.json`. Defaults OK, index.js->server.js
  - `npm install --save mqtt lodash mongoose intel-commercial-edge-network-database-models`
  - `npm install` # run again to be sure
  - Create `server.js` -> long file from [db](http://104.236.186.62/#/labs/databases) lab
* Start node server: `node server.js`
  - fails unless certs are added to /etc/mosquitto/certs...
  - Certification [source](https://github.com/owntracks/tools/blob/master/TLS/generate-CA.sh) script
    o rename and move the .key, .crt files per server.js
* That's it!

### Summary

* Lab solution
  - [Solution Directory](lab-solution-monitor-daemon)
  - [My solution directory](monitord)
* Solution git repo
  - [SSG-DRD-IOT/lab-solution-sensor-monitor](https://github.com/SSG-DRD-IOT/lab-solution-sensor-monitor)

### Docker containerized solution

* SSG-DRD-IOT/docker-ciotlabs [github](https://github.com/SSG-DRD-IOT/docker-ciotlabs)
  - Ubuntu docker image for Intel Gateway + Arduino 101 with MRAA

	**How to Run:**
	`docker run -ti --device=/dev/ttyACM0 huzefank/gateway-mraa`

	It will take some time (~3 mins on a core i7 gateway and ~10 mins on an Atom gateway) to install all the dependencies. Once on the prompt test the setup using a led-blink program to blink a LED on Arduino 101 board.

	`cd /root/led-blink node main.jsi`

	**Note:** If the Gateway has WR Linux installed this should just work, if it has Ubuntu installed the Modem manager might be holding up the ttyACM0 port for which it has to be disabled (check running services and stop Modem service using ttyACM0 port)

	If upm libraries are required, they can be installed with command npm install upm -g

	Any additional UPM libraries (for e.g. LCD can be installed separately as required) npm install jsupm_i2clcd -g

