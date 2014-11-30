aaSplunko
=================

A set of scripts for a system platform object to send data to a [Splunk Enterprise](www.splunk.com) system.

## Motivation

Recently (late 2014) [Kepware](http://www.kepware.com) introduced what they called the [Industrial Data Forwarder](http://www.kepware.com/spec-sheets/industrial-data-forwarder-for-splunk.asp).  I knew at the most basic level that sending data to Splunk was not a difficult matter so that inspired me to write an example object showing you how you can do the same thing from a System Platform object. 

## Installation

I am using Elliot Landrums [aaTemplateExtract](https://github.com/aaOpenSource/aaTemplateExtract) tool to extract all of the scripts. Unfortunately it does not yet extract UDA's.  So here is a list of the UDA's and types you need to create to support the scripts.

- _SocketAppDomainName (String)
- CMD.Connect (Boolean)
- Config.HostAddress (String)
- Config.Port (Integer)
- Config.TimestampFormat (String Default = yyyy-MM-dd HH:mm:ss.fff K) (Note the use of this is still a work in progress)
- Flag.Debug.Level (Integer)
- Status.IsConnected (Boolean)
- Value (Float) - This is the value that you will be logging to Splunk.  Obviously you would fine tune for your own needs.

You will also need these declarations for each of these scripts.


- scrConnect

>     dim vSocket as System.Net.Sockets.TcpClient;
    
scrSendData

    dim vSocket as System.Net.Sockets.TcpClient;
    dim localSB as System.Text.StringBuilder;
    dim ServerStream as System.Net.Sockets.NetworkStream;
    dim StreamWriter as System.IO.StreamWriter;
    dim localTimestamp as System.DateTime;
         
## Platforms

This code was built on System Platform 2014 P01 but in theory it should work on any flavor of System Platform as long as you have the .Net Framework support.  I have spot checked some of the core pieces like TCPClient and GetStream.  Both have support going all the way back to .Net 1.1 so you should be good for just about any System Platform version.

## TODO List

See my current roadmap and overall [TODO list](/TODO.md)

## Contributors

* [Andy Robinson](mailto:andy@phase2automation.com), Principal of [Phase 2 Automation](http://phase2automation.com).

## License

MIT License. See the [LICENSE file](/LICENSE) for details.
