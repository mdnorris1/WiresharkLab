# Wireshark

As part of the fantastic Antisyphon training with John Strand, I got to use packet captures to analyze network traffic.

Firts I opened magnitude_1hr in the Open Capture File box. 

When Wireshark opens, you will see packets represented in three different windows.

The top window shows each individual packet in order.

The second window shows a "decode" of any packet that is selected.

Any of the lines with a > can be expanded.

The last window is the hex for the packet.

Please select Statistics > HTTP > Requests:

![](attachments/Clipboard_2020-12-09-18-42-30.png)

This will show us the various HTTP requests for the capture:

![](attachments/Clipboard_2020-12-09-18-43-37.png)


Now, let's look at Statistics > Conversations:

![](attachments/Clipboard_2020-12-09-18-45-30.png)

This will give us a breakdown of who was talking to whom:

![](attachments/Clipboard_2020-12-09-18-46-16.png)

Please select IPv4:

![](attachments/Clipboard_2020-12-09-18-46-38.png)

Then click on the top of the packets column twice:

![](attachments/Clipboard_2020-12-09-18-47-21.png)

This gives us a breakdown of who was chatting with what system the most.  Click it again and it will sort the opposite direction and show you the least:

![](attachments/Clipboard_2020-12-09-18-48-14.png)

Really want to know what those systems were saying to each other?  Right click on a conversation and select Apply as Filter > Selected > A<->B

![](attachments/Clipboard_2020-12-09-18-49-33.png)

You should see the main Wireshark screen change

Then, close the Conversations window:

Notice the following in the filter bar

`ip.addr==68.183.138.51 && ip.addr==192.168.99.52`

![](attachments/Clipboard_2020-12-09-18-51-35.png)

This is saying:

"IP address equals 68.183.138.51 And IP address equals 192.168.99.52"

If a packet meets both of those critiera it is displayed:

![](attachments/Clipboard_2020-12-09-18-53-19.png)

Now, right-click on any of the packets and select Follow > TCP Stream:

![](attachments/Clipboard_2020-12-09-18-54-10.png)

This is showing the request (in red) and the response (in blue) between our two systems:

![](attachments/Clipboard_2020-12-09-18-55-09.png)

Anything look strange there?  If you look closely, there is a lot of encoded PowerShell.

Now, let's play with some basic filters in the filter bar.  We have already seen how Wireshark can filter on IP addresses.  But we can also filter on protocols.

To start, just type l.

Notice how Wireshark tries to help you with possible completion options as you type.

Now finish typing llmnr.

Then hit enter.

![](attachments/Clipboard_2020-12-11-08-57-52.png)

Notice that when you type llmnr and hit enter, Wireshark shows you all packets that are that protocol

Now try ipv6 and hit enter:

![](attachments/Clipboard_2020-12-11-08-58-47.png)

This allows you to very quickly drill in on any specific protocols you are reviewing in a packet capture.

Remember the PowerShell from tcpdump?  It had the string New-Object? Well, we can search though all the http traffic looking for that specific string:

Put the following into the filter bar:

http contains "New-Object"

![](attachments/Clipboard_2020-12-11-09-02-28.png)

With Wireshark, we can search through all our packets looking for specific strings and data.







