Chef
----

## Development
#### Logging
`Chef::Log.debug(m)`

#### New cookbook
`knife cookbook create splunk -o ~/Projects/cookbooks/; cd ~/Projects/cookbooks/splunk; berks init; kitchen init;`

#### Sensu check
```
sensu_check 'metrics_event_queue' do
  type 'metric'
  command "#{script_path} --env=#{node['event']['stat_namespace']} --nl-app-id=#{node['event']['deployment']['app_id']} --event-host=#{node['network']['internal_ip']}"
  standalone true
  handlers %w{graphite}
  interval 10
  additional(:output_type => node['sensu_client']['output_type'])
end
```

## SEARCH
`knife search 'roles:event AND chef_environment:production_*'`
`knife search 'role:event'`

## DEPLOY

### Bootstrap
#### Chef 10
`knife10 bootstrap <hostname> -r 'role[role1], role[staging], role[role2], role[ldap_auth_client]' -x root --bootstrap-version=10.26.0 -E <environment>`
#### Chef 11
`knife bootstrap <hostname> --run-list "role[event]" --environment <environment> --bootstrap-template chef-full --ssh-user root --bootstrap-version=11.18.6`

#### Re-chef
`knife ssh 'roles:event AND chef_environment:production_*' 'sudo DEPLOY=1 chef-client' -x <ldap_user> -C 3 -A`


## INFO
#### Last cheffed/deployed
`knife status name:<nodename>`

## MANAGEMENT
`knife ssh 'roles:dynomite AND chef_environment:staging*' 'sudo service dynomite restart' -x yourusername -A`

### Chef-client
#### Install specific version
`curl -sL https://www.opscode.com/chef/install.sh | sudo bash -s -- -v 10.32.2`

## Berkshelf
#### Public source
`source 'https://supermarket.chef.io'`

#### Upload
`berks upload apid`

## KNIFE
#### Role
`knife role from file /path/to/file`
