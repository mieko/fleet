# Configuring an stunnel service
================================

We run stunnel as an instance-per-service, instead of a forking daemon.  So
the config file has to be self-contained.

For an example of a proper configuration, check out redis-server.

In the end you'll want a file in /etc/stunnel/your-service.conf, and to enable
it with:

 $ systemctl enable stunnel@your-service.service
