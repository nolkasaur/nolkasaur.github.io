---
title: Hello World
published: true
---

Hi.

I've gone through Heath Adam's (TCM Security Inc.) three courses, [Practical Ethical Hacking - The Complete Course](https://academy.tcm-sec.com/p/practical-ethical-hacking-the-complete-course), [Linux Privilege Escalation for Beginners](https://academy.tcm-sec.com/p/linux-privilege-escalation) and [Windows Privilege Escalation for Beginners](https://academy.tcm-sec.com/p/windows-privilege-escalation-for-beginners).
I took some notes [here](https://github.com/nolkasaur/Practical-Ethical-Hacking-course-notes-KeepNote-).

I also wrote down a bunch of the most common and useful commands I saw:

# Windows

## System Enumeration

>hostname

>systeminfo

>systeminfo \| findstr /B /C:"OS Name" /C:"OS Version" /C:"System Type"

>wmic qfe

>wmic qfe get Caption,Description,HotFixID,InstalledOn

>list drives

>wmic logicaldisk

>wmic logicaldisk get caption,description,providername

## User Enumeration

>whoami

>whoami /priv

>whoami /groups

>net user

>net user administrator

>net localgroup

>net localgroup administrators

## Network Enumeration

>ipconfig

>ipconfig /all

>arp -a

>route print

>netstat -ano

## Password Hunting

>findstr /si password *.txt *.ini *.config

## AV and Firewall Enumeration

>sc query windefend

>sc queryex type= service

>netsh advfirewall firewall dump

>netsh firewall show state

>netsh firewall show configuration

# Linux

## System Enumeration

>hostname

>uname -a

>cat /proc/version

>cat /etc/issue

>lscpu

>ps aux

>ps aux \| grep root

## User Enumeration

>whoami

>id

>sudo -l

>cat /etc/passwd

>cat /etc/passwd \| cut -d : -f 1

>cat /etc/shadow

>cat /etc/group

>history

>sudo su -

## Network Enumeration

>ifconfig

>ip a

>route

>ip route

>arp -a

>ip neigh

>netstat -ano

## Password Hunting

>grep --color=auto -rnw '/' -ie "PASSWORD" --color=always 2> /dev/null

>locate password \| more

>find / -name id_rsa 2> /dev/null

I've also gone through a few articles I had bookmarked (I have a lot of them):

* [SecurityAdvice](https://github.com/exaybachay-ak/SecurityAdvice)

    Short article about general security advice. Talks about Blue Teaming, Red Teaming, certifications, social networking and interviewing skills. In there I found [another link](https://github.com/sbilly/awesome-security), which contains a collection of software, libraries, documents, books, resources and all around cool stuff about security.
    
* [How To Become A Penetration Tester](https://www.concise-courses.com/how-to-become-a-penetration-tester/)

    Interesting article where you can read advice from several people about how to get into the security field and how they personally managed to do so.

* [How to Build a Cybersecurity Career](https://danielmiessler.com/blog/build-successful-infosec-career/)

    Great article about the field of Infosec: beginner advice, expectations, certifications, methodologies, online presence, social networking, job landing and career paths. I really liked this quote: **Top candidates are having conversations as opposed to being interviewed**. Also found a [video](https://www.youtube.com/watch?v=Qw1nNPiH_Go) about Jason Haddix's Bug Bounty Hunter Methodology.

* [How to get into cybersecurity?](https://www.reddit.com/r/cscareerquestions/comments/4k7g9y/how_to_get_into_cybersecurity/d3d1qai/?context=3)

    Reddit comment with relevant and useful info.

* [So You Want to Be a Security Expert](https://www.schneier.com/blog/archives/2012/07/how_to_become_a_1.html)

    Article about getting into the security field. I liked this quote: **Good engineering involves thinking about how things can be made to work; the security mindset involves thinking about how things can be made to fail**.  

* [Infosec list of resources and study direction.](https://www.reddit.com/r/ITCareerQuestions/comments/dvynd8/im_seeing_a_lot_of_the_how_do_i_get_started_in/)

    Great post with a bunch of information about career paths (offensive and defensive) including certification paths to take.

* [Hacking Your Pen Testing / Red Teaming Career: Part 1](https://medium.com/munrobotic/hacking-your-pen-testing-red-teaming-career-part-1-cc816aca0980)

    Helpful short article with good professional/career advice in the field (part 1 of 2). I thought this quote was interesting: **A lot of people can be stuck in what I call the ‘teacher-student mind-set’, especially early in their career. What this is, is the misapprehension that anyone else has responsibility and accountability for your learning and it’s normally a symptom of the school system**.

* [Hacking Your Pen Testing / Red Teaming Career: Part 2](https://medium.com/munrobotic/hacking-your-pen-testing-red-teaming-career-part-2-5d8612a976bc)

    Helpful short article with good professional/career advice in the field (part 2 of 2). I thought this quote was interesting and it is something I personally struggle with: **Where I think people get it wrong early in their career, is they see these high flying people who’re super-focused on one particular area and they look for the quickest way to become like them. It can be really enticing to shoot for that early on, as your perception may be that they’ve always been focused on that area, but I would advise against it. When you look at high performers who’re specialist, they normally have a background with broad experiences. They’ve been a generalist before they’ve become a specialist, in fact that generalism has allowed them to become the ninja they are. There are some exceptions to this, but generally you’ll find that you need broad foundations on which to build. My advice is to spend a few years exploring things with a technology focus. Live outside your comfort zone and get used to being a perpetual beginner. This may feel unsettling at first, but it will set you up with the right mind-set to be open to new ideas and experimentation, which is key**.

