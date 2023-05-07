# Hacking
Hacking
DnsCacheManipulator.setDnsCache("hello.com", "192.168.1.1");
// support IPv6
DnsCacheManipulator.setDnsCache("world.com", "1234:5678:0:0:0:0:0:200e");

// The above settings take effect globally, 
// and then all the domain name resolution logic in Java will be the IP set above.
// Let's use a simple method to get the IP of the domain name to demonstrate:

String ip = InetAddress.getByName("hello.com").getHostAddress();
// ip = "192.168.1.1"
String ipv6 = InetAddress.getByName("world.com").getHostAddress();
// ipv6 = "1234:5678:0:0:0:0:0:200e"


// set multiple IPs
DnsCacheManipulator.setDnsCache("hello-world.com", "192.168.2.1", "192.168.2.2");

String ipHw = InetAddress.getByName("hello-world.com").getHostAddress();
// ipHw = 192.168.2.1, read the first IP
InetAddress[] allIps = InetAddress.getAllByName("hello-world.com");
// Read the multiple IP setting


// Set the expiration time, unit is milliseconds
DnsCacheManipulator.setDnsCache(3600 * 1000, "hello-hell.com", "192.168.1.1", "192.168.1.2");
