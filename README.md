# veamer
Auto instrumentation of search and mange microservices.

language : python3

framework : flask

install python3 latest version.

creating virtual environment will help to keep dependencies separate.


for creating virtual env :

$ python3 -m venv /path/to/new/virtual/environment


to activate venv

$ . /path/to/new/virtual/environment/bin/activate




$ pip3 install flask

$ pip3 install opentelemetry-sdk

$ pip3 install opentelemetry-instrumentation

$ pip3 install opentelemetry-instrumentation-flask

$ pip3 install requests

$ pip3 install opentelemetry-sqlite3






install docker 

Running docker image for jaeger :

open terminal and run 


$ docker run --name jaeger -d -p 6831:6831/udp -p 16686:16686 jaegertracing/all-in-one:latest



now open two seperate terminal tabs/windows and activate virtual environment.

on each terminal run tracer.py from both veamer_search and veamer_manage directories.


teerminal 1:

$ cd veamer_manage

$ export OTEL_PYTHON_TRACER_PROVIDER=sdk_tracer_provider

$ opentelemetry-instrument python3 tracer.py


terminal 2 :

$ cd veamer_search

$ export OTEL_PYTHON_TRACER_PROVIDER=sdk_tracer_provider

$ opentelemetry-instrument python3 tracer.py


make http requests using curl or postman or any app

to see jaeger :

open any browser and go to http://localhost:16686/search

now you will see traces.




note : if any library is missing python will tell you that rightaway. please install it.
