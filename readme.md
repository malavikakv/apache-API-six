curl http://127.0.0.1:9180/apisix/admin/routes/5 -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1' -X PUT -d '
{
    "uri": "/influx",
     "plugins":{
     "openid-connect":{
         "client_id":"iplonclient",
         "client_secret":"3b107286-8cd3-4fb0-bf1a-6b776ce3060c",
         "discovery":"http://127.0.0.1:8080/auth/realms/iplon_realm/.well-known/openid-configuration",
     "introspection_endpoint": "http://localhost:8080/auth/realms/iplon_realm/protocol/openid-connect/token/introspect",
     "bearer_only": true,
     "realm": "iplon_realm",
     "introspection_endpoint_auth_method": "client_secret_basic"
}
},
"upstream": {
     "type": "roundrobin",
     "nodes": {
         "127.0.0.1:6500": 1
     }
}
}'
