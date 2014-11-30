aaSplunko
=================

A set of scripts for a system platform object to send data to a [Splunk Enterprise](www.splunk.com) system.

## Motivation

Recently (late 2014) [Kepware](http://www.kepware.com) introduced what they called the [Industrial Data Forwarder](http://www.kepware.com/spec-sheets/industrial-data-forwarder-for-splunk.asp).  I knew at the most basic level that sending data to Splunk was not a difficult matter so that inspired me to write an example object showing you how you can do the same thing from a System Platform object. 

I think there are some huge opportunities for sending some of this data to Splunk in addition to a traditional Historian.  For starters, and apologies in advance to Schneider/Invensys/Wonderware, but the cost of Splunk Enterprise is a fraction of the cost of the Historian.  Yes the Historian may be more efficient at storing data but frankly these days disk space is dirt cheap so that's not a great differentiator any more.  Also the out of the box visualization tools provided with Splunk are really stunning and so much more powerful than anything Wonderware is currently providing.  My general feeling on the topic is that the "rest of the world" has solved some really basic problems and it's time the automation world started to recognize that others are doing some things much better, faster, and cheaper than the proprietary tools we have to slave with.  Yes, the Historian Client is a very nice tool and is very powerful but I suspect with a little HTML5/CSS/jQuery magic someone could produce a web based interface to this Splunk data that does about 95% of what the current Historian client tool does.  It's not so much the cost as it is the cost model.  Should I really pay the same price for a boolean tag that changes 10 times a day vs a floating point that changes every 250ms?  I think WW is on to something with the pricing model for Historian online being user based but still seems odd.  To be fair this does give much more predictable pricing for customers and I can empathize... is it acceptable in Web 2.0 world to rant in a GitHub readme?  Anyway, on  to the good stuff.


## Installation

I am using Elliot Landrums [aaTemplateExtract](https://github.com/aaOpenSource/aaTemplateExtract) tool to extract all of the scripts. Unfortunately it does not yet extract UDA's.  So here is a list of the UDA's and types you need to create to support the scripts.

    _SocketAppDomainName (String)
    CMD.Connect (Boolean)
    Config.HostAddress (String)
    Config.Port (Integer)
    Config.TimestampFormat (String Default = yyyy-MM-dd HH:mm:ss.fff K) (Note the use of this is still a work in progress)
    Flag.Debug.Level (Integer)
    Status.IsConnected (Boolean)
    Value (Float) - This is the value that you will be logging to Splunk.  Obviously you would fine tune for your own needs.

You will also need these declarations for each of these scripts because they are not exported with the aaTemplateExtract tool.  I have added a [TODO](https://github.com/aaOpenSource/aaTemplateExtract/blob/master/TODO.md) for Eliot on this.

- scrConnect
    
    dim vSocket as System.Net.Sockets.TcpClient;
        
scrSendData

    dim vSocket as System.Net.Sockets.TcpClient;
    dim localSB as System.Text.StringBuilder;
    dim ServerStream as System.Net.Sockets.NetworkStream;
    dim StreamWriter as System.IO.StreamWriter;
    dim localTimestamp as System.DateTime;
         
Finally, in the Christmas Spirit I have posted the AAPKG file if you have 2014P01 and just want to download the AAPKG and roll with it.

## Platforms

This code was built on System Platform 2014 P01 but in theory it should work on any flavor of System Platform as long as you have the .Net Framework support.  I have spot checked some of the core pieces like TCPClient and GetStream.  Both have support going all the way back to .Net 1.1 so you should be good for just about any System Platform version.

## TODO List

See my current roadmap and overall [TODO list](/TODO.md)

## Contributors

* [Andy Robinson](mailto:andy@phase2automation.com), Principal of [Phase 2 Automation](http://phase2automation.com).

## Shoutouts to ma Peeps
Big thanks to Brian Gilmore (@BrianMGilmore) of @splunk for lots of help and a kick in the pants to make this happen. 

## License

MIT License. See the [LICENSE file](/LICENSE) for details.
