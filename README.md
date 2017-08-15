# Gatling-Testing---HBase

## Execution

From your project home directory run:

`mvn test`

## Config File

We can input a **JSON file** which will contain the list of URLs gatling's simulation will execute.
Each JSON object can take the following parameters:
- *url*
- *method:* get
- *parameters:* a list of key-value formatted query parameters for the URL
- *feeder:* path to a JSON file which will contains data to generate more URLs

A sample config file is as below:

```JSON
{
"requests":[
{"url":"url1", 
"method":"get",
"parameters":{"param1":"value1", "param2":"value2"}
},
{"url":"url2", 
"method":"get", 
"feed":"path to a json file"
}
]
}
```
## Feeder File

Input to a feeder file can be specified to each URL in the config file. A feeder file is a JSON file which contains query parameters to generate more URLs.

See [Feeders](http://gatling.io/docs/current/session/feeder/#feeder)

The format of a feeder is as below:
```JSON
[
  {
    "timestamp":1500598138304,
    "value":"email"
  },
  {
    "timestamp":1500598138304,
      "value":"web"
  }
]
```
## Environment

To specify the file path to the config file or to specify run duration and other parameters modify /src/test/scala/main/Utils/**Environment.scala** file

To specify various other injection load parameters in Simulation, see [Simulation setup](http://gatling.io/docs/current/general/simulation_setup/)

To specify any header information required for the API service, edit  /src/test/scala/main/Utils/**Headers.scala** file
