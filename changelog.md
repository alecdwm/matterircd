# v0.16.5
## New features
* Add support for private channels in slack #142

## Bugfix
* Slack: fixes join/parts #143, #146
* Slack: fixes away #144

# v0.16.4
## Bugfix
* Fix some messages going to &messages #140

# v0.16.3
## Bugfix
* Fix crash on /nick change when not logged in #141

# v0.16.2
## Bugfix
* Remove crash on channel lookup of private messages

# v0.16.1
## Bugfix
* Remove debug code which could cause a crash
* Only append channel name to sender once in &messages

# v0.16.0
## New features
* `-conf` option (for a config file). See https://github.com/42wim/matterircd/blob/master/matterircd.toml.example for an example. Thanks @slowbro for this PR.
* New config file options
   * JoinExclude: an array of channels that won't be joined on IRC.
    Messages that get sent to unjoined channels (but you're joined on mattermost) will
    get sent to the &messages channel.
    You can still /JOIN exclude channels.

    JoinExclude = ["#town-square","#boringchannel"]

    * JoinInclude: an array of channels that only will be joined on IRC.
    If it's empty, it means all channels get joined (except those defined in JoinExclude)
    Messages that get sent to unjoined channels (but you're joined on mattermost) will
    get sent to the &messages channel.

    JoinInclude = ["#devops"]

    * PartFake: a bool that defines if you do a /LEAVE or /PART on IRC it will also
    actually leave the channel on mattermost.
    Default false

    PartFake = true

* don't log passwords used with 'mattermost' and 'slack'. Closes #73

## Bugfix
* Already read messages are replayed again and again #130
* Update to latest mattermost (4.6) libs
* Deprecated flags `-bindinterface` and `-port` removed

# v0.15.0
## New features
* Support mattermost 4.2 and higher (4.x) (use mattermost v4 API)
* Add -mmskiptlsverify option to skip TLS certificate checks on mattermost

## Enhancements
* Display nickname, if set #120
* Replace IRC parsing function with shellwords like function to allow for passwords with spaces. (#8)

# v0.14.0
## New features
* Support mattermost 4.1
* Add initial support for slack

# v0.13.0
## New features
* Support mattermost 4.0

## Enhancement
* Show slack attachments if they have a fallback/contain text
* Show links even when public links are disabled #105
* Edited messages now have "(edited)" appended
* ```-bind ""``` now disables non-tls port-binding when you have ```-tlsbind``` specified #109

## Bugfix
* Long messages from mattermost will be split in multiple smaller messages #103
* Fix join/leave messages for recent mattermost versions #113, #104
* Ignore messages sent to &users #108 
* Ignore posts that have a reaction (emoji) added #111


# v0.12.0
(thanks to @recht matterircd fork)
## New features
* Add KICK support
* Add INVITE support
* Also relay edited messages

## Enhancement
* Show the original message/author after replied messages
* Print timestamp of replayed messages
* Faster startup (joining channels)

## Bugfix
* Do not clear topic on empty /TOPIC command
* Fix various possible panics

# v0.11.6
## New features
* Support mattermost 3.10.0

# v0.11.5
## Bugfix
* Fix crash #97

# v0.11.4
## New features
* Support mattermost 3.9.0
## Enhancement
* Use props instead of ZWSP to check if message comes from matterircd (no more spaces after messages from matterircd -> mattermost)

# v0.11.3
## New features
* Support mattermost 3.7.0 and 3.8.0
## Bugfix
* Make public links (pasted images/attachments) work again

## New features
* Add support for public links in SCROLLBACK and SEARCH

# v0.11.2
## Bugfix
* Use correct status for /WHO #81
* Fix ISON for misbehaving clients #78

## New features
* Support mattermost 3.6.0

# v0.11.1
## Bugfix
* Fix crash on new channel joins #77
* Fix crash on channel join/leaves of other mattermost users #77

# v0.11.0
## New features
* Support mattermost 3.5.0
