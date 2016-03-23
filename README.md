# tsung-elasticsearch-test
A sample Tsung config file for load testing an Elasticsearch cluster with a set of REST APIS

# Requirements
* Erlang
* Tsung

# Usage
Open a terminal and run 

```bash
> tsung -f es1.xml start
```

# Explanation
The es1.xml file is a sample Tsung test script which generates "users" arriving at varying speeds
in three phases and then executes a POST requests with a JSON payload that contains a few 
properties found in an apache log file. Since we don't actually use an apache log file here, we 
just generate some variables (e.g. request, bytes, response, and @timestamp) and inject it into 
a JSON template (row.json). We generate the values using some built in functions in Tsung as well
as making use of an anonymous Erlang function. There may be better ways to do this such that we do
not need to compute this on the fly as the load test is being executed. An example of this would be
to generate a list of files in a directory which are named a certain way and then POST those files
in the script itself.
