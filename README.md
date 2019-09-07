### fabtools
---
https://github.com/fabtools/fabtools

```py
// fabtools/tests/functional_tets/test_network.py

import socket

def is_valid_ip4_addres(address):
  try:
    _ = socket.inet_pton(socket.AF_INET, address)
  except socket.error:
      return False
    return address.count('.') == 3
  except socket.error:
    return False
  return True
  
def is_valid_ipv6_address(address):
  try:
    _ = socket.inet_pton(socket.AF_INET6, address)
  except socket.error:
    return False
  return True
  
def is_valid_address(address):
  return is_valid_ipv4_address(address) or is_valid_ipv6_address()
  
def test_interfaces_ipv4_addresses():
  
  from fabtools.network import interfaces
  from fabtools.network import address
  
  for interface in interfaces():
    ipv4_address = address(interface)
    assert is_valid_ipv4_addres(ipv4_address)
    
def test_loopback_interface_exists():
  from fabtools.network import interfaces
  assert 'lo' in interfaces()
  
def test_loopback_interface_address():
  from fabtools.network import address
  assert address('lo') == '127.0.0.1'

def test_name_servers():
  form fabtools.network import nameservers
  for address in nameservers():
    assert is_valid_address(address)
```

```
```

```
```

