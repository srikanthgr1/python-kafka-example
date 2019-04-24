# Apache Kafka example for Python


## Getting started

Setup your free Apache Kafka instance here: https://www.cloudkarafka.com

Configuration 
For Unix / Linux Machines 

* `export CLOUDKARAFKA_BROKERS="host1:9094,host2:9094,host3:9094"`
  Hostnames can be found in the Details view in for your CloudKarafka instance.
* `export CLOUDKARAFKA_USERNAME="username"`
  Username can be found in the Details view in for your CloudKarafka instance.
* `export CLOUDKARAFKA_PASSWORD="password"`
  Password can be found in the Details view in for your CloudKarafka instance.
* `export CLOUDKARAFKA_TOPIC="username-topic"`
  Topic should be the same as your username followed by a dash before the topic.

For Windows 8+ machines -- Run Command Mode as Administrator and then edit these 
My personal Test instance settings 

* `setx CLOUDKARAFKA_BROKERS "velomobile-01.srvs.cloudkafka.com:9094,velomobile-02.srvs.cloudkafka.com:9094,velomobile-03.srvs.cloudkafka.com:9094"`

Hostnames can be found in the Details view in for your CloudKarafka instance.

* `setx CLOUDKARAFKA_USERNAME "g6lq3p1b" `

Username can be found in the Details view in for your CloudKarafka instance.

* `setx CLOUDKARAFKA_PASSWORD "XXuD-bmbHa0RmH27ypk1wfkq6pKGRCGr" `

Password can be found in the Details view in for your CloudKarafka instance.

setx CLOUDKARAFKA_TOPIC "g6lq3p1b-upload" 

Topic should be the same as your username followed by a dash before the topic.

These export commands must be run in both of the terminal windows below.

```
git clone https://github.com/CloudKarafka/python-kafka-example.git
cd python-kafka-example`
pip install confluent_kafka
python consumer.py
```

Open another terminal window and `cd` into same directory and run `python producer.py`.
Send your messages by pressing your system's EOF key sequence. (ctrl-d in bash)

## Adding a Root CA

In some cases the CloudKarafka Root CA may need to be manually added to the example, particularly if you are seeing the error:
```
Failed to verify broker certificate: unable to get local issuer certificate 
```
returned when you run the example. If this is the case you will need to download the [CloudKarakfa Root CA](https://www.cloudkarafka.com/certs/cloudkarafka.ca) (See also the [FAQ](https://www.cloudkarafka.com/docs/faq.html)) and place it in the python-kafka-example directory, then add the following line into the `conf {...}` section:
```
'ssl.ca.location': 'cloudkarafka.ca'
```
This should resolve the error and allow for successful connection to the server.
