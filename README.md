# kracken-openssl
-------------------------------------------------------------------------------------------------------------------------------

### To Verify Certificates Through Certificate Authority

```
master $ openssl verify -CAfile /etc/kubernetes/pki/ca.crt /etc/kubernetes/pki/apiserver.crt

  apiserver.crt: OK
```
> Verification failed
```
master $ openssl verify -CAfile /etc/kubernetes/pki/ca.crt /etc/kubernetes/pki/

  O = system:masters, CN = kube-apiserver-etcd-client
  error 20 at 0 depth lookup: unable to get local issuer certificate
  error apiserver-etcd-client.crt: verification failed
```

### To check the SSL Certificate of HTTPS Service 

- This will print the ssl certificate used by service.
- format :- `openssl s_client -connect ip-addr:port`
```
master $ openssl s_client -connect localhost:2379

  CONNECTED(00000005)
  depth=0 CN = controlplane
  verify error:num=20:unable to get local issuer certificate
  verify return:1
  depth=0 CN = controlplane
  verify error:num=21:unable to verify the first certificate
  verify return:1
  {....}
```

### Troubleshooting Tools || Networking Troubleshooter Tools

- dig
- tcpdump
- netcat
- ss
- ifconfig/route -> ip addr show, ip route show
- netstat -> ss

### Docker Tools

- `docker inspect -f/--format '{{.State.Pid}}' container_id`
- `nsenter -t container_pid -n command`



