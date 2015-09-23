ansible-memcached-docker role
=============================

Installs & runs memcached in a docker container.

The point is to be able to deploy multiple memcached instances on a host
without having to fiddle with init scripts.

This role is datadog enabled, and will add configuration so all memcached
containers are properly monitored. Tags will be set according to
`memcached_docker_port` and `memcached_docker_name`.

Usage
-----

    - role: ansible-memcached-docker
      memcached_docker_name: memcached-a
      memcached_docker_max_connections: "1234"
      memcached_docker_memory: "128"
      memcached_docker_listen: 0.0.0.0
      memcached_docker_port: "11211"
    - role: ansible-memcached-docker
      memcached_docker_name: memcached-b
      memcached_docker_max_connections: "4321"
      memcached_docker_memory: "256"
      memcached_docker_listen: 0.0.0.0
      memcached_docker_port: "11212"

Bugs
----

Docker module restarts your container everytime it is run and thus, your cache
gets cleaned. Who said cache invalidation was hard :p

Author
------

Michel Blanc <mb@mbnet.fr>
