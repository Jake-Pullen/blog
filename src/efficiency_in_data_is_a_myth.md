# Efficiency in Data is a myth

Not to long back, i was having a conversation with our head of development.  
He said to me, why use python? c# is faster. My reply was why use c#? Assembly is faster...  

But in all seriousness, if you are choosing a language just because it is faster, then I don't want to work with you.  
I promise this is going somewhere.  


People choose a language to learn for all sorts of reasons; ecosystem, beginner friendly,
error or type handling... you get it, there is a million and one reasons  
I chose python because it was a natural fit for my career progression as a data engineer,
so when i was tasked with deleting sensitive data from a fragile production database
I spoke to the head of development to make sure it was okay for me to install python on a server
in the same environment (on prem' days, i miss you sometimes) so i could build a python application
to slowly and carefully delete the data, while maintaining logs and an audit trail of what it had
deleted so we had 100% confidence that 1 the data was gone and 2 only the data we wanted to delete was gone!  

That is when he asked me, why use python? 
- This was a production web application with billions of rows and thousands of users.
- The terms of this deletion was that we could only delete in a 5 hour window from 6pm-11pm, but we could do this over any period of days/weeks.
- We have to log all the deletions in detail, and also store every delete statement we used for the process.

So tell me, why would i use a language that i don't know or understand... just because its faster,
when speed is not a problem here?  

And this is where I get to the main point, I'm a big advocate of writing code that is easily
readable, understandable and auditable.Don't get me wrong, I am impressed at the people who can 
solve an advent of code in a single line of code. But it doesn't matter if that line of code breaks.
I'd fail your pull request in a blink if you submit something like to me.

In my context of a data engineer, most of our data pipelines run over night.
I would rather have my code take a few seconds or even minutes more,
so i can log in the next morning and see every step of what happened in detail.  
And if it does go wrong I want to see exactly what line of code or data caused me the headache.  
These extra steps of making the code more readable, more reliable, more auditable will always add
more run time on to the code but this is not a speed contest, its a confidence contest. How confident
are you in fixing the error while all of your stakeholders are complaining about not being able to
see fresh data in their power bi dashboards. Me? My past self always has my future self's back...

Oh, and the data deletion? I built not only the application that worked flawlessly. I built a little
ingestion piece to load all of the logs into a database and a PowerBi dashboard to report on them.
So Every morning for 2 weeks, I would log in and open up the powerBi dashboard to see the
current progress of the deletion. Including things like seeing the times the deletions started & stopped
based on the 5 hour window, if any deletes had failed and the estimate time to completion.
