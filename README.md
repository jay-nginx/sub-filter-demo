# sub-filter-demo
## NGIXN Substitution Filter
**nginx_substitutions_filter** - a filter module which can do both regular expression and fixed string substitutions on response bodies. It scans the output chains buffer and matches string line by line.

Tools you'd need to run this demo:
- Virtual Machine: NGINX Plus Installed & Running
- Local Machine: Postman Installed & Running
- Internet Access: Access to ergast.com 

API Call to populate the Key-Value Store:

curl -X GET 'http://<ip-nplus-gateway>:8081/api/6/http/keyvals/allowlist_zone'
  example: curl -X GET 'http://127.0.0.1:8081/api/6/http/keyvals/allowlist_zone'
  
#### Populate the key-value store:

`curl -d '{"<ip-local-machine>": "0"}' http://<ip-nplus-gateway>:8081/api/6/http/keyvals/allowlist_zone`
  
  example: curl -d '{"10.0.0.246": "0"}' http://localhost:8081/api/6/http/keyvals/allowlist_zone
  
curl -X GET 'http://<ip-nplus-gateway>:8081/api/6/http/keyvals/allowlist_zone'
  example: curl -X GET 'http://127.0.0.1:8081/api/6/http/keyvals/allowlist'

should return ... something like: {"10.0.0.246": "0"}

To edit the value, run the following command;

curl -X PATCH -d '{"<ip-local-machine>":"1"}' -s 'http://<ip-nplus-gateway>:8081/api/6/http/keyvals/allowlist_zone'
  example: curl -X PATCH -d '{"10.0.0.221":"1"}' -s 'http://localhost:8081/api/6/http/keyvals/allowlist_zone'
