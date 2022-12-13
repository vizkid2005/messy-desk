+++
author = "Huzefa Dargahwala"
title = "Creating Outgoing Calls using CallKit on iOS"
date = "2022-12-11"
description = "Explains the key concepts of creating an outgoing VoIP call on your iOS app"
tags = [
    "xcode",
    "iOS",
    "CallKit",
    "iPhone",
]
+++

# Introduction

This is Part 2 of a 2-part series about using CallKit on iOS. [Part 1]({{< ref "/posts/handling-incoming-calls-using-callkit-ios" >}} "Part 1") explained how to report and handle an incoming VoIP call. In this part I will explain how to create an outgoing call and report it to the OS. 

CallKit expects the app owner to manage the AudioSession configuration and internals of the their VoIP application. At the same time, CallKit provides APIs that allow us to report various states of the call, eg: Ongoing, On Hold, Ended, etc. to CallKit and it will take care of managing the Native call experience. There is also a way to suppress the Native call screen but that is another post. 

With CallKitProviderDelegate, we get methods that can be overridden and observe GUI actions on the Native interface provided by CallKit. When the user presses the end call button, the `provider(provider: CXProvider, action: CXEndCallAction)` callback will be called by the OS. Your app can then implement the logic to end the current VoIP call in progress.

# Project Setup and Pre-requisites

To avoid replication and save the readers time, please refer to the [setup instructions]({{< ref "/posts/handling-incoming-calls-using-callkit-ios" >}}) in Part 1 of this series. The [code on GitHub](https://github.com/vizkid2005/CallKitSample) has the Sample project already setup, so feel free to use that as well. 

