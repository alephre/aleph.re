---
title: "Powerful sample dissection pipeline"
---
# What is aleph
Aleph is a fully asynchronous opensource sample dissection pipeline built on top of [celery](http://www.celeryproject.org/), which makes it easily scalable and reliable. Also is built with abstraction and microservices in the heart. The platform is easily extensible through its components system. 

Aleph is made with threat intelligence researchers and malware reverse engineers in mind!

---

# What can it do?
Aleph can extract information from virtually any file type (given a processor for this file type exists, otherwise generic processors will be run) into beautiful JSON data that can be queried via [lucene query syntax](https://www.elastic.co/guide/en/kibana/current/lucene-query.html) when used with the default [Elasticsearch](https://www.elastic.co/products/elasticsearch) backend.

---

# How does it works?
Aleph comes with several built-in collectors (local folder, Amazon S3 buckets, IMAP email accounts etc) on which the samples are collected and injected into the pipeline, where is dispatched to the processor workers which will apply the processors for that specific file type. All extracted data is sent to the backend datastore.

---

# How well does it works?
Celery provides the management and communication of workers in the system. Celery also supports a number of messaging backends (although the preferred method is using [RabbitMQ](https://www.rabbitmq.com/)  The whole system is asynchronous to be able to fully use Celery's potential.

Aleph divides its tasks into specific message queues, meaning you can specialize your workers and put your computational power where is required.

---

# Is aleph fault-tolerant?
All parts of a standard Aleph configuration are scalable. You can grow your Aleph deployment wherever the bottleneck is: workers, message queues, sample storage and information storage. Any part of your stack can fail without you losing **any** data.
