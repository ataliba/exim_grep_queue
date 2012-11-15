exim_grep_queue
===============

A simple plugin for nagios to search for a string on exim queue

-------------------------------------------------------------------------------------------


This plugin is very easy to use on your nagios 

First, you need the python installed on your system and the nrpe ( the remote execution program from nagios ). 

Put this on a directory of your operational system ( on this example i put the plugin on the /usr/local/bin ) 
and configure your nrpe to use this command. 

The script has this arguments to use in your nagios/nrpe : 

-S -> the string you need to search on exim queue
-c -> the critical level for this monitoringo on nagios 
-w -> the warning level of this monitoring on nagios 

For example if I need to monitor the queue for yahoo.com.br I use this : 

/usr/local/exim_grep_queue -w 20 -c 100 -S yahoo.com.br 

If I need to monitor a user on my system, I use this : 

/usr/local/exim_grep_queue -w 20 -c 100 -S user@mydomain.com 

To use this plugin you need to put a line like this on your nrpe.cfg: 

command[check_string]=/usr/local/bin/exim_grep_queue -w 5 -c 30 -S string.com.br

On the source code of the script change this line to your path of exiqgrep : 

# Change this for your path of Exiqgrep 
Exiqgrep=/usr/sbin/exiqgrep

And on your suoders file put a line like this ( using the same path you put on the source code ) : 

%nagios ALL=(ALL)   NOPASSWD:/usr/sbin/exiqgrep

If your nrpe runs on another group, change the %nagios option. 

And on your nagios configure a service to get this information of this instance on 
nrpe. 

If you have a doubt about the use of this script go to this page  ( http://cerebro.freeshell.org/log/plugin-for-nagios-exim_grep_queue/ ) or 
open a request here on github. 


