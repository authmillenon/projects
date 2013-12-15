# 6LoWPAN plugtests
## Usage
The plugtests are compilable in two configurations: as a shell application and
as single test binaries. The shell application is the default but if you need
the parameter, its

```bash
USE_SHELL=1 make
```

To compile a single test as binary you need to specify which test you want to
run and which test unit (EUT) you want to use. FORMAT tests are selected with
the variable ``FORMAT``, HC tests are selected with the variable ``HC``,
ND tests are selected with the variable ``ND``, and ND_HC tests are selected
with the variable ``ND_HC`` (see Test descriptions).

```bash
USE_SHELL=0 FORMAT=1 EUT=1 make
```

There is a script, that generates all tests as binaries in the form ``<group><nr>_eut<eut>.elf``. 

```bash
./build_all.sh
```

## Test descriptions (by ETSI)
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_FORMAT_01
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle uncompressed 6LoWPAN packets (EUI-64
link-local)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Node-Node
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 4944 5.1, 8
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is disabled on both EUT1 and EUT2
</li>
<li>
EUT1 and EUT2 are configured to use EUI-64
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's link-local address
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
<li>
EUT1 sends an uncompressed 6LoWPAN packet containing the Echo Request
message to EUT2's link-local address
</li>
<li>
Dispatch value in 6LowPAN packet is “01000001”
</li>
<li>
Both source and destination addresses are EUI-64 link-local
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Check
</td>
<td>
<li>
EUT2 sends an uncompressed 6LoWPAN packet containing the Echo Reply
message to EUT1's link-local address
</li>
<li>
Dispatch value in 6LowPAN packet is “01000001”
</li>
<li>
Both source and destination addresses are EUI-64 link-local
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Verify
</td>
<td>
EUT1 receives the Echo Reply message from EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Check
</td>
<td>
The data received in the echo reply message is identical to that sent in
EUT1's echo request message
</td>
</tr>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_FORMAT_02
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle uncompressed 6LoWPAN packets (16-bit
link-local)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Node-Node
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 4944 5.1, 8
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is disabled on both EUT1 and EUT2
</li>
<li>
EUT1 and EUT2 are configured to use 16-bit short address
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's link-local address
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
<li>
EUT1 sends an uncompressed 6LoWPAN packet containing the Echo Request
message to EUT2's link-local address
</li>
<li>
Dispatch value in 6LowPAN packet is “01000001”
</li>
<li>
Both source and destination addresses are 16 bit short link-local
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Check
</td>
<td>
<li>
EUT2 sends an uncompressed 6LoWPAN packet containing the Echo Reply
message to EUT1's link-local address
</li>
<li>
Dispatch value in 6LowPAN packet is “01000001”
</li>
<li>
Both source and destination addresses are 16 bit short link-local
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Verify
</td>
<td>
EUT1 receives the Echo Reply message from EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Check
</td>
<td>
The data received in the echo reply message is identical to that sent in
EUT1's echo request message
</td>
</tr>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_FORMAT_03
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle uncompressed 6LoWPAN fragmented packets
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Node-Node
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 4944 5.1, 5.3
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
Header compression is disabled on both EUT1 and EUT2
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's link-local address
</li>
<li>
ICMP payload = 253 bytes, total IPv6 size 301 bytes
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
<li>
EUT1 sends a sequence of uncompressed 6LoWPAN packets containing the
Echo Request fragments to EUT2
</li>
<li>
EUT1 correctly fragments the Echo Request:
</li>
<li>
a 6LoWPAN FRAG1 header (dispatch 11000xxx) is included in the first
packet
</li>
<li>
a 6LoWPAN FRAGN header (dispatch 11100xxx) is included in all following
packets
</li>
<li>
the offsets form a contiguous sequence
</li>
<li>
all fragments except the last one must be multiples of 8 bytes
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Verify
</td>
<td>
EUT2 reassembles correctly the fragments and receives the Echo Request
message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Check
</td>
<td>
<li>
EUT2 sends a sequence of uncompressed 6LoWPAN packets containing the
Echo Reply message to EUT1
</li>
<li>
EUT1 correctly fragments the Echo Reply:
</li>
<li>
a 6LoWPAN FRAG1 header (dispatch 11000xxx) is included in the first
packet
</li>
<li>
a 6LoWPAN FRAGN header (dispatch 11100xxx) is included in all following
packets
</li>
<li>
the offsets form a contiguous sequence
</li>
<li>
all fragments except the last one must be multiples of 8 bytes
</li>
<li>
The data in the echo reply message packets is identical to that sent in
the echo request message packets
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Verify
</td>
<td>
EUT1 correctly reassembles the fragments and receives the Echo Reply
message from EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Verify
</td>
<td>
The data in the received echo reply message is identical to that sent in
the echo request message
</td>
</tr>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_FORMAT_04
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle maximum size uncompressed 6LoWPAN
fragmented packets
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Node-Node
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 4944 5.1, 5.3
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
Header compression is disabled on both EUT1 and EUT2
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's link-local address
</li>
<li>
ICMP payload = 1232 bytes, total IPv6 size 1280 bytes
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
<li>
EUT1 sends a sequence of uncompressed 6LoWPAN packets containing the
Echo Request fragments to EUT2
</li>
<li>
EUT1 correctly fragments the Echo Request:
</li>
<li>
a 6LoWPAN FRAG1 header (dispatch 11000xxx) is included in the first
packet
</li>
<li>
a 6LoWPAN FRAGN header (dispatch 11100xxx) is included in all following
packets
</li>
<li>
the offsets form a contiguous sequence
</li>
<li>
all fragments except the last one must be multiples of 8 bytes
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Verify
</td>
<td>
EUT2 reassembles correctly the fragments and receives the Echo Request
message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Check
</td>
<td>
<li>
EUT2 sends a sequence of uncompressed 6LoWPAN packets containing the
Echo Reply message to EUT1
</li>
<li>
EUT1 correctly fragments the Echo Reply:
</li>
<li>
a 6LoWPAN FRAG1 header (dispatch 11000xxx) is included in the first
packet
</li>
<li>
a 6LoWPAN FRAGN header (dispatch 11100xxx) is included in all following
packets
</li>
<li>
the offsets form a contiguous sequence
</li>
<li>
all fragments except the last one must be multiples of 8 bytes
</li>
<li>
The data in the echo reply message packets is identical to that sent in
the echo request message packets
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Verify
</td>
<td>
EUT1 correctly reassembles the fragments and receives the Echo Reply
message from EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Verify
</td>
<td>
The data in the received echo reply message is identical to that sent in
the echo request message
</td>
</tr>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_FORMAT_05
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle uncompressed 6LoWPAN multicast to
all-nodes (16-bit link-local)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Node-Node
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 4944 5.1, 8
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is disabled on both EUT1 and EUT2
</li>
<li>
EUT1 and EUT2 are configured to use 16-bit short address
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
EUT1 initiates an echo request to the link-local all-nodes multicast
address (FF02::1) (ICMP payload = 4 bytes, total IPv6 size 52 bytes)
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
EUT1 sends an uncompressed 6LoWPAN packet containing the Echo Request
message to EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “01000001”
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Check
</td>
<td>
EUT2 sends an uncompressed 6LoWPAN packet containing the Echo Reply
message to EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “01000001”
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Verify
</td>
<td>
EUT1 receives the Echo Reply message from EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Check
</td>
<td>
The data in the echo reply message is identical to that in the echo
request message
</td>
</tr>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_FORMAT_06
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle uncompressed 6LoWPAN multicast to
all-nodes (EUI-64 link-local)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Node-Node
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 4944 5.1, 8
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is disabled on both EUT1 and EUT2
</li>
<li>
EUT1 and EUT2 are configured to use EUI-64
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
EUT1 initiates an echo request to the link-local all-nodes multicast
address (FF02::1) (ICMP payload = 4 bytes, total IPv6 size 52 bytes)
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
EUT1 sends an uncompressed 6LoWPAN packet containing the Echo Request
message to EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “01000001”
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Check
</td>
<td>
EUT2 sends an uncompressed 6LoWPAN packet containing the Echo Reply
message to EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “01000001”
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Verify
</td>
<td>
EUT1 receives the Echo Reply message from EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Check
</td>
<td>
The data in the echo reply message is identical to that in the echo
request message
</td>
</tr>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_FORMAT_07
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle uncompressed 6LoWPAN packets (EUI-64 to
16-bit link-local)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Node-Node
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 4944 5.1, 8
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is disabled on both EUT1 and EUT2
</li>
<li>
EUT1 is configured to use EUI-64 and EUT2 is configured to use 16-bit
short address
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's link-local address
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
<li>
EUT1 sends an uncompressed 6LoWPAN packet containing the Echo Request
message to EUT2's link-local address
</li>
<li>
Dispatch value in 6LowPAN packet is “01000001”
</li>
<li>
Source address is EUI-64 link-local
</li>
<li>
Destination address is 16 bit short link-local
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Check
</td>
<td>
<li>
EUT2 sends an uncompressed 6LoWPAN packet containing the Echo Reply
message to EUT1's link-local address
</li>
<li>
Dispatch value in 6LowPAN packet is “01000001”
</li>
<li>
Source address is 16 bit short link-local
</li>
<li>
Destination address is EUI-64 link-local
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Verify
</td>
<td>
EUT1 receives the Echo Reply message from EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Check
</td>
<td>
The data received in the echo reply message is identical to that sent in
EUT1's echo request message
</td>
</tr>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_FORMAT_08
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle uncompressed 6LoWPAN packets (16-bit to
EUI-64 link-local)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Node-Node
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 4944 5.1, 8
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is disabled on both EUT1 and EUT2
</li>
<li>
EUT1 is configured to use 16-bit short address and EUT2 is configured to
use EUI-64
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's link-local address
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
<li>
EUT1 sends an uncompressed 6LoWPAN packet containing the Echo Request
message to EUT2's link-local address
</li>
<li>
Dispatch value in 6LowPAN packet is “01000001”
</li>
<li>
Source address is 16 bit short link-local
</li>
<li>
Destination address is EUI-64 link-local
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Check
</td>
<td>
<li>
EUT2 sends an uncompressed 6LoWPAN packet containing the Echo Reply
message to EUT1's link-local address
</li>
<li>
Dispatch value in 6LowPAN packet is “01000001”
</li>
<li>
Source address is EUI-64 link-local
</li>
<li>
Destination address is 16 bit short link-local
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Verify
</td>
<td>
EUT1 receives the Echo Reply message from EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Check
</td>
<td>
The data received in the echo reply message is identical to that sent in
EUT1's echo request message
</td>
</tr>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_HC_01
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle compressed 6LoWPAN packets (EUI-64
link-local, hop limit=64)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Node-Node
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6282 section 3
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both EUT1 and EUT2
</li>
<li>
EUT1 and EUT2 are configured to use EUI-64
</li>
<li>
EUT1 and EUT2 are configured with a default hop limit of 64
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's link-local address
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
<li>
Hop Limit is 64, no traffic class or flow label is being used
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
EUT1 sends a compressed 6LoWPAN packet containing the Echo Request
message to EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Feature
</td>
<td>
In IP_HC, SAC=0, SAM=11; DAC=0; DAM=11
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Check
</td>
<td>
EUT2 sends a compressed 6LoWPAN packet containing the Echo Reply message
to EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
8
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
9
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
10
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
11
</td>
<td>
Feature
</td>
<td>
In IP_HC, SAC=0, SAM=11; DAC=0; DAM=11
</td>
</tr>
<tr>
<td>
</td>
<td>
12
</td>
<td>
Verify
</td>
<td>
EUT1 receives the Echo Reply message from EUT2
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
<li>
The feature tests check that best compression is used (but this is not a
requirement for interoperability)
</li>
<li>
The Echo Reply message might use a different hop limit in some
implementations, then the HLIM value might also be different.
</li>
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_HC_02
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle compressed 6LoWPAN packets (16-bit
link-local, hop limit=64)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Node-Node
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6282 section 3
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both EUT1 and EUT2
</li>
<li>
EUT1 and EUT2 are configured to use 16-bit short address
</li>
<li>
EUT1 and EUT2 are configured with a default hop limit of 64
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's link-local address
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
<li>
Hop Limit is 64, no traffic class or flow label is being used
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
EUT1 sends a compressed 6LoWPAN packet containing the Echo Request
message to EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Feature
</td>
<td>
In IP_HC, SAC=0, SAM=11; DAC=0; DAM=11
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Check
</td>
<td>
EUT2 sends a compressed 6LoWPAN packet containing the Echo Reply message
to EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
8
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
9
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
10
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
11
</td>
<td>
Feature
</td>
<td>
In IP_HC, SAC=0, SAM=11; DAC=0; DAM=11
</td>
</tr>
<tr>
<td>
</td>
<td>
12
</td>
<td>
Verify
</td>
<td>
EUT1 receives the Echo Reply message from EUT2
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
<li>
The feature tests check that best compression is used (but this is not a
requirement for interoperability)
</li>
<li>
The Echo Reply message might use a different hop limit in some
implementations, then the HLIM value might also be different.
</li>
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_HC_03
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle compressed 6LoWPAN packets (EUI-64
link-local, hop limit=63)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Node-Node
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6282 section 3
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both EUT1 and EUT2
</li>
<li>
EUT1 and EUT2 are configured to use EUI-64
</li>
<li>
EUT1 and EUT2 are configured with a default hop limit of 63
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's link-local address
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
<li>
Hop Limit is 63, no traffic class or flow label is being used
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
EUT1 sends a compressed 6LoWPAN packet containing the Echo Request
message to EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 00 and the hop limit field is carried in-line
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Feature
</td>
<td>
In IP_HC, SAC=0, SAM=11; DAC=0; DAM=11
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Check
</td>
<td>
EUT2 sends a compressed 6LoWPAN packet containing the Echo Reply message
to EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
8
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
9
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
10
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 00 and the hop limit field is carried in-line
</td>
</tr>
<tr>
<td>
</td>
<td>
11
</td>
<td>
Feature
</td>
<td>
In IP_HC, SAC=0, SAM=11; DAC=0; DAM=11
</td>
</tr>
<tr>
<td>
</td>
<td>
12
</td>
<td>
Verify
</td>
<td>
EUT1 receives the Echo Reply message from EUT2
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
<li>
The feature tests check that best compression is used (but this is not a
requirement for interoperability)
</li>
<li>
The Echo Reply message might use a different hop limit in some
implementations, then the HLIM value might also be different.
</li>
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_HC_04
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle compressed 6LoWPAN packets (16-bit
link-local, hop limit=63)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Node-Node
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6282 section 3
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both EUT1 and EUT2
</li>
<li>
EUT1 and EUT2 are configured to use 16-bit short address
</li>
<li>
EUT1 and EUT2 are configured with a default hop limit of 63
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's link-local address
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
<li>
Hop Limit is 63, no traffic class or flow label is being used
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
EUT1 sends a compressed 6LoWPAN packet containing the Echo Request
message to EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 00 and the hop limit field is carried in-line
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Feature
</td>
<td>
In IP_HC, SAC=0, SAM=11; DAC=0; DAM=11
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Check
</td>
<td>
EUT2 sends a compressed 6LoWPAN packet containing the Echo Reply message
to EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
8
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
9
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
10
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 00 and the hop limit field is carried in-line
</td>
</tr>
<tr>
<td>
</td>
<td>
11
</td>
<td>
Feature
</td>
<td>
In IP_HC, SAC=0, SAM=11; DAC=0; DAM=11
</td>
</tr>
<tr>
<td>
</td>
<td>
12
</td>
<td>
Verify
</td>
<td>
EUT1 receives the Echo Reply message from EUT2
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
<li>
The feature tests check that best compression is used (but this is not a
requirement for interoperability)
</li>
<li>
The Echo Reply message might use a different hop limit in some
implementations, then the HLIM value might also be different.
</li>
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_HC_05
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle compressed UDP packets (EUI-64, server
port 5683)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6282, 4.3
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both Host and Router
</li>
<li>
Host is configured to use EUI-64 address
</li>
<li>
A CoAP ping server is installed on port 5683 of the host
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
6LR initiates a CoAP Ping request to Host's CoAP Ping server
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
6LR sends a 6LoWPAN packet containing the CoAP Ping message to Host
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Feature
</td>
<td>
NH is set, NHC is 111100x0, the source port is compressed to 8 bits
(x=1) or uncompressed (x=0), the destination port is uncompressed 5683
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Verify
</td>
<td>
Host receives the CoAP Ping message from 6LR
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Check
</td>
<td>
Host sends a 6LoWPAN packet containing the CoAP Reset message to 6LR
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Feature
</td>
<td>
NH is set, NHC is 1111000x, the source port is uncompressed 5683, the
destination port is compressed to 8 bits (x=1) or uncompressed (x=0)
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Verify
</td>
<td>
6LR receives the CoAP Reset message from Host
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
The feature tests check that best compression is used (but this is not a
requirement for interoperability)
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_HC_06
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle compressed UDP packets (16-bit, server
port 5683)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6282, 4.3
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both Host and Router
</li>
<li>
Host is configured to use 16-bit address
</li>
<li>
A CoAP ping server is installed on port 5683 of the host
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
6LR initiates a CoAP Ping request to Host's CoAP Ping server
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
6LR sends a 6LoWPAN packet containing the CoAP Ping message to Host
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Feature
</td>
<td>
NH is set, NHC is 111100x0, the source port is compressed to 8 bits
(x=1) or uncompressed (x=0), the destination port is uncompressed 5683
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Verify
</td>
<td>
Host receives the CoAP Ping message from 6LR
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Check
</td>
<td>
Host sends a 6LoWPAN packet containing the CoAP Reset message to 6LR
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Feature
</td>
<td>
NH is set, NHC is 1111000x, the source port is uncompressed 5683, the
destination port is compressed to 8 bits (x=1) or uncompressed (x=0)
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Verify
</td>
<td>
6LR receives the CoAP Reset message from Host
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
The feature tests check that best compression is used (but this is not a
requirement for interoperability)
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_HC_07
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle compressed UDP packets (EUI-64, server
port 61616)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6282, 4.3
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both Host and Router
</li>
<li>
Host is configured to use EUI-64 address
</li>
<li>
A CoAP ping server is installed on port 61616 of the host
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
6LR initiates a CoAP Ping request to Host's CoAP Ping server
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
6LR sends a 6LoWPAN packet containing the CoAP Ping message to Host
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Feature
</td>
<td>
NH is set, NHC is 111100x1, the destination port is compressed to 4 bits
of 0000 (x=1) or 8 bits of 0xb0 (x=0)
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Verify
</td>
<td>
Host receives the CoAP Ping message from 6LR
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Check
</td>
<td>
Host sends a 6LoWPAN packet containing the CoAP Reset message to 6LR
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Feature
</td>
<td>
NH is set, NHC is 1111001x, the source port is compressed to 4 bits of
0000 (x=1) or 8 bits of 0xb0 (x=0)
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Verify
</td>
<td>
6LR receives the CoAP Reset message from Host
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
The feature tests check that best compression is used (but this is not a
requirement for interoperability)
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_HC_08
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle compressed UDP packets (16-bit, server
port 61616)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6282, 4.3
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both Host and Router
</li>
<li>
Host is configured to use 16-bit address
</li>
<li>
A CoAP ping server is installed on port 61616 of the host
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
6LR initiates a CoAP Ping request to Host's CoAP Ping server
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
6LR sends a 6LoWPAN packet containing the CoAP Ping message to Host
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Feature
</td>
<td>
NH is set, NHC is 111100x1, the destination port is compressed to 4 bits
of 0000 (x=1) or 8 bits of 0xb0 (x=0)
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Verify
</td>
<td>
Host receives the CoAP Ping message from 6LR
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Check
</td>
<td>
Host sends a 6LoWPAN packet containing the CoAP Reset message to 6LR
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Feature
</td>
<td>
NH is set, NHC is 1111001x, the source port is compressed to 4 bits of
0000 (x=1) or 8 bits of 0xb0 (x=0)
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Verify
</td>
<td>
6LR receives the CoAP Reset message from Host
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
The feature tests check that best compression is used (but this is not a
requirement for interoperability)
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_HC_09
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle compressed 6LoWPAN packets (EUI-64 to
16-bit link-local, hop limit=64)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Node-Node
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6282 section 3
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both EUT1 and EUT2
</li>
<li>
EUT1 is configured to use EUI-64 and EUT2 is configured to use 16-bit
short address
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's link-local address
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
<li>
Hop Limit is 64, no traffic class or flow label is being used
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
EUT1 sends a compressed 6LoWPAN packet containing the Echo Request
message to EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Feature
</td>
<td>
In IP_HC, SAC=0, SAM=11; DAC=0; DAM=11
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Check
</td>
<td>
EUT2 sends a compressed 6LoWPAN packet containing the Echo Reply message
to EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
8
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
9
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
10
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
11
</td>
<td>
Feature
</td>
<td>
In IP_HC, SAC=0, SAM=11; DAC=0; DAM=11
</td>
</tr>
<tr>
<td>
</td>
<td>
12
</td>
<td>
Verify
</td>
<td>
EUT1 receives the Echo Reply message from EUT2
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
<li>
The feature tests check that best compression is used (but this is not a
requirement for interoperability)
</li>
<li>
The Echo Reply message might use a different hop limit in some
implementations, then the HLIM value might also be different.
</li>
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_HC_10
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs correctly handle compressed 6LoWPAN packets (16-bit to
EUI-64 link-local, hop limit=64)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Node-Node
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6282 section 3
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both EUT1 and EUT2
</li>
<li>
EUT1 is configured to use 16-bit short address and EUT2 is configured to
use EUI-64
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's link-local address
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
<li>
Hop Limit is 64, no traffic class or flow label is being used
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
EUT1 sends a compressed 6LoWPAN packet containing the Echo Request
message to EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Feature
</td>
<td>
In IP_HC, SAC=0, SAM=11; DAC=0; DAM=11
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Check
</td>
<td>
EUT2 sends a compressed 6LoWPAN packet containing the Echo Reply message
to EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
8
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
9
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
10
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
11
</td>
<td>
Feature
</td>
<td>
In IP_HC, SAC=0, SAM=11; DAC=0; DAM=11
</td>
</tr>
<tr>
<td>
</td>
<td>
12
</td>
<td>
Verify
</td>
<td>
EUT1 receives the Echo Reply message from EUT2
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
<li>
The feature tests check that best compression is used (but this is not a
requirement for interoperability)
</li>
<li>
The Echo Reply message might use a different hop limit in some
implementations, then the HLIM value might also be different.
</li>
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_ND_01
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that a host is able to register its global IPv6 address (EUI-64)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6775 10.2
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both Host and Router
</li>
<li>
Host is configured to use EUI-64 address
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
Initialize the network interface of the Host
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
The Host sends a Router Solicitation to all-routers multicast address
with SLLAO (EUI-64). Source = link local based on EUI-64
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Verify
</td>
<td>
The Router receives the Router Solicitation from the host.
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Check
</td>
<td>
<li>
The Router sends a unicast Router Advertisement containing PIO and
optionally 6COs to the host.
</li>
<li>
Link local addresses are used.
</li>
<li>
The L bit is not set.
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Verify
</td>
<td>
The host receives the Router Advertisement from the router
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Check
</td>
<td>
The host configures its tentative global IPv6 address based on the PIO
information in RA from the Router (EUI-64)
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Check
</td>
<td>
The host registers its tentative address by sending a unicast Neighbor
Solicitation containing ARO and SLLAO. Source = GP64
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Verify
</td>
<td>
The Router receives the Neighbor Solicitation from the host.
</td>
</tr>
<tr>
<td>
</td>
<td>
8
</td>
<td>
Check
</td>
<td>
The Router sends a Neighbor Advertisement with Status set to 0 (Dest =
GP64)
</td>
</tr>
<tr>
<td>
</td>
<td>
9
</td>
<td>
Verify
</td>
<td>
The host updates the status of the tentative address
</td>
</tr>
<tr>
<td>
</td>
<td>
10
</td>
<td>
Stimulus
</td>
<td>
<li>
The Router initiates an echo request to the Host's new global address,
using its own global address as the source
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
<li>
Hop Limit is 64, no traffic class or flow label is being used
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
11
</td>
<td>
Check
</td>
<td>
The Router sends a 6LoWPAN packet containing the Echo Request message to
the Host
</td>
</tr>
<tr>
<td>
</td>
<td>
12
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
13
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
14
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
15
</td>
<td>
Verify
</td>
<td>
The Host receives the Echo Request message from the Router
</td>
</tr>
<tr>
<td>
</td>
<td>
16
</td>
<td>
Check
</td>
<td>
The Host sends a 6LoWPAN packet containing the Echo Reply message to the
Router
</td>
</tr>
<tr>
<td>
</td>
<td>
17
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
18
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
19
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
20
</td>
<td>
Verify
</td>
<td>
The Router receives the Echo Reply message from the Host
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
The Echo Reply message might use a different hop limit in some
implementations, then the HLIM value might also be different.
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_ND_02
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that a host is able to register its global IPv6 address (16-bit)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6775 10.2
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both Host and Router
</li>
<li>
Host is configured to use 16 bit short address
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
Initialize the network interface of the Host
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
The Host sends a Router Solicitation to all-routers multicast address
with SLLAO (EUI-64). Source = link local based on EUI-64
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Verify
</td>
<td>
The Router receives the Router Solicitation from the host.
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Check
</td>
<td>
<li>
The Router sends a unicast Router Advertisement containing PIO and
optionally 6COs to the host.
</li>
<li>
Link local addresses are used.
</li>
<li>
The L bit is not set.
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Verify
</td>
<td>
The host receives the Router Advertisement from the router
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Check
</td>
<td>
The host configures its tentative global IPv6 address based on the PIO
information in RA from the Router (16-bit)
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Check
</td>
<td>
The host registers its tentative address by sending a unicast Neighbor
Solicitation containing ARO and SLLAO. Source = GP16
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Verify
</td>
<td>
The Router receives the Neighbor Solicitation from the host.
</td>
</tr>
<tr>
<td>
</td>
<td>
8
</td>
<td>
Check
</td>
<td>
The Router sends a Neighbor Advertisement with Status set to 0 (Dest =
GP16)
</td>
</tr>
<tr>
<td>
</td>
<td>
9
</td>
<td>
Verify
</td>
<td>
The host updates the status of the tentative address
</td>
</tr>
<tr>
<td>
</td>
<td>
10
</td>
<td>
Stimulus
</td>
<td>
<li>
The Router initiates an echo request to the Host's new global address,
using its own global address as the source
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
<li>
Hop Limit is 64, no traffic class or flow label is being used
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
11
</td>
<td>
Check
</td>
<td>
The Router sends a 6LoWPAN packet containing the Echo Request message to
the Host
</td>
</tr>
<tr>
<td>
</td>
<td>
12
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
13
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
14
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
15
</td>
<td>
Verify
</td>
<td>
The Host receives the Echo Request message from the Router
</td>
</tr>
<tr>
<td>
</td>
<td>
16
</td>
<td>
Check
</td>
<td>
The Host sends a 6LoWPAN packet containing the Echo Reply message to the
Router
</td>
</tr>
<tr>
<td>
</td>
<td>
17
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
18
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
19
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
20
</td>
<td>
Verify
</td>
<td>
The Router receives the Echo Reply message from the Host
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
The Echo Reply message might use a different hop limit in some
implementations, then the HLIM value might also be different.
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_ND_03
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check Host NUD behavior
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6775 5.5
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both Host and Router
</li>
<li>
Host is configured to use EUI-64 address
</li>
<li>
Host is up and registered its global address with the Router
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
Host sends a sequence of echo requests to 2001:db8::1
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Verify
</td>
<td>
Host sends a unicast NS message to the 6LR to perform NUD
</td>
</tr>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_ND_04
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check 6LR NUD behavior (ICMP version)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6775 5.5
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both Host and Router
</li>
<li>
Host is configured to use EUI-64 address
</li>
<li>
Host is up and registered its global address with the Router
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
6LR sends a sequence of echo requests to Host
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Stimulus
</td>
<td>
After 10 seconds, echo reply function is disabled on host
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Verify
</td>
<td>
6LR sends a unicast NS message to the host to perform NUD
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
Optional, as not all hosts allow disabling echo reply function
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_ND_05
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check 6LR NUD behavior (UDP version)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6775 5.5
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both Host and Router
</li>
<li>
Host is configured to use EUI-64 address
</li>
<li>
A CoAP ping server is installed on port 5683 of the host
</li>
<li>
Host is up and registered its global address with the Router
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
6LR sends a sequence of CoAP pings to Host
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Stimulus
</td>
<td>
After 10 seconds, CoAP server function is disabled on host
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Verify
</td>
<td>
6LR sends a unicast NS message to the host to perform NUD
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
Optional, as not all hosts allow disabling CoAP server function
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_ND_06
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check host behavior under multiple prefixes (EUI-64)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 4861 3.1
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both Host and Router
</li>
<li>
Host is configured to use EUI-64 address
</li>
<li>
Router is configured with multiple prefixes
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
Initialize the network interface of the Host
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
The Host sends a Router Solicitation to all-routers multicast address
with SLLAO (EUI-64). Source = link local based on EUI-64
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Verify
</td>
<td>
The Router receives the Router Solicitation from the host.
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Check
</td>
<td>
<li>
The Router sends a unicast Router Advertisement containing PIO with
multiple prefixes and optionally 6COs to the host.
</li>
<li>
Link local addresses are used.
</li>
<li>
The L bit is not set.
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Verify
</td>
<td>
The host receives the Router Advertisement from the router
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Check
</td>
<td>
The host configures a number of tentative global IPv6 address based on
the PIO information in RA from the Router (EUI-64)
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Check
</td>
<td>
The host registers its tentative addresses by sending unicast Neighbor
Solicitations containing ARO and SLLAO. Source = GP64
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Verify
</td>
<td>
The Router receives the Neighbor Solicitations from the host.
</td>
</tr>
<tr>
<td>
</td>
<td>
8
</td>
<td>
Check
</td>
<td>
The Router sends Neighbor Advertisements with Status set to 0 (Dest =
GP64)
</td>
</tr>
<tr>
<td>
</td>
<td>
9
</td>
<td>
Verify
</td>
<td>
The host updates the status of the tentative addresses
</td>
</tr>
<tr>
<td>
</td>
<td>
10
</td>
<td>
Stimulus
</td>
<td>
<li>
The Router initiates an echo request to one of the Host's new global
addresses, using the appropriate own global address as the source
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
<li>
Hop Limit is 64, no traffic class or flow label is being used
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
11
</td>
<td>
Check
</td>
<td>
The Router sends a 6LoWPAN packet containing the Echo Request message to
the Host
</td>
</tr>
<tr>
<td>
</td>
<td>
12
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
13
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
14
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
15
</td>
<td>
Verify
</td>
<td>
The Host receives the Echo Request message from the Router
</td>
</tr>
<tr>
<td>
</td>
<td>
16
</td>
<td>
Check
</td>
<td>
The Host sends a 6LoWPAN packet containing the Echo Reply message to the
Router
</td>
</tr>
<tr>
<td>
</td>
<td>
17
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
18
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
19
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
20
</td>
<td>
Verify
</td>
<td>
The Router receives the Echo Reply message from the Host
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
<li>
Optional, as not all 6lrs and hosts allow multiple prefixes
</li>
<li>
The Echo Reply message might use a different hop limit in some
implementations, then the HLIM value might also be different.
</li>
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_ND_07
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check host behavior under multiple prefixes (16-bit)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 4861 3.1
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both Host and Router
</li>
<li>
Host is configured to use 16 bit short address
</li>
<li>
Router is configured with multiple prefixes
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
Initialize the network interface of the Host
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Check
</td>
<td>
The Host sends a Router Solicitation to all-routers multicast address
with SLLAO (EUI-64). Source = link local based on EUI-64
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Verify
</td>
<td>
The Router receives the Router Solicitation from the host.
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Check
</td>
<td>
<li>
The Router sends a unicast Router Advertisement containing PIO with
multiple prefixes and optionally 6COs to the host.
</li>
<li>
Link local addresses are used.
</li>
<li>
The L bit is not set.
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Verify
</td>
<td>
The host receives the Router Advertisement from the router
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Check
</td>
<td>
The host configures a number of tentative global IPv6 address based on
the PIO information in RA from the Router (16-bit)
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Check
</td>
<td>
The host registers its tentative addresses by sending unicast Neighbor
Solicitations containing ARO and SLLAO. Source = GP16
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Verify
</td>
<td>
The Router receives the Neighbor Solicitations from the host.
</td>
</tr>
<tr>
<td>
</td>
<td>
8
</td>
<td>
Check
</td>
<td>
The Router sends Neighbor Advertisements with Status set to 0 (Dest =
GP16)
</td>
</tr>
<tr>
<td>
</td>
<td>
9
</td>
<td>
Verify
</td>
<td>
The host updates the status of the tentative addresses
</td>
</tr>
<tr>
<td>
</td>
<td>
10
</td>
<td>
Stimulus
</td>
<td>
<li>
The Router initiates an echo request to one of the Host's new global
addresses, using the appropriate own global address as the source
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
<li>
Hop Limit is 64, no traffic class or flow label is being used
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
11
</td>
<td>
Check
</td>
<td>
The Router sends a 6LoWPAN packet containing the Echo Request message to
the Host
</td>
</tr>
<tr>
<td>
</td>
<td>
12
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
13
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
14
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
15
</td>
<td>
Verify
</td>
<td>
The Host receives the Echo Request message from the Router
</td>
</tr>
<tr>
<td>
</td>
<td>
16
</td>
<td>
Check
</td>
<td>
The Host sends a 6LoWPAN packet containing the Echo Reply message to the
Router
</td>
</tr>
<tr>
<td>
</td>
<td>
17
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
18
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
19
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
20
</td>
<td>
Verify
</td>
<td>
The Router receives the Echo Reply message from the Host
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
<li>
Optional, as not all 6lrs and hosts allow multiple prefixes
</li>
<li>
The Echo Reply message might use a different hop limit in some
implementations, then the HLIM value might also be different.
</li>
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_ND_HC_01
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs make use of context 0 (EUI-64)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6775 5.4, RFC 6282 3.1.1
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both EUT1 and EUT2
</li>
<li>
EUT1 and EUT2 are configured to use EUI-64
</li>
<li>
EUT1 and EUT2 are configured with a default hop limit of 64
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
Host is set up with 6LR and receives context 0 for the global prefix
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's GP64 address
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
<li>
Hop Limit is 64, no traffic class or flow label is being used
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Check
</td>
<td>
EUT1 sends a 6LoWPAN packet containing the Echo Request message to EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Feature
</td>
<td>
The compression makes use of the global prefix (SAC/DAC = 1,
SAM/DAM=01/11)
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Feature
</td>
<td>
The context identifier extension is not present (CID = 0)
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
8
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
9
</td>
<td>
Check
</td>
<td>
EUT2 sends a compressed 6LoWPAN packet containing the Echo Reply message
to EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
10
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
11
</td>
<td>
Feature
</td>
<td>
The compression makes use of the global prefix (SAC/DAC = 1,
SAM/DAM=01/11)
</td>
</tr>
<tr>
<td>
</td>
<td>
12
</td>
<td>
Feature
</td>
<td>
The context identifier extension is not present (CID = 0)
</td>
</tr>
<tr>
<td>
</td>
<td>
13
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
<li>
The feature tests check that good compression is used (but this is not a
requirement for interoperability)
</li>
<li>
The Echo Reply message might use a different hop limit in some
implementations, then the HLIM value might also be different.
</li>
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_ND_HC_02
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs make use of context 0 (16-bit)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6775 5.4, RFC 6282 3.1.1
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both EUT1 and EUT2
</li>
<li>
EUT1 and EUT2 are configured to use 16-bit short address
</li>
<li>
EUT1 and EUT2 are configured with a default hop limit of 64
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
Host is set up with 6LR and receives context 0 for the global prefix
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's GP16 address
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
<li>
Hop Limit is 64, no traffic class or flow label is being used
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Check
</td>
<td>
EUT1 sends a 6LoWPAN packet containing the Echo Request message to EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Feature
</td>
<td>
The compression makes use of the global prefix (SAC/DAC = 1,
SAM/DAM=10/11)
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Feature
</td>
<td>
The context identifier extension is not present (CID = 0)
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
8
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
9
</td>
<td>
Check
</td>
<td>
EUT2 sends a compressed 6LoWPAN packet containing the Echo Reply message
to EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
10
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
11
</td>
<td>
Feature
</td>
<td>
The compression makes use of the global prefix (SAC/DAC = 1,
SAM/DAM=10/11)
</td>
</tr>
<tr>
<td>
</td>
<td>
12
</td>
<td>
Feature
</td>
<td>
The context identifier extension is not present (CID = 0)
</td>
</tr>
<tr>
<td>
</td>
<td>
13
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
<li>
The feature tests check that good compression is used (but this is not a
requirement for interoperability)
</li>
<li>
The Echo Reply message might use a different hop limit in some
implementations, then the HLIM value might also be different.
</li>
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_ND_HC_03
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs make use of context ≠ 0 (EUI-64)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6775 5.4, RFC 6282 3.1.2
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both EUT1 and EUT2
</li>
<li>
EUT1 and EUT2 are configured to use EUI-64
</li>
<li>
EUT1 and EUT2 are configured with a default hop limit of 64
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
Host is set up with 6LR and receives context ≠ 0 for the global prefix
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's GP64 address
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
<li>
Hop Limit is 64, no traffic class or flow label is being used
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Check
</td>
<td>
EUT1 sends a 6LoWPAN packet containing the Echo Request message to EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Feature
</td>
<td>
The compression makes use of the global prefix (SAC/DAC = 1,
SAM/DAM=01/11)
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Check
</td>
<td>
A Context Identifier Extension (CID) is used for this
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
8
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
9
</td>
<td>
Check
</td>
<td>
EUT2 sends a compressed 6LoWPAN packet containing the Echo Reply message
to EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
10
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
11
</td>
<td>
Feature
</td>
<td>
The compression makes use of the global prefix (SAC/DAC = 1,
SAM/DAM=01/11)
</td>
</tr>
<tr>
<td>
</td>
<td>
12
</td>
<td>
Check
</td>
<td>
A Context Identifier Extension (CID) is used for this
</td>
</tr>
<tr>
<td>
</td>
<td>
13
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
<li>
The feature tests check that good compression is used (but this is not a
requirement for interoperability)
</li>
<li>
The Echo Reply message might use a different hop limit in some
implementations, then the HLIM value might also be different.
</li>
</td>
</table>
<table border="1" width="100%">
<tr>
<th colspan="4">
Interoperability Test Description
</th>
</tr>
<tr>
<th width="15%">
Identifier:
</th>
<td colspan="3">
TD_6LoWPAN_ND_HC_04
</td>
</tr>
<tr>
<th>
Objective:
</th>
<td colspan="3">
Check that EUTs make use of context ≠ 0 (16-bit)
</td>
</tr>
<tr>
<th>
Configuration:
</th>
<td colspan="3">
Host-6LR
</td>
</tr>
<tr>
<th>
References:
</th>
<td colspan="3">
RFC 6775 5.4, RFC 6282 3.1.2
</td>
</tr>
<tr>
<th>
Pre-test conditions:
</th>
<td colspan="3">
<li>
Header compression is enabled on both EUT1 and EUT2
</li>
<li>
EUT1 and EUT2 are configured to use 16-bit short address
</li>
<li>
EUT1 and EUT2 are configured with a default hop limit of 64
</li>
</td>
</tr>
<tr>
<th>
Test Sequence:
</th>
<td width="10 %">
Step
</td>
<td width="15 %">
Type
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
</td>
<td>
0
</td>
<td>
Stimulus
</td>
<td>
Host is set up with 6LR and receives context ≠ 0 for the global prefix
</td>
</tr>
<tr>
<td>
</td>
<td>
1
</td>
<td>
Stimulus
</td>
<td>
<li>
EUT1 initiates an echo request to EUT2's GP16 address
</li>
<li>
ICMP payload = 4 bytes, total IPv6 size 52 bytes
</li>
<li>
Hop Limit is 64, no traffic class or flow label is being used
</li>
</td>
</tr>
<tr>
<td>
</td>
<td>
2
</td>
<td>
Check
</td>
<td>
EUT1 sends a 6LoWPAN packet containing the Echo Request message to EUT2
</td>
</tr>
<tr>
<td>
</td>
<td>
3
</td>
<td>
Feature
</td>
<td>
In IP_HC, TF is 11 and the ecn, dscp and flow label fields are
compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
4
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
5
</td>
<td>
Feature
</td>
<td>
The compression makes use of the global prefix (SAC/DAC = 1,
SAM/DAM=10/11)
</td>
</tr>
<tr>
<td>
</td>
<td>
6
</td>
<td>
Check
</td>
<td>
A Context Identifier Extension (CID) is used for this
</td>
</tr>
<tr>
<td>
</td>
<td>
7
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<tr>
<td>
</td>
<td>
8
</td>
<td>
Verify
</td>
<td>
EUT2 receives the Echo Request message from EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
9
</td>
<td>
Check
</td>
<td>
EUT2 sends a compressed 6LoWPAN packet containing the Echo Reply message
to EUT1
</td>
</tr>
<tr>
<td>
</td>
<td>
10
</td>
<td>
Feature
</td>
<td>
In IP_HC, HLIM (HL) is 10 and the hop limit field is compressed away
</td>
</tr>
<tr>
<td>
</td>
<td>
11
</td>
<td>
Feature
</td>
<td>
The compression makes use of the global prefix (SAC/DAC = 1,
SAM/DAM=10/11)
</td>
</tr>
<tr>
<td>
</td>
<td>
12
</td>
<td>
Check
</td>
<td>
A Context Identifier Extension (CID) is used for this
</td>
</tr>
<tr>
<td>
</td>
<td>
13
</td>
<td>
Check
</td>
<td>
Dispatch value in 6LowPAN packet is “011TFxHL”
</td>
</tr>
<th>
Notes:
</th>
<td colspan="3">
<li>
The feature tests check that good compression is used (but this is not a
requirement for interoperability)
</li>
<li>
The Echo Reply message might use a different hop limit in some
implementations, then the HLIM value might also be different.
</li>
</td>
</table>
