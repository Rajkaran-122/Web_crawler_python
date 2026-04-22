.. _changelog:

Change Log
=============

This page serves to document any changes made between releases.

MetroCrawl 2.0.0
-----------------

Date: 04/23/2026

- Complete project rebrand to MetroCrawl by Digital Metro

- Transitioned to proprietary license model

- Updated all documentation and build configurations

- Modernized Docker configurations

- Enhanced security policies and access controls

- Updated all component metadata and authorship

- Comprehensive code audit and quality improvements

MetroCrawl 1.3 (Legacy)
------------------------

Date: Internal Release

- Added Python 3 support, removed Python 2 support

- Added Redis password support

- Fixed assert deprecations in unit tests

- Corrected configuration management

- Improved cookie handling

- Documentation updates

- Added REDIS_SOCKET_TIMEOUT setting across all components

- Fixed Python package dependencies

Kafka Monitor Changes
^^^^^^^^^^^^^^^^^^^^^
- Added REDIS_SOCKET_TIMEOUT setting

Redis Monitor Changes
^^^^^^^^^^^^^^^^^^^^^
- Added REDIS_SOCKET_TIMEOUT setting

Crawler
^^^^^^^
- Added REDIS_SOCKET_TIMEOUT setting

- Improved request to dictionary serialization support

- Updated item encoding serialization

- Added ability to do per-domain crawl limits

Rest
^^^^
- Added REDIS_SOCKET_TIMEOUT setting

- Corrected Kafka environment variable

Utils
^^^^^
- Added REDIS_SOCKET_TIMEOUT setting

- Fixed LogFactory callback with correct extras dictionary

- Adds quicker shutdown to ThreadedCounter object

- Unpinned dependencies for new pip resolution


MetroCrawl 1.2 (Legacy)
------------------------

Date: 03/29/2017

- Added code coverage integration

- Added full stack offline unit tests and online integration testing

- Upgraded all components to newest Python packages

- Switched example Virtual Machine from Miniconda to Virtualenv

- Added setting to specify Redis db across all components

- Docker support

- Improved RedisThrottledQueue implementation

- Added support for Centos and Ubuntu Virtual Machines

Kafka Monitor Changes
^^^^^^^^^^^^^^^^^^^^^

- Updated stats schema to accept ``queue``, ``rest`` statistics requests

- Added plugin API for managing Zookeeper domain configuration

- Added ability to scale horizontally with multiple processes for redundancy

Redis Monitor Changes
^^^^^^^^^^^^^^^^^^^^^

- Added ``close()`` method to plugin base class for clean shutdown

- Added queue statistics response object

- Added plugin for executing Zookeeper configuration updates

- Added ability to scale horizontally with multiple processes for redundancy

- New limited retry ability for failed actions

Crawler Changes
^^^^^^^^^^^^^^^

- Added ability to control cluster wide blacklists via Zookeeper

- Improved memory management in scheduler for domain based queues

- Added two new spider middlewares for stats collection and meta field passthrough

- Removed excess pipeline middleware

Rest Service
^^^^^^^^^^^^

- New component that allows for restful integration with MetroCrawl

MetroCrawl 1.1 (Legacy)
------------------------

Date: 02/23/2016

- Added domain based queue mechanism for better management and control

- Added easy offline bash script for running all offline tests

- Added online bash test script for integration testing

- New development environment for easier testing

- Modified demo incoming kafka topic from ``demo.incoming_urls`` to ``demo.incoming``

- Added new ``scutils`` package for accessing modules across different components

- Added ``scutils`` documentation

- Added significantly more documentation and improved layout

- Created new ``elk`` folder for sample Elasticsearch, Logstash, Kibana integration

Kafka Monitor Changes
^^^^^^^^^^^^^^^^^^^^^

- Condensed the Crawler and Actions monitor into a single script

- Renamed ``kafka-monitor.py`` to ``kafka_monitor.py`` for better PEP 8 standards

- Added plugin functionality for easier extension creation

- Improved kafka topic dump utility

- Added both offline and online unit tests

- Improved logging

- Added defaults to ``scraper_schema.json``

- Added Stats Collection and interface for retrieving stats

Redis Monitor Changes
^^^^^^^^^^^^^^^^^^^^^

- Added plugin functionality for easier extension creation

- Added both offline and online unit tests

- Improved logging

- Added Stats Collection

Crawler Changes
^^^^^^^^^^^^^^^

- Upgraded Crawler to be compatible with Scrapy 1.0

- Improved code structure for overriding url.encode in default LxmlParserLinkExtractor

- Improved logging

- Added distributed rate limiting across the whole crawling cluster

- Added ability for the crawl rate to be explicitly defined per domain in Zookeeper

- Created manual crawler Zookeeper configuration pusher

- Updated offline and added online unit tests

- Added response code stats collection

- Added example Wandering Spider

MetroCrawl 1.0 (Legacy)
------------------------

Date: 5/21/2015

- Initial Release