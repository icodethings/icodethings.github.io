---
layout: post
title:  "House #2: Wifi Link"
date:   2016-01-21 17:00
categories: ['house']
tags: ['house', 'tech', 'networking', 'ubiquiti']
series: 'house'
---

My new house is about 210m from my parents house - line of sight. While some people might think of this as a downside, I
don't mind at all. It also gives me the ability to get faster internet.

In Australia the average internet connection is ADSL2+, according to a quick google, the average speed being around
10Mbps. While that's not that bad, some areas have the ability to get [HFC](https://en.wikipedia.org/wiki/Hybrid_fibre-coaxial)
at about 100Mbps. Something my parents house has and my house doesn't. While I could get an ADSL2+ connection, I thought
it would be a good chance to play with PTP wireless network links.

<!--more-->

The idea was pretty simple: put an antenna at my parents house and point it to another one at my house.

### Hardware

At each house I have a [Ubiquiti NanoBeam AC](https://www.ubnt.com/airmax/nanobeam-ac/). They are essentially a pretty
small, focused 802.11ac WiFi AP. They have a few configuration modes, but I have it setup to be P2P. It essentially acts
as a really long ethernet cable.

The router for the entire network is still at my parents house with the internet connection. I do plan on setting up a
second subnet for my house with a local router but right now the link is stable enough to do everything though it.

![Ubiquiti NanoBeam AC in box](/public/images/house/nanobeam-box.jpg)

### Mounting

For my parents house, I purchased Ubiquiti's standard mounting pole that is attached to their chimney on the second
level. The goal was to make it as subtle as possible.

![Ubiquiti NanoBeam AC mounted on chimney](/public/images/house/parents-mount.jpg)

With mounting for my house, I was able to mount it as high as possible without having to worry about making it as
subtle. So I extended the existing TV antenna pole up a couple of meters and placed it at the top.

![Ubiquiti NanoBeam AC mounted on antenna pole](/public/images/house/mine-mount.jpg)

### Results

After a bit of difficult aligning, messing with channels, chanel widths and power output, I'm super happy with the
results. The latency is basically nothing (sub 1ms) and the reported throughput capacity averages over 450Mbps.

![Screenshot of graph showing average through capacity](/public/images/house/ubnt-throughput.jpg)

I'm able to use the full 100Mbps HFC connection at my parents house without any hint it's traveling over a PTP
wireless link. After a bit of tweaking and aligning we haven't had any issues with this for the few months we've been
relying on it. Overall I'm very happy with the results. I don't expect to need any sort of backup connection in the near
future.

Right now the only bottleneck is the 100Mbit switch and the 2.5GHz 802.11n wifi router at my house. Because of this I'm
not able to actually utilize the full available throughput of the wireless link.

### What's Next

I do want to set up each house as isolated networks, just in case the link goes down. Right now all DHCP goes though the
wireless link and all UDP broadcast packets go across it too. Not too bad at the level of traffic we are at right now.
But not ideal.

The next step is to upgrade the main switch to a managed Gigabit one along with upgrading the one WiFi AP at my house to
a 801.11ac one.