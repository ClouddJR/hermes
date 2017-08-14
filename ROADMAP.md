# Roadmap

This document contains general overview of things that we are either working in current quarter or have plans for.
Please create PRs with changes if you want to add or reprioritize goals.

## Currently working on

* Easy migration from JSON to Avro: removing all knobs from Hermes and placing them in external service, leaving Hermes with 
  only basic `JSON -> Avro` switch. Additional service might be OpenSourced if needed
* Securing Hermes Frontend and Consumers: allow to easily plug own implementation of classes to secure Hermes incoming and 
  outgoing traffic
* HTTP/2 in Hermes Frontend and Consumers: currently we allow on turning on HTTP/2 in Frontend, the implementation will be
  revisited and we will also add same capabilities to Consumers 

## Must happen before 1.0.0

* Refactoring `Configs` class: split Frontend/Consumers config and make them easily extendable. Also documentation should be
  autogenerated based on comments in config classes
* Unifying configuration options in Frontend/Consumers/Management: while Frontend and Consumers have pretty standard names,
  Management due to using different stack has totally different option names, which is confusing
* Refactoring Hermes Frontend & Consumers Builder API

## Going to happen someday

* Unify tech stack for Consumers/Management/Frontend: using totally different technologies is confusing and counterproductive
* Changing Dependency Injection in Frontend and Consumers: we have way too much boilerplate code with `hk2`
* Improvements in Management handling of data: each API query ends up in Zookeeper, we can be more efficient
* Switch from Zookeeper events to Kafka for broadcasting changes: we use ZK events as kind of internal message bus, but at
  some point it will stop scaling; we have perfectly suitable message bus available: Kafka