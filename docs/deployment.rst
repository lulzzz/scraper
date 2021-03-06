==========
Deployment
==========

Server Setup
------------

General
^^^^^^^
Deployment of all server parts is done on an ``Ubuntu 14.04`` ``AWS/EC2`` instance, Python ``fabric``
is used for deployment automation, fabric files can be found in ``openfarmsubsidies-scraper`` repository.

The following fabric tasks are just for orientation what need to be installed/done
and are not intended to pass through, depending on your system pre-requisites::

  fab prepare_system
  fab install_deps

Script templates for setting up ``Gunicorn``, ``Nginx`` and ``Supervisor`` can be
found in the ``conf`` folder.

SSL
^^^
``SSL`` cert is created with **Let's Encrypt** with the following command::

  sudo /home/ubuntu/.local/share/letsencrypt/bin/letsencrypt certonly -d openfarmsubsidies.org -d www.openfarmsubsidies.org -d scraper.openfarmsubsidies.org -d api.openfarmsubsidies.org

Elasticsearch
^^^^^^^^^^^^^
``Elasticsearch`` is installed as deb (Debian) package following 
`this instructions <https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-elasticsearch-on-ubuntu-14-04>`_.

Installation can be found at ``/usr/share/elasticsearch/``, start/stop is done via
``init.d`` script ``sudo /etc/init.d/elasticsearch start``.

Index backup can be done with::

  sudo cp -Rp /var/lib/elasticsearch /var/lib/elasticsearch-backup-2017-06-28

