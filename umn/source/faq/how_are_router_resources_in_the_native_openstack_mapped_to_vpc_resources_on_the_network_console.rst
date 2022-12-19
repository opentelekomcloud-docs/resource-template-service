:original_name: rts_faq_0002.html

.. _rts_faq_0002:

How Are Router Resources in the Native OpenStack Mapped to VPC Resources on the Network Console?
================================================================================================

Symptom
-------

The router ID cannot be found on the network console when you create a VPC stack using a template.

Solution
--------

RTS uses the localized OpenStack network model, including routers, networks, and subnets. The router, router ID, network, and network ID are respectively mapped to the VPC, VPC ID, subnet, and network ID of the VPC service on the network console.
