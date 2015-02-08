JLRoutes
========
### The original ###
https://github.com/joeldev/JLRoutes

### What is changed from the original JLRoutes? ###
A completion block has been added to the routeURL so that you get a chance to work with the object returned by a mapped route. 

### Example ###

```objc

- (void)someMethod {
  // ...
  // register route, note the completion block that is provided as a parameter in the handler block
  [JLRoutes addRoute:@"/users/:userID" handler:^BOOL(NSDictionary *parameters, JLCompletionBlock completionBlock) {
    NSString *userID = parameters[@"userID"]; // defined in the route by specifying ":userID"
    // fetch some resource
    User *user = [User userById:userID];
    completionBlock(user);
    return YES; // return YES to say we have handled the route
  }];
  // ...
  // test 
  [JLRoutes routeURL:[NSURL urlWithString:@"users/123"] completionBlock:^(id result){
  	User *user = (User *)result;
  	// do something with the user
  }]
}
```
### Installation ###

```
pod 'JLRoutes', :git => 'https://github.com/grillbiff/JLRoutes.git'
```

### License ###
BSD 3-Clause License:
> Copyright (c) 2013, Joel Levin. All rights reserved.
 
> Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:
 
>*  Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
* Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
* Neither the name of JLRoutes nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

> THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

