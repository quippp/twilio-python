# twilio-release-6x-patch
Add a patch in order to fix current 6x release candidate.

## Install

```bash
pip install -e git://github.com/quippp/twilio-python.git@release-6x-patch-1#egg=twilio
```

or add this in requirement.txt

```txt
-e git://github.com/quippp/twilio-python.git@release-6x-patch-1#egg=twilio
```

# twilio-python

[![Build Status](https://secure.travis-ci.org/twilio/twilio-python.png?branch=master)](http://travis-ci.org/twilio/twilio-python)

A module for using the Twilio REST API and generating valid
[TwiML](http://www.twilio.com/docs/api/twiml/ "TwiML -
Twilio Markup Language"). [Click here to read the full
documentation.][documentation]

## Installation

Install from PyPi using [pip](http://www.pip-installer.org/en/latest/), a
package manager for Python.

    pip install twilio==6.0rc4

Don't have pip installed? Try installing it, by running this from the command
line:

    $ curl https://raw.github.com/pypa/pip/master/contrib/get-pip.py | python

Or, you can [download the source code
(ZIP)](https://github.com/twilio/twilio-python/zipball/master "twilio-python
source code") for `twilio-python`, and then run:

    python setup.py install

You may need to run the above commands with `sudo`.

### Migrate from 5.x
[Upgrade Guide][upgrade]

## Feedback
Report any feedback or problems with this Release Candidate to the [Github Issues](https://github.com/twilio/twilio-python/issues) for twilio-python.

## Documentation
[Here][documentation]

## Getting Started

Getting started with the Twilio API couldn't be easier. Create a
`Client` and you're ready to go.

### API Credentials

The `Twilio` needs your Twilio credentials. You can either pass these
directly to the constructor (see the code below) or via environment variables.

```python
from twilio.rest import Client

account = "ACXXXXXXXXXXXXXXXXX"
token = "YYYYYYYYYYYYYYYYYY"
client = Client(account, token)
```

Alternately, a `Client` constructor without these parameters will
look for `TWILIO_ACCOUNT_SID` and `TWILIO_AUTH_TOKEN` variables inside the
current environment.

We suggest storing your credentials as environment variables. Why? You'll never
have to worry about committing your credentials and accidentally posting them
somewhere public.


```python
from twilio.rest import Client
client = Client()
```

### Make a Call

```python
from twilio.rest import Client

account = "ACXXXXXXXXXXXXXXXXX"
token = "YYYYYYYYYYYYYYYYYY"
client = Client(account, token)

call = client.calls.create(to="9991231234",
                           from_="9991231234",
                           url="http://twimlets.com/holdmusic?Bucket=com.twilio.music.ambient")
print(call.sid)
```

### Send an SMS

```python
from twilio.rest import Client

account = "ACXXXXXXXXXXXXXXXXX"
token = "YYYYYYYYYYYYYYYYYY"
client = Client(account, token)

message = client.messages.create(to="+12316851234", from_="+15555555555",
                                 body="Hello there!")
```

### Handling a call using TwiML

To control phone calls, your application needs to output
[TwiML](http://www.twilio.com/docs/api/twiml/ "TwiML - Twilio Markup
Language"). Use `twilio.twiml.Response` to easily create such responses.

```python
from twilio import twiml

r = twiml.Response()
r.say("Welcome to twilio!")
print(str(r))
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<Response><Say>Welcome to twilio!</Say></Response>
```

### Digging Deeper

The full power of the Twilio API is at your fingertips. The [full
documentation][documentation] explains all the awesome features available to
use.

* [Retrieve Call Records][calls]
* [Retrieve Message Records][messages]
* [Search for a Phone Number][number]
* [Buy a Number][number]
* [Validate a Phone Number][validate]
* [List Recordings][recordings]

[number]: http://twilio-python.readthedocs.org/en/latest/usage/phone-numbers.html#searching-and-buying-a-number
[validate]: http://twilio-python.readthedocs.org/en/latest/usage/caller-ids.html
[recordings]: http://twilio-python.readthedocs.org/en/latest/usage/recordings.html#listing-your-recordings
[messages]: http://twilio-python.readthedocs.org/en/latest/usage/messages.html#retrieving-sent-messages
[calls]: http://twilio-python.readthedocs.org/en/latest/usage/phone-calls.html#retrieve-a-call-record
[issues]: https://github.com/twilio/twilio-python/issues
[documentation]: http://twilio-python.readthedocs.org/en/release-6x/
[upgrade]: https://github.com/twilio/twilio-python/wiki/Python-Version-6.x-Upgrade-Guide
