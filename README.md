DOS Modificacion Estupida Para que sera
external-dns
==========
Service updating external DNS with records generated by Rancher. Initial version comes with Route53 support; pluggable provider model makes it easy to implement other providers later.

Design
==========
* external-dns gets deployed as a Rancher service containerized app. It enables all other services belonging to the same environment, to be registered to exteral DNS.

* external-dns service would be periodically fetching info from rancher-metadata server, compare it with the data returned by DNS provider, and propagate the changes to DNS provider.

* Every service will get a domain name in a following format:

```
<service_name>.<stack_name>.<environment_name>.<root_domain> {record set}
```
"root_domain" is a user set env var on external-dns service; record set - host ip addresses where service is deployed.

Example: service "foo" in stack "bar" belongs to environment "baz" has containers deployed on host1 and host2. Root_domain is set to "qux.com":

```
foo.bar.baz.qux.com [host1.ip, host2.ip]
```

Contact
========
For bugs, questions, comments, corrections, suggestions, etc., open an issue in
 [rancher/rancher](//github.com/rancher/rancher/issues).

Or just [click here](//github.com/rancher/rancher/issues/new?title=%5Brancher-dns%5D%20) to create a new issue.

License
=======
Copyright (c) 2015 [Rancher Labs, Inc.](http://rancher.com)

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
