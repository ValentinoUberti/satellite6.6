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








