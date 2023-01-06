# iotma
projet iot 
This code is a Node.js server that listens on two HTTP ports (1123 and 1124) for incoming requests. When a request is received, it is processed and a point is created and written to an InfluxDB database. The code has the following functions:

creationPoint(value, mode, threshold, code): creates a point with the given value, mode, threshold, and code.
sendPoint(pt): writes the given point to the InfluxDB database and flushes the write.
requestListener(req, res, type): a helper function for the HTTP request listener functions that receives the request, response, and type (either "temperature" or "humidity"). It processes the incoming data and calls the processInput function with the appropriate type.
tRequestListener(req, res): HTTP request listener function for temperature data. Calls the requestListener function with the "temperature" type.
hRequestListener(req, res): HTTP request listener function for humidity data. Calls the requestListener function with the "humidity" type.
processInput(mode, res, data): processes the incoming data, creates a point using the creationPoint function, and writes the point to the database using the sendPoint function.
fromByte(string): converts a hexadecimal string to an integer.
parseValue(string, indexStart, indexEnd): extracts a substring from the given string and converts it to an integer using the fromByte function.
close(): closes the write API to the InfluxDB database.
The code also sets up two HTTP servers, one for temperature data and one for humidity data, and listens for incoming requests on those servers. Finally, it has event listeners to close the write API when the process exits or when the SIGINT signal is received (e.g. when the user terminates the process with Ctrl + C).
