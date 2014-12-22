## pmoust/puppet ##

`puppet` docker image based on Ubuntu Trusty bundled with `librarian-puppet`.

1. Use this image as base for self-provisioned containers using Puppet and librarian-puppet, i.e:

```
FROM pmoust/puppet
RUN git clone git@github.com/organization/code-base.git /tmp/example
WORKDIR /tmp/example
RUN librarian-puppet install
RUN puppet apply
```

2. Use it with a Puppet ENC

With a puppet.conf that points to the puppet master

```
FROM pmoust/puppet
ADD puppet.conf /etc/puppet.conf
RUN hostname web01.example.com
RUN puppet agent -t
```
