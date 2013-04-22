# <center>Transit</center>
### <center>Relayed Query Protocol</center>
---------------------------------------------

__Table Of Contents__
<ol>
<li>
    <strong><a href="#1-introduction">Introduction</a></strong>
    <ol>
        <li><a href="#1.1-master">Master</a></li>
        <li><a href="#1.2-opmode">Operation Modes</a></li>
        <li><a href="#1.3-clients">Slave</a></li>
        <li><a href="#1.4-channels">Channels</a></li>
    </ol>
</li>
</ol>


<div name="1-introduction">
<h2>Introduction</h2>
<br />
Transit is a solution that allows servers to be managed in bulk.  It also lets you query each server specificly for colleting statistics and issuing commands on remote servers.
<br /><br />
It is based on the <a href="http://github.com/substack/dnode">dnode</a> protocol, and also includes HTTP.  The design goal for Transit is to rquire as little configuration as possible.

<div name="1.1-master">
<h3>Master</h3>
<br />
The master is responsible for total coordination of the Transit network.  All slave nodes make a JOIN request to the master, which then attempts to authenticate the slave.  If the authentication is sucuessful than the master will create a connection to the slave node.
<br /><br />
The master is also responsible for things such as message routing.  The master hosts <abbr title="communication channels">channels</abbr> which the buffer messages recieved from the slave nodes.  
