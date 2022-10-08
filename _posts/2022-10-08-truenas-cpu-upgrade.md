---
layout: post
title: TrueNas Scale 🖥 CPU upgrade ↗️🚀
---

In a [previous post]({% post_url 2022-10-02-truenas-ram-upgrade %}), I described my dilemma with having bought the wrong RAM 🐏 kit.
Today, I want to report how that story continued and, _teaser_, ended successfully.
As I wrote, I bought another [8-core Intel(R) Xeon(R) CPU E5-2620 v4 @ 2.10GHz](https://ark.intel.com/content/www/de/de/ark/products/92986/intel-xeon-processor-e52620-v4-20m-cache-2-10-ghz.html) for € 38,85 on eBay.
I couldn't find the exact CPU cooler 🧊 that I already had.
However, I found a slightly bigger version from the same manufacturer and product line (server coolers, made for 24/7 operation): [Freezer 34 CO](https://www.arctic.de/freezer34co) for € 21,02.
All parts arrived within a couple of days.

I had never installed something on a server-grade motherboard before.
And now, I have to say, it was _so_ much easier!
The fact that I didn't have to take out the motherboard to install a cooler back-plate but could simply screw it into the already existing counterpart on the board was genius 💡.
I marked those screws with red circles ⭕️ in the next picture, which also shows the CPU already installed.

![only-cpu]({{ site.baseurl }}/images/2022-10-08/only-cpu.jpg){:width="70%"}

After the raiser screws had been installed, mounting the rest was super easy as well.
In hind-sight, it is actually quite beneficial to have a bigger CPU cooler now.
The airflow is right to left, towards the case fan on the rear of the case.
As you can see in the next two pictures, the air first passes through the 1st (right) CPU's cooler.
Of course, that would heat it up during high-intensity workloads.
If the second cooler would be of equal size and thus cooling capacity, the 2nd CPU would be heated with warmer air than the 1st.
It would probably run always a few degrees higher than the 1st as well, and thus age faster.
But with the bigger diameter of the 2nd cooler, that is not the case.
Sweet 😋.

![installed-top]({{ site.baseurl }}/images/2022-10-08/installed-top.jpg){:width="70%"}

![installed-side]({{ site.baseurl }}/images/2022-10-08/installed-side.jpg){:width="70%"}

The system booted smoothly after the installation, everything worked ✅ out of the box 📤.
The TrueNas dashboard shows twice the cores (2x 8) and twice the threads (2x 16).

![dashboard-cpu]({{ site.baseurl }}/images/2022-10-08/dashboard-cpu.png){:width="40%"}

Also the 2nd half of the RAM 🐏 kit is not accessible and the system has a total of 64 GB ECC DDR4-RAM available ☺️.

![dashboard-ram]({{ site.baseurl }}/images/2022-10-08/dashboard-ram.png){:width="40%"}
