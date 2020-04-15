# Satellite 6.6 notes

## Verify satellite services status and health

``` 
satellite-maintain service list
satellite-maintain health check
systemctl status chronyd
```

Verify firewall ports

Verify correct reverse DNS resolution of the satellite server

## Hammer
- Create an organization

```hammer organization create --name MyOrg --label MyLabel --description MyDesc```

- Create a location and associate it to an organization

```
hammer location create --name MyLocation
hammer location add-organization --organization MyOrg --name MyLocation  
```

- Associate a CDN to an organization

```hammer organization update --name MyOrg --redhat-repository-url REDHAT_REPOSITORY_URL```

- Import a Manifest for multiple organization

```hammer subscription upload --file manifest.zip --organization "Default_Organization" ```

- Import a Manifest for an organization

```hammer subscription upload --file manifest.zip --organization MyOrg```

- List organization

```hammer list organization```

- List location

```hammer list location```

- List location belonging to an organization

```hammer list location --organization MyOrg```

- List repository

```hammer --output json repository list```

- Sync repository

```hammer repository synchronize --id <id>```

- Managing life cycle environments 

```hammer lifecycle-environment create --name <> --organization <> --description <> --prior <Library>```

- List lifecycle environment
  
```hammer lifecycle-environment list --organization <organization-name>```

- List lifecycle environment paths

```hammer lifecycle-environment paths --organization <organization-name>```

- Create an activation key

```hammer activation-key create --name "<activation_key_name" --unlimited-hosts --description "<description" --lifecycle-environment <environment-name> --content-view <content_view_name> --organization "<organization_name>"```

- Add a subscription to an activation key

```hammer subscription list --organization "<organization_name>"```

take the UUID

```hammer activation-key add-subscription --name <activation_key_name> --subscription-id <UUID> --organization <organization_name>```




## Sync Red Hat Content

- Content -> Red Hat Repositories
  ```
  Add wanted repos
  ```
  
- Content -> Products
  ```Select the rpms and click sync now```
  
  #This task requires a lot of time...
  
  
## Create a sync plan

 - Content -> Sync Plans -> Create Sync Plans
 
 - Monitor -> Recurring Logics for checking also sync plans
 
## Create a SDLC (Software deployment life cycle)

 - Content -> Lifecycle Envoronments -> Create Environment path
 
The first environment is always called 'Library'.
Library environment receive updates constantly.


## Content views (Create -> Pubblish -> Promote)

- Content -> Content Views -> Create New View

- Yum content -> Repositories -> Add

- Content -> Content Views -> Select Content View -> Publish New Version

- Content -> Content Views -> Select Content View -> Version -> Actions -> Promote

## Registering an host

Managing Hosts > Chapter 3. Registering Hosts

- Ensure chronyd is running on the host we want to register
- Update yum and subscription-manager

```yum update -y subscription-manager yum```

- Install the customer certificate from Satellite server

```yum localinstall http://<satellite_server>/pub/katello-ca-consumer-latest.noarch.rpm```

- Clean old registration data

```subscription-manager clean```

- Register the host to an organization

```subscription-manager register --org <organization_label> --environment <Life-cycle-environment>/<Promoted_content_view>```

- Install the katello-agent for package and errata management

```yum install katello-agent```

## Configuring registered host from Satellite server

- Host properties

```Hosts -> Content Hosts -> Details```

- Host subscriptions

```Hosts -> Content Hosts -> Subscriptions -> Add -> Add Selected```

- Product Content Access

```Hosts -> Content Hosts -> Repository Sets > Select Action ```


## Host Collections

Logical group of hosts

-> Create a host collection

```Hosts -> host collections```

-> Add an host to an host collection

```Hosts -> host collections -> Details```

## Automating content host registration (Activation key)

Content management guide -> Managing activation keys (10)

- Create an actiovation key

```Content -> Activation Keys```

- Add subscription to activation key

```Content -> Activation Keys -> Subscriptions -> Add```

- Add host collection to activation keys

```Content -> Activation Keys -> Host Collections -> Add```


## Preparing an host for registration to Satellite

- Ensure chronyd is running on the host we want to register
- Update yum and subscription-manager

```yum update -y subscription-manager yum```

- Install the customer certificate from Satellite server

```yum localinstall http://<satellite_server>/pub/katello-ca-consumer-latest.noarch.rpm```

- Clean old registration data

```subscription-manager clean```

- Register the host to an organization

```subscription-manager register --org <organization_label> --activationkey <activation_key_name>```

- Install the katello-agent for package and errata management

```yum install katello-agent```




