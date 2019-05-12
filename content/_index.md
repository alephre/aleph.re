---
title: "Powerful sample dissection pipeline"
---
# What is aleph
Aleph is a fully asynchronous opensource sample dissection pipeline written in Python 3, built on top of [Celery](http://www.celeryproject.org/) - used by companies such as Instagram - which makes it scalable and reliable. With abstraction and microservices in the heart, the platform is easily extensible through its components system. 

Aleph is made with threat intelligence researchers and malware reverse engineers in mind!

---

# What can it do?
Aleph can extract information from virtually any file type (given a processor for that file type exists) into beautiful JSON data that can be queried via [Lucene query syntax](https://www.elastic.co/guide/en/kibana/current/lucene-query.html) when used with the default [Elasticsearch](https://www.elastic.co/products/elasticsearch) backend.

---

# How does it works?
Aleph comes with several built-in collectors (local folder, Amazon S3 buckets, IMAP & POP email accounts etc) that dispatches the samples to the workers which will apply the processors for that specific file type which will carve the information out. 

All extracted data is sent to the backend datastore. Later, analyzer components can run intelligence analysis on the combined output of all processors.

---

# How well does it works?
The workers in the system execute asynchronous tasks, enabling multiple parallel Aleph instances working together and idependently at the same time. All tasks are divided into specific message queues, meaning you can specialize your workers and put your computational power where is required.

---

# How aleph scales and handle failures?
All parts of a standard Aleph configuration (Aleph itself, [Elasticsearch](https://www.elastic.co/products/elasticsearch) and [RabbitMQ](https://www.rabbitmq.com/)) are scalable. You can grow your Aleph deployment wherever your bottleneck is - workers, message queues, sample storage and information storage - giving you a much more efficient use of your infrastructure. 

With all moving parts being clusterable, any part of your stack can fail without you losing **__any__** data.
