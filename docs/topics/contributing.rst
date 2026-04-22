Contributing
============

MetroCrawl is a proprietary project developed and maintained by Digital Metro.

.. note::

    This is proprietary software. External contributions are not accepted
    without prior written authorization from Digital Metro.

Internal Development Guidelines
-------------------------------

For authorized developers working on MetroCrawl:

Testing
^^^^^^^

Run the offline test suite to verify your changes:

.. code-block:: bash

    ./run_tests_offline.sh

For integration testing with all external services:

.. code-block:: bash

    ./run_tests_online.sh

Code Standards
^^^^^^^^^^^^^^

- All code must follow PEP 8 standards
- New features must include unit tests
- All tests must pass before merging
- Documentation must be updated for any API changes

Branch Strategy
^^^^^^^^^^^^^^^

* ``master`` -- Latest stable release
* ``dev`` -- Active development branch

Docker Testing
^^^^^^^^^^^^^^

Use the Docker Compose setup for isolated testing:

.. code-block:: bash

    docker-compose up -d --build
    # Run your tests
    docker-compose down

Contact
-------

For development inquiries: rajkaran@digitalmetro.dev

---

Copyright (c) 2024-2026 Digital Metro. All Rights Reserved.
