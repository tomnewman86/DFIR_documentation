# Expanding Chainsaw

- Tool: https://github.com/countercept/chainsaw
- Documentation: https://github.com/countercept/chainsaw/tree/documentation_improvements

## Description:

Chainsaw provides a powerful ‘first-response’ capability to quickly identify threats within Windows event logs. It offers a generic and
fast method of searching through event logs for keywords, and by identifying threats using built-in detection logic and via support for
Sigma detection rules.

Following a recent request, the developer of Chainsaw provided some documentation to help users expand on the tool. This included
how the Chainsaw mappings worked and how to link them to sigma rules and also how to create your own mappings and associate
them with rules of interest (either preexisting or bespoke self creations)

To help support this new guidance documentation and help understand the mappings better myself, I have run some tests with some
new mappings and sigma rules I have created and thought I’d write up and step by step as to how I achieved this.

Firstly, I created a very simple rule that simply looks at my own workstations Security.evtx for a 4624 login from my username and
local loopback address as I knew it existed and wanted to see if it appeared in the chainsaw standard out in the terminal amongst it’s
usual built in logic returns.

This was relatively straightforward and I was pleased to see, was successful. I also tested using the –csv switch and successfully
outputted the results .csv including my test rule.

Following my success with this somewhat easy and useless rule, I decided I would use one of Chainsaw’s provided EVTX attack
examples to create the necessary mappings and rules to detect all of the known IOCs from these provided .evtx files. The attack
example I chose was:
[https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES/tree/b947ed80cd67a7413f6689d032eb1151f85f9df6/Command%20and%20Control](https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES/tree/b947ed80cd67a7413f6689d032eb1151f85f9df6/Command%20and%20Control)

The original evtx files were all contained within a folder with a pcap, log files and a README.md. To save the frustration of potential
conflicts or errors when pointing chainsaw at this folder, I moved the evtx files into their own directory leaving me with:
