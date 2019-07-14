# outbound sample

Outbound sample


| sample   |  fix 1  |    |    |
|:---|:---|:---|:--:|
| username=7211
type=peer
secret=7211
progressinband=yes
port=5060
insecure=invite,port
host=10.0.3.3
dtmfmode=inband
disallow=all
context=from-trunk
allow=ulaw
qualify=no

And my Inbound
type=peer
secret=7211
progressinband=yes
dtmfmode=inband
disallow=all
context=from-internal&from-trunk
qualify=no   | type=friend
username=7211
secret=7211
progressinband=yes
dtmfmode=inband
port=5060
insecure=invite,port
host=10.0.3.3
dtmfmode=inband
disallow=all
allow=ulaw
context=from-trunk
qualify=no   |    |    |
|    |    |    |    |
|    |    |    |    |
<pre>
username=7211
type=peer
secret=7211
progressinband=yes
port=5060
insecure=invite,port
host=10.0.3.3
dtmfmode=inband
disallow=all
context=from-trunk
allow=ulaw
qualify=no

And my Inbound
type=peer
secret=7211
progressinband=yes
dtmfmode=inband
disallow=all
context=from-internal&from-trunk
qualify=no
</pre>