# Wireshark

As part of the fantastic Antisyphon training with John Strand, I got to use packet captures to analyze network traffic.

Firts I opened magnitude_1hr in the Open Capture File box. 

When Wireshark opens, you will see packets represented in three different windows.

The top window shows each individual packet in order.

The second window shows a "decode" of any packet that is selected.

Any of the lines with a > can be expanded.

The last window is the hex for the packet.

Please select Statistics > HTTP > Requests:

This will show us the various HTTP requests for the capture:

<br/>
<img src="https://github.com/mdnorris1/WiresharkLab/blob/main/assets/css/http%20requests.png" height="80%" width="80%" alt="ifconfig command"/>
<br />

Now, let's look at Statistics > Conversations:

This will give us a breakdown of who was talking to whom:

<br/>
<img src="https://github.com/mdnorris1/WiresharkLab/blob/main/assets/css/conversations2.png" height="80%" width="80%" alt="ifconfig command"/>
<br />

Please select IPv4:

Then click on the top of the packets column twice:

<br/>
<img src="https://github.com/mdnorris1/WiresharkLab/blob/main/assets/css/packets3.png" height="80%" width="80%" alt="ifconfig command"/>
<br />

This gives us a breakdown of who was chatting with what system the most.  Click it again and it will sort the opposite direction and show you the least:

Really want to know what those systems were saying to each other?  Right click on a conversation and select Apply as Filter > Selected > A<->B

<br/>
<img src="https://github.com/mdnorris1/WiresharkLab/blob/main/assets/css/filter4.png" height="80%" width="80%" alt="ifconfig command"/>
<br />

You should see the main Wireshark screen change

Then, close the Conversations window.

Notice the following in the filter bar

`ip.addr==68.183.138.51 && ip.addr==192.168.99.52`

<br/>
<img src="https://github.com/mdnorris1/WiresharkLab/blob/main/assets/css/filterbar5.png" height="80%" width="80%" alt="ifconfig command"/>
<br />

This is saying:

"IP address equals 68.183.138.51 And IP address equals 192.168.99.52"

If a packet meets both of those critiera it is displayed.

Now, right-click on any of the packets and select Follow > TCP Stream:

This is showing the request (in red) and the response (in blue) between our two systems:

<br/>
<img src="https://github.com/mdnorris1/WiresharkLab/blob/main/assets/css/request6.png" height="80%" width="80%" alt="ifconfig command"/>
<br />

There is a lot of encoded PowerShell here.

I then got to try some basic filters in the filter bar, so after filtering on IP addresses, I was now filtering on protocols.

using the filter: llmnr.

Then hit enter.

Notice that when you type llmnr and hit enter, Wireshark shows you all packets that are that protocol

Now try ipv6 and hit enter:

This allows you to very quickly drill in on any specific protocols you are reviewing in a packet capture.

<br/>
<img src="https://github.com/mdnorris1/WiresharkLab/blob/main/assets/css/ipv67.png" height="80%" width="80%" alt="ifconfig command"/>
<br />

We had previously found the string New-Object in tcpdump so now I could search though all the http traffic looking for that specific string, by putting the following into the filter bar:

http contains "New-Object"

With Wireshark, we can search through all our packets looking for specific strings and data.

<br/>
<img src="https://github.com/mdnorris1/WiresharkLab/blob/main/assets/css/newobject8.png" height="80%" width="80%" alt="ifconfig command"/>
<br />

Hope you enjoyed the walkthrough of the project!





