DMMSecretary
============

[![Build Status](https://travis-ci.org/dmiedema/DMMSecretary.svg?branch=master)](https://travis-ci.org/dmiedema/DMMSecretary)
[![Coverage Status](https://coveralls.io/repos/dmiedema/DMMSecretary/badge.svg?branch=master)](https://coveralls.io/r/dmiedema/DMMSecretary?branch=master)

[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)

[![Version](https://img.shields.io/cocoapods/v/DMMSecretary.svg?style=flat)](http://cocoadocs.org/docsets/DMMSecretary)
[![License](https://img.shields.io/cocoapods/l/DMMSecretary.svg?style=flat)](http://cocoadocs.org/docsets/DMMSecretary)
[![Platform](https://img.shields.io/cocoapods/p/DMMSecretary.svg?style=flat)](http://cocoadocs.org/docsets/DMMSecretary)

[![Twitter: @no_good_ones](https://img.shields.io/badge/contact-@no_good_ones-blue.svg?style=flat)](https://twitter.com/no_good_ones)


[ Some Cool Picture Here ]

`DMMSecretary` is a library to hold or forward `NSNotification`s as you'd like.

#### Why would I want that?

Let's say there is a notification you're interested in but for some reason you won't be able to respond to it.

```objc
DMMSecretaryNotification *notification = [DMMSecretaryNotification secretaryNotificaionWithObserver:self selector:@selector(someMethod:) name:@"NotificationNameIWant" object:nil];
[DMMSecretary createInbox:@"UniqueInboxIdentifier" notifications:@[notification]];
```

That will create you an inbox & set you up to receive notifications. No different than registering with `[NSNotificationCenter defaultCenter]`

```objc
[DMMSecretary startHoldingMessagesForInbox:@"UniqueInboxIdentifier"];
```

Maybe we only care about a single copy of a notification instead of receiving a possible flood of `UIKeyboardDidShowNotification` for example. Simply run

```objc
[DMMSecretary onlyKeepUniqueMessages:YES forInboxIdentifier:@"UniqueInboxIdentifier"];
```


Now, if 'NotificationNameIWant' happens we won't receive it, the secretary is holding notifications for us.

When we _do_ want our notifications forwarded to us, we can just call

```objc
[DMMSecretary sendHeldNotificationsForInbox:@"UniqueInboxIdentifier"];
```

To ask the secretary to stop holding our notifications we can call

```objc
[DMMSecretary stopHoldingMessagesForInbox:@"UniqueInboxIdentifier"];
```

## Generating Code Coverage Report

~~Since I haven't figured out how to automate the process of generating code coverage to have a cool badge, its currently a manual process.~~ [Slather](https://github.com/venmo/slather) & [coveralls](https://coveralls.io) are currently used for automated coverage reporting.

Local code coverage reports currently uses http://frankencover.it which has instructions more or less explaining how I set this all up.

To generate code coverage reports just run 

```sh
$ scripts/generateCodeCoverage.sh DMMSecretary
``` 
from within the root of the project.


## License

    The MIT License (MIT)

    Copyright (c) 2015 Daniel Miedema

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.
