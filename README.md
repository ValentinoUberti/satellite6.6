# Satellite 6.6 notes

## Verify satellite services status and health
- satellite-maintain service list
- satellite-maintain health check
- systemctl status chronyd

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

```hammer -u <USER> -p <PASSWORD> subscription upload --file manifest.zip --organization MyOrg```

- List organization

```hammer list organization```

- List location

```hammer list location```

- List location belonging to an organization

```hammer list location --organization MyOrg```






