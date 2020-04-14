# Satellite 6.6 notes

## Verify satellite services status and health
- satellite-maintain service list
- satellite-maintain health check
- systemctl status chronyd

Verify firewall ports
Verify correct reverse DNS resolution of the satellite server

## hammer
- Create an organization
```hammer organization create --name --label --description
