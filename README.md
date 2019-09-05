# AWS Puppet Commands
```
yum install https://yum.puppet.com/puppet6-release-el-7.noarch.rpm
yum -y install puppet-agent puppetserver git
/opt/puppetlabs/puppet/bin/gem install r10k
mkdir /etc/puppetlabs/r10k
```

contents of /etc/puppetlabs/r10k/r10k.yaml:

```
# The location to use for storing cached Git repos
:cachedir: '/var/cache/r10k'

# A list of git repositories to create
:sources:
  # This will clone the git repository and instantiate an environment per
  # branch in /etc/puppetlabs/code/environments
  :my-org:
    remote: 'https://github.com/dongleuk/puppettest.git'
    basedir: '/etc/puppetlabs/code/environments'
```

```
/opt/puppetlabs/puppet/bin/r10k deploy environment -p
systemctl start puppetserver
```

Append to: /etc/puppetlabs/puppet/puppet.conf
```
[main]
server = puppetmaster
```

## ToDo:

 * Yum certs (done?)
 * Rename master branch?
 * Incorporate into CloudFormation


## Links:
 * https://github.com/puppetlabs/r10k/blob/master/doc/dynamic-environments/quickstart.mkd
