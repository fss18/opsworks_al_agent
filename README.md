# Opsworks Chef 11 with AL Agent

Sample implementation of AL Agent cookbook into Opsworks using Chef v11.

## Getting Started

Clone the repository, make adjustment as needed and store it on your own private repo if necessary. Do not reference your custom cookbook in OpsWork directly to this repo, this example may changes or removed in the future. Original AL Agent cookbook can be found at https://github.com/alertlogic/al_agents

### Notes
Running AL Agent cookbook in Opsworks with Chef v11 will require specific version for the cookbook dependency:
1. SELinux Policy v1.1.1
2. Rsyslog v2.2.0
3. Line v0.6.3

Make sure you have the right version of each cookbook dependency in your repository.

In specific for SELinux Policy v1.1.1 (https://github.com/sous-chefs/selinux_policy/blob/v1.1.1/metadata.rb)
Modify the line:
```
issues_url 'https://github.com/BackSlasher/chef-selinuxpolicy/issues'
source_url 'https://github.com/BackSlasher/chef-selinuxpolicy'
```
into
```
issues_url 'https://github.com/BackSlasher/chef-selinuxpolicy/issues' if respond_to?(:issues_url)
source_url 'https://github.com/BackSlasher/chef-selinuxpolicy' if respond_to?(:source_url)
```

And comment the line:
```
depends 'yum', '~> 4.0'
```
Into
```
#depends 'yum', '~> 4.0'
```

