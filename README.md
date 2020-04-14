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

```hammer location create --organization MyOrg --name MyLocation```


