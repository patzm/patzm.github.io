---
layout: post
title: "BOINC: donating compute"
---

Ever since, but especially since my [RAM and CPU upgrade]({% post_url 2022-10-02-truenas-ram-upgrade %}), my server sits idle 💤 pretty much all the time.
So I thought:
can't I donate my compute resources?
For a long time, especially during COVID 😷, I _actually did_ the same with my iPhone 📱.
The Vodafone Foundation has brought out the [DreamLab](https://www.vodafone.com/vodafone-foundation/focus-areas/dreamlab-app) application.
It essentially computes exiting stuff like COVID research 🧪 on your smartphones (yes! It is a computer) CPU and GPU (and NNU?).

So I sought to find a similar thing, but Docker 🐳 based and for `x86` architectures.
And I found it in [BOINC](https://boinc.berkeley.edu/) 🎉.
Setting it up through `docker-compose` wasn't 100% trivial, especially because of the ports and rather poor documentation on that end.
And probably because I wanted some parts of this to go through my reverse proxy.
But eventually, I got it to work.
The Docker 🐳 stack is published in my `dockerfiles` repo [here](https://github.com/patzm/dockerfiles/tree/master/boinc).
The stack is based on the official [`boinc` client](https://hub.docker.com/r/boinc/client) Docker 🐳 image.


And now: I have 100% CPU utilization 🥵😅🎉:
![cpu-utilization]({{ site.baseurl }}/images/2023-01-31/cpu-utilization.png)
Right now, the only workload I could find was from the project [World Community Grid](https://www.worldcommunitygrid.org/), an early initiative by IBM Corporate Social Responsibility.
I would also like to contribute to (i.e. compute for 😏) [Rosetta@home](https://boinc.bakerlab.org/), but there were no CPU tasks ready at the time of setup.

Oh, and this also means that my power consumption went from ~120 W to 240W ⚡🔋.
So at 26 ct/kWh (yes, Ökostrom) that is roughly 250 💶 per year 🙈.

### On ports
Like I said earlier, configuring the ports wasn't trivial.
I first started out by simply exposing the default BOINC port `31416` through the reverse proxy Traefik at `https://boinc.patz.app`.
However, that doesn't work and this isn't how it is intended.
It seems, that the traffic shall not be encrypted and thus not be resolved by the reverse proxy.
I now opened the ports on my router and pipe them to the container.
You can see this in the configuration here:
<script src="https://emgithub.com/embed-v2.js?target=https%3A%2F%2Fgithub.com%2Fpatzm%2Fdockerfiles%2Fblob%2Faa9931429372c16b70d042245ef8061fc1244691%2Fboinc%2Fdocker-compose.yml%23L10-L12&style=default&type=code&showBorder=on&showLineNumbers=on&showFileMeta=on&showFullPath=on&showCopy=on"></script>

_**Update:**_
I closed the ports on the router again, because that's really not required.
And every *unnecessarily* open port is an unnecessary security risk 🤷‍♂️.