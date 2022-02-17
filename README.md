Harbor playbook
=========

А set of ansible roles for installing docker, docker compound, harbor

Roles 
--------------
1) Preinstall (update&install  repo|package, add pgp verification key, create user&group, some PCI)
2) Docker (install docker.ce(!set_version!), docker-compose(!set_version!), enable --now service)
3) Install Harbor ()


Requirements
------------


Role Variables
--------------


Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
