# JS8Call Net Check In Protocol <!-- omit from toc -->

## Table of Contents <!-- omit from toc -->

- [Version History](#version-history)
- [1. Introduction](#1-introduction)
- [Important: verify that you do NOT check the box “Allow sending standard messages without callsign” – the automated sign-in to the net depends on your station always transmitting your call sign.](#important-verify-that-you-do-not-check-the-box-allow-sending-standard-messages-without-callsign--the-automated-sign-in-to-the-net-depends-on-your-station-always-transmitting-your-call-sign)

## Version History

This document was oroginally found at [here](https://qsl.net/nf4rc/2021/ProposedNetCheckInProtocolV100.pdf)

- Version 1.0 Jan 1, 2021 G. Gibby (with revisions from Ross Merlin)
- Modified by Phillip Jubb VK6DEV 2024

      Quick start: The typical station operator will only need to configure their station (Appendixes 1 and 2) and read sections “1.
      Introduction” and “2. Check-in Protocol”. The rest of the 
      information pertains mainly to Net Control Stations but is included
      to allow participants the full view of the process.

## 1. Introduction

Why pursue this?

Radio net operations often start by taking check-ins – the net control
station finds out which stations are on the frequency and acknowledges that
their presence is known. This takes a lot of time, especially for weaker
stations who cannot be heard over the stronger stations. It’s even worse
when participating stations can’t hear the primary net control and only
occasionally get instructions from the alternate net control! Typically,
stations are acknowledged one at a time, then the net control stations
repeats the invitation for more stations to check-in, etc. JS8Call software
allows for many stations to check-in at the same time by spreading narrow
digital signals throughout the same passband that would accommodate only one
voice signal at a time—and all with advanced digital modulations offering
dozens of dB advantages over voice telephony. This paper discusses features
for the net control station to receive and acknowledge the stations
checking-in, and the features and procedures for net members to check-in
using JS8Call. This has been developed for use in U.S. Government SHARES HF
radio nets but could be used in amateur radio and other operations.

### Bandwidths and approximate speeds available in JS8Call

| Mode Speed | Frame Time |Bandwidth | Approximate Speed in WPM | SNR limit (approx) | Approx advantage of VOICE (assuming 6dB required for voice) |
|---|---|---|---|---|---|
|Slow | 30 seconds | 25 Hz |8 WPM |-28 dB | 34 dB |
|Normal | 15 seconds | 50 Hz | 16 WPM | -24 dB |30 dB (1000-fold) Primary mode for primary Net Control and participating stations |
|Fast | 10 seconds | 80 Hz | 24 WPM | -20 dB | 26 dB|
|Turbo| 6 seconds | 160 Hz | 40 WPM | -18 dB | 24 dB (> 200-fold) Primary mode for backup Net Control |

ß
       Step One: Software Download: http://files.js8call.com/latest.html Available for operating systems:
• MacOS
• Windows
• Raspberry Pi • Linux
Open and install.
1
   Changes required for U.S. Amateur Radio usage will be added as footnotes.
JS8 Net Protocol 2 01/01/2021

Step Two: Getting your RADIO connected
Configuration suggestions to get your RADIO connected are contained in Appendix One. Anyone who has used FT8 or a soundcard-based digital modulation will find this familiar.
Step Three: Getting your Software Configured for Automatic Replies
Configuration suggestions to get your SOFTWARE configured for the necessary procedures are contained in Appendix Two. These settings are very important for smooth operation of the net. The Appendix provides step by step instructions with screen shots. This will take a few minutes but will result in check-ins becoming almost completely automatic for the participant – Net Control issues a directed call and your station will automatically check you in! More advanced operators may wish to add CAT control of their radio, which is derived from WSJT-X and well in JS8Call. This process may be quite familiar to many operators from Field Day or DX-chasing (Amateur Radio activities).
Step Four: Familiarization With The Screen
Throughout this document, the following “anatomy” terms of the screen display will be used:
      Recommended documentation: “JS8Call Guide”
https://docs.google.com/document/d/159S4wqMUVdMA7qBgaSWmU-iDI4C9wd4CuWnetN68O9U/ edit
(34 pages)
Step Five: Technique for Time Synchronization
If you have done any FT8 work, you already understand how to do this. There are ways to sync using Windows time change screen, but I use a freebie program “Dimension 4” for this purpose:
  JS8 Net Protocol 3 01/01/2021

Download: http://thinkman.com/dimension4/d4time531.msi
Home Page: http://thinkman.com/dimension4/
and I’ve allowed it to override the internal Windows systems. You only need to sync once before each net; the synchronization will remain “good enough” for many hours. Alternatively, as you’ll read below and in Appendix Three, JS8Call provides a way for you to click when you see other stations starting, or stopping their transmissions, allowing you to sync even without the Internet. Getting within a second or so is adequate.
If you have ever operated FT8 (e.g. Field Day, DX), the JS8Call application is very quick to learn. A few additional features:
• JS8Call includes an ability to sync manually by pressing a mouse button either when the beginning or end of other stations’ calls are heard. This allows sync even when no Internet is available to reach traditional time servers. (See instructions & illustration in Appendix Three.)
• JS8Call includes directed commands that can receive automated replies from other stations, including querying for SNR (signal to noise ratio), GRID location, STATUS, what stations the other station is HEARING, and MESSAGE which allows you to request another station to relay for you: e.g. KN4CRD>DR4CNK>HELLO! (will send message to DR4CNK through receiving station KN4CRD) and multiple other Commands.
• As configured in Appendix Two, your station will automatically respond correctly to commands from the primary Net Control Station to check into the net.
   JS8 Net Protocol 4 01/01/2021

2. Net Check-in Protocol: Participants
General principles
• Assumes stations are operating in a directed net, with primary and backup net control stations
(NCS).2
• Everyone uses upper sideband; this allows you to hear the voice communications without any
changes to your radio and simultaneously use digital communications. (Some radios may pick up extraneous microphone audio, so avoid loud noises or speaking while your station is digitally transmitting if this is the case with your radio.)
• Reserve audio frequencies 500-999 for NCS.
• Use audio frequencies 1000-2499 (1500 Hz) for remainder of stations.3
• Utilize directed calls as much as possible, so net check-ins are made automatically.
• Begin with primary NCS using NORMAL frames (15 seconds, 50 Hz bandwidth) and backup
NCS using TURBO mode (6 seconds, 160 Hz).
• Backup NCS avoids using directed calls, to prevent their station being additionally addressed
by participating auto-stations.
• ALL check-in stations use NORMAL mode (15 second frames, 50 Hz bandwidth) as using
faster modes reduces the available bandwidth for others to check in.’
READER’S DIGEST VERSION OF TASKS FOR STATIONS TO CHECK IN
    TIME
ACTION
COMMENT
Before the Net
Check that your station is configured properly:
1. Set to transmit NORMAL mode (Main Menu: MODE | Click “JS8 (Normal...”)
2. Set to decode all speeds simultaneously (Main menu bar: MODE | Click “Enable simultaneous decoding of all speeds”)
3. Transmit audio window offset frequency (red box) set appropriate for your last letter of your call sign.
The transmit audio window you choose is semi-random, but depends on whether your call sign ends in a letter or a number:
Those ending in a LETTER:
Pick an audio frequency (left edge) roughly in line with the following groups:
1000-1450 A-G 1500-1950 H-O 2000-2450 P-Z
Those ending in a NUMBER:
1000-1450 1,2,3 1500-1950 4, 5, 6 2000-2450 7, 8, 9, 0
     2
3
Backup Net Control is optional but easy to do in JS8Call because both stations can transmit simultaneously, something that is difficult with voice nets.
Testing has demonstrated that with some radios, audio frequencies as low as 200 Hz and as high as 3000 Hz may be usable.
JS8 Net Protocol 5 01/01/2021

     These are not rigid but are designed to spread out stations in the audio passband, and may be adjusted by NCS or leadership as needed
Before the net
Test that you can transmit by briefly executing a TUNE and observing your power output on a suitable monitor/meter. The TUNE button is at the upper right-hand side of your JS8 software screen.
Don’t forget to deselect the TUNE after a few seconds. Observe that your TX button goes RED when you are transmitting.
During the net
Your station should AUTOMATICALLY reply and check in when any one of the Call Sign Groups that you specified when configuring your JS8Call software [Appendix Two] are called up by the Net Control Station.
Observe the application and verify that it does check in. If there is a problem, you can try again after the primary NCS lists all the call signs or suffixes heard.
When Primary NCS lists call signs or suffixes of stations heard
If you do not see your call sign or suffix listed, type your call sign in the transmit pane at the appropriate time, and press SEND to allow it to be sent again
Throughout net
Observe instructions of the NCS and transmit when requested
     JS8 Net Protocol 6 01/01/2021

3. Net Check-inn Protocol: Net Control Stations
Net Control Stations will benefit from installing the custom application developed to capture all stations checking in for them. See Appendix Four for information on this application.
Within SHARES, you can easily and quickly alternate between VOICE and DIGITAL on the same frequency with generally the same settings of your transmitter. 4
This allows you to make voice introductions to the net, and then intersperse digital check-ins. Remember that due to skip-zone, D-layer absorption and other atmospheric issues, it is likely that some potential participants are not hearing you well enough to comprehend! These same participants may possibly hear a digital call-up due to the many dB advantage, but that isn’t guaranteed either. However, using JS8Call both the Primary and Backup NCS can simultaneously provide instructions.
To avoid confusion, in the following suggested Protocol, only the Primary NCS issues Directed Calls that will create an automated response (therefore all automated check in’s will address the Primary NCS call sign). The Backup NCS in this protocol uses simple text messages, but at TURBO speed to provide more detailed information for those who can only hear the backup NCS.
Call Sign Groups
If the net control were to initiate a directed call for check-ins from the entire group at once, it is likely that some nets would be overwhelmed by 30+ simultaneous check-ins. To avoid this, pre-determined “call sign groups” are created and each member is asked to add the appropriate groups in their own configuration. Call sign groups include @SHARES (everyone), those based on the STATE of the participant, and those based on a characteristic of their call sign (principally the number of numerical digits). These groups will show up in the right-hand side list of group/stations on JS8Call. To address one of these groups (or an individual callsign) one left-clicks the desired group and then right-clicks to get options for directed calls.
       Amateur radio-based nets will obviously choose different call sign groups depending on the makeup of their net. For example, a state net might divide stations by regions of the state.
      GROUP
MEANING
@SHARES
All SHARES stations of any type
@1NUM
Participating stations with 0 or 1 number in their call sign
@2NUM
Participating stations with 2 numbers in their call sign
@3NUM
Participating stations with 3 or more numbers in their call sign
      4
Other than selective calling tones, US Amateur Regulations do not allow concurrent data operations on voice frequencies. If it is desired to implement this net Protocol on an Amateur Radio voice net, utilizing two frequencies may be the best option – one within the RTTY/Data segment of a band, and the other within the Phone/Image segment. (See: http://www.arrl.org/files/file/Regulatory/Band Chart/Band Chart 8_5 X 11 Color.pdf ) Many transceivers provide A/B VFO control which can make switching between the two frequencies simpler.
 JS8 Net Protocol 7 01/01/2021

To make it easy to address these pre-determined call sign groups, the primary NCS must have the following Call Sign Groups as part of their configuration:
@1NUM @2NUM @3NUM @SHARES
However, it is also possible for a net control station to simply type into the transmit buffer pane a message creating a directed call to a group. For example
@1NUM SNR?
when transmitted will cause that call sign group to respond with SNR (signal to noise ratio) measurements, just as if the net control had selected the @1NUM group, and right clicked to send a directed message “SNR?” to that group.
      Seque nce
Approx imate Time (Begin)
Required Time
Action
NOTES &
Left Edge of Frequency Slot
1
0:00
45 sec
OPTIONAL
NET ANNOUNCEMENT & Emergency/Priority message solicitation (45 seconds)
A voice net call-up may precede the digital call up to any degree desired within the SHARES system where digital and voice can be used on the same frequency.
Primary and backup NCS should both have their time services properly synchronized to the same time.
Digital Transmission:
Primary NCS (NORMAL)
SH DIG CKIN – EM/PR TFC LIST NOW
-or-
ZKE EM/PR TFC
Backup NCS (TURBO)
SH DIG CKIN – EM/PR TFC
LIST NOW
-or-
ZKE EM/PR TFC
Net Control: Left edge at 800 Hz (uses 800-850 Hz), NORMAL mode
Backup Net Control: Left edge at 500 Hz (uses 500-660 Hz in TURBO mode)
By keeping these two stations away from the reply frequencies of all the others, their transmissions are more likely to be observed properly.
The suggested frequencies allow for substantial frequency inaccuracy on the part of participating stations without overshadowing the NCS.
    JS8 Net Protocol 8 01/01/2021

      Seque nce
Approx imate Time (Begin)
Required Time
Action
NOTES &
Left Edge of Frequency Slot
2
0:45
30 sec
Recommend waiting two full frames (30 seconds) for any emergency / priority traffic listing to begin. During this time, primary and backup NCS can ready their call ups.
During this time, the NCS can ready their next transmissions so that there is no wasted time.
3
1:15
30sec
CHECK IN CALLUP #1
Primary NCS issues directed call for group 1NUM 5
@1NUM SNR? (approx. 30 sec) (Note: this is done by clicking the @1NUM group, right clicking to reach directed calls, and selecting SNR?)
Backup NCS will transmit:
1NUM CHKIN
-or-
1NUM ZKE (approx 18 sec)
4
1:45
15 sec
Replies at NORMAL speed (15 second frames)
Stations with no digit or 1 digit in their call sign respond to group 1NUM. They should pick an audio frequency (left edge) roughly in line with the following ranges based on the last character of the call sign:
1000-1450 A-G, 1, 2, 3 1500-1950 H-O, 4, 5, 6 2000-2450 P-Z, 7, 8, 9, 0
E.g., a station like AAR1AG would choose toward the upper end of the range of 1000-1450.
        5
US Amateur nets might prefer to use Call Sign groups based on States, Regions, or as some voice net do, arbitrary assignment to “days of the week”. Any set of call sign groups that fits the purposes of the Net and divides the likely responses into group of 10-15 should be useful.
JS8 Net Protocol 9 01/01/2021

      Seque nce
Approx imate Time (Begin)
Required Time
Action
NOTES &
Left Edge of Frequency Slot
NCS: Don’t worry about copying all these stations down as our software application will capture the reply stations for you.
5
2:00
30 sec
CHECK-IN CALL-UP #2
Primary NCS issues directed call for group 2NUM stations, all of which have two digits in their call sign (e.g. KGD34 or NF01XY)
@2NUM SNR? (approx 30 sec)
Backup NCS will transmit:
2NUM CHKIN
-or-
2NUM ZKE (approx 18 sec)
NCS: If you aren’t using the NetControlJS8 software, during this 30 second call up, make a list of all the stations that checked in on the first call- up.
6
2:30
15sec
2nd Group Replies at NORMAL speed (15 second frames)
Stations with 2 digits in their call sign respond to group @2NUM. They should pick an audio frequency (left edge) roughly in line with the following ranges based on the last character of the call sign: an (left edge) audio frequency roughly in line with the following groups:
1000-1450 A-G, 1, 2, 3 1500-1950 H-O, 4, 5, 6 2000-2450 P-Z, 7, 8, 9, 0
E.g., a station ending in 1 or A might choose 1000 or 1050 while a station ending in 0 (zero) or Y might choose 2400 or 2450
7
2:45
30sec
CHECK-IN CALL-UP #3 (final for this
NCS: (if not using
       JS8 Net Protocol 10 01/01/2021

      Seque nce
Approx imate Time (Begin)
Required Time
Action
NOTES &
Left Edge of Frequency Slot
example)
Primary NCS issues directed call for group 3NUM stations, all of which have three or more digits in their call sign (e.g. NCS123 or KD8973 or WPQR876)
@3NUM SNR? (approx 30 sec)
Backup NCS will transmit:
3NUM CHKIN
-or-
3NUM ZKE (approx 18 sec)
NetControlJS8 software) during this call up, copy down the stations that replied in the 2nd group.
8
3:15
15 sec
3rd Group Replies at NORMAL speed (15 second frames)
Depending on whether their call sign ends in a letter or a number, audio frequencies for reply are chosen as above
9
3:30
30sec
Delay dead time for NCS to complete list of stations heard.
Using Rick McDonald’s NetControlJS8 software, this is completely simple: just click the button “Send ALL” and your transmit buffer is automatically filled with ALL of the call signs that have been received. See Appendix Four.
If using the NetControlJS8 software, this time delay can be completely eliminated.
If desired NCS can have their station transmit STANDBY
10
4:00
60 sec
To save time, NCS can optionally switch to TURBO mode, which is approximately 40 wpm.
Primary NCS sends call signs of all stations heard. Everyone copies this, including backup NCS.
Time may vary depending on number of stations checked in
       JS8 Net Protocol 11 01/01/2021

      Seque nce
Approx imate Time (Begin)
Required Time
Action
NOTES &
Left Edge of Frequency Slot
Expected time for 20 check-ins: 1 minute @ TURBO speed.
1
5:00
15 sec
Optional expected 15 seconds for backup net control and others to conclude they need to supply additional station names that were missed. Stations that were HEARD keep silent
Thinking and execution time.
Backup NCS can simply execute the button SEND ALL on their own copy of NetControlJS8 and compare the list to that transmitted by Primary NCS – both are alphabetized – noting any that were missed.
12
5:15
30 sec
Backup NCS and other stations reply at NORMAL or faster speed with any stations that were missed.
13
5:45
30 sec
Primary NCS concludes the digital check-ins:
CHKIN DONE ## STNS
(replace ## with the number of stations that were heard)
14
6:15
FINISHED
NCS can now make a voice announcement that the digital check-in process has been completed and note the number of stations that were checked in.
(Can be reduced to under 6 minutes if emergency/priority check is not required.)
        Optional Reference Information for those interested in other approaches to data-based nets:
Whitepaper on NBEMS and net operation: http://w1hkj.com/usercontrib/K3EUI_NBEMS_nets.pdf Whitepaper on NBEMS and south-east Florida nets: https://fparc.org/du/docs/30.D.pdf
Philosophy of NBEMS emergency traffic: https://www.jeffreykopcak.com/tag/nbems/
   JS8 Net Protocol 12 01/01/2021

4. Suggested Protocol for Sending Bulletins from NCS
Both Primary NCS and backup NCS can send the same bulletin simultaneously. They may wish to send it as a directed message to @SHARES. Since they are on different frequency offsets, their messages will aggregate separately in the Band Activity pane
Presuming that most participants can hear one or the other of the primary and backup net control stations well, they may wish to send bulletins at a faster speed than NORMAL (15 sec frames). FAST mode offers approximately 24wpm and TURBO offers 40 wpm.
JS8 Net Protocol 13 01/01/2021

5. Suggested Protocol for Moving Traffic Between Net Participants
Situation: Station A lists traffic that Station B needs to receive.
    Step
Action
Comment
1
NCS directs a call to Station A to determine if they
are hearing Station B
QUERY CALL [CALL SIGN]?
(There is a directed message to accomplish this)
2
NCS directs a call to Station B to determine if they are hearing Station A, and in the process recognizes whether they are on suitably separated frequencies
QUERY CALL [CALL SIGN]?
Note the reply frequency of Station B and determine whether it is suitably separated from Station A for Normal or a faster transfer.
3
NCS instructs Station A to send their message to Station B, after requesting any change in frequency necessary. 6
TO DO: work on suggestions on how to negotiate faster speeds.
4
Once the transfer is begun, the NCS can move on to other duties ...
... since NCS is on a completely separate frequency.
5
At some point later, NCS requests of net if there is other business: OTH BUS?
6
If A and B have completed their transfer, at such an invitation by NCS, they each reply
QRU or DONE
(meaning they have nothing more)
          6
For US Amateur radio nets, the NCS can simply assign an offset frequency which may be completely out of the current passband, for the two stations to use. Depending on net common practice this might be as simple as “QSY DWN 3 QPSK31” or “QSY DWN 3 WL VARA” for example. Procedures will vary by net.
JS8 Net Protocol 14 01/01/2021

Techniques for moving the traffic:
    #
Message Passing Technique
Advantages / Disadvantages
1
Simply send as text using JS8 NORMAL mode.
Slow, but excellent ability to capture text. ICS-213 can be easily “encapsulated” as a radiogram or just sent as field: contents and so on until completely transferred.
2
Use JS8 but move to faster frames
Uses more bandwidth but since other stations probably don’t need to transmit in the “participant station” portion of the SSB bandpass, this shouldn’t cause any problem. With 1500 Hz available (1000Hz-2500Hz) as many as EIGHT simultaneous transfers could occur while net controls are still running the net, and those transfers would be moving as fast as 40 wpm (twice as fast as people can hand copy). Still just plain text (no fancy “forms” available)
3
Participants switch to using FLDGI suite of software and utilize any narrow technique, including those that include ARQ error correction. A significant advantage for SHARES and EMCOMM nets is the ability to move typical FEMA / ARC FORMS easily using built-in systems of this suite.
Using a technique with only 250 Hz bandwidth or less can allow error-free communications of message including the use of “forms” by using higher level layers of the FLDGI suite, such as FLMSG etc.
This requires significantly more sophistication, training and coordination than many participants may have at this time.
4
Participants may switch to peer-to-peer WINLINK narrowband (500 Hz) techniques 7 A significant advantage for SHARES and EMCOMM nets is the ability to move typical FEMA / ARC FORMS easily using built-in systems of this suite.
Important that the participants know how to configure for NARROW (500 Hz) techniques, otherwise they may cover up the entire net with a wideband technique! (See the Figure below for an example).
This technique fits in well with the SHARES digital WINLINK techniques that many participants already know how to utilize. Allows passing of formal ICS forms with ease.
        7
These instructions were written for SHARES nets, which are constrained in channelized frequencies. Amateur Radio nets can simply utilize multiple alternate frequencies, often taking advantage of “panadapter” views to recognize available empty frequencies, and dependent on current state of regulations, can use wider bandwidths and faster transmission speeds.
JS8 Net Protocol 15 01/01/2021

Example of how to set up WINLINK PEER TO PEER ARDOP for transmitting messages within a small section of the SHARES audio passband.
Ensure that the station’s ARDOP TNC is set for narrow (500 Hz) communications:
 JS8 Net Protocol 16 01/01/2021

Example Explanation of How to Setup WINLINK PEER TO PEER VARA HF for Transmitting Messages Within a Small Section of the SHARES Audio Passband.
 JS8 Net Protocol 17 01/01/2021

Adjusting Station Frequency to Allow Multiple Simultaneous WINLINK Message Transactions8
WINLINK communications systems are typically set for a Center Frequency of 1500 Hz within the passband (whereas WSJT-X, JS8Call and FLDGI allow the user to select which portion of the passband to use for their transmission). Thus a 500 Hz communication would utilize 1250-1750 passband. If there is only one message to be transacted between network participants at a time, this will work well and requires no changes by the participating stations in their dial frequency (net frequency). This is far from the Net Control reserved band (500-999 Hz).
However, if desired, up to three simultaneous WINLINK peer to peer transmissions can occur by having stations alter their DIAL FREQUENCY temporarily only to establish WINLINK peer to peer connection and move the traffic. The following table illustrates the frequency assignments the Net Control might issue to coordinate these simultaneous transactions.
     Simultaneous message passing #
Audio passband to be utilized from the normal net upper side band dial frequency
Adjustment to station frequency needed by the two participant stations
When finished with message passing
#1
1000-1499 (center 1250)
Adjust dial frequency 250 Hz lower than standard net frequency.
Return to normal net dial frequency and re- utilize JS8Call
#2
1500-1999 (center 1750)
Adjust dial frequency 250 Hz higher than standard net frequency
Return to normal net dial frequency and re- utilize JS8Call
#3
2000-2499 (center 2250)
Adjust dial frequency 750 Hz higher than standard net frequency
Return to normal net dial frequency and re- utilize JS8Call
       8
the frequency for two stations to QSY (move) to.
These instructions are unnecessary for US Amateur nets, where the net control can simply identify by Dial or Center, JS8 Net Protocol 18 01/01/2021

Appendix One: Getting your RADIO Connected in JS-8Call
Notation:
FILE | SETTINGS means click the menu bar option “FILE” and then click the submenu item “SETTINGS” Similar nomenclature will be used throughout this document.
DISCLAIMER
My experience with getting CAT / flrig / similar rig control systems to work properly is limited. If you have successful experience getting WSJT-X to control your rig, you are likely to succeed with this software as well. I have often preferred to merely get the modulations to be created, transmitted, received, and detected, and set the frequencies for JS-8 manually, on the radio itself. Thus the “displayed frequency” on my JS8Call software will be meaningless. However, it isn’t difficult to set up full CAT control of frequency, and PTT on many modern radios, and this has worked well on my ICOM 7300.
I utilize a SignaLink (or similar homebrew sound card systems) for connection to older transceivers. Connections for modern transceivers with integral soundcard systems may be different.
For simple systems, using SignaLink-type systems:
 JS8 Net Protocol 19 01/01/2021

FILE | SETTINGS | “Radio” tab
• Rig: leave set to None
• Rig Options Tab: PTT Method: check “VOX” - causes SignaLink to handle the
push to talk (PTT) line
• Tx Delay: leave at default of 0.2 seconds
• Suggest that you do NOT check the box “Hold PTT between frames....”
FILE | SETTINGS | “Audio” tab
• Modulation Soundcard: Select your soundcard in both the “input” and “output” lines; often the soundcard will have the word “codec” or “USB” or similar in it as a give-away. For rigs with internal soundcard, there may be a portion of your radio in the name.
• Notification Soundcard: Leave this set to your computer’s internal audio system, so that you can hear notifications.
Click OK to exit. The settings are automatically saved.
Obviously, users who have more advanced radios, and those with significant experience with WSJT-X and similar systems may have to make more advanced settings to fully utilize the capabilities of their radios beyond the “basic” settings above. For example, we were able to select ICOM 7300 and fully configure CAT control at our local EOC.
 JS8 Net Protocol 20 01/01/2021

Setting Receive Audio Signal Level
Verify that when signals are present in the audible passband of your receiver, they are visible in the WATERFALL.
Verify that the INPUT AUDIO LEVEL (lower left-hand bar graph of the screen) is somewhere around the “middle” of the bar graph (green display), not too high, not too weak. If necessary, adjust your RF gain and if necessary adjust WINDOWS or other operating system microphone controls until you have an adequate input signal.
Setting Transmit Audio Signal Level
A single sideband transmitter does not produce any output (other than a well-suppressed carrier) if there is no microphone audio. With increasing audio input, the output signal should also rise linearly. Do NOT use “compression” with digital modes such as JS8. It is recommended to set your transmitters “power” level for a high level (e.g. 100 watts) and then adjust your actual transmitted signal level with the audio controls of your SignaLink / JS8 software. This allows the greatest linearity of your system.
TUNE – in the upper right-hand portion of your JS8Call software there is a TUNE button. When pressed, your station should go into TRANSMIT mode. Using your mouse in the WATERFALL area, select an audio offset frequency in the mid portion of the passband (e.g. 1500 Hz) and on a suitable frequency, connected to a good antenna or dummy load, on a non-busy channel, press TUNE and verify that your station goes into TRANSMIT. Adjusting the Transmit Audio Level slider on the bottom right of JS8Call software, in conjunction with your SignaLink TX GAIN (or equivalent software control on a more advanced transmitter), arrange for your transmitted output power to be approximately HALF of your station's full power output. Example: if you have set your transmitter for 100 watts, adjust these gain controls for approximately 50 watts of output power. Do not TUNE for more than about 10 seconds at a time. DE-select the TUNE option when not tuning.
JS8 Net Protocol 21 01/01/2021

Appendix Two:
Configuring Software for Net Check-In
There are several settings that we recommend for optimal usage of this advanced software.
Call sign and Privacy
  FILE | SETTINGS | General | Station | Station Details
• Enter your SHARES call sign (NOT an amateur radio call sign!)
• Maidenhead locator: you may wish to leave this blank for anonymity
• Call sign Groups: This will be used to “group” your station for orderly check in, and
your regional or national net may have specific instructions. Multiple entries are possible separated by commas. These can be no longer than 8 characters. These allow net control stations to request entire groups to log in simultaneously and significantly speed operations.
JS8 Net Protocol
22 01/01/2021
◦ ◦
◦ ◦
As a “default” please enter @SHARES as your first group.
Additionally, add a designator for your STATE, e.g, @SHARESFL if you are in Florida (use 2 capital letters, United States postal abbreviations), unless prohibited by your agency’s OPSEC (operational security) requirements;
Additionally add one designator for your FEMA REGION (see: https://www.fema.gov/about/organization/regions) e.g., @REG4 for persons in the southeastern area of the country that is FEMA Region 4, unless prohibited by your agency’s OPSEC (operational security) requirements;
Choose the appropriate one of the following three designators based on the number of digits in your call sign. It is likely that this will be a primary means of distributing check ins into groups, so this is important!
▪ ▪
@1NUM if there are no digits or 1 digit in your call sign @2NUM if there are 2 digits in your call sign

Transmit Your Callsign
▪ @3NUM if there are 3 or more digits in your call sign
◦ Your regional leadership may additionally break their region into groups, such as @SE1, @SE2 for Southeast groups 1 and 2 in the Southeastern net, for example. Look for specific instructions from your regional leadership.
  SETTINGS | General | Behavior
Important: verify that you do NOT check the box “Allow sending standard messages without callsign” – the automated sign-in to the net depends on your station always transmitting your call sign.
------------------------------------
Networking & AutoReply
For most efficient operation of our nets, your station should be configured to automatically reply to requests.
FILE |
 JS8 Net Protocol 23 01/01/2021

 FILE | SETTINGS | General | Networking & Auto reply
• Set your check boxes as shown in the figure above.
◦ Check “Turn autoreply on at startup”
◦ Uncheck “Ask for confirmation before sending autoreply transmissions”
◦ Using the “down” button, take the “Idle Timeout – disable autoreply after:” (last
option) all the way to 0.
JS8 Net Protocol
24 01/01/2021

Reporting
In general, we do not want our SHARES stations creating automated reports to outside systems, so we turn OFF reporting:
FILE | Settings | Reporting
• Leave the alternate operator call sign BLANK
• Uncheck “Enable spotting to reporting networks (JS8NET, PSKReporter, etc)”
• In the API area, unless you have specific instructions, do not allowing setting station
information from the API (box unchecked)
  JS8 Net Protocol 25 01/01/2021

Mode
Set your station to send at normal 15-second frame speed but be able to decode all speeds (unless you have an extremely slow computer) and to be able to participate in the heartbeat (HB) automatic reply system.
Experiments have suggested that there is a benefit in the learning phase to have Heartbeat acknowledgment also enabled:
Mode
  • Check options as show in the figure above.
• In the subsection of Decoder Sensitivity, start with 3X 3 Decode passes.
JS8 Net Protocol 26 01/01/2021

Control
  Enable the Receiver and Transmitter, but not Spotting.
As a check, your status buttons at the upper right hand side of the JS8Call application should look like this:
Receive is Enabled.
Transmit is Enabled
Normal speed
Decoding multiple different speeds AUTO response is enabled Participating in Heartbeat.
 JS8 Net Protocol 27
01/01/2021

VIEW
  Set your VIEW settings as shown in the Figure above.
Recommend sorting band activity by “Last heard timestamp (recent first)”, which will allow you to see responding stations at the TOP of the leftmost of the viewing panes.
JS8 Net Protocol 28 01/01/2021

Appendix Three:
Additional Information on Time Synchronization
The easiest method for my time synchronization has been to install the “Dimension 4” application and give it rights to override Windows internal time sync.
However, JS8Call provides a way to sync even if you have no Internet available. Over in FT8 land of amateur radio (typically 74 kHz up from the bottom of any active band) there are a plethora of every- 15-seconds FT8 signals, and JS8 provides buttons that allow you to use the mouse to select at either the BEGINNING of their transmission or END to sync your clock adequately. We have routinely practiced this technique at our EOC and it works well.
The buttons appear somewhat differently in different versions of JS8Call but in the most recent version they are accessible to the right of the Waterfall - see section outlined in red under “Timing”.
Although the FT8 signals may not decode, once you’re synchronized you can see them fit correctly in your waterfall and when you return to JS8 communications, decoding should be successful.
 JS8 Net Protocol 29 01/01/2021

Appendix Four:
Net Control Station Setup
A special application has been created to assist Net Control Stations (both primary and backup) with collecting and reporting the stations that check in. Jordan Sherer, the creator of JS8Call, encouraged our effort to find a volunteer who could take advantage of the hooks provided in the JS8Call Application Programmer Interface (API) and thankfully Rick McDonald stepped forward to help us! Note: Current version of this software is 004.
This software is custom built by a volunteer and isn’t commercial grade (yet). You’ll be given a link where to download this software. As you might expect, your Microsoft virus checker may complain but our experience so far is that it is perfectly safe.
Using Windows “Extraction” techniques, extract the application from the zip file in which it comes, and install it in a suitable place on your computer. I suggest creating a directory
C:\SHARES
and allow it to install within that directory. It will create its own subdirectory and inside that subdirectory you’ll find the file
NetControlJS8v00X.exe
If you right-click that file, you can select the option “Send to Desktop (create shortcut)” and create an icon on your Desktop for easier access in the future.
UDP – Connections
This software connects via internet-protocol (IP) message datagrams of the UDP variety, for highest speed. For this to work, Net Controls must additionally modify their “Reporting” settings to allow UDP connections on port 2242 (different from the default):
JS8 Net Protocol 30 01/01/2021

 FILE | Settings | Reporting
Within
• Check the box to “allow setting station information (Grid, Info, Status, etc) from the
APIs
• Leave the UDP Server Hostname as 127.0.0.1 (your own computer)
• UDP Server Port: 2242
• Check the Box “Enable UDP Server API”
• Check the Box “Accept UDP Requests”
NOTE: The program must be stopped and restarted for these changes to take effect.
When both JS8 and the NetControlJS8 application are running, they establish a connection internally and then as stations show up within your receive list, you will see them populating on the Net Control Application:
the API paragraph:
JS8 Net Protocol 31 01/01/2021

 Figure: Showing NetControlJS8 in action.
It is then easy, after having called for check-ins (“SNR?”) from all desired subgroups, to click the button “Send All to JS8Call” and the application will populate your transmit buffer with a list of ALL stations heard. At that point it marks all those stations as having been “SENT”.
If you then call for any missed stations, you’ll see new stations populating with “new” as their Status – allowing you to press the button “Send New to JS8Call” and get a list of all the new check-ins. These features should make it effortless to acquire and update your reporting on who has checked in.
From either this application, or from your receive pane in JS8Call, you can create a handwritten list later if you need it for recordkeeping purposes.
If you wish to clear out previously heard stations from being sent over with one of the SEND buttons, use the “Clear Status” button. This blanks out the status of all previously heard stations, in effect giving you a “clean slate”. If a station newly responds, they will now be listed as “new” and if they respond again, they will be listed as “revised” allowing you to create lists of stations reporting to different queries.
JS8 Net Protocol 32 01/01/2021

JS8 Net Protocol 33 01/01/2021
