

## Services -> BIND -> Settings -> Advanced Features -> Global settings
Use the folloinwg to allow additional keys for client DDNS update, you can generate the key on pfS using tsig-keygen
```
key "<keyname>" {
        algorithm hmac-sha256;
        secret "<key>";
};
```
## Services -> BIND -> Zones
Name Server
```
127.0.0.1 
```

Enable update-policy
Add the following to update-policy
```
grant rndc-key zonesub any;
grant <additional_keyname> name <FQDN> any;
```

# include this for DHCP hostname registration
## Services -> DHCP/v6
ipv4 or ipv6
```
DDNS Domain Key name: rndc-key
Key algorithm: <typically hmac-sha256>
Key secret: <secret>
DDNS Client Updates: Ignore
```


