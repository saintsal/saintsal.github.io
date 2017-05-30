---
layout: post
title:  "How do Lean and Agile teams deliver working code faster? A technical explanation for non-techies."
date:   2012-07-07 15:13:33
tags:   lean-startup leadership
---

Agile is associated with speed. The promise of Agile is working code faster, but how does this happen in practice? Though practices like Test-driven Development (TDD,) Continuous Integration (CI) and Continuous Deployment (CD.)

These are easier to understand when you see them in action, so imagine you're standing over the shoulder of a web programmer, who's building blog software.  They start by writing the "write blog post" screen, and then they load up their browser to see it. Something's not quite right, the post button is in the wrong place. So they go back to their HTML editor, make a fix, then check the browser again, hitting the refresh button. Ah, that's better.  Now they go back to their HTML editor and add some PHP code so it connects to the database and saves the post. They go back to their browser, try it, then they check the database to see if the blog post really got stored. Nope, it missed some data. So back to the PHP code to find the bug... and this back and forth continues until that screen works properly.

If you're lost by this example, there's an analog. Imagine writing a long document, but whenever you want to re-read anything you just typed, you've got to print it.  That's a lot of waiting for the printer.  Same thing with coding.
<h2>Test-Driven Development</h2>
Test-Driven Development changes this. It means the programmer starts by writing automated tests to test if the code is working, and those tests show as red and green lights as they write code. These are called Unit Tests. So instead of going back and forth to the browser, they can stay in their coding program and just check the traffic lights to see if they've turned green.  This speeds things up tremendously because the programmer isn't constantly running manual checks.

It's like writing a document with the proof-reader standing over your shoulder giving instant feedback when you need it.
<h2>Continuous Integration</h2>
These speed improvements actually accumulate over time, because the previous Unit Tests save from horrible, time-consuming debugging as the software gets more complex. Have you ever worked with a programmer who accidentally broke something that'd been working for a long time?  As your code matures, interdependencies get tough to spot so stuff breaks.  The result is a time-consuming step of "staging" new versions so we can kick the tires and make sure nothing broke. This forces us to release code in larger batches which slows us down even more.

Instead of manually testing on the staging server, we can automatically release code that passes all of our prior tests. This is called Continuous Integration. For example, if our blog programmer starts writing a complicated new feature but accidentally breaks old functionality, the old traffic light will turn red and point it out to them right away. Since they know they just created the bug, they know where it is and can address it quickly.  If it were later caught on a staging server, it wouldn't be fresh in the programmer's mind so it would take a lot of time finding the bug.
<h2>Continuous Deployment</h2>
The confidence of your accumulated test suite allows you to start deploying code live automatically. Automated checks and tests on production servers make sure everything is okay – both technically (the servers and code are functional) and functionally (the key business metrics and user behaviours are not negatively affected), otherwise there's an automatic rollback to the previous working version.
<h2>Are these useful outside of the development team?</h2>
Even at an early stage, these start to deliver <a href="http://www.saintsal.com/2012/07/3-commonly-missed-benefits-of-lean-agile-moving-as-a-team-understanding-customers-informed-strategic-decisions/">benefits to the whole team beyond deployment speed and quality</a> - moving as a team, understanding customers &amp; informed strategic decisions.
