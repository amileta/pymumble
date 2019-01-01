PYMUMBLE python library
=======================

STOP! You're probably looking for [azlux's pymumble](https://github.com/azlux/pymumble)
------------------------------------------------------------------------------

The **pymumble** that is most maintained is azlux's fork. This fork is just for some experimenting. I might consider contributing back if I find this useful for my projects.

Description
-----------

This library is a fork of a fork of a fork (initial from https://github.com/Robert904/pymumble). But we will try to make pymumble better. So i consider this fork (the [@Azlux](https://github.com/azlux/pymumble) one) the current fork alive of pymumble.

The wiki/API explanation is [HERE](API.md)

The **Python 3** version is available in the [pymumble_py3 branch](https://github.com/azlux/pymumble/tree/pymumble_py3). I'm working on it with @ranomier, and it's working !! You can try this version and report bugs. In the futur the python3 version will be the main branch of pymumble.

For a client application example, you can check https://github.com/azlux/MumbleRadioPlayer or https://github.com/Robert904/mumblerecbot

Status
------
- Compatible with mumble 1.2.4 and normally 1.2.3 and 1.2.2
- Support OPUS. Speex is not supported
- Receive and send audio, get users and channels status
- Set properties for users (mute, comments, etc.) and go to a specific channel
- Callback mechanism to react on server events
- Manage the blobs (images, long comments, etc.)
- Can send text messages to user and channel
- Ping statistics

### What is missing:
###### I don't need those features, so if you want one, open an issue and i will work on it.
- UDP media.  Currently it works only in TCP tunneling mode (the standard fallback of mumble when UDP is not working)
- basically server management (user creation and registration, ACLs, groups, bans, etc.)
- Positionning is not managed, but it should be easy to add
- Audio targets (whisper, etc.) is not managed in outgoing audio, and has very basic support in incoming
- Probably a lot of other small features

Architecture
------------
The library is based on the Mumble object, which is basically a thread.  When started, it will try
to connect to the server and start exchange the connections messages with the server.
This thread is in a loop that take care of the pings, send the commands to the server,
check for incoming messages including audio and check for audio to be sent.
The rate of that loop is controlled by how long it will wait for an incoming message before going further.

It rely on several other modules and objects, but they should probably never be instanciated by an application.

Requirements/installation
-------------------------
It seems to work fine on Python 2.6 and 2.7.
I have used it on both Windows and Linux

Check the setup.py to know the versions of opuslib and protobuf needed

Thanks
-----------
- [@raylu](https://github.com/raylu) for making pymumble speak into channels
- [@schlarpc](https://github.com/schlarpc) for fixes on buffer


License
-------
Copyright Robert Hendrickx <rober@percu.be> - 2014

pymumble is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
