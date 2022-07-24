---
title: "Whirlwind (also, a cool morse code script)"
date: 2022-07-24
---

Wow....four months later... lets see all that has happened since then:
- wrapped up 2 tough class projects
- graduated (yay!)
- got a job
- finished the sak&#233;
- traveled all over the country for various work things (all awesome) 
- Got my UAS pilots license (and played with a bunch of drones)
- probably a lot more that I'm missing 

Anyway, I'm not too upset with myself for not writing, but it's ironic my last post that was suppose to highlight the first quarter of the year and emphasis focus, I have been so focused I haven't even written for a whole quarter. No worries. I'll get back to it from time to time. None of that is really the point of this particular post, I just realized I hadn't posted in a while. Now to the point:

One of my favorite books, that I first read a *looong* time ago, well before I knew how to program more than a few line of BASIC, is Cryptonomicon, by Neal Stephenson. at one point in the book, Randy Waterhouse is in a Phillippine prison but for some strange reason given his laptop computer to use while in his cell. For this reason he is strongly suspicious that he is being monitored via [Van Eck Phreaking](https://en.wikipedia.org/wiki/Van_Eck_phreaking). To circumvent this he builds two programs, one to input text into a buffer via the space bar and Morse code, and another to read him the contents of a text file by blinking the characters to him via the LEDs on the keyboard. 

"His computer told him using Morse code. Computer keyboards have LED's on them that are essentially kind of useless: one to tell you when NUM LOCK is on, one for CAPS LOCK, and a third one whose purpose Randy can't even remember. And for no reason other then the general belief that every aspect of a computer should be under the control of hackers, someone, somewhere, wrote some library routines called XLEDS that make it possible for programmers to turn these things on and off at will. And for a month, Randy's been writing a little program that makes use of these routines to output the contents of a text file in Morse code, by flashing one of those LED's."
~Cryptonomicon, Chapter: Arethusa

I thought this was soo cool when I first read it. Years later I remembered the idea when reading about keyboard scancodes and I/O stuff in general. I couldn't find XLEDS but I did find a library called [PyAutoGUI](https://pyautogui.readthedocs.io/en/latest/index.html) which lets you simulate various keyboard and mouse inputs. One is the 'capslock' and 'numlock' keys. While not manipulating the LED directly, it seems many keyboards keep this state across all connected keyboards, so it accomplishes the same purpose. So I wrote up a script! (and in much less time than the month it took Randy. :P ). Once I found PyAutoGUI it was just a matter of adding a Morse code dictionary and the requisite plumbing to read in a file and break it down to individual characters. As of this writing it handles lowercase A-Z, 0-9, space and newline characters. It also lets you input the filename as a command line argument and the optional argument for which LED you want to blink. (default is numlock).

You can find it in my [vaillock](https://github.com/ninjajoe9/vaillock) repo. Syntax as follows:

**python3 vaillock.py** \[FILE\] \[LED\] 

I'll probably fix it to convert the uppercase to lowercase and add more symbols. It also hangs if it encounters a symbol not in the list so I should fix that at some point too. Finally there is a 'WPM' variable that doesn't actually control the words per minute, but is setup to do so if I figure out the math later. Either way, it was a fun little project and could possibly the the basis of some sort of library for future Morse stuff. 

P.s. it's called vaillock because allegedly Alfred *Vail* actually invented the version of Morse code we use today and 'lock' for caps*lock* and num*lock* ~JL