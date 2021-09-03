---
title: "Homelab Software"
---

This is the second in a series of regular posts detailing my journey building a "mini-data center" (and I use that term very losely), or homelab. Today's post is about the software I've decided to use to build said homelab.

## TL;DR

My homelab will mainly consist of a Kubernetes cluster (specifically [k3s](https://k3s.io/)), backed by a [TrueNAS Core NAS](https://www.truenas.com/truenas-core/), and run on a [Ubiquiti managed network](https://www.ui.com/). Most of the custom applications I deploy to the cluster will be developed with a mix of C# and React, since those are the 2 development platforms I'm most familiar with. My home automations will be controlled by [Home Assistant](https://www.home-assistant.io/) if I can make that work, and some cobbled together nonsense if I can't. Which, given how incohesive smart home stuff is, will happen more often than I like, but that should make for more entertaining blog posts.

## Kubernetes

When people talk about Kubernetes (k8s), they usually talk about how you can scale up to [Amazon/Google levels of container instances](https://www.youtube.com/watch?v=ngKT3MIfwpo), automated and seamless rollouts and rollbacks, self-healing, replication, etc. etc. But, I'm running 1 instance of most of my apps, and 99.9999999% reliability isn't really something I'm concerning myself with for a hobby project, so why use k8s?

Well, there's the up-skilling aspect. Learning new things is always great. But, k8s also gives me some practical benefits that make it worth the time to learn. k8s gives me the ability to unceremoniously chuck my code at a bunch of servers and just have everything work out (mostly). I don't have to worry about balancing apps across servers, exposing ports, assigning certificates, routing traffic, etc. And that's a huge advantage, because all those things are big hurdles to actually completing projects. I love writing new code to solve a problem. Screaming at my Ubuntu instance because I can't figure out why my connection is being refused? Not so much. I'm much more likely to actually work on things if a ton of tedious, unrewarding work isn't waiting for me at the end of days or weeks of coding.

## TrueNAS

I tried rolling my own NAS with NFS and boy did that just not work out at all. Switching back and forth between SMB and NFS, headaches with authorization and permissions, Windows just outright refusing to connect at times, and the lack of any advanced features made me decide to go with TrueNAS Core. For right now I'm still running NFS on a Pi, but switching that out has quickly become my #1 priority. I'll likely make a blog post about setting that all up in the future.

## Ubiquiti

I explained my reason for choosing their hardware in the previous post, but from a software perspective learning networking in-depth enough to use something like [pfsense](https://www.pfsense.org/) and/or a collection of other great software to handle my networking needs just wasn't something I wanted to prioritize. I'll pay the premium and deal with the somewhat walled garden approach Ubiquiti takes if it means I can focus my time on the things that are more important. I still had a _fun_ time setting it all up, but again, there'll be another post for that.

## Home Assistant

My thoughts on smart home tech will probably be another post on their own, but Home Assistant seems to be the #1 choice for people looking to get down and dirty with smart home tech. And I'm certainly looking to do just that.
