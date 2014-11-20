Ansible Role: Supervisor
========================

Installs minimal Supervisor on CentOS 6.5

Requirements
------------

None.

Role Variables
--------------

Default values:

* supervisor_user: root                                       # default user
* supervisor_sock: /var/run/supervisor.sock                   # path to your socket file
* supervisor_conf_file: /etc/supervisord.conf                 # path to your conf file
* supervisor_pidfile: /var/run/supervisord.pid                # pidfile location
* supervisor_programs_dir: /etc/supervisor/conf.d/            # child programs location
* supervisor_childlogdir: /var/log/supervisor/                # where child log files will live
* supervisor_logfile: /var/log/supervisor/supervisor.log      # supervisord log file
* supervisor_logfile_maxbytes: 50MB                           # maximum size of logfile before rotation
* supervisor_logfile_backups: 10                              # number of backed up logfiles
* supervisor_loglevel: debug                                  # info, debug, warn, trace
* supervisor_nodaemon: false                                  # run supervisord as a daemon
* supervisor_minfds: 1024                                     # number of startup file descriptors
* supervisor_minprocs: 200                                    # number of process descriptors

You can override these values on your playbook.

Optional variables
To enable the WEB Interface, you will have to define these variables:

* supervisor_web_host # you can use "{{ inventory_hostname }} here"
* supervisor_web_port
* supervisor_web_user
* supervisor_web_pass

Dependencies
------------

* tcosta84.yum
* tcosta84.python

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: tcosta84.supervisor }

With optional variables:

    - hosts: servers
      vars:
        - supervisor_web_host: "{{ inventory_hostname }}"
        - supervisor_web_port: 9001
        - supervisor_web_user: admin
        - supervisor_web_pass: 12345
      roles:
         - { role: tcosta84.supervisor }

License
-------

BSD

Author Information
------------------

This role was created by [Thiago Costa](http://thiagocostapy.com)
