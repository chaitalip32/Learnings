# Learnings
Learning github.
<br>
Author-Chaitali P
<br>
This is readme file
sfsf





















Prac2 
Basic Command

configuring and displaying network interfaces
Ifconfig

Dispalys and manipulates routing, devices and tunnels.
ip

Shows version and output of ip commands
ip -V

Shows ip addresses
ip addr

Displays detailed ip configuration
ip addr show lo

Shows and configures network interfaces
ip link

Displays the current routing table
ip route show

Shows a short summary of network interfaces
ifconfig -s

Queries DNS Servers for information.
dig google.com

Queries internet name servers interactively for domain name .
nslookup google.com

Displays all active TCP Connections
netstat -at

performs DNS lookup to find ip addreses
host google.com

sends ICMP echo request to test network
ping -c 5 google.com

Traces the route packets take to reach a network host
sudo traceroute -T 184.95.56.34
sudo traceroute -T 127.0.0.53

Displays or modifies the ip routing table
route

Displays or modifies the ARP
arp

Configures wireless network interfaces
iwconfig

Fetches domain registration information.
whois google.com






Prac 3 - point to point Topology
 Copy the first.cc file and paste in scratch folder

~/ns3/ns-allinone-3.35/ns-3.35 (right click on it and open terminal )

~/ns3/ns-allinone-3.35/ns-3.35 $- 

For running :-
./waf --run scratch/first  
or 
./waf --run first


./waf --run scratch/first --vis 
		or
./waf --run first --vis




Prac 4 - Bus  Topology
 Copy the second.cc file and paste in scratch folder

./waf --run scratch/second
./waf –run scratch/second –vis


Prac 5 - star topology

Open the ns3.35 folder , go to examples and open tcp folder. 
You will find the star.cc there ..Copy the star.cc file to scratch folder

./waf --run scratch/star  
Or
 ./waf --run star


./waf --run scratch/star --vis  
or 
./waf --run star --vis


Prac 6 - mesh topology
Ns.3.35 -> src -> mesh folder-> example -> mesh.cc   copy and paste in scratch folder

./waf --run scratch/mesh.cc

./waf --run scratch/mesh --vis  




NetAnim
Prac7 : Hybird topology

Example -> tutorial -> Third.cc   copy paste in scratch and rename to hybridanim

On terminal ~/ns3/ns-allinone-3.35/ns-3.35 (right click on it and open terminal )

Edit the file:
gedit scratch/hybridanim.cc

//netanimation  header files
#include "ns3/netanim-module.h" 
#include "ns3/mobility-module.h"
Line no.184 before smulator::run() add below lines

AnimationInterface anim("hybridanim.xml"); anim.SetConstantPosition(p2pNodes.Get(0),10.0,10.0); anim.SetConstantPosition(p2pNodes.Get(0),20.0,20.0);


Run 

./waf --run scratch/hybridanim.cc


Go to netanim folder -> open in terminal

./NetAnim

Go to £ symbol for opening xml.file 
Ns3 -> ns-allinone -> ns-3.35 -> hybridanim.xml

Open this file and run 


Prac 8 : UDP Client
Open the ns3.35 folder and copy paste the udp-client-server.cc  file to scratch.

./waf --run scratch/udp-client-server.cc
./waf --run scratch/udp-client-server.cc --vis

Prac 9 or 10
Ns 3.35->examples->tcp->Tcp.bulk.send.cc

./waf --run scratch/Tcp.bulk.send.cc

./waf --run scratch/Tcp.bulk.send.cc  --vis

Practical 11
Wireshark

Practical 12
Copy first.cc in scratch
In terminal 
Gedit scratch/first.cc

//Add header file

#include "ns3/flow-monitor.h" 
#include "ns3/flow-monitor-helper.h" 
#include "ns3/traffic-control-module.h" 
#include "ns3/ipv4-flow-classifier.h"

//After line no. 81  clientApp.stop(second(10.0));

bool tracing = true; // Added tracing variable 
FlowMonitorHelper flowHelper;
Ptr monitor = flowHelper.InstallAll();

Simulator::Stop(Seconds(10.0));

if (tracing) {
	pointToPoint.EnablePcapAll("p2p"); // Fixed missing semicolon
}

//After Simulator run  Simulator::Run ();

monitor->CheckForLostPackets();
Ptr classifier = DynamicCast(flowHelper.GetClassifier());
std::map<FlowId, FlowMonitor::FlowStats> stats = monitor->GetFlowStats();

./waf --run scratch/first.cc


