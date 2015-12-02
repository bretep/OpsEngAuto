# Operations: Engineering and Automation


Total Sections: 302   Populated Sections: 56
Current Goal: Populate Empty Sections: 246   (Done: 18.5%)


Lines: 2328

Words: 39637


# Chapter 1: Preface (README.txt)


What will you get out of this book?  Why read it?



What I hope to impart here is a view into how I see operations, and how I automate operations.



In the case of the book, "operations" means "networked operations", "server operations", "datacenter operations", "production operations", all rolled into one term.  The field is both specific and non-specific, as operations can mean other things, but these fields are what I'm referring to.



What I hope you will gain from my perspective is a new foundation you can use as a point of reference to build your own operations experiences from, whether you are already an experienced operations engineer or new to the field. 



I will be covering a very large arena of information, so I will try to present a coherent picture, even though I cannot go into full details on every aspect, as it covers too many disciplines.



This book's format is meant to be read from start to finish.  It starts off more general, and very philosophical, setting up terminology and scenarios.  Then will become more specific as we get into implementation details.  Finally, it will go back to being more general as we discuss how to implement in your current environment.



This book is more about depth than about breadth, and as such we will continue to come back to examples over and over again, looking at them in different ways, to give a deeper understanding of all the components that make them up.  This is in contrast to many books that are meant to describe an array of information and give you a broader understanding of how to work and how to use them specifically.



<h2 id=8d921a98a2974ea61b905ce719a9f121><a href="#8d921a98a2974ea61b905ce719a9f121">1.1</a>: Where Ive Been, What Ive Been Doing, Why I Wrote this Book.</h2>
<br>
I've been working in the industry for over 20 years, and have been programming for over 30 years.  I've written over 1000 programs of varying size (the bulk of them being smaller, and operational in nature), but have also written and deployed PC games, end-user productivity tools, accounting software, end-user websites, as well as a lot of operations related monitoring, alerting, log parsing, configuration and automation logic required for operations work.<br>
<br>
Some names of places I've worked, named where you may know them, and grouped as industries where it's unlikely:<br>
<br>
Google, VMWare, Netflix, Cisco, Pacific Telesis, Lawrence Livermore Labs, Mobile Game Companies, PC Game Industry, Mortgage Industry, Financial Security Industry, Internet Startups (SaaS and end-user websites)<br>
<br>
You can see my abbrieviated job history at LinkedIn:<br>
<br>
https://www.linkedin.com/in/ghowland<br>
<h2 id=4135cf6df0e576145b37ff7fe29922a3><a href="#4135cf6df0e576145b37ff7fe29922a3">1.2</a>: The promise of automation is removing classes of work, while you get the desired results</h2>
<br>
At this point, everyone knows that automation is a necessary thing.  It wasn't always this way.  I spent much of my career trying to automate things and getting strong pushback from both management and peers.  <br>
<br>
These days people usually have some aspects of automation, and are comfortable with those, so it is only the areas that they do not yet have experience which are hard to get implemented.  A major impetus in writing this book is to resolve those problems, by making the concepts better publicized and hopefully well understood.<br>
<br>
The issues I find these days are not that people do not want comprehensive automation, but that there is not a clear understanding on what comprehensive automation entails, what it takes to build, how things will change once it is in place, and how the life-cycle of operations changes to modify it.<br>
<br>
With all of these things, it is best to stay results-focused, and look to what you want to achieve out of automation, and in my opinion the ultimate goal should be "removing classes of work".<br>
<br>
What is a "Class of Work"?  We will look at this in many ways over the course of this book, but we can start by summarizing it as "anything that is done".<br>
<br>
This may be a specific thing such as "update a DNS zone file" (text file).  When this "Class of Work" is comprehensively automated, then no one will ever again update the text file relating to DNS zones.<br>
<br>
This could be extended to "configuring DNS", in which case all zone files are automatically generated, the serial numbers are always incremented properly, the configuration files that specify the zones are generated, and all the transfers and tests to ensure that these changes are pushed out into production and contain valid entries are validated and monitored.<br>
<br>
This is a "Class of Work" that requires people to do currently, in some ways if it is already automated.<br>
<br>
If you have a service (SaaS, such as a web-site like "DNS Made Easy") that does this for you, then someone still needs to enter the data.  The data entry is still a manual process, and part of the Class of Work.<br>
<br>
How would you remove this manual work?  It will need to be generated from either a template of hostnames for the type of services being provided, or some other automated mechanism.<br>
<br>
When no one has to think about the life-cycle changes or perform manual labor relating to this area of work, then this Class of Work has been comprehensively automated, and has been removed.  <br>
<br>
Updating the system that manages this Class of Work remains manual labor, as writing logic has not yet been turned into an automatable task, but the regularity of updating the automation logic should happen far less frequently, and is more knowledge-work than data-entry work.<br>
<br>
Knowledge work is more stimulating, and known to be something that needs reviews and tests, whereas manual data-entry work is more prone to mistakes, because it is done so regularly that constant vigilance becomes impossible.  Eventually someone will make a typo or other data-entry mistake, and it will not be caught in review, and will be pushed out to production.<br>
<br>
With automated logic, these kinds of repetitive data changes and verifications can be done as correctly as the logic specifies, and if it is written correctly, it will be done correctly forever.<br>
<h2 id=205420c1274a2b80366e988715cd32f8><a href="#205420c1274a2b80366e988715cd32f8">1.3</a>: Writing in the first-person.  I will try to write as much as possible in the first-person, as I am speaking of my opinions, my experiences, etc.  I also find that this avoids the tone that can be see as "scolding" or "commanding" in write, as in the second-person "you must do this", etc.  When reading speech in the first person, I am more likely to see the information as informative, coming from the writers' perspective, rather than commanding and authoritative, in that this is an instruction or order for you.</h2>
<br>
You may have noticed, but I am writing quiet frequently in the first person, and will try to keep this consistent as much as possible.<br>
<br>
I am speaking of my experiences, perspectives and opinions, and so I think this is best done using "my own" voice, instead of a more factual "voice of authority".<br>
<br>
In my view, all information should be considered as coming from the source of origin, where you discovered it.<br>
<br>
When I say "X is Y", I think this should be read as "Geoff said X is Y", and not that X really is Y.  Whether X is really Y or not should be something that you validate for yourself, in your own experience, in your specific situation.<br>
<br>
The situation I could be using as my example may not match up to the situation you are working in, and my perspective may not be a useful one.<br>
<br>
Moreover, language itself is very flexible in what is what is meant, as many things could be intended by the same word, like the very overloaded word of "operations".  There is frequently a COO, Chief Operations Officer, in large or public companies, and this person's role and department has absolutely nothing to do with "production operations", "network operations", "server operations", "datacenter operations", etc.<br>
<br>
Because of this, it is useful to limit what you take from incoming information to what the speaker was trying to convey to you, as coming from them, from that particular situation, and their particular perspective and experiences.<br>
<br>
This separation from incoming-information to "fact" makes taking in more perspectives easier, as they do not need to be turned into a one-size-fits-all world view of truth.  As I learn more, I find that having such a one-size-fits-all is often a hindrance to communicating with other people, and learning new things.  It is certainly a hindrance to having an open mind to new information which may conflict with your current world view.<br>
<br>
Instead having a "this person said this thing" stance, allows any new information to come in as it arrived.  You experienced getting the information in some way, and that is that.<br>
<br>
Whether you utilize that information, or make it part of how you make decisions is up to you.  Whether it is applicable to your situation is up to you.  Whether it seems logical and grounded in reality as you understand it is up to you.  There is no reason to reject or accept it, as it is simply information.<br>
<br>
There will be quite a bit of this kind of introspection into language and meaning in this book, as it is in part a book on the philosophy of engineering and automation, because this is much more important than common jokes about philosophy majors in college may lead one to believe.<br>
<br>
I also find that when writing in the first person, it is less of a commanding or authoritative approach, rather than writing in the second person ("you will then do this") has more opportunities to throw readers off if they disagree, do not want to do that, or are tired of being lectured to.<br>
<br>
This is a one-way conversation, in that it is a book, but it is meant to be taken as a conversational approach to learning, so that you can grow from it as best is possible, and not merely a display of my knowledge and set of instructions for others to follow.<br>
<h2 id=8c769f9c732b984ba19311c211e281ab><a href="#8c769f9c732b984ba19311c211e281ab">1.4</a>: Writing Stylistic Conventions</h2>
<br>
There will likely be some writing stylistic conventions I use that are new for you to read, and perhaps you don't like, and certainly you will not find approved in English Grammar books.<br>
<br>
I have developed my style of written communication over my life, and continue to refine it still.  I am more concerned with having my intent and detailed messages understood than in complying with grammatical rules, and so will bend and break them as needed to achieve my desired results.<br>
<br>
As such, as I will quote "things" whenever I want to emphasize them specifically, as introduced by Alfred Korzybski, from his methodology of General Semantics (although not following his strict guidelines).<br>
<br>
I will also interject parentheticals (like this), whenever I want to make an immediate "aside" comment or clarification (like this).<br>
<br>
I will also make up words whenever they seem to work better, or sometimes I will think I am making up a word, but it might end up being an existing word that I didn't know, and has a different standard meaning.  I will try to explain my meaning any time I think I am making a concept that may not be a standard one, so try to read it with my intent, instead of against a standard, as if I stuck to the standards I don't think I could get the details with the pacing that I want.<br>
<br>
I am going to frequently switch words such as "I", "you", "we", "one" to account for the subject, and I have specific meanings for this:<br>
<br>
- "I": I am talking about myself and my experience.  As previously said, I will try to do this as much as possible, because this is a transference of knowledge, from me to you.<br>
<br>
- "You": I am talking about you, the reader.  I have written this for you, even though I probably don't know you, but I have you in mind when I am writing, and I am thinking "What will you be aware of at this time, from previous material?  What I am trying to get you to?  Is it clear to you?"<br>
<br>
- "We": You and I are on a short journey together, although at different times and different places, but I am relaying information into this medium, and you are consuming this information, and that creates an informal relationship between us.  I like to think in terms of "we" for this, as it is a shared journey.  <br>
<br>
When I write code I often like to document things like "Here we are doing this" and "We don't want this effect, so I am doing this".  In this "future readership" situation, I am thinking of the code documentation's future reader, which may be myself or someone else.  In either case, that reader will be in a different state than I was at the time I wrote the code and documented it, so I am trying to bridge that gap, and make it another "shared journey".<br>
<br>
- "One": This is when I am trying to give advice to some sort of direction.  I really don't think I should be telling you what to do, and I don't want to.  I want to assist in enabling you to do things better, and to make your own choices, and make your own processes, and methodologies and philosophies.  Telling you to do things is in opposition to these goals, so I use the word "one", such as:<br>
<br>
"One like's one's tea with slightly sweet biscuits."<br>
<br>
It is kind-of the British Royal "we", but in reverse, is the "all encompassing singular", but I write it mostly so if you don't want to accept it is is still easier to digest, because it is directly toward the aether, and not directly at "you" in a tone of command.  When I hear people speaking in the British Royal tone-of-language, they use "one" in basically the same way I am using it.  I feel this is a way one can make generalizations and advice, without making the statement too-pointed-at-you.<br>
<br>
I will also hyphenate-things-to-make-compound-ideas.  This allows words to be read in the sense of "all these things are one thing", and help in any kind of grammatical parsing.  As I understand it, not being able to speak German, the German language has "compound nouns", in which many nouns are put together in sequence to form a new word that is a combination of all of these.  I think this is a cool method of communication, and these long-chains-of-hyphenated-words are like, that but for any type of word, not just nouns.  They create Compound Concepts.<br>
<br>
I was born and have lived almost exclusively in the United States of America, and only in a few small areas of that space, and so my language usage is set up in a certain way.  Additionally being an Internet-denizen, I have a very fluid use of that language.<br>
<br>
My usage of English, or maybe "American", may not be easy for you to parse if you are not familiar with the way people similar-to-myself communicate, or English may not be your first language.  <br>
<br>
Even if you have a very similar usage of language that I do, the ideas I am expressing are complex and riddled with detail, so these mechanism of asides, and compound ideas, and such are methods to make parsing these ideas more clear.<br>
<br>
I am mostly writing in a tone of conversation, and so will jump around more than if this was a text book.  This is certainly not a text book, and should not be read as such.<br>
<br>
If you jump to a section, and find it extremely confusing, it is likely because ideas were introduced and specified in a previous section, and their immediate usage (without that previous information) may seem very alien indeed.<br>
<br>
This is a trade-off between writing styles, and for this work I have chosen this style as the one I think will yield the best results for the audience most-likely to be able to intake this information and make use of it.  That is only a guess, but I have to pick a methodology and stick with it.<br>
<br>
I will also be making Liberal Use of capitalizations.  I will have certain terms that I always capitalize, as I am using them as "Proper Nouns" (like a person's name), but I will also sometimes capitalize Random Words, because I am introducing a concept and want to draw attention to those specific words in the sentence.  It may be that I will capitalize them the first time I talk about them, and then never again, because the point was made, and the attention to them was drawn.<br>
<br>
All of this makes a real jumble of what is considered proper English, but I am doing more than relaying my thoughts and experiences and methodologies to you in English, I am trying to communicate the underlying ideas behind them, and those concepts are far more detailed and complex than English (or any language as I know them) can relay.<br>
<br>
There is a reason we have poetry, because the intent is to express something beyond the words, and often the structure of normal language communication is broken or modified to relay those intentions through the language, as the language is a barrier.<br>
<br>
My usage is similar, but is the Poetry of Engineering, as I see it.<br>
<h2 id=c0288d74f0dd8cb74fcb23af5ce26a0e><a href="#c0288d74f0dd8cb74fcb23af5ce26a0e">1.5</a>: Hopefully, this will provide you with a set of foundational experiences from my expeirence, in which you can use to form your own opinions, methods, philosophies, procedures, axioms, and systems.</h2>
<br>
The ultimate goal in this book is that it improves your ability to function as an operational engineer, and to write automation that achieves the results that you want.<br>
<br>
If you find any areas difficult to understand, or believe that sections are not explained well or are incorrect, feel free to write me and I will try to get back to you and update the work as best I can.<br>
<br>
My personal email is:  geoff@gmail.com<br>

# Chapter 2: Introduction


One of the major focuses of this book will be to differentiate the real from the virtual.



This may seem like something that is common sense, but I have found wide spread and scale disagreement on in what is real and what is not real, and this creates a lot of communication and planning problems.



If we can't agree on what is real, how can we agree on our priorities?  We will value things differently, because we understand them differently at a very fundamental level, and all communication will be moving past each other, instead of directly engaging.



The results will be poor, and without coming to terms with why this fundamental mis-communication is occurring, we may never be able to see eye-to-eye, and may end up being unable to work to get good results with each other.



Going to the very basics and working up from there will allow us to develop a common method of communicating, starting from terms, and moving to axioms, and then goals, and finally into priorities so that we can come up with plans where we agree on the components and end results.

<h2 id=ff17d94c0d49aab3e372e47b64b96ea7><a href="#ff17d94c0d49aab3e372e47b64b96ea7">2.1</a>: Focus on the virtual/physical management, specifically around internet and network services, but relatable to other industries.  All use cases will be around data centers and networked services.</h2>
<br>
"What is reality?" is a question that is too big and general to be dealt with here, if you want a good introduction on how to understand this from an engineering perspective, you can see Bertrand Russell's book {{ book_russell_reality }}.  It does a good job of describing how reality can be determined from our senses, and is a fairly short read.  You can also take a look on Wikipedia at the philosophical movement, Logical Positivism, which is a useful philosophy for engineers, and is one of the philosophical methodologies I use and reference in this book.<br>
<br>
For our purposes, it is good enough to have a summary of this, and for me to describe on which side of real vs. virtual (un-real) various elements reside in, for our purposes.  Again, this is not meant to be "ultimate truth", but a tool for communication, so that we can come to common terms and understandings, and grow our engineering abilities and get better results.  It is not meant for purposes outside of this endeavor.<br>
<br>
To be brief, I will use Russell's example converted into the experience you are having right now.<br>
<br>
At present, you are somewhere reading this text.  You are real, you exist, because you have tangible properties, such as mass, made of of molecules and atoms, in a certain state that make you you.<br>
<br>
The text you are reading is either in a book form, such as paper, or an electronic form, such as a monitor or e-ink display.<br>
<br>
If you are reading a book, the book is real, because like you, it is made of molecules, and has physical properties.  It resides in a certain position in the world.<br>
<br>
If you are reading from a monitor, then the monitor has similar physical properties.<br>
<br>
These things are all real, for our purposes of reality.<br>
<br>
The way you are able to read is that either ambient light is refracting off of the book, or is being emitted from the monitor, and those photons are striking your eyes, and the rods and cones in your eyes are being stimulated, and sending "signals" into your brain and nervous system.<br>
<br>
These things are all real.  Photons have physical properties, and while different than molecules and atoms, are able to be physically described and interacted with.<br>
<br>
At this point, you are probably affirming why you may have not read more philosophy works in your life, right?  Nothing new here, but lots of words to get to that point.<br>
<br>
Now, we enter into the realm of the un-real, the virtual world.<br>
<br>
How you interpret the words is not real.  It is a virtual type of understanding, though the word "virtual" is usually confined to computer related terms, I am going to use it universally to all things to differentiate from real.  Because we are mostly going to be discussing computer-related un-real concepts, it is easier to just stick to real vs. virtual.<br>
<br>
So, what am I getting at here?<br>
<br>
You are real, the device (book/monitor/device) is real, the photons traveling to your eyes are real, but your understanding and interpretation of the words is virtual.  Your feelings about the words is virtual, and in fact the words themselves are virtual.<br>
<br>
The ink on the paper, or the electrons producing the physical effects are real, but your understanding and interpretations of them are virtual.<br>
<br>
What's the point of this?  It will become clearer as we go on why I am leading with this, and it's not to make myself seem like a fancy-pants smart guy, it's because without this agreement now, there will be many more disagreements in the future, and it will hinder our communication about the more interesting and relevant parts of engineering and automation.  Please, bear with me here.<br>
<br>
So.  We have real books, devices, you are real, I am real, but your understanding and my understanding of things is not real, and even the words I am writing and you are reading are not real.<br>
<br>
How are words not real?  It is because they are symbolic.  They represent an idea, or set of ideas, which are also not real.<br>
<br>
The word for "book" exists separately then the object they describe.  In other languages, the word "book" changes (libre, knega, etc), yet the book itself does not change.  This illustrates how words are different than the things that they describe.<br>
<br>
Words can also be written in different fonts, and I could call this a "manual" instead of a "book", and yet what you are reading would not change.<br>
<br>
Symbolic things are not real, they are virtual, or logical.  I will use virtual instead of logical, as I will be differentiating "Virtual" as un-real, from "Logic" to be used for processes and code, or programming.<br>
<br>
Let's create a quick list of things that are real and virtual, for an immediate reference:<br>
<br>
- Hardware:  Real.  Something you buy, put an OS on, and runs your software, or something similar.<br>
- Software: Virtual.  Electricity (RAM), magnetism (rotating disks) or electro-chemical (SSDs/NAND) stores bits of information that can be executed.<br>
- Data: Virtual.  Same as software, but can't necessarily be executed.<br>
- Operating System:  Virtual.  Collection of software and data to make hardware perform operations.<br>
- Book: Real.<br>
- Words.  Virtual.<br>
- "A network": Virtual.  It's a concept of something that "networks", or more specifically may be an network IP address (data), that describes the network.<br>
- Network cables: Real.  Physical objects, that carry current.<br>
- Ethernet protocol: Virtual.  A collection of data and logic that describes how to communicate over electrical signals.<br>
- Layer 1 Ethernet: Real.  Physical electrical signals<br>
- Layer 1 Ethernet standard:  Virtual.  The description of how the physical Layer 1 ethernet will operatie.<br>
- Layer 2 Ethernet: Virtual.  How the Layer 1 physical (real) is used via the Layer 1 Ethernet standard (virtual), to create a Layer 2 ethernet connectivity effect (virtual).<br>
- IP Address: Virtual.  Data.<br>
- Hostname:  Virtual.  Data.<br>
- My engineering perspectives:  Virtual.  Data.<br>
- My engineering experience:  Virtual.  Data.<br>
- The actual things I have been through in my life:  Real.  Things happened, involving molecules and stuff over time (entropic heat exchange, etc)<br>
- My perspectives and memories of the actual things I have experienced:  Virtual.  Data, and summarized data at that, since I was not aware of the full-state of the physical (real) occurrences around me, and my memory (virtual) of them is a summary of that as well.<br>
<br>
<br>
I hope this short list and hopefully not-too-painful fundamental section has left what I am referring to in a clear state with you.  <br>
<br>
If not, please skim it again.  You don't need to agree with me on these things, you merely need to understand what I am trying to say clearly to get the information I am trying to convey.<br>
<br>
If you ever hit parts that feel wrong to you, or you reject, try to use the mechanism I presented in the preference of: "Geoff says X"<br>
<br>
This means you can take in this information, as "Geoff is saying this to me", without having to update your world-view at this moment to include what I am saying as "the truth", and in fact, I am not asking you to ever do this.  This is a communication to hopefully provide you more insight, which will include my perspectives, not as instructions on how you should see the world once you have finished reading this.<br>
<h2 id=75d62671847424a563ec929a890245c5><a href="#75d62671847424a563ec929a890245c5">2.2</a>: I only really know what I myself have experienced.  Everything else is hear-say, and while there may be a solid model behind it, I do not actually have experience in the matter, so I cannot trust the information to make solid engineering decisions on.  If I have nothing better, I may need to use this as the best course of action, and it may sound like a good thing to try, so I might experiment with it, but I have to recognize that this is an experiment, and so there is a great risk of failure.</h2>
<br>
What do I know?  What do I really know?<br>
<br>
Or, to paraphase a Sherlock Holmes quote, "What do I know, and how do I know it?"<br>
<br>
In any situation, this is a relevant question, as it directs where I will go next.<br>
<br>
If I believe I have solid information, that I can take action on, I can begin immediately to take action on that information.<br>
<br>
If I know that I do not have solid information, then I know that the first thing I need to do is to get some solid information I could work on.<br>
<br>
How do I know if what I really know is good information?<br>
<br>
It should be sourced from my own experiences, or it should be planned to quickly make checking the information so that it becomes part of my personal experience.<br>
<br>
Things I have personally experienced, I can say I have knowledge of.  Things I have read or heard, or that someone (including myself) just thought up may not be related to the reality of what is going on at the moment.<br>
<br>
Actions based on this kind of information are going to yield extremely unreliable results, because the information was not grounded in the circumstances it is being applied to.<br>
<br>
Let's create an example, a problem for us to solve.  We'll be doing a lot of this during the course of the book, so to get the most out of these I would suggest taking a moment each time one is introduced to try to model it out in your mind, imagine it, draw it out on paper, or do whatever works best for you.  I will discuss techniques for doing this a bit later on.<br>
<br>
The problem will be a common one:  Alerts are going off on our monitoring system, and tell us that we are having problems with our web servers.<br>
<br>
The monitor alerts are not extremely specific in this case and report something like "HTTP test failure".  More specific alerting would be helpful here, but those tests take time to set up, and in our immediate example environment they don't exist.<br>
<br>
A group of people forms up to deal with the alerts, and immediately several things are suggested as problems:<br>
<br>
- Maybe there was a bad code push?<br>
- Maybe the logs have filled up the disks?<br>
- Maybe There is a DDOS or other hacking attack occurring?<br>
- Maybe someone is doing work on it, and forgot to tell anyone and made a mistake?<br>
<br>
All of these are possible, and while some are more likely than others, and could be used to prioritize where we start looking, the question remains:  What do we know?<br>
<br>
What we have experienced so far, and what we really know, is that we got an alert of "HTTP test failure", and this has something to do with our web server environment returning correct results to the monitor health checks.<br>
<br>
This is all we know in this circumstance.<br>
<br>
Was there a bad code push?  We don't know, because we haven't made it part of our example.  Let's add some data around that.<br>
<br>
We have 2 options:<br>
<br>
- We ask developers or release engineers (or whomever, for this purpose we will say "release engineers") if they have recently pushed any code.<br>
- We go and look to see if the code has been updated.<br>
<br>
Both of these options will yield us new information we can work from, but will each of them give us solid information?<br>
<br>
Asking the release engineers will give us the hear-say information that whoever we asked gives their best current information.  Do they check first before responding, to see if anyone has pushed code lately, or do they use their current information to tell us?<br>
<br>
If they say, "No, no one has pushed any code lately.  We won't be doing that until X time", then we will leave that conversation with information that says no new code was recently pushed, and we will have impetus to de-prioritize the possibility of new-bad code being pushed into production causing the monitoring alert.<br>
<br>
But is this solid information?  They may be the only person who does the code pushes, and so they may be the "definitive" answer on the subject, but what if someone new accidentally did it for some reason?  The "definitive" person would not know this, unless they checked, and their information would not be congruous with reality.<br>
<br>
If we take the second option, and we look for ourselves, then we can see if the timestamps on the files have been updated, or if the log files say that the web or application servers have been reloaded.<br>
<br>
The second option gives us information that we have personal experience with, and this is solid information.  If we do not have access to go look ourselves, then the next best thing would be getting someone who does have access to verify it themselves and preferably show us the result, but they could also provide unique information such as "X was the last time code was pushed", instead of a more vague answer like "No, no code has been pushed lately".<br>
<br>
So we have 2 lessons we can take from this example problem.  One, that information we have personal experience on is better than hear-say information, or information we do not have personal experience with.  Second, that there are degrees to "information solidity", or the reality-based nature of the information.<br>
<br>
Looking ourselves yields the highest relation to reality.  We were there, we looked at the information, and it said "X".  We have very high reliability with this information, as long as we were paying attention to what "X" was, and paid attention to get into the right position to look at the right data (not accidentally looking in a different server or directory, at the wrong files), then we have solid actionable information to work off.<br>
<br>
This would be the same level of information if someone else did this work, but showed us while they did it.  We saw them do it, we saw the results.  It would take some acts of deception to make this data questionable, and since we are referring to working in a work-environment, we will assume that all people are behaving as Good Actors for these examples.  Later, we will also look at how some people act as Bad Actors, and can create bad data, for instance trying to hide a mistake that have made.  (We could call this section, "Do you even audit, bro?")<br>
<br>
Less reliable is information that someone told us they looked, but did not show us, and gave us exact data, such as "X was the last time code was pushed, I checked the directory timestamps and logs".  This is good data, but we do not have personal experience with it, so it is less-good than data we verified ourselves.<br>
<br>
Next, we have a situation where someone else tells us "No, no code was pushed recently".  This is not data we have verified ourselves, so we have no personal experience with it, and it is not specific as to when the code was actually released.  It is possible that this person did not check, and is just telling us from their own perspective that they don't believe it was pushed recently.  This is beginning to be invalid data.  <br>
<br>
We could still ascribe Good Actor behavior to this person, and take them for their word, however, what will be the result if we do take them at their word, and de-prioritize looking at a bad code release, and start looking at other problems.  We end up exhausting the search on other things, and much down-time has accrued with the "HTTP test failure" alert still going off, and eventually someone looks and see that indeed new code was pushed out, and it contained a bug.<br>
<br>
Rolling back the code resolves the problem, and the HTTP server starts to return correct tests to the monitoring system.<br>
<br>
Much of the downtime accrued because of working with non-verified information could have been avoided by getting personal verification of the exact time of the last code push.  I have seen this exact situation happen many times, and bad-code or bad-configuration changes are one of the most common outages for networked services.<br>
<br>
Even though these are common, the common-ness alone does not mean that it is solid information.  It only means it is something that should be verified quickly to see if it is a contender for causing the problem.<br>
<br>
We will be exploring the idea of what makes good information in detail in this book, and I will change this introductory terminology of "solid information" into a more precise definition of Intelligence, which we can categorize in many ways:  Verified, Unverified, Actionable, Unactionable, etc.<br>
<h2 id=10fc971fd9dc706d141c5ada28fd9ae3><a href="#10fc971fd9dc706d141c5ada28fd9ae3">2.3</a>: What is Operations?</h2>
<br>
Keeping up our short tradition of asking questions that seem pointlessly basic, I will ask:  What is operations?<br>
<br>
Why do we do what we do?  Why does it exist?  What is it?  What are the goals?  What are the priorities?  What are the procedures that makes up an Operations department?<br>
<br>
The more questions that are asked, stemming from the original question, the less the question seems to be pointless, and the more the questions start to become the ones we deal with every day.  But, we skip the first question.  Why?<br>
<br>
We skip it because we already assume that we all know the answer, and that we are already in agreement about the answer.  It is taken as a given, but in my experience, there are many differences of opinions in even the most basic answers to what it is.<br>
<br>
People have different values, and they have different skills and personal experiences, and from these, they have a world-view that is also different.<br>
<br>
Getting to the fundamentals of what we mean by something like "Operations" means that we can start to align our views, and in aligning our views, we will communicate more effectively, and become able to work more effectively together.<br>
<br>
It is really these fundamental issues that make communication so hard and ineffective, because we do not drop down to discussing what we are fundamentally doing, and get buy-in from everyone on the team about each of the layers in the stack of what makes up an environment's operations.<br>
<br>
So, what is operations?<br>
<h3 id=0671652556ae5d62c827e6db8082bab7><a href="#0671652556ae5d62c827e6db8082bab7">2.3.1</a>: Ops is about Control.  Letting everyone do their own thing is not-control.  It is individual control, for them, but the company is not in control as there are too many different types of activities going on for the same task, so the task is constantly done differently, creating cruft and stuff.  You can move faster, but not in an aligned way.</h3>
<br>
I will posit that the primary thing that operations is about is Control.<br>
<br>
Why control?  Why not up-time, availability, responsiveness to business direction, or any other valid priority?<br>
<br>
My reason for this is that without control, you cannot be efficient in any other areas.  You can only be as efficient as your level of control allows you to be.<br>
<br>
You can always make progress in any area by applying resources to it:  people, time, money, hardware, etc.  <br>
<br>
These will make progress on problems you have and want to solve, but the limiting factor to each of them will be your ability to control the environment.<br>
<br>
If you have an up-time failure event, to fix the problem quickly you must be able to determine what is wrong, which takes the ability to gather information, and you must be able to take action to resolve the problem, which takes the ability to change the environment.<br>
<br>
Both of those actions, "gather information" and "change the environment" have Control as a central tenet.  <br>
<br>
How can you gather information without the control of the environment to yield you information?  In the most basic example, if you do not have access to the information, you cannot gather it, and you certainly do not have control over it.<br>
<br>
If you do not have access to change the environment, you cannot change it, and do not have control over it.  <br>
<br>
Like many things, Control can be seen a spectrum.  We can illustrate in on a line segment, such as:<br>
<br>
No Control <-----> Total Control<br>
<br>
This spectrum would represent all possibilities of "Control", having no control, and having total control.<br>
<br>
Control is a tricky subject, in that it is not only un-real (Virtual), but it is even more Virtual than many other things, because it more like a concept than something that is valid data.<br>
<br>
Unlike other Virtual (non-real) things, Control cannot be verified like data can be verified.<br>
<br>
If I have a variable "X" and I set X to 5 (X=5), and then I check if X is 5 (X==5?), I can get a result that is True or False.  X is either 5 or it isn't.<br>
<br>
But with a concept like "Control", there is no way to check that you have control or not.  You can check that you have access to some data, which is an aspect of control, and you can check if you can change data (by changing it, or looking at permissions (less good)), and this tells you more aspects about control, but there are so many other things that go into this that are very difficult to inspect or verify.<br>
<br>
For instance, one aspect of Control is, "Do we have enough time to do the work we need to do?"  This is an aspect of controlling one's schedule, so that good work can be produced.<br>
<br>
If we do not have control over our schedules, and work is required to be done before it can be done to our satisfaction of "good work", then we do not have control over this, and we will see problems arise from this fact.<br>
<br>
There are many other aspects of Control that we will look at, and I will make more cases on why I believe this is the central tenet of Operations and why understanding what you do have good control over, and do not have good control over is very valuable and actionable information.<br>
<p id=126b3100e0bafcd606cdb539413d4ce5><b><a href="#126b3100e0bafcd606cdb539413d4ce5">2.3.1.1</a>: "De facto" ops vs. "planned/controlled" ops</b></p>
<br>
If Control is the central tenet of Operations, what is the opposite side of the spectrum?  Uncontrolled operations?<br>
<br>
I think it's clearer to say that the opposite side of the spectrum from control is "de facto" operations.  What simply happens because there are business goals that need to be solved, and resources were put towards solving them, again and again.<br>
<br>
It is fairly easy, in my experience, to handle every situation in an efficient manner for the problem at hand, and still end up with a total mess of an operations environment, because the actions while individually efficient do not work together as a whole efficiently.<br>
<br>
This is often seen in naming conventions that change frequently, or that you could say there is not really a "convention" to the naming of things.  The same goes with what kind of hardware you purchase, if every time you purchase hardware you pick the "right tool for the job", but you end up with unique hardware configurations for every problem solved that required a purchase, then you have N number of hardware configurations to support and manage.<br>
<br>
The maintenance work to keeping many hardware configurations versus a limited number (say 2-4 unique hardware specifications per generation of hardware purchases), will mean many more problems have to be solved in upgrading software, and many more security and firmware upgrades will need to be tested.  It can easily create a situation that either requires many people to support, or more likely it to not worth the cost of actively supporting everything, and so support is only assigned when a high priority problem arises.<br>
<br>
"De facto" just means "In reality", but in common terms it means "the way things happens", like "this is what we have got from our low-coordinated efforts".<br>
<br>
So a spectrum for Control would look like:<br>
<br>
De Facto <----> Planned<br>
<br>
Planned operations will have strict naming conventions, where all the data required to be derived from a name is embedded in the name, and when new services, products, environments, and other things arrive, they are intelligently inserted into the existing convention and do not create new conventions.<br>
<br>
An example of "de facto" naming of hostnames might be like this:<br>
<br>
- chicken.domain.com<br>
- trex.domain.com<br>
- saturn.domain.com<br>
- monkeyknifefight.domain.com<br>
- web1.prod.domain.com<br>
- web9.prod.domain.com<br>
- web10.prod.domain.com<br>
- redis-01.sf.prod.domain.com<br>
- redis-01.nyc.prod.domain.com<br>
- redisqa-01.nyc.prod.domain.com<br>
- redis-01.nyc.stage.domain.com<br>
- git.corp.domain.com<br>
<br>
And a list of the same names, in a "planned" fashion might be like this (which provide the same services as the above machines, in a 1-1 fashion):<br>
<br>
- ops-001.infra.admin.sjc.domain.com<br>
- ops-002.infra.admin.sjc.domain.com<br>
- ops-003.infra.admin.sjc.domain.com<br>
- monitor-001.infra.admin.sjc.domain.com<br>
- web-001.product.prod.sjc.domain.com<br>
- web-009.product.prod.sjc.domain.com<br>
- web-010.product.prod.sjc.domain.com<br>
- redis-001.product.prod.nyc.domain.com<br>
- redis-001.product.qa.nyc.domain.com<br>
- redis-001.product.stage.nyc.domain.com<br>
- git-001.infra.corp.sjc.domain.com<br>
<br>
A couple of things can be immediately seem from these lists, as you compare the each ordered element against the same position in the other list.<br>
<br>
Some striking differences:<br>
<br>
- No "funny" or special names for machines.  "monkeyknifefight" is great imagery, and fun to say, but it has no business in your operational data.  It does not explain what services are provided, who owns the machine, where it is located, or any other actionable information.  It is essentially dis-information, since you know less about the machine then if it was called "misc" or "general".<br>
<br>
- In a planned naming structure, all names have the same number of elements, and the elements are in the same order, and written in the same sequence and pattern.<br>
<br>
In the list I have just made up, you can tell a number of things about any of the given hostnames' servers:  <br>
<br>
What general function they provide (web, git, redis).  <br>
<br>
What location is the server in?  SJC and NYC seems to be our options.  This is much clearer than "sf", as they are airport codes, and so provide more than city or regional information.<br>
<br>
What environment is this used for?  Production, staging, QA, corporate?<br>
<br>
What instance number of the service is this?  001, 010?  <br>
<br>
In addition, the instance numbers are always written in the same format, providing a standard for where to start a new service:  001 (or 000, if you prefer computer counting)<br>
<br>
The planned naming convention can scale significantly, while keeping a pattern that fits any of the machines, new or old.  Selecting the proper format for naming hosts is so important, because it is a direct factor in Control.<br>
<br>
If you cannot name something accurately, how can you control it?  How can I access a server, if I do not know it's name?  How can I change the state of a server, if I do not know it's name?<br>
<br>
I have worked in environments where naming conventions changed even in the same service.<br>
<br>
Take this for example:<br>
<br>
- redis-01-1.product.prod.domain.com<br>
- redis-02-1.product.prod.domain.com<br>
- redis-2-001.product.prod.domain.com<br>
- redis-2-002.product.prod.domain.com<br>
<br>
These are 4 redis servers, in the same "pool" of servers (used by the same application servers, in the same production data center), but halfway through someone changed the naming convention (out of a much larger pool than 4 machines, more like 40).<br>
<br>
They started out with "shards" as "redis-XX-#", where "#" is the "shard" number (relating to a master-slave set of data), and "XX" was the "shard instance" number, where "01" might be the Master (takes writes) and "02" would be the Slave.<br>
<br>
Then later they or someone else (more likely) created a new set of machines with the shard and shard-instance values flipped, and the shard-instance values now have 3 digits, instead of 2.<br>
<br>
This creates problems every time someone tries to work on these machines.  Logging into any given machine takes either trial-and-error, memorization, or looking it up.  Each of these is inefficient in time and personnel resources, and as the site scales up (more servers, more services), these kinds of time-personnel costs start to become major factors in both how much work can be accomplished in a given period of time, how frequently mistakes are made (not updating all the servers in the same fashion, performing work on the wrong servers), how long it takes to train new employees, and how well any employee really knows the environment.<br>
<br>
We are probably in agreement that planned naming conventions is better than unplanned or de facto naming conventions, but we are engineers, and it is not enough to think something is better, we require being able to dissect the issue to see what the components make it up, so that we can build it better for our specific needs.<br>
<br>
Let's take a look at the original planned naming convention I gave, and see how we can make it more efficient, since we want it to be our one-and-only naming convention.<br>
<br>
- web-001.product.prod.sjc.domain.com<br>
<br>
Let's look at each part of this name:<br>
<br>
- web<br>
- 001<br>
- product<br>
- prod<br>
- sjc<br>
- domain.com<br>
<br>
These are the components that make up this name.  Do we have the right components for our current needs?  What about our future needs?<br>
<br>
One can certainly over-engineer a problem and "prematurely optimize" it against future concerns, but not looking at what is likely to come in the future is on an extreme side of the spectrum for planning for the future.<br>
<br>
Taking each section individually:<br>
<br>
- web<br>
<br>
This seems pretty self-explanatory.  If we call things "web" servers, and they do "web" things, and we don't have other services that also do the same thing in the same environment and could cause confusion, this is good enough.<br>
<br>
If we do have other services that do the same or similar things, we might need some alternative names, such as "app", "webmain", or "webfront" or something similar.  Try to make it what people in your environment call it verbally, and there will be less confusion when switching from discussions to typing in data.<br>
<br>
I will call this first part of a naming convention our "Host Class".  So machines hostnames that start with "web" have a Host Class of "web".<br>
<br>
- 001<br>
<br>
This is our Instance number.  It is the first (or second if starting from 000) machine in in the "web" Host Class.<br>
<br>
This has an obvious limit of stopping at 999, and then the naming convention breaks.  Many organizations will never have more than 999 servers of any type, but this is not a reason to fail to plan for the case of scaling past that point.<br>
<br>
It costs very little to make a good naming convention, and only requires diligence and checking your work to ensure that no one creates names they should not, and it will save much pain in having issues with naming down the line.<br>
<br>
Scripts are written whose logic may not be able to deal with naming conventions that change, and this can cause problems in your environment as you pass these thresholds.  We'll cover how to solve this shortly.<br>
<br>
- product<br>
<br>
This is an example product name for your organization.  This should be a short product or project name that clearly differentiates it's purpose from other products or projects.  Notice in the example I use "product" and "infra" to differentiate the organization's product, which may generate revenue, from the infrastructure servers used to support the product's operational environment.<br>
<br>
- prod<br>
<br>
This is an "environment" description, and differentiates machines in production (being used by end-users, or running financially impacting services), differentiating it from servers performing the same actions, but that run in development, QA, staging, corporate, or other environments which have different users and impact if they go down or degrade.<br>
<br>
Common examples:  prod, stage, qa, dev, corp, net<br>
<br>
- sjc<br>
<br>
This is the location of the datacenter the server is in.  Whether it is a closet, or a Tier-4 Gold data center, you have assigned a location to it, so no one has to guess.  If you are consistent and only put the correct location labels into the hostnames, you will not have confusion over where machines physically reside when this becomes an issue, say for maintenance, repairs, or networking changes.<br>
<br>
Using airport codes, of the airport closest to the location, is a common practice and a good one.  It allows being fairly specific, but not having to debate over whether something is inside this-or-that region.  Simply find the closest airport with a 3-letter airport code and use that.  It doesn't matter how big the airport is, if it is a registered airport it is guaranteed to be unique and give you a latitude and longitude to the general area in a consistent manner.<br>
<br>
- domain.com<br>
<br>
The example domain of our example organization.  The important part here is that it is consistent.<br>
<br>
There is a difference between internal names and external names, in that internal names can be kept consistent with the work of the Operations department, but external names are frequently in control of other departments such as Marketing, Business Development, Sales, etc.<br>
<br>
As such, they should be treated differently.  Internal names should be rigidly controlled, and external names should come with high recommendations for using naming conventions.  You could even provide several different recommendations for external naming conventions, to try to get other departments to constrain themselves and avoiding total naming-anarchy.<br>
<br>
{{ aside_begin }}<br>
Frequently non-Operations departments do not understand the use of sub-domains like "product.domain.com", and will create new base level domains for every project.  Sometimes this is required (legal and business reasons) and other times, it is only because they didnt know they could have "newproduct.domain.com".  This is especially a problem for certificates, like for HTTPS, as new domains require new certs and updating them every year or so, while sub-domains may use star-certs (*.domain.com), and roll up hundreds of sub-domains under a single certificate to manage them.<br>
{{ aside_end }}<br>
<br>
<br>
Now that we have gone over a bit about the initial planned naming convention, let's make it better.  Here is a proposal:<br>
<br>
- web-1-001.product.prod.sjc1.domain.com<br>
<br>
I have only added 3 characters to this name, but I have made it both significantly more scalable, and provided a new level of control.<br>
<br>
First, how is it more scalable than the previous naming convention of "web-001.product.prod.sjc.domain.com"?<br>
<br>
It is more scalable in 2 ways.<br>
<br>
First, it is more scalable in the location.  Previously we had "sjc", which meant that the server was located near the closest airport code of SJC (San Jose, California), but which data center is this?<br>
<br>
If you only have 1 data center, then you know.  But what if you get a second data center, for redundancy or growth?  What do you name it?  sjc2?  <br>
<br>
If you name the second data center "sjc2" and the first was "sjc", you now have a naming convention discrepency.  You previously had 3 letters, now you have 3 letters and 1 number.  This can create parsing problems in scripts, and is inconsistent when you type names.  As you grow in number of data centers in the SJC area, you will have more problems when "sjc3" and "sjc4" are consistent, but the original "sjc" is not.<br>
<br>
If you know that something is likely to grow in count, then you should start with a numerical indicator from the beginning.<br>
<br>
What about "product", is it likely to grow in count too?  No, there is not necessarily a requirement for this.  If a new product does come out that is called "product2", then it is still differentiated from "product", and while it shares the same look and feel as the datacenter location scaling problem, it is actually a different type of scaling.<br>
<br>
This is likely to be controversial, as it is difficult to back up with solid data quickly, so we will cover how to differentiate data like this later to keep the pace moving along.<br>
<br>
The second way it is more scalable is that we have a secondary numerical counter for the Host Class.  "001" has now become "1-001".<br>
<br>
This provides 2 methods of scaling.  For Host Classes that merely collect a lot of servers, this means we can use the same naming convention once we pass "999" instances for the "web" Host Class in our production SJC facility for our given product.<br>
<br>
This would look like:  web-2-001.product.prod.sjc1.domain.com<br>
<br>
However, many services have a more interesting use case for this number than simply going rolling over at 1000, which is separating sets of machines that hold related information.  Consider these names:<br>
<br>
- redis-1-001.product.prod.sjc1.domain.com<br>
- redis-1-002.product.prod.sjc1.domain.com<br>
- redis-2-001.product.prod.sjc1.domain.com<br>
- redis-2-002.product.prod.sjc1.domain.com<br>
<br>
These are 4 machines, grouped into 2 sets of 2:  1-001/1-002 and 2-001/2-002<br>
<br>
These can be used in many ways, but one way would be that this represents a Master-Slave relationship of data being written and read to 1-001 and 2-001, until one of those machines goes down, and then the other would take over such as 1-001 going down, it would be: 1-002 and 2-001 which are active for reads and writes.<br>
<br>
What data is sent to each of these machines could be done based on doing a modulus of an index ID (shard = index_id % 2), or another lookup method (rings, partitions, etc).<br>
<br>
In this case I refer to the first number as the "Shard" and the second number as the "Shard Instance", so redis-1-001 is Shard 1, Shard Instance 001.<br>
<br>
This is a very scalable naming convention.  It allows for different Host Classes (web), different Shards of data (-1-), different instances in the shards (-001.), different products (.product.), different environments (.prod., .qa.), different data centers (.sjc1.) and the common domain name for internal server hostnames.<br>
<br>
Separate from being scalable, this also provides a new layer of Control.<br>
<br>
Data in Shard 1 is different than data in Shard 2, and may even have different logic operate against it.  This is more easily handled than differentiating "redis-001, redis-002" from "redis-003, redis-004" for logic that groups data on servers by their position in a sequentially numbered set of server instances.<br>
<br>
It is generally better still to use the same logic on all Host Classes of type "redis" and merely differentiate the data sets by the Shard, but if you have grouped the Shards as different distinct numbers, you have this additional ability to control them accurately based on this data.<br>
<br>
There are other ways of organizing this data into names, and it depends on what data you need to track, but starting from a naming convention like this when you don't yet have that information is a safer bet than starting with less planning than this.<br>
<br>
If you know you have additional requirements, be sure that they are implemented into the naming convention, and kept in the standard.  This is a good standard to be extremely rigid with, as the benefits for having consistent naming are large and increase over time.  <br>
<br>
If you already have a naming convention, it is better to stay with it than to change it, but if you do need to change it, it is better to make a new standard, and make all new machines comply with it (if they are not in existing services with the old naming convention).<br>
<br>
This way you can at least control your naming conventions in a generational sense, and if you are doing planned work, you should have a very limited number of total generations.<br>
<br>
There is a lot more that could be said on just this example, and we will come back to it later, as naming things is, after all, one of the two hard computer problems, along with cache poisoning and off-by-one errors.<br>
<p id=e6f860a586c5005530de3736bbf50109><b><a href="#e6f860a586c5005530de3736bbf50109">2.3.1.2</a>: Alignment takes "vision" and knowledge.  Not someting someone new to the process can understand well, because they are new.</b></p>
<br>
Another important aspect of operational engineering, and engineering in general, is "alignment".<br>
<br>
Things must align with each other for their full efficiency to be able to be used.  This is easy to see in the physical world: all sections of a bridge must align with one another, fence parts must be in alignment to be a good fence, and support beams must align with each other to provide continuous support.  Engine linkages must align with transmissions and so on.<br>
<br>
It is no less important in the virtual world.  The entire field of networking is about aligning physical cables and virtual configuration to move frames and packets from source to destination.  Databases are about aligning data together so that it can be stored and retrieved efficiently.<br>
<br>
Everywhere you look alignment is an important factor on the quality, reliability, resilience, and structure and yet like many fundamental aspects of engineering, this topic itself is not discussed directly, and typically indirectly discussed as in how "everything must match up" given different protocols.<br>
<br>
You may see where I'm starting to go at this point with all of these fundamental questions and inspections:  these are fundamentals of engineering that we are using every day, but are not being discussed directly in our conversations about our environment, resources, goals, and what we are going to do to achieve our goals.<br>
<br>
This lack of introspection of our process results in a lot of miscommunication, and different visions struggling for the chance of being implemented, but without the necessary alignment between all the points of implementation to give us the kind of efficiencies, resiliency and other effects that we desire.<br>
<br>
Having this vision requires being able to see "the big picture" as well as the details, and it is important to be able to go from detail to big picture, back to details again repeatedly to see what any proposed changes will mean with regard to aligning with the rest of our details, to create the final result which occurs when all of those details are taken in whole.<br>
<br>
This is the methodology I use in designing any solution, and I will try to describe it in enough detail that you can inspect the process for yourself and can hopefully positively supplement your current methods for doing similar activities.<br>
<br>
One thing about "vision" is that it is something that takes a bit of experience to be able to see.  One needs to have had personal experience implementing things to really know what effects will result in the implementation, and across enough areas of the environment so that one can see how things align well or do not align well.<br>
<br>
This experience is less about how many years one has worked in an industry or environment, and more about the experiences one has had in one's lifetime.  <br>
<br>
If you have never worked in the industry before, you will not know how organizations that run production operations, especially internet facing production operations at large scale (which I use as an extreme end of the scaling spectrum), will function and what changes will do those organizations and operating environments.<br>
<br>
The more you work in different environments, and complete more areas of implementation, the more experiences you will gain.  You can supplement these by setting up your own virtual environments on any cloud hosting providers, or on your own machines with a series of virtual machines.<br>
<br>
All projects, whether in-industry or outside of it, are limited, and never give complete information, because one's viewpoint is limited and the amount of details one can interact with is limited.  So even if you know one environment from beginning to end, having created all of it, you will find another environment that you didn't create to have many different properties, even if all the software used is the same, due to the alignment choices made in it's creation.<br>
<h3 id=7bdf31941d762810d8c81c360d28d38c><a href="#7bdf31941d762810d8c81c360d28d38c">2.3.2</a>: An Explanation of what Operations.  And why every company is an Operations company (internet or not), and how now almost every company is first and foremost an Ops company, though almost no companies recognize this.</h3>
<br>
This section could be headlines on the front page of any magazine targeted at CIOs, and so may seem a little fluffy and self-serving.<br>
<br>
Sales people think of organizations in terms of their sales generating revenues.<br>
<br>
Developers think of organizations in terms of the software they write, which may be sold to generate revenue.<br>
<br>
Managers think of organizations in terms of the people they manage that do the work.<br>
<br>
Customer Support thinks about organizations in that customers would be completely dissatisfied without their support.<br>
<br>
Finance thinks about organizations in terms of cash flow, as when an organization runs out of money, they can no longer pay their building leases or employees.<br>
<br>
Etc...<br>
<br>
Each department in an organization thinks it is a critical department, and they are all right.  No organization would pay the financial and opportunity costs in maintaining any department that is unnecessary, so they are all critical.  Operations is no different here.<br>
<br>
There was a time that operations was a lot more like Facilities departments, they bought things and maintained them.  Keeping them powered up and plugged in, and keeping people from stealing or damaging them.  This is not really accurate, but from the perspectives of people paying for these employees, it is pretty close to accurate, and we are currently discussing how organizations see themselves and their actions, and organizations act through using money to pay for services.<br>
<br>
What has changed, and what companies have for the most part not caught on to yet, and it will behove operational engineers to start repeating ad nauseam is operations is now the front-line of many companies ability to collect revenue.<br>
<br>
This started changing for many companies in the late 1990s, and started to become normal in the 2000s, and by this current 2010s almost every company's interactions with it's customers are going through a network, to servers, and software and databases that run on those servers.<br>
<br>
The majority of the companies I have worked for have completely downgraded the importance of their operations departments, giving much more staffing and scheduling priority to other departments.<br>
<br>
There are a number of reasons for this, and they are all valid in themselves, as many perspectives are when given in their own context.<br>
<br>
However, in a context that is grounded in the physical world the connection to their revenue might look like this for different companies, starting from the least-technological and moving to the most:<br>
<br>
- Physical good company.  Makes things that are sold in metal cans, etc:<br>
	- Supply chain management has a basis in digital records at every step.  Some steps involve calling people, writing things on paper, but these are recorded in at least Excel type spread sheets, and at any larger organizations something more similar to an Enterprise Resource Planning (ERP) software to coordinate all the steps are required.<br>
<br>
	- Communication with vendors in the chain may have many physical components, but ultimately they are also recorded into digital mediums, at least the low-level of email, if not higher level tracking software.<br>
<br>
	- Employee time and pay records are now kept in a mostly or purely digital form.<br>
<br>
	- End-user support is typically done via electronic medium (emails, customer support) to <br>
<br>
	- The larger the organization for all non-Internet based companies, the more corporate infrastructure that will be needed to provide support to desktops, laptops, servers to manage directory services (AD/LDAP), backups, storage, centralized software, etc.  More of these services are moving into online-only for small-medium companies.<br>
<br>
	- Hold outs will be older (pre-PC age computers) and will need to be small, to maintain operating the manual labor scales<br>
<br>
- Non-Internet Services Company<br>
	- Similar to physical companies, but with more smaller companies that can get by without much technology.  Real estate agents are a famous example of this.  Doctors and lawyers are also slow to adopt technology in tracking their clients and work, but in most medical institutes I have seen recently, all patient visit tracking is being digitally tracked.<br>
<br>
- Physical software companies<br>
	- Software is sold in boxes, in stores or shipped via the mail on DVDs.<br>
<br>
	- All software is written in a networked environment which must remain up for any productivity.  Developers cannot all go home and continue working if the infrastructure going down, and as security levels increase, this is not possible for those reasons as well.<br>
<br>
	- Customer support is usually entirely digital, unless it is for Enterprise level software, and then there is phone call and occasional in-person visits as well, mostly as good-faith efforts, not to solve immediate problems.<br>
<br>
- Internet Service Companies<br>
	- This is where the real change occurs, and many businesses are becoming more Internet service oriented.<br>
<br>
	- Almost every interaction the company has with end-users/customers is over the Internet, and handled by servers that the company manages, and may or may not own/lease.<br>
<br>
<br>
This is a very simplified spectrum of business, and not meant to be correct or truly representative, but merely to paint a quick picture I need for this example, which I'll start describing... now.<br>
<br>
<br>
The change is that these days if your operations is not reliable, and you have frequent outages, or long-term degraded performance, or you are unable to respond to customer demands in a "reasonable" time, or competitors have a more reliable and reachable service, then you are directly impacted in your revenue.<br>
<br>
If your operations is down, your customers cannot reach you to pay you.<br>
<br>
As someone reading this book, this is no surprise to you, but what may be somewhat surprising is that many companies I have worked for, and you may have as well, display all the symptoms of completely not behaving like this is true.<br>
<br>
Some of these symptoms are:<br>
<br>
- Not properly staffing their operation teams for the workloads they are required to perform.<br>
<br>
- Not giving proper lead times on work that is due, such as finishing a project that the operations team was not notified about, and expecting an immediate release to the public of that project.  Not taking into account either ordering hardware, or configuring systems to support the software.<br>
<br>
- Not giving significant information on how to maintain, run, or even install the software to be released and supported.<br>
<br>
- Prioritizing work that does not yield to improving or supporting the revenue generating and employee supporting software and services.<br>
<br>
There are many other symptoms, but these are large enough to illustrate this point.  Other departments have similar complaints with regard to notice ahead-of-time, and schedules.  See any book on Software Development project management for examples close to operations.<br>
<br>
This is not a problem that is likely to be solved soon, if every solved, because there are a number of difficult factors that cause it, the primary one being the structure of organizations themselves.  When something is structure a certain way, it will tend to produce certain results, and producing different results is very difficult, and often only temporarily possible.<br>
<br>
Since the organizational structure of organizations is not likely to change, the best hope in making progress here is something akin to the Agile movement in development, where all developers just kept repeating the same things and eventually the management of companies started to be populated with managers who also said the same things, and their world changed.<br>
<br>
It's debatable on whether their world really changed that much for the better, but there are many distinct differences in the pre-Agile development world, from the post-Agile development world, and it was this change in perspective and discussing it that caused those changes to take effect.<br>
<p id=5bc4c817bd8491f2de4fcd4fa234cca9><b><a href="#5bc4c817bd8491f2de4fcd4fa234cca9">2.3.2.1</a>: Their ability to stay online and available and provide their service is what keeps them making money.  How is this not a core-service?</b></p>
<br>
One concept that organizations have a pretty good grasp on is "core services".  They understand there are some services that they cannot outsource to other organizations and remain an efficient operation.<br>
<br>
The core-est of these core services are: management, finance and human resources (HR).<br>
<br>
Almost no organization outsources its' people managers.  They are the most core-service that a company has.<br>
<br>
Similarly, there will almost always be at least 1 to several people in the finance department, even if they use external services for many services that used to be hired in-house.<br>
<br>
HR in the past decade has begun to be outsourced, but once a company reaches a certain size, they always have their own HR departments.  This is the same for legal services, though this can be configured in a number of ways for companies, so I'm not listing it as a core service.<br>
<br>
Many companies outsource their development departments, and many companies also try to outsource their operation department, though this does not usually last long, and they may try to stick with it by turning their developers into their operations staff, but eventually some people will end up being the de facto operations team, regardless of their titles.<br>
<br>
If a company is primarily a software or internet service organization, and these are the types of companies I focus on, so they will be the majority of what we spend time inspecting, then they are much less likely to outsource their development departments.<br>
<br>
They realize the developing software is a core business service, and without direct control of their developers and efficient communications, they are unlikely to make consistent progress.  Many companies that try to outsource this department end up moving it back into their company after poor experiences, unless the product being developed itself is not all that important to the company, or can be treated as a throw-away product (like a phone application they only need to do XYZ "well enough").<br>
<br>
This is all a pretty subjective description, and I won't use up the space to turn it into a more objective one.  You should review your own experiences with these descriptions to determine how accurate they seem to you.<br>
<br>
The point of this discussion on core services is that for any company that relies on Internet or networked services for revenue generation, their operations department is not only a core service, but is often the front door to any other services.<br>
<br>
If their operations is not available, or performance is significantly degraded, then their customers and partners are not able to use their services, and they cannot generate revenue.<br>
<br>
This would be similar to sales people losing the ability to contact customers, completely making that department unable to provide benefit.<br>
<br>
If a company develops software, and end-users cannot reach that software, then there was no reason to develop it.<br>
<br>
This is where operations sits in the revenue chain, and companies are not yet currently recognizing the important distinction.<br>
<br>
I have used many similies for this over time, such as:<br>
<br>
- Operations is like the tires of the car.  We are the part of the car that comes into contact with the road.  Your driving can only be as good as your traction against the ground.  If you lose a tire, your ability to drive is severely impacted or not possible. <br>
<br>
- Operations are like the roads.  You can have a fleet of cars or trucks, but you cannot efficiently move them around without roads to provide consistent surfaces.<br>
<br>
A lot of people shop for cars, but not a lot of people are involved in the building or maintenance of roads.  This is similar to many people using networked services, but not being aware of what it takes to build or maintain them.<br>
<p id=109a7a222581029b6b3ed44aeb36acbc><b><a href="#109a7a222581029b6b3ed44aeb36acbc">2.3.2.1.1</a>: Just because its Core doesnt mean they need to own all of it, but as they grow they will pay more and more for what they do not control, and control well.</b></p>
<br>
A service may be a core service, but that does not mean all of it needs to be internally owned and operated.<br>
<br>
Cloud datacenter operations and Software-as-a-Service (SaaS) have changed the way many companies perform their internal and external operations, and has provided new ways for many engineers to think about solving problems.<br>
<br>
Just because you are paying someone else to maintain hardware or software for you does not mean that you do not need to manage it.  Some SaaS products do not require much management, but other still requires one or more full time staff to help manage it for the rest of the departments.<br>
<br>
For machine and datacenter operations, having Cloud offerings like Amazon or Googles offerings does not stop operational work from being created, it only raises the bar on what type of work is required.<br>
<br>
The basics of buying machines, racking them, cabling them, keeping them physically functioning (replacing disks and RAM, etc) and doing basics like assigning their primary IPs is taken care of for you.<br>
<br>
Everything above that level is up to you to manage, and these are the more complex problem areas, as the lower level areas are more logistical, scheduling and manual labor intensive.<br>
<br>
Who will manage all of the rest of the decisions and life-cycle maintenance problems that your network services require to function properly?<br>
<br>
Whoever they are, whatever you call them, they are your operations team, and are providing the operational core services for your organization.<br>
<br>
Outsourcing works up until the point where you lose Control that you need over the environment.  At some scaling point in every organizations usage of an external service, their needs and the services offerings will start to part ways, and the service will start requiring more work than previous to perform the same benefits for the organization.<br>
<br>
Once this reaches a critical point, either though financial cost, personnel time cost, or cost in terms of outages, degraded performance or misalignment in terms of providing the kinds of services the organization requires.<br>
<br>
Once this point is met, there will be a new transition where the problem areas are migrated to another service, which it is hoped will solve these problems, or the services are migrated in-house to be internally managed.<br>
<br>
At present the financial costs alone seem to be consistently measuring up like this:<br>
<br>
- Internally managed infrastructure.  1x cost, of hardware, data center and network services to provide an operational environment.  This is the base-line, doing it yourself.<br>
<br>
- Managed services that are comparable to doing it yourself, but letting others do it for you, about 3x the base-line cost.<br>
<br>
- Using cloud services, where you manage all your infrastructures through a virtual interface is about 5x the cost of doing it yourself.<br>
<br>
This is highly subject to change, as many things are involved in pricing, but as of 2015, this has been accurate in all the measurements I have made in about 10 environments I had direct internal access to, from 2008 to 2015.<br>
<br>
What are the differences in cost in your current environment, between total ownership/leasing, managed services (someone else buys/leases and maintains), or going completely virtual?<br>
<br>
You should know these differences, as they will make data points in decisions on how to run your departments as the costs start to outweigh the benefits of any solution.<br>
<br>
This 1-factor look at the problem, finance, is not a "big picture" view, it is only a single detail, so there are many other factors which make using services that may be 5x or 3x as expensive, and provide worthwhile benefits, such as the total cost being low enough to be worth it, or the faster turn around time on new machines, or not having decided on the hardware requirements to make it practical to start ordering hardware yourselves.<br>
<br>
There are many more factors in this, and we will get into some of them later, but they are not the focus of this book, so we will not cover them comprehensively.<br>
<p id=0932b206900bdd69c2b6cc7a46dfee68><b><a href="#0932b206900bdd69c2b6cc7a46dfee68">2.3.2.1.1.1</a>: Typically companies still dont tell ops departments that they need anything, until its due, all decisions are done, and its time to roll out.</b></p>
<br>
The problem of communication between departments, especially in regard to lead times between knowing they need work to eventually be done, and when they alert another department or team that they need that work done is such a classic problem that we can just assume it will happen everywhere, in every circumstance, unless people do something to change the pattern.<br>
<br>
In places where departments are giving each other prior notice of work coming down the pipeline, and involving the teams they will need to do that future work in the design phase, it is very likely that this was set up on purpose, and either by "visionary" early employees or founders, or through great work of some individuals to make changes to the de facto process of only asking for work to be done, when it is at the end of the project and time to release.<br>
<br>
I say it's most likely that this is the problem, because I have only worked in a couple environments, out of a large number of environments, where this happened as a normal occurrence.<br>
<br>
The point I am making is that one shouldn't be surprised when another department or group arrives and says they have finished a project, and they "just need it deployed into production", and has no time available in their release schedule for doing things like:<br>
<br>
- Productionizing the release process<br>
- Productionizing the configuration<br>
- Doing security audits and fixes<br>
- Writing an operational manual with support play book, enumeration of error codes, instructions as to options<br>
<br>
Frequently projects just being released into production do not have good performance tests done of them, although this happens more frequently than others, so I'm not including it in the above list.<br>
<br>
One of the lessons it took me a very long time to learn, but has served me well since learning it, is that if you recognize a pattern as occurring regularly, it is better to simply plan to deal with that pattern than to put up any resistance to it's existence.<br>
<br>
What I mean by this is not to get upset when you are given these types of projects, and they require immediate action, and things are requested to be done "wrong" and they cause havoc with the clean environment you are trying to make.<br>
<br>
Instead, see them as failure to get ahead of a pattern that occurs so frequently that you can simply assume that there are cases in process of coming to you right now.<br>
<br>
Knowing this, how do you get ahead of this problem?  You can't completely solve it, as it requires cooperation from other people, and the root of the problem is that they themselves aren't coming forward to cooperate before they normally would.<br>
<br>
Some things you can do:<br>
<br>
- Regularly, say every month, send out a standard template communication (email, etc) to all departments asking if they have any projects that will coming down the pipeline and will need operational resources.<br>
<br>
- Describe in the communication what "requires operational resources" means, such as machines in production, adding a new service, making changes to services which aren't already in production or that the operations department doesn't know about, etc.<br>
<br>
- Describe any lead-times you require for these types of projects.<br>
<br>
This is the direct-but-passive communication approach, and will allow people who are up for communicating ahead of time to communicate with you in a way they can understand is helpful.  This will not catch all new projects.<br>
<br>
From there you can also create a department policy, document it in your online documentation site (wiki, etc) as to how you accept new projects, and when people ask you for them,  you can refer them to the "new project on-boarding" documentation that describes how you would like to work.<br>
<br>
This provides some "back end" type protections, as people will see that they didn't communicate with your regular email, and now they are learning how the operations department works.<br>
<br>
But this will still not stop any externally set schedules, as if the company requires a product is launched on a given date, then this is a higher priority than following any department's self-appointed rules, and will override them in many circumstances.<br>
<br>
The direct-active approach is the best, but requires more resources, this would be someone who is acting a department project manager would meet with the other department heads or team managers directly, and ask them what they are working on, and when they will need operational resources.<br>
<br>
This direct-active approach is more likely to be successful, as the managers will know what projects they are working on, and are not trying to hide their project's work, they are simply working to complete their projects, and in this way you are assisting them in getting to the final steps of completion.<br>
<br>
If this can be approached in a "let us help you" manner, then collaboration can begin, and hopefully will improve the working conditions for everyone, as handing off work between groups is a difficult process.<br>
<p id=d05edb2ae926b6b3071c2d16497f5721><b><a href="#d05edb2ae926b6b3071c2d16497f5721">2.3.2.1.1.1.1</a>: The ops department is blamed for all lag.  Developers are blocked, legitimately and not-legitimately.</b></p>
<br>
A look at the more negative side of this problem between groups is that the operations departments are often claimed to be creating lag between work being completed by other teams (typically development, sometimes marketing or business development).<br>
<br>
From the perspective of the non-operations teams, this is a true statement.  They finished their work, and now they want to put it into production for end-users to be able to access, and any time between them being "finished" and the end-user being able to access the work is considered lag created by the operations department.<br>
<br>
The issue here is one of "someone else's problem", which comes down to empathy and a realistic view of the nature of all work involved in a company, not just one's own work in the company.  This is not a problem that can be solved directly, as people's ability to appreciate other's positions is not going to change easily, or deterministically.<br>
<br>
So what we can do is to look to ameliorate this problem as much as we can, by getting ahead of the requests.  This means having a process that people can easily follow to getting what they want.<br>
<br>
For example, create a limited set of Hardware Specifications that you purchase, for any generation of hardware.  The typical basics of this as of 2015 are usually a "utility" class machine, a "relational database" class machine, and a "non-relational database" class machines.<br>
<br>
To simplify what we call a Hardware Specification, let's use the acronym for Stock Keeping Unit (SKU), which is very general.<br>
<br>
Utility class machines are for running general purpose software, and typically are mostly used for web and application services in production.  There may be two SKUs if there is a "low memory" and "high memory" version.  Caching services (memcache, redis) usually use a low amount of CPU, but a high amount of RAM, and may reside alone on machines due to their critical nature.  Utility machines typically do not need much in the way of storage, and almost any small redundant disks are good enough.<br>
<br>
Relational Database class machines are typically used for relational SQL databases like MySQL, PostgreSQL, etc.  They need both a lot of RAM, a lot of cores, and they need very fast disk.<br>
<br>
Non-Relational Database class machines are usually running software like Hadoop, Cassandra, or any of the other many column-oriented databases that are better at storing logs, events, time-series and other databases.  They typically need a lot of CPU, memory, and much more storage than relational databases.  If a relational database might need 5TB of storage, a non-relational database might need 30TB, or something in this type of proportion.<br>
<br>
Starting with these 3 base SKUs, and perhaps several sub-SKUs for more RAM, you can offer departments easy choices for how they want to deploy their software.  Providing them virtual machines for some services may also be a good match, depending on their usage patterns and criticality.<br>
<br>
For each type of request they are likely to make, having already worked out in advance what options they will need, in a sort of restaurant-like menu, will allow you to make the requests more streamlined, and work better with your organization.<br>
<br>
You can add SKUs if necessary, when they have a strong need (for example, a large order of systems that have a usage pattern that do not match any of your existing SKUs), and otherwise they have an easier by simply selecting what seems best to them.<br>
<br>
This can also be done for:<br>
<br>
- Networks:  Have set ranges of IP space that you assign to a given network, such as standardizing on /23, /22 and /20.  If you only create server networks of these sizes, then it should be pretty easy to size them appropriately for a given request that needs their own network.<br>
<br>
- Load Balancing:  If you have a pre-determined set of options say using SNAT with X-Forwarded-For for all web services, then you can announce that early, and avoid running into problems where web applications require the source IP in the request.<br>
<br>
- Host names: As we went over earlier, there is a lot of information stored in names.  If you give a guideline of what your convention is, and how to apply that convention to various configurations, you can avoid being requested to make names that do not fit the convention, as you have already described how to take their configuration and put it into your naming convention.<br>
<br>
- Accessing production machines:  You should have a security policy that can be applied in a standard way to all requests.  Do you allow root logins?  Root escalation?  Sudo?  Role accounts?  Copying data to machines?   You should write each of these things down, and where you do not allow something, you should have a method for how to accomplish that goal in a manner that is consistent with your security policy.  If you do not do this, people will just work around your enforcements and create many messes as everyone does it slightly differently.<br>
<br>
It is unlikely that people who perform different roles will start to become empathetic that the work done in others' roles really does take expertise and time, since we have so much history of people not having this empathy, but we can do things to try to bridge these gaps by being aware of them and tuning our behaviors accordingly.<br>
<p id=565cd0fce08c8934484649d6a9f5b105><b><a href="#565cd0fce08c8934484649d6a9f5b105">2.3.2.1.1.1.1.1</a>: Everyone doing everything themselves is great for a boot-strap project, but just does not work in a Mission-Critical environment.  Launch NASA rocket with newbies running things?  No, experience is needed for precision and taking into account All The Things.</b></p>
<br>
One important component of all operational environments is standardization.  At the extreme end of that spectrum would be uniformity and at the other extreme everything is unique:<br>
<br>
Everything Is Uniform <---> Everything Is Unique<br>
<br>
Since we know that not everything can be uniform, since we are already starting with a base of 3 SKUs (Utility, Relational Database, Non-Relational Database), that side of the spectrum is already constrained.<br>
<br>
However, it is completely possible to have an "everything is unique" operational system, and this might be labelled something like "operational hell", where everything is a special snow-flake one-off case.<br>
<br>
In an "operational hell" environment, no change can be assumed to work for more than 1 specific case.  That case must be inspected just prior to being modified, because it could be in any type of state or configuration at all, and the only way to have reasonable confidence that the change will not break things would be to look at everything going on on the machine, all configuration, all currently running processes, and to determine through expert-understanding that the planned change will work with the existing configuration.<br>
<br>
This is the most dangerous type of environment to work in, with regards to uptime, stability, efficiency, and all the other positive attributes we want to imbrue our operational environments with.<br>
<br>
All it takes to create an "everything is unique" environment is to let everyone solve every problem in the way they see best, at the time they got the request, without communicating the changes to others, and aligning the changes so that they follow a planned path.<br>
<br>
Many requests into operations will diff from previous requests in some way, making it impossible for the current request to be handled in the same fashion as the previous request, because of those differences, but still the methods used to take care of the previous and current requests could be aligned with one another.<br>
<br>
This type of alignment does not come for free, and it does not come naturally.  It is a process that must be learned, and it takes coordination of all the different members of a team to work together in ensuring that this alignment takes place.<br>
<br>
Alignment itself has a spectrum, and is best seen at different levels of details.<br>
<br>
We can "block box" anything into:  Inputs, Outputs, Side-Effects<br>
<br>
Inputs are what comes into the black box, say HTTP requests for a web server.<br>
<br>
Outputs are what comes out of the black box, sat the HTTP response for a web server.<br>
<br>
And side-effects are what happens beyond the outputs, say that a database is updated, and a memory caching server is updated, and logs are written to storage.<br>
<br>
Black boxes are an appropriate level for a group to be able to discuss alignment, as getting into implementation details of how a web server is configured should be left to the sub-team that deals with that web server. <br>
<br>
This is to allow people and sub-teams autonomy of action, as centralized planning cannot deal with all details and all contingencies efficiently, while still allowing a larger centralized inspection of the black boxes, to achieve a total operational system alignment.<br>
<br>
There's a lot involve in this, and we will be going into more depth as we move from philosophy and general issues into implementation.<br>
<p id=e08a32902b4d3960b8ee560f8851f34f><b><a href="#e08a32902b4d3960b8ee560f8851f34f">2.3.2.1.1.1.1.2</a>: Balance to this.  What can be self-service, and what cant.  PaaS for production, IaaS for development and Ops usage.</b></p>
<br>
One goal for an operations team that has decided they want to get the benefits of comprehensive automation is to provide more and more self-service tools to the departments they support.<br>
<br>
The benefit for the operations team is that they can remain more focused on improving infrastructure, rather than performing requests that were made by other teams to simply set up, configure and change existing infrastructure.<br>
<br>
There is also a spectrum of productivity to this:<br>
<br>
Handling Requests <---> Improving Infrastructure<br>
<br>
The more of the operational team's resources (time, people) that are committed to processing requests made from outside the team (other departments, higher management), the less time the team is able to work on improving the infrastructure that exists, including improving the ability to handle the incoming requests in the first place.<br>
<br>
I have worked in many organizations where the operations team spends nearly all of their time performing requests, and almost no time improving the infrastructure, and as a result the infrastructure becomes more and more fragile as request after request is done in a manner that is not scalable or supportable, but is required to meet business timelines and direction.<br>
<br>
Achieving business goals is the reason all departments exist, so this is a good thing, in itself, but it can be performed in a manner where the business begins to not operate efficiently, and eventually starts to fail frequently, causing harm to other business goals, such as customer retention, which effects revenue.<br>
<br>
In order to handle requests efficiently, the infrastructure must be one that can reasonably be altered to support this requests, and as the business changes in scale, scope, and direction, this takes either a very well put together operational environment that is made to be changed quickly in these manners (possible, but difficult to assemble, and easy to turn less-functional), or it requires time before requests are done, to prepare the environment, or more time after the requests are done to fix the system after the fact.<br>
<h2 id=7ef5e6c23b6cb4359f88aea566c255fb><a href="#7ef5e6c23b6cb4359f88aea566c255fb">2.4</a>: What is a System?</h2>
<br>
There are a lot of ways the word "system" could be used.  We're going to look at a general version of the word first, and then a specific version for our exact purposes afterwards.<br>
<br>
When I was growing up and for the first 10 years of my career, operational engineers were called "System Administrators".  Today some people use this term derogatorily as lower-level or older style work, and while anyone can have any perspective they'd like, this is not consistent with history.<br>
<br>
I was lucky enough to spend some around professional system administrators throughout the 1980s, before I was old enough to work, and I got to see them doing core dumps and reading through the hexadecimal output to find where the problems in their code were, and even fix some problems through a hex editor.  I also got to get a bit of their practical advice and viewpoints, and I believe that after 5 or so years of professional operations work the lessons I saw back then started to filter back in to be more conscious rather than subconscious guides and role models.<br>
<br>
So what is a system?  Historically, in the computer industry, a system was often referred to as a single machine with an operating system on it, and the environment that was then configured on top of that to create a working environment.<br>
<br>
So a system was sometimes a machine's hardware, an operating system was also a system, and the eventual configured environment was a system.<br>
<br>
One of the interesting properties of the word "system" is that all of these things were and are true.  And all of these things together are also a system.<br>
<br>
A system is an generalized term for a set of interrelated, connected things that work together to produce effects.  Like anything, it is black-boxable into inputs, outputs and side effects, and has sub-components which can be similarly black-boxed, etc.<br>
<br>
So a system is a flexible term, and is something like an "environment" or an "ecosystem" in common usage.<br>
<br>
I like to think of systems as being somewhat like virtual machines, in the actual sense not in the container operating system sense.  A system's connections can be graphed, like a network, and each component and be described by the inputs, outputs and side effects it causes, and may contain many layers of other systems, and may be part of a bigger system.<br>
<br>
Why is any of this important?  Because your understanding of how systems works will determine your ability to mentally map the systems that you work with, so that you can think in terms of how those systems function.<br>
<br>
Without having this mental mapping, and having a mind that over time becomes more and more comfortable learning about systems, and understanding system intra-action and interactions, one will have gaps in their understanding.<br>
<br>
These gaps are perfectly fine if they are properly black-boxed to create a comprehensive system, where you may not know how memory data is shuttled between the RAM chips and the CPU, but you have a model for how this works, and that model, while not physically accurate in detail, has a strong correlation to reality and can be used to make good decisions and predictions.<br>
<br>
We will go deeper into Modeling in the future, but building accurate models of the systems you are working with is an important part of operations.<br>
<br>
When someone has a poor Model they are working with, they will be confused by things that occur, and are likely to have "magical thinking" ideas, like "out of nowhere, X just happened".<br>
<br>
When someone has a good Model and "X happens", they can see that X is related to Y and Z, and without first Y occurring, and then Z occurring, then X could not occur.<br>
<br>
They can trace this backwards and confirm that indeed Z occurred, and Y occurred, and so of course X was going to occur in sequence after them.<br>
<br>
For a common example of this, a web server starts to fail, and on inspection the disk is full, and on further inspection no log rotation was configured, and so the web server failing is a mechanical response to the disk filling up, which is a mechanical response to not having logs being rotated.<br>
<br>
If you do not rotate logs (or truncate them), then with any activity at all, it is guaranteed that eventually the disk will fill up, and any services which might use the disk for writes (such as logging) will fail.<br>
<br>
This is a simple system, and indeed anything can be turned into a system.<br>
<br>
The power of Systems is that they can be created at any time, to describe any thing, provided you are capable of properly black-boxing the components of the system you want to construct.<br>
<br>
You do not need to constrain yourself to existing systems, that other people have described, even when working with their work which have their own systems already described.  You can create your own systems for your own purposes.<br>
<br>
You might create alternative systems to simply understand other people's described systems.  Sometimes it is harder to understand someone else's work than your own, and so creating your own work can illuminate a subject.  <br>
<br>
As an exercise while you read this book, try to create your own systems based on "the big picture" to understand what is currently being discussed.  As new information comes in, update your system to reflect these changes.<br>
<br>
You can do this on paper, in your head, you can find software that helps you create systems quickly (like Mind Map software), or use relational databases to track discrete data.  Flow charts are one way to map systems, finite state machines are others ways, behavior trees are another way, but you can also describe them in prose, or doodles or any other way.<br>
<br>
How you describe a system is merely a view into the system, and will never cover every aspect of a system.  Only the actual components of a system describe the system, and any attempt to review the system will only give a partial insight into it.  Systems are tricky in this way, but this is also where their power comes from, because they are not limited by them either.<br>
<h2 id=61fc96e11d2dd57966d2b5b014f1a2dc><a href="#61fc96e11d2dd57966d2b5b014f1a2dc">2.5</a>: Systemic Thinking</h2>
<br>
System Thinking is one of the tools that I believe is the most powerful, and could use a lot more of the educational spotlight.  In terms of yielding positive results in learning, creating things, and in performing maintenance (in a very general sense), system thinking is one of the most useful tools.<br>
<br>
System Thinking has a number of prerequisites, such as a general understanding of how systems work, how to create systems, how to modify a system, how to inspect and evaluate the connections and links between system components, and a good basis in critical thinking.  Having the ability to thinking deductive is critical.<br>
<br>
If you have not yet read a book on critical thinking, you should to ensure you have down the basics of the topic.  Deductive and inductive thinking, boolean logic, and set logic are primary tools for doing analysis, and any troubleshooting of systems will be significantly improved if you can break things down to terms and evaluate them.<br>
<br>
How do you use System Thinking?<br>
<br>
The first thing to do is to take whatever you are thinking about, and turn it into a system.  Anything can be turned into a system, and this system can be as large or small as you need, and can contain any number of components.<br>
<br>
Since we, as humans, are limited in the number of things we can think about simultaneously, on a conscious level especially, we need to break things into small groups of related ideas.<br>
<br>
Let's create a system right now and do some reasoning with it, to use as an example.  We will continue to use the web server analogy, as it is one that many people will already be familiar with, or will probably spend a lot of time dealing with in their careers.  You can think of this as an "Application Server" instead of web server if you like, the important thing is that it takes requests and servers back data.<br>
<br>
In the simplest of web server systems, we have static content serving.  This is when someone has pre-created text (HTML, CSS, etc) and binary (images, videos) and the web server's job is to take requests for specific static files, and to relay those files to the requester.<br>
<br>
Since we can create a system out of any components, let's decide what our components will be:<br>
<br>
- A network connection to the Internet, which end-users are making requests on.<br>
- The IP protocol for networking, and basic TCP session management, on a Linux server.<br>
- A web server that listens on TCP port 80 on that server.<br>
- A file system that locally contains system files.<br>
- A file system that locally logs requests and processing.<br>
<br>
This is a slice of components involve in web process, and just as I have arbitrarily picked these for this example, you can pick any components you want to build your own systems.  You can continue to refer to the same system over time to get more familiar with all the details of that system, as is important in operational and application documentation, or you can abandon the system as soon as it's immediate purposes are over.  Systems can be used forever or can be completely ephemeral, they are abstractions for reasoning and understanding reality, which remains too detailed and complex for us to directly understand.<br>
<br>
Let's create an event that occurs and exercises these components, as a sequence:<br>
<br>
- An end-user requests a file from the remote web server: http://www.domain.com/images/unstoppabletrex.png<br>
<br>
- The request performs operations outside of this system (LAN, routing, DNS, etc), but eventually opens a TCP socket to port 80 on the web server.  The web server and the end-user now have a persistent session to communicate bidirectionally.<br>
<br>
- The end-user requests the URL specified above (broken into URI and Host Header sections), and relays any cookie and browser header information.<br>
<br>
- The web server accepts the input of the request, and goes through a process of routing the request internally, where it matches the domain in the Host Header value to any Host Headers it processes, and then determines if there are any directory modifications to look for the static file.<br>
<br>
- Having determined what the path of the static file is on the local file system, if the file exists, the web server opens the file, reads it, and relays the data into the content section of the HTTP response.  After relaying the contents, it closes the file, creates a successful HTTP status code, and returns the results.  In this case we will assume that HTTP keep-alive is not enabled, and the HTTP server will close the connection afterwards.<br>
<br>
- The web server logs the request and successful response, appending to it's access log on the local file system.<br>
<br>
- The end-user's web browser will have received the HTTP response, getting the status code and body of the content, and in this case will display the image to the screen.<br>
<br>
This is one way that a request event could be processed by a web server.  We can similarly model of the file does not exist, the web server may do something similar, except return a 404 File Not Found static content.<br>
<br>
In the case of a more dynamic system, the web server could proxy the request to an application server, which then makes database calls and performs formatting logic, and then returns a dynamic result instead of a static one.<br>
<br>
The important of systemic thinking in this is that there are no gaps.  Every connection that is required is modeled, and if new connections are required, they are added, and the remaining components need to be updated so that the system remains internally consistent.<br>
<br>
Internal Consistency is a very important factor in any system, for it to be a properly functioning system, and will be another topic we delve into deeply.  Internal consistency has similarities to Alignment, where components are aligned with one another for maximum efficiency, but Alignment requires Internal Consistency, where something can be Internally Consistent but not aligned.  In this way Internal Consistency is a super-set of Alignment, in order to be aligned, things must be consistent, but things can be consistent and yet not well-aligned.<br>
<h3 id=03071c27c692b17c5d7f95b9d4f021a4><a href="#03071c27c692b17c5d7f95b9d4f021a4">2.5.1</a>: Philosophers Knife</h3>
<br>
One important tool in creating systems is the concept of the "Philosopher's Knife".<br>
<br>
This is a virtual knife, meant for cutting ideas into sections.<br>
<br>
The most basic way of dividing ideas is to split them in half.<br>
<br>
For instance, you can say something is "Black or White", and then take any concept and add it into the "Black camp" or the "White camp".  This is a basic process of sub-division with things that appear to be opposites.  In subtractive light frequencies, black is the absences of color, and white is all of the colors.  In additive pigments, black is the combination of all pigments required to absorb all frequencies, and white is the absence of pigments that absorb frequencies, so that the frequencies are refracted and appear to be total spectrum, or white.<br>
<br>
Being able to divide things in this way is a useful tool, but it is also a primitive inspection of the information, and in fact creates a frame that excludes almost all data.<br>
<br>
For instance, in making the split between "Black and White", the frame of reference created ignores that fact that black and white are both colors, which means they are very similar to each other, and much less different from each other than say the word "duck".<br>
<br>
If we took the sets of "Black, White" and "Duck, Goose", we see that black and white have much more in common with each other than duck and goose.  Because of this, even though in our first example we contrasted black and white as opposites, they are in fact much more similarly related to each other than many other things.<br>
<br>
This is both the power and the limitation of the philosophers knife.  It can reveal differences, and it can obfuscate similarities.  How you use it will depend on the results you are looking for, and your skill at applying this technique to create those results.<br>
<br>
For our purposes, we are looking at how to use the philosophers knife to sub-divide systems, for the purposes of Systemic Thinking.<br>
<br>
The most important element in creating a well-cut concept into a system, is that nothing is left behind.  The use of the philosopher's knife should account for all components and options of a system, and while it is sub-dividing them, they never lose their whole.<br>
<br>
Their "whole" is what makes up the "system".  If you lose a part of the system while sub-dividing it, you have not correctly used the philosophers knife.  This will be important when designing your system, implementing it, and troubleshooting it, or in creating a Model to understand an existing system.<br>
<br>
Let's first use our previous example of the static HTTP web request.<br>
<br>
I used the philosopher's knife on the system of "making HTTP requests from a web server over a network" to come up with 5 elements of the process:<br>
<br>
- A communication network (Internet): part of the environment.<br>
- A protocol and environment (TCP/IP on Linux): part of the environment.<br>
- A request handler (web server on TCP port 80): the Input to the black-box.<br>
- A content location (static files on local filesystem): a component of the Output to the black-box.<br>
- A log location (appending results to log file): a Side-Effect of the black-box operation.<br>
<br>
I could have sliced this in a different manner, and instead focused on the TCP packet exchange, or I could have cut it so we delved deeper into the end-user's process of getting it's request to the web server (LAN, routing, DNS, TCP handshakes, etc).<br>
<br>
I was able to slice this process into the layer's I chose, because I wanted to discuss those elements, and not other elements.  This ability to exclude what information is being inspected, while not losing any of those excluded areas of data in the total picture is the real power of systemic thinking, is the function of the philosopher's knife in this process.<br>
<br>
We can take the exact same example process, and re-slice it any way we want, and the events would be the same, but in the information we look at, and how we inspect it would be different.  The system has not changed, the actions that occur in reality did not change, the results did not change, the inputs, outputs and side-effects did not change, and yet we are able to look at the problem in a completely different way, and take different lessons and gather different information from it.<br>
<h3 id=1f4b194d8569136439831f483c38a264><a href="#1f4b194d8569136439831f483c38a264">2.5.2</a>: Slicing the pie vs aggregation</h3>
<br>
In the last section we covered the importance of slicing with the philosopher's knife without losing any information.<br>
<br>
One easy way of thinking about this is that you are cutting up a pie with the philosopher's knife.<br>
<br>
No matter how you slice a pie, the amount of pie has not been reduced.<br>
<br>
If you cut a piece directly down the middle, creating 2 symmetrical pieces, no pie is lost.  You have 2 pieces that compose the entire pie before slicing.<br>
<br>
Similarly if you cut a pie into any configuration, with any number of cuts, whether it is symmetrical, asymmetrical, whether the cuts are vertical, horizontal, diagonal, straight or wavy, the results are the same, in total all the pieces still contain all the original matter of the pie.<br>
<br>
In our philosophical cuts, the structure of the "pie" does not change, unlike a real pie, which deforms with the pressure of cuts, and will turn into a mess.<br>
<br>
In our virtual "pies" of information, or systems, we can slice any number of times in any direction, and the information remains the same, but on each side of the cut, we have made a division.<br>
<br>
For instance, we can look at an Operating System that runs on hardware (like Linux, OS X or Windows), and divide the it into code that runs in "Kernel space" vs code that runs in "User space".<br>
<br>
This divides all code that is executed from the operating system.  We can take the same system, and make a cut between "firmware" (code that executes from BIOS and other places closer to hardware) and "software", which is executed from RAM on the main CPU.<br>
<br>
Whether we have divided by "Kernel vs User" or "Firmware vs Software", nothing about the system has changed, we have simply decided to cut the pie in a different place, and we can then use this division for some sort of useful inspection.<br>
<br>
Cuts can be layered on top of each other, like dividing into Firmware/Software, and then dividing Software into Kernel/User space, and could continue to be divided, such as dividing User space into shared library code vs. application local code.  Share library code will be executed by more than one application, and is stored in a .so or .dll type file, and application code will be stored in a program's ELF or EXE formatted binary file.<br>
<br>
For purposes of discussion and illustration we can be fairly fluid about our definitions, and decisions on where to slice, because they are throw-away examples, and exist only for as long as they are useful to us.<br>
<br>
As we get deeper into the topics of Engineering Axioms and automation, we will see that while this can be used fluidly, the ability to use it deterministically, in a repeatable pattern, across many topics, becomes of paramount importance.<br>
<br>
The reason for this is the difference between a comprehensive system (correctly sliced with the philosophers knife), and an aggregated system, which is built not as a complete system that is sliced into pieces of the pie that can be put together to form the whole, but is aggregated from components.<br>
<br>
The problem with aggregated "systems" is that they are not always in jeopardy of becoming not-internally-consistent.  Due to being "aggregated" into creation, where one piece is created, and then another piece, and then the two are put together, and then a change is made, and then a new piece is added, you get the result of not having a "complete pie" when it is resembled.<br>
<br>
In fact, I will attempt to prove later on that it is impossible for a system that is aggregated to ever become a complete and comprehensive system, whereas if you always work from the method of "slicing the pie", you will always have a comprehensive system.<br>
<br>
The work involved to do both are very similar, and in some cases exactly the same, but the manner of thinking about the elements in them are very different, and yield very different results.<br>
<br>
As of 2015, I do not know of any operational environments which work in a manner that is consistent with "slicing the pie" vs aggregation.  I will explain this assertion as we get more into details, but this puts the use of systemic thinking in an operational environment into a purely "mythical" state at the moment.<br>
<br>
Part of the purpose of this book is to provide a path for others to understand these differences, so that paths can be built to allow us to create these comprehensive and complete systems, and to manage them accordingly, to get the benefits which they provide.<br>
<br>
We know the benefits and fallbacks of the aggregation system, though without comparing them to another method it is merely the de facto operations of all environments.  Making a change requires both defining the goals we want to achieve, and the current state of things, to know what is required to make a change to get to our goals.<br>
<h3 id=f32b593542b3562df78d89693543c0fe><a href="#f32b593542b3562df78d89693543c0fe">2.5.3</a>: Systemic Thinking.  Philosophers Knife.  Slicing the pie vs Aggregation.  Completeness, ease of understanding, ease of building, life-cycle maintenance.  Where do you spend your time?</h3>
<br>
So far we've gone over the general definition of a system, and created some examples, and looked at how to slice components of a system up to leave the system intact, but able to looked at from different perspectives, and to separate out different components.<br>
<br>
How does this affect our ability to perform operational duties?  How will it help in automation, and in the life-cycle management of an operational environment?<br>
<br>
Firstly, if one cannot understand something in detail for one's self, then it will be difficult to work with that thing efficiently.  I hope I have shown that being able to slice up a topic in any way you would like can produce sub-divisions which allow inspection and description, and which do not change the whole of system, and can be sub-divided further, or sub-divided differently to provide examples to compare and contract with one another, and to inspect their relationships and how work might flow through them.<br>
<br>
Once one has an understanding for one's self, then the ability to communicate effectively about the topic becomes a possibility.  If I don't understand a topic thoroughly, I will have a very hard time having a thorough discussion of that topic for someone else, in fact I believe this is impossible to do.  I must have a thorough and comprehensive understanding myself if I wish to be able to communicate with someone else with clarity.<br>
<br>
Through the power of using systems and the philosopher's knife, and black-boxing, I can take topics I do not comprehensively understand, and transform them into topics I do comprehensively understand.<br>
<br>
By reducing a system or component to it's Inputs, Outputs and known Side-Effects, I can clearly talk about what is going on as it relates to other systems or components.  <br>
<br>
If I can come to an agreement on terms and what the Inputs, Outputs and Side-Effects are for the given systems/components we are talking about, we have a much higher likelihood of coming to consensus on what we are talking about, and will be less likely to be talking about completely different things, while we are trying to communicate about a problem, or a solution, or whatever.<br>
<br>
Additionally, once we can create a system out of any environment and events, we can begin to Model that system so that we can come up with procedures on what we should do in different circumstances.<br>
<br>
For instance, in our web request and logging examples, we have determined that without log rotation we will in time fill up the storage, and fail to be able to take more requests (and log their results), and so we are sure to have failures on any active systems where this is the case.<br>
<br>
From this we can create a policy that requires all services to have log rotation or truncating configured for any software before it is put into active service.  We can go over the results we will achieve without this, and determine that are not the results that we want, and come up with a test for whether this is enacted on a given server to ensure that we have done this work, and have protected ourselves from this deterministic outcome.<br>
<br>
This is the type of leverage that these tools provide, and when we get into the details of automating an entire operational environment, through it's life-cycles, with change management and ensuring that all things are internally consistent, and well-aligned, to accomplish our goals, we will find that without these tools for clear and consistent "breaking things apart" and "putting them back together again" without losing any information, we will not be able to get comprehensive coverage without this.<br>
<br>
The short-comings of aggregated systems, versus comprehensive systemic systems is not yet clear, but as we define our terms more concretely, and begin to use them to deconstruct on operational environment, and then put it back together again, while keeping track of everything, we will see how aggregated systems are incapable of performing this task, while whole-systems always provide an accurate representation, if they are viewed with accuracy.<br>
<h2 id=da54e5ab11aae5fc49994945cb3bc9a8><a href="#da54e5ab11aae5fc49994945cb3bc9a8">2.6</a>: Terminology</h2>
<br>
Congratulations!  You've made it to the second beginning of the book, where we go over the definitions of terminology we will be using.<br>
<br>
I thought it was important to give a bunch of background on what we were going to talk about before we got to the definitions, because my terminology definitions may be quite different than how you already think of these terms.<br>
<br>
For the purposes of this book, please accept my definitions as I will use them in this book.  If it helps you can mentally append "Geoff is saying he means X when he says Y in this book", if the terminologies conflict too much with your existing use of the words.<br>
<br>
The important part of this is that you gain insight into my perspectives, as I will be using those descriptions of my perspectives to build up a detailed map of how to inspect an environment, how to design and compose an environment, how to implement it, how to automate it, how to troubleshoot it, how to perform maintenance and life-cycle changes to it, how to document it, describe it to other people, etc.<br>
<br>
This is all too much to do with just anyone's terminology, and the only terminology that will be able to consistently deliver these results will be my own.  So try to accept all of these for the tools that they are in getting to these goals, and not as universal definitions that should be written into dictionaries, or compared against them.<br>
<br>
I will be using the capitalization of proper nouns with these special terms, so that they are clearly my definition, for the purpose of this book, and not meant as the general term.  The only time this may be confusing is when the word starts the beginning of a sentence, but I hope context will keep that clear.<br>
<h3 id=9b48a00c792d88dfa31f203429758f84><a href="#9b48a00c792d88dfa31f203429758f84">2.6.1</a>: Data: data</h3>
<br>
In the virtual world, Data is king.<br>
<br>
I will support this assertion throughout this entire work, as it has become a central tenet in my thinking about how to do any sort of digital engineering.<br>
<br>
As I asserted in {{ section_ff17d94c0d49aab3e372e47b64b96ea7 }}, Data is an un-real thing.  It is virtual.  It does not have physical properties, and does not exist in the physical world.<br>
<br>
Electrons and magnetic forces exist, which we use to encode data into storage and processing mediums, but the Data itself does not physically exist.<br>
<br>
This is an important fundamental to understand, and more important for the purpose of learning from this book, to accept as the usage under which I will giving examples and explaining things.<br>
<br>
Data is symbolic and descriptive.  It can be used in any way, to accomplish any purpose at which the data has usefulness.<br>
<br>
You can use Data to accomplish things it was not intended.  For instance I could take the textual data inside a Linux /etc/passwd file and turn that into a musical score, by converting the characters and terms into frequencies, and by playing it.<br>
<br>
It would likely sound incoherent, and not be considered musical, but that is the power of Data.  It can be used as you see fit.<br>
<br>
Data resides in a Data Source, which could be anything, such as: files, database tables and rows, returned by networked services, etc.<br>
<br>
Data can be stored in many formats, and these formats can dramatically change the way the data is stored, and yet if it is not corrupted, the data can still function in the same way.<br>
<br>
Consider that data stored in a CSV (Comma-Separated Value) file and data stored in a YAML or JSON format look very different, and yet both can be loaded, parsed, and used as if they were stored in the same format.<br>
<br>
Data could be formatted to fit inside a relational database, so that it is spread into tables and fields, and looks nothing like a CSV file, and yet after querying the database I can get the data back in the same format which I could parse from a CSV file.<br>
<br>
This shows the dynamic nature of Data, while still providing us with consistent information that can be used by humans or Logic.<br>
<h3 id=69371f3e438e2ed281f525ac57e65e3c><a href="#69371f3e438e2ed281f525ac57e65e3c">2.6.2</a>: Logic: code</h3>
<br>
I'm going to try to constrain myself to using the capitalized (proper noun) "Logic" any time I am referring any of the following things:<br>
<br>
- Code<br>
- Programming<br>
- Scripts<br>
- Decision trees<br>
- Finite State Machine processes<br>
- etc<br>
<br>
I will also use these other terms in their normal meanings throughout the book, but I will refer to Logic when I am combining what is created in order to manage things that are done programmatically.<br>
<br>
It's good that our industry has many terms for things, as it makes them specific, but I will using the roll-up term, Logic, in order to simplify and generalize what we are talking about.<br>
<br>
One simple definition could be:<br>
<br>
- Logic is Data that is executable.<br>
<br>
In this definition, Logic is a sub-set of Data.<br>
<br>
This could be executable because it is in a native format an Operating System can load and execute (ex: ELF, EXE, etc), or via an interpreter (ex: Python, Ruby, PHP, Bash), or via a Virtual Machine executor (ex: Java, .NET/Mono).<br>
<br>
Logic is used when one wants to operate on data in a digital environment.  With Logic we will change the data, create new data, validate data, and perform side-effect type actions where we do things like copy data to different locations, remove it, create directories, start and stop services, as well as anything else we could do manually.<br>
<br>
Essentially Logic is the way we take action through digital means, where we would otherwise take actions manually.<br>
<br>
Of course, in a digital environment, all actions eventually require Logic.<br>
<br>
If I am in a command-line shell, and I run a command to create a directory, I have manually initiated Logic to perform this work.<br>
<br>
If I write logic to inspect a data source, and then to create directories based on that data in that source, then I do not need to manually initiate the Logic to create the directory.  There will be some kind of timed period (ex: cron jobs) or event (ex: monitoring initiated execution) that will initiate the Logic.<br>
<br>
As we went over in {{ section_ff17d94c0d49aab3e372e47b64b96ea7 }}, Logic is un-real or virtual.  It is not a physical thing, with physical properties.  It does not exist in the physical world at a given location or orientation.<br>
<br>
One can say that that bits that describe the Logic do reside on a physical storage medium (rotating disk, SSD, RAM, etc), but I am separating these physical attributes from the Logic itself, which could be anywhere, and in a given physical device, it will almost always reside in multiple locations, both on storage, and in RAM and perhaps in a CPU cache, and perhaps partially in CPU registers.<br>
<br>
I will end up breaking down many things to Logic layers and Data layers, and how Logic works on Data, and how Data is the stable foundation of Logic.  In my perspective, this is a reversal of how many people see the relationship between Logic and Data, but I will make a case for why Data is the core and Logic is the shell.<br>
<br>
To make the assertion as briefly as I can:<br>
<br>
1. Data is what you know at a given time.  This is useful forever.  It could be useful hundreds of years for now, for the same reasons it is for us today (using it to configure things), or strictly for historical or analytical purposes.  Data has essentially no "death" or time where it becomes invalid or unusable, as a general resource.  <br>
<br>
Not to say Data cannot be corrupted, or be invalid to our purposes, but it remains valid as a source of information even if it is corrupted (though perhaps not actionable for our immediate use).<br>
<br>
2. Logic is the codification of goals.  What we want to occur is processed through Logic.  Because of this, Logic has a number of environmental factors that work in some conditions, but there are many states where Logic cannot be used, except if it is seen as "Data" and is no longer executable.<br>
<br>
Logic requires a valid environment to run on.  Logic created to run on Linux will not run on Windows, or OS X, without being re-compiled, or being somehow universally compiled.<br>
<br>
Logic expects certain environmental requirements to exist.  It may expect to run in a certain directory structure, which contains certain files, formatted a certain way, and containing specifically formatted data.<br>
<br>
Or Logic could require access to network services which must exist for it to properly work.  <br>
<br>
Logic has dependencies.  It runs on a given "platform", and does not run on other platforms.<br>
<br>
Data needs a place to reside (ex: database, file system, etc), but it does not require a specific environment, it could be stored in a YAML format, JSON format, in a relational database, a flat file with comma or colon separation, or any type of format or storage system at all.<br>
<br>
The methods to access the Data will change, but the Data itself can remain the same.<br>
<br>
In order for Logic to run in a different environment, it is likely going to need changes.  Some programming languages offer cross platform execute, via being run by an interpreter or virtual machine executor which was natively compiled to the target operating system.<br>
<br>
However, there are still many places that Logic may not be able to work cross-platform without changes, such as moving from Linux to Windows there is a difference in how Windows access some storage, because it uses "Drive Letters" as device targets, and Unix-style operating systems use a single directory hierarchy.<br>
<br>
Other changes may be system files it expects to find in certain places, or required libraries that may not be installed, or may be an incompatible version.<br>
<br>
These are lower-level types of problems that Logic has, and why unless it is running in a hardware emulator Logic written decades ago generally cannot be executed properly on modern hardware and modern operating systems.  <br>
<br>
There are some exceptions to this, such as code that ran on very old versions of Windows, and has had fixes installed throughout Windows versions up until the modern times to allow this code to still work.  These are the minority of cases though.<br>
<br>
A more likely (who runs multi-decade old code frequently, for business purposes?) scenario is that the organizational goals have changed.<br>
<br>
Goals change frequently, and so requirements change frequently, and Logic is codification of requirements.  Once you have different goals, it is very unlikely that the code that worked for the previous goals will still work with the new goals.<br>
<br>
The conditions for when the same Logic will give correct results once you goals have changed is when that Logic is being used as a "tool" or "utility", in which case it operates on data to perform it's actions.<br>
<br>
This accounts for the long-life span of Unix-style environments, which are historically largely made up of software that performs generalized operations against a set of data.  That data might resides in a file, a database or be given by user input on the command-line or through a series of prompts.  <br>
<br>
In these "tool" type of Logic, it is the data that tells the Logic how to achieve a goal, and so again the Data gains primacy over the Logic in being the key element.<br>
<br>
For our purposes, in automating an operational environment, we will be extending this "tool" type processing greatly, so that we create a large pool of interconnected data, and then create Logic that works against this data to achieve the goals we want.<br>
<br>
Like the Unix-style environment that allows so much control and flexibility, we will create a layer on top of current Operating Systems, which allows the accomplishment of goals with a minimum amount of changes to Logic, as the Logic is driven by the Data.<br>
<h3 id=aa2640c210126a47b684283980210b76><a href="#aa2640c210126a47b684283980210b76">2.6.3</a>: Rules: policies about how you do stuff</h3>
<br>
For the purpose of this book, I'm going to use a term I don't usually use in real life, which is "Rules".<br>
<br>
In this case I will define Rules to mean the way we do things, encoded into Logic and Data.<br>
<br>
I will use this to separate out digital Rules from policies and procedures that departments and organizations use to determine how people do things.<br>
<br>
This could be seen in the sense of "Rule Processing Systems", or something similar, where Rules are constraints or requirements in how Logic will operate.<br>
<br>
And the Rules are specified either directly in the Logic (hard-coded rules), or in Data.<br>
<br>
Rules encoded in Logic will require more effort to change, and are not able to be changed automatically, unless you are generating the code.  Generated code is more of the side of the spectrum of Data than Logic, because Logic is generally created by humans.<br>
<br>
In the case of generated Logic, it will be generated from Logic created by humans, and is a type of template that has data populated into it, or loops of generated chunks with data populated into them.<br>
<h3 id=3393e40f9f65bba3ee24fc4f744c792b><a href="#3393e40f9f65bba3ee24fc4f744c792b">2.6.4</a>: Distributed: dealing with N nodes</h3>
<br>
You may have used the word "distributed" before, such as in "distributed systems".<br>
<br>
My meaning will be very similar to this usage, but I will use it a little more generally to mean any time you need to work across many nodes of something.<br>
<br>
For instance having to control 200 web servers will be a Distributed service of web servers.<br>
<br>
This usage stems from a single web server being able to do the same thing as 200 web servers (configured in the same manner), but the "load" is "distributed" across the 200 web servers, making this a distributed network service.<br>
<br>
The reason for being very general in this usage is that it provides a comparison point between single processing system and a distributed processing system.<br>
<br>
As I will cover in more detail later on, there are 3 cases you should account for in operations:<br>
<br>
- Zero instances of something.  You do not do this thing.  In some cases this is simply something you do not require, but in the more sophisticated case, this is work you are still accomplishing, but in a manner that does not need an instance of anything, it is an efficiency gain.  In either case, it is important to know that "not having something" is a state.<br>
<br>
- One instance of something.  This is when you one thing that you use, it is a centralization of a service.  There may still be a pair of machines (Master/Slave) supporting this one-thing, and there may be more than a pair, but if there is logically a "single instance" of the thing, then it is a "one instance".<br>
<br>
- Infinite instances of something.  As soon as you move beyond "one instance", you move into the realm of many-things.  If you think you can move to "just two" or "just three" you are not taking into account all of history which shows continual sub-division and growth in all things that are not "shutting down".  "infinite instances" may currently be at a count of "2", but in order to handle the growth that will eventually come, it should be implemented as an N-instance, or infinite instance system.<br>
<br>
These differentiates can be seen in the phase:<br>
<br>
"0, 1, Infinity.  There is no 2."<br>
<br>
Make this an internal meme for yourself, and watch as things start to make more sense in terms of problems with scaling.  When a number larger than 1-instance is introduced, you will eventually see that number grow, and sub-divide into different domains.<br>
<br>
Having a 1-instance system is incredibly difficult.  Pressures will continually be applied to grow into an N-system, and it will take work and perseverance to keep a 1-instance system at 1-instance.<br>
<br>
0-instance systems, when not just the identity of "we don't do that here", come from efficiencies.  This is when a 1-instance or N-instance system has been replaced in such a way that the work does not need to specifically occur, and yet the goals are still achieved.  If this sounds a lot like what I referred to as "removing Classes of Work", it is because it is exactly that.<br>
<br>
I will cover this concept in full detail later on, because it is critical to understanding how scaling works in practice.<br>
<h3 id=a709b239027a030b1a2dc4d500e49a24><a href="#a709b239027a030b1a2dc4d500e49a24">2.6.5</a>: Real/Virtual.  Strict definitions.</h3>
<br>
I won't go through the explanation that I made in {{ section_ff17d94c0d49aab3e372e47b64b96ea7 }} again here, as I think we covered the differences between what I meant by real and un-real, or virtual there.<br>
<br>
I'll just say that like other this-book-only terms, I will be using Real and Virtual as proper nouns to describe things I mean to be having physical properties as Real, and things that do not have physical properties are Virtual.<br>
<br>
If this seems vague, please review {{ section_ff17d94c0d49aab3e372e47b64b96ea7 }} again, as the specific use of these terms for the purposes of this book is important for understanding what I'm trying to convey.<br>
<p id=031f037060d88ef98ae42ae359b42dd0><b><a href="#031f037060d88ef98ae42ae359b42dd0">2.6.5.1</a>: Be clear about the differences:  Physical (Real), Logical (Virtual), Data (Virtual)</b></p>
<br>
Since I think we have a clear working definition for the terms Real and Virtual, we start to do some comparisons between them and see what other things are different.<br>
<br>
Since they have very different properties, as they are about as different as anything can be, that means that those different properties should have different advantages and disadvantages when looking at them from different perspectives.<br>
<p id=5a2ee645ef74425ffa093976096dee18><b><a href="#5a2ee645ef74425ffa093976096dee18">2.6.5.1.1</a>: Can never know everything about something Real (physical), because of limited insight into what is going on with it</b></p>
<br>
The first important thing to know about the difference between Real and Virtual things is that you cannot know everything about a Real thing.<br>
<br>
Determine what the state of a Real thing is is essentially impossible, but we can have approximations that are good enough.<br>
<br>
Why is it impossible to know that "true state" of a real thing?  Because it's state varies with every atom, and collectively all the atoms of a physical thing are too numerous and beyond inspecting in many dimensions.<br>
<br>
This is not taking this too far either, it is simply being clear about what is possible, and what is not.<br>
<br>
So, if we can't know everything, then what is possible, and what are those limitations?<br>
<br>
Let's take something fairly simple for example, such as temperature.  What temperature is a physical device, we will say a 1U 19" rack server?<br>
<br>
Well, that depends on where you are measuring it from.  Modern servers can have dozens of temperature sensors throughout their chassis, and those temperature sensors will approximate the temperature fairly accurately for part of the device.<br>
<br>
We could measure the each CPU socket temperature, and the temperature near the power supply, and the fans, and then we can approximate from these or list them, but there remains many places we are not even directly measuring.<br>
<br>
It happens that this is not necessarily important for our purposes, but it is important to understand and accept that this data is simply not available to us, and we have sensors in place to detect some aspects of it.<br>
<br>
Other aspects we may not have any sensors for.  For instance, mobile devices often come with accelerometers, which will detect movement of the devices.  Rack servers do not currently come with these sensors, and for a fairly reasonable reason, as they are not in demand.<br>
<br>
But this is one type of data that we cannot collect about this server.  It could be that the amount of vibration the servers are going through could end up causing problems over large numbers of servers, and by doing correlative analysis on part failures with vibrations, and by determining where the vibrations were worse, we could contact our data center's staff and see if they could fix the problem, as it may be an undetected problem on their part.<br>
<br>
This is a completely theoretical example, but it illustrates that there are things we know, but not completely (temperature), and there are things we do not know at all about Real things.<br>
<p id=e529c9c5431e0acff31b16484c63dfad><b><a href="#e529c9c5431e0acff31b16484c63dfad">2.6.5.1.2</a>: Can know everything about Virtual (Logic/Data), because they are limited, and they are fully contained and inspectable.</b></p>
<br>
In the last section we learned that there are things we cannot know, or know with full accuracy about Real things.  Their very nature means that they are not fully knowable, but we can know enough about them to make use of them effectively, and have a long history of doing so.<br>
<br>
How do Virtual things align on this same spectrum of "knowability"?<br>
<br>
Some Virtual things can be completely known.  Other Virtual things remain unknowable.<br>
<br>
We can use the examples we used in a previous chapter.<br>
<br>
Let's look at a variable that we assign:<br>
<br>
X = 5<br>
<br>
Here, I have made X to be equal to 5.  Can we know everything about this Virtual thing?<br>
<br>
Yes, we can.<br>
<br>
We can inspect this in any way we like, and know everything to know about it.  We can compare it to different numbers:  X < 6, X > 4, X == 10, and see if it is similar to them.  <br>
<br>
Any operation we wish to make, we can perform and know the full extent of what there is to know about this Data.<br>
<br>
Now, let's look at a Virtual thing that is not fully knowable, we will look at the word and symbol of "idea".<br>
<br>
We can take the word "idea" and trace it's language roots, and compare it to other languages, and find common usage of it in popular literature, and we can ask people what it means, and in all of these things we will gain information.<br>
<br>
But, we will never know everything there is to know about the word and symbol of "idea" because it is not a concrete thing.  It has subjectivity and flexibility, and can be used in different ways in different circumstances.<br>
<br>
The same is true for many things.  So we have a class of Virtual things about which anything can be completely known, and another class of Virtual things about which only some things can be known.<br>
<br>
Let's simplify this into two more terms:  Knowable Virtual things, and Unknowable Virtual things.<br>
<br>
We could call this "Knowable Virtual Data", but since Data is a subset of Virtual, and there exists other things that are virtual, and may be completely Knowable, that do not meet the same definition as Data, we will use the label "Knowable Virtual" and then can append anything onto it afterwards, like Data, to describe what exactly the Knowlable Virtual thing is.<br>
<br>
Let's create a spectrum for these labels:<br>
<br>
Knowable Virtual thing <---> Unknowable Virtual thing<br>
<br>
We're going to build a little forest of terms and spectrums (or axes) over the course of the book, because once we have clear terms like this, we can use them in different ways than if they were still more vague, and less specific.<br>
<br>
Terms such as these can have specific properties, which contract with other terms, such as Knowable Virtual Data vs. Unknowable Virtual Data.  We already have at least 1 property between these things that we can use in any algorithm as something that is clearly understood.<br>
<br>
Over time we will build up a toolset of these, so that we can communicate about incredibly complicated topics, and reason about them efficiently and clearly.<br>
<br>
As an exercise, can you come up with any terms off the top of your head now that you understand well enough to define in these ways?  Through your own definitions, and understanding, as I am doing here?<br>
<br>
If you can, great, write them down and add more to that list as you think of more, and it will start your own set of terminology in which you can reason with, having more understanding of it than my terminology, which I have created.<br>
<br>
If you can't think of any now, that's not a problem, but if any come to mind in the future, write them down, and over time more and more may start to come to you.<br>
<p id=dd889cf6d887f391188383b428c7ebfc><b><a href="#dd889cf6d887f391188383b428c7ebfc">2.6.5.1.2.1</a>: However, between Data and Logic is a huge gap, as Data is "perfectly" understandable, while Logic is not, due to Halting Problems and all other things CS-academia knows and describes very well.</b></p>
<br>
Another Unknowable Virtual thing is Logic.<br>
<br>
Logic, as we defined earlier, is an all-emcompassing term for anything to do with software or decisions, or scripts or other methods of manipulating data, executing statements, etc.<br>
<br>
One of the famous problems of computer science is the Halting Problem.<br>
<br>
This problem is essentially that is impossible to know if a program is every going to stop executing once it starts.  There is a lot of information about this problem out there, so we will just leave it with that description and realize that Logic has an Unknowable Virtual element to it.<br>
<br>
However, Logic also has many Knowable Virtual elements to it, because as in our example of "X = 5", this is a statement that can be made in Logic.<br>
<br>
Additionally, just like in our example we can use the Logic itself to inspect this, or we can externally inspect the Logic using a debugger, and we can verify the data, and it is Knowlable Virtual Data.<br>
<br>
So, while Logic contains some properties that are Unknowable (the halting problem being one example), it also contains properties that are Knowable, and the Unknowable does not stop us or hinder us in any way from gaining full access to the Knowable.  <br>
<br>
This puts Logic in a murky place on a spectrum of Knowlable to Unknowable, but that's OK!<br>
<br>
What we need to do in this instance is simple break up what Logic is, and look at each of the components on the spectrum, and we will have a correct view into it.<br>
<br>
So, that would look like:<br>
<br>
- Logic: Will it ever stop running?  On the Unknowable part of the spectrum.<br>
- Logic: Variables and other values?  On the Knowable part of the spectrum.<br>
<br>
I leave off calling them directly Knowable and Unknowable, because Logic can be tricky, and there can be tricky things done inside logic, and perhaps in some circumstances this means that variables are not completely knowable, and there might be circumstances where we have a high confidence that a program will halt, like this pseudo-code:<br>
<br>
{{ start_code }}<br>
main()<br>
{<br>
  return 1;<br>
}<br>
{{ end_code }}<br>
<br>
We can be reasonably sure that if this program compiles, and there are not problems with dynamically linked libraries, and there are not somehow crazy macros in the white space or brackets, that this program will eventually stop running.<br>
<br>
This tells us another Knowable property of Logic, which is that it is very complex, and can it's meanings can be obscured.<br>
<br>
Take for example this Python code snippet which uses a Decorator.  It's OK if you don't know Python or aren't familiar with Decorators, because it's just an example and I'll explain my meaning of it.<br>
<br>
{{ start_code }}<br>
@HelloWorldDecorator<br>
def HelloWorldFunction():<br>
    return 'Hello World!'<br>
{{ end_code }}<br>
<br>
If the "@SomethingSomething" wasn't there, this would read like a beginning Hello World! program, as when you call the HelloWorldFunction() function, and it returns the string "Hello World!".<br>
<br>
However, there is a Decorator to this function call "HelloWorldDecorator", which modifies the behavior.  The decorator code may live in another file, so it may not be obvious what is happening when you simply look at the code.  You assume it's basically going to return "Hello World!".<br>
<br>
Let's look at the decorator code I have created:<br>
<br>
{{ start_code }}<br>
# Decorator<br>
def HelloWorldDecorator(function_reference):<br>
    def DecoratorInside():<br>
        # Call the Function we are wrapping<br>
        intitial_result = function_reference()<br>
        <br>
        return intitial_result.replace('Hello', 'Goodbye')<br>
    <br>
    return DecoratorInside<br>
{{ end_code }}<br>
<br>
The decorator code creates the required wrapper for the functions, as that is what decorators do in Python, and it calls the function reference, but instead of simply returning the result, as if we had called the code without a decorator, it modifies the result.<br>
<br>
It replaces the string "Hello" with "Goodbye", so we get the very different result of the "Goodbye World!" string being returned, changing our peppy introductory function into something much darker.<br>
<br>
This melodramatic example shows that we can see something that looks very clear in code, and yet something that does not necessarily looks like it will change the result we clearly see, in fact, does change that result.<br>
<br>
This is another aspect of Logic's being on the Unknowable side of the spectrum, due to it's ability to contain very high complexity.<br>
<p id=99b45325e58458c65965de974e2f7dc2><b><a href="#99b45325e58458c65965de974e2f7dc2">2.6.5.1.2.2</a>: This difference also tells us why Data is more important than Logic, because Data is more trustworthy than Logic.  When making changes to data, the changes are straight-forward to understand, when making changes to Logic, the side-effects (unintended consequences) can be far-reaching and completely not understandable, and frequently enough are this way.</b></p>
<br>
Now that we have established that collectively, Virtual Data, which I will just call Data, since it is always Virtual, is Knowable.<br>
<br>
And we have established that collectively Logic is Unknowable, even though components of it may be knowable, we can use this information to set up a hierarchy, which we can use to build more robust engineering solutions.<br>
<br>
If Data is Knowable, and Logic is Knowable, then we should base our actions on our Data, and treat that as the supreme truth.  Our Logic is not less important because of this, as it serves the same role as it would if Logic was King, and reigned supreme over Data.<br>
<br>
However, knowing that we can treat Data as the most important thing in our operational environment means that we will always first focus on the data being correct, and then secondarily we will look at how the Logic interacts with the Data, with an careful watch that the Logic does not do anything to the Data that would cause us problems.<br>
<br>
Of course, you don't have to have any of this kind of analysis to know that you should not corrupt your data with your code, but this is the path I have taken to understanding where to place priorities, and how to approach working, and they have served me well.  I hope to prove after we have gotten through this introductory phase, into the details phase, and finally into going over implementation, how these fundamentals are truly critical to building large, robust, resilient, controllable, manageable operational automation environments.<br>
<br>
Without all of these details, all the adjectives I just used to describe what we will build may still be applied, but they may not be true, and we may not really get those effects.  Through using well defined fundamentals, we can being to bring this assurance in.  This is an important part of what Knowability gives us.<br>
<p id=3b9a062658c7f15e53b7601de12d3857><b><a href="#3b9a062658c7f15e53b7601de12d3857">2.6.5.1.2.2.1</a>: Changes to data, that meets constraints, will not harm other data, but can harm Logic that acts on the data (results of Logic, rather)</b></p>
<br>
When working with Data, is it required that certain constraints are met.  This is normal database 101 stuff.  If you have a relationship between 2 tables, the the primary key of Table A is referenced in Table B, and then you change that primary key in Table A, but do not update all external references to it (such as in Table B), then you will have created an inconsistency.<br>
<br>
There are methods for forcing this to not be allowed in many database software's schema configuration, using constraints and foreign keys, etc.<br>
<br>
In an Operational Automation environment it is likely that the data sets will stay small enough that you can work with these constraints enabled, and the changes are important enough to deal with the performance hit the constraints provide anyway.  So, I recommend leaving them on, and letting the database software manage enforcement of constraints.<br>
<br>
If you find yourself in a place where constraints are causing a real performance problem, and are not working, I suggest only turning off the constraints that are the problem points, and leaving the rest of them enabled.<br>
<br>
For the areas where data constraints are turned off, you must be especially careful when making changes to this data not to lose any of the referential integrity that the constraints would have provided, with your own changes via Logic, or in unfortunate times when you manually update the database (which you should try to never, ever do).<br>
<br>
Another Knowable thing about Data, is that if you have these constraints active, then you can Know that the data is correctly configured, and it's referential integrity is consistent.<br>
<br>
There are some operations, such as dumping data and mass-importing it, that can cause these checks to be turned off, so be careful when you do this to do everything that is involved at the same time (all tables that reference each other), to ensure that you have not imported things into an inconsistent state.<br>
<br>
We've now covered that Data can have an additional area of Knowability.  How does this relate to Logic?<br>
<br>
Well, it turns out this is another area where Logic provides a fundamental weakness, and in a way that is Unknowable.<br>
<br>
You can have perfectly consistent and correct Data, with all constraints active, and have Logic that works perfectly well with all of the current data.<br>
<br>
And then you can make a change to that Data, which does not violate any of the comprehensive validation tests, and yet afterwards the Logic fails against the Data.  How?<br>
<br>
Logic is not actually tied to Data in that same way that Data can be tied to itself.  In a database, let's use an abstract general SQL database with transactions for this case, we can insert a row into database table, that is perfectly valid, and all the tests are made in the transactional commit process, and the data is put through correctly.<br>
<br>
When the Logic next tries to access this data, it finds the new table row, and it goes about it's normal logic, which has always worked before, but this time the data it receives is not something the Logic accounted for.<br>
<br>
Say you have a field that is an unsigned integer, so it goes from 0 to some very large amount (it depends on implementation, so I will leave it vague), and the Logic expects that this data is in the range of 0 to 100.<br>
<br>
If the data entered is actually 5000, and the Logic expected it to never be more than 100, then the Logic will do something incorrect, perhaps making something that shouldn't be 50 times larger, such as memory allocations of a Java Virtual Machine, which might fail and cause a service to not start on the next attempt.<br>
<br>
Whose problem is this, Data or Logic?<br>
<br>
It is a shared problem with between the two, because the Data contains valid data (0 to large number), and the the Logic is only handling 0 to 100, and so a failure has been entered between the two, even though the Data is correct.<br>
<br>
There are many ways to approach this problem.  Databases frequently have code that you can put into the database to execute at certain times, which could validate the values and enforce only numbers 0-100 are put in them.<br>
<br>
There are some problems with this, in the long term you have probably tied yourself to this database platform for a very long time, whether you want to be or not, because after all of that Logic is put into the database to validate the Data, it would take a large effort to re-create it all correctly in another database's methods, and those methods may not be fully compatible, in that you can't do everything in the target database that you could do in the original database.<br>
<br>
That is a manageable problem, however, as it deals with timescales of years, and is likely worth of the cost-benefit tradeoff.<br>
<br>
However, there is another problem is that now you are putting Logic into your Data.  We know that Data is Knowable, and Logic is Unknowable, and when you put an Unknowable into your Knowable, the result is that you end up with an Unknowable.<br>
<br>
We have just transformed our safe-space of Data into an un-safe space, because now we have custom Logic in there as well.  So we do not have anywhere that is just Data.<br>
<br>
This is a huge problem as we will never be able to be assured that the Data we are accessing is going to be accessed correctly.  <br>
<br>
To take our "X=5" type example, if we have a field "X" in a database table, and we have Logic running in that database, it is possible that as we test and modify that "X" field, the Logic will be invoked, and it could change the results.<br>
<br>
With this being the case, we can no longer trust that we set "X=5" and then we test "X > 4" (X is greater than 4), and we receive a positive.<br>
<br>
The Logic may have silently changed X to 4, because it had a constraint that we did or didn't know about at some point, and now we do 2 steps in a row, where we assume success is guaranteed, and we end up with failure.<br>
<br>
This is a large problem.  <br>
<br>
Another issue that we deal with is that writing Logic for databases is not as manageable over time as writing Logic in other platforms, such as directly for execution or interpretation in an operating system.  That is because database's purposes are to serve data, and so they do not get "best of breed" software development environments.<br>
<br>
There are many more examples I can give on how you can have consistent Data, but inconsistencies between the Logic and Data.  The end result of all of these is that you must simply be very cautious when creating your Logic, and provide as many safe guards as is warranted by the needs of your organization to provide that the Logic works cleanly with the Data.<br>
<br>
There are many techniques for this that we will cover once we get to implementation.<br>
<h3 id=9ea896216c817034b6d3858d8f934e34><a href="#9ea896216c817034b6d3858d8f934e34">2.6.6</a>: Knowability</h3>
<br>
I didn't know this before I just looked it up, but Knowability is already a word in dictionaries, so there is not a lot of reason to cover it in depth.<br>
<br>
We've already been using it quite a lot, but I thought it would make sense to shortly define it.<br>
<br>
Knowability is a spectrum of how well you can know something, in full, at all levels.  It needs to be extreme knowledge like our "X=5" example, where we know absolutely everything about it.<br>
<br>
Any ambiguity or aspects that remain not-perfectly-knowable need to count against it being on the extreme side of Knowability, and more towards the side of Unknowability.<br>
<br>
To set up the spectrum, it looks like this:<br>
<br>
Unknowable  <--->  Knowable<br>
<h3 id=e2a0bb61f2d74d70b31bf533e2b1c260><a href="#e2a0bb61f2d74d70b31bf533e2b1c260">2.6.7</a>: Class of Work: a specific type of work that is done, may be domain specific or general across the company</h3>
<br>
We briefly defined Class of Work in the beginning of the book, but let's take a slightly deeper look at what it means.<br>
<br>
Initially I just said it was "anything that is done", and this is true but perhaps "work" work suffice to say that, and everyone would understand.<br>
<br>
However, there is more depth we can gain from looking at it deeper.<br>
<br>
I initially used the example of automating the DNS zone file updating.<br>
<br>
If you aren't familiar with DNS zone files, they are text files look like this:<br>
<br>
{{ example_dns_zone_file }}<br>
<br>
One aspect of manual workflow generally goes:<br>
<br>
- A new system is created, and needs a name matched to it's IP address (an address "A" record)<br>
<br>
- Someone goes to the server that hosts the DNS Master files (the machine people use to make edits on, and where the changes will be diseminated)<br>
<br>
- That add the line with the hostname fragment, and the "A" for address record, and the IP address<br>
<br>
- They update the serial number of the zone file (so the DNS software knows the file has been changed)<br>
<br>
- They test the file with the DNS software's configuration file validation<br>
<br>
- If the test passes, they reload the DNS zone file into the server.<br>
<br>
- Then they tell the Slave DNS servers (other machines that reference this Master machine's DNS service to get records), and tell them to do a zone transfer.  This might also be configured to happen automatically on the Zone file changing, through the Master DNS server's software (although there are some reliability problems with this, in practice)<br>
<br>
<br>
These steps might take a person 10-15 minutes to perform, on an individual basis, and slightly longer to implement for larger changes.<br>
<br>
Sometimes it is a problem that people just forget to do this, although since the new machines wont have DNS names, people will only be able to reference them by IP address, so usually the problem is quickly remedied.<br>
<br>
A larger problem is that people can type things incorrectly, and while the validation tests find some problems, they will not find correctly formatted zone or configuration files, which have bad data in them.<br>
<br>
If a line that used to exist was removed, then very shortly afterwards services that referred to that previously-existing DNS name will start to fail, as the name no longer resolves.<br>
<br>
These problems are usually caught quickly, as things will fail and alert, if monitoring is set up properly, but there was just an outage, and revenue may have been lost, or other negative consequences for an organization.<br>
<br>
Humans making manual entry mistakes are simply unavoidable.  As the population of humans doing manual work increases, and the amount of work each human does increases, so will the amount of failures.<br>
<br>
Some failures only show up when multiple mistakes occur, so the original set-up problem may have occurred days, weeks or months before, but the secondary mistake triggers that mistake, making it very difficult to troubleshoot.<br>
<br>
The "second mistake" may not have even been a mistake at all, and on inspection it is found that it looks correct, so it is put back in, and the failure occurs again.  <br>
<br>
This is a component of Alignment, which I mentioned in the beginning of the book, but we haven't referenced in a while.<br>
<br>
The Alignment in question for our original "DNS zone entry is removed" is this:<br>
<br>
- A service, say a web server, references a database by DNS name, and is live and working<br>
<br>
- A person makes a change to the Zone file, removing the database name, but leaving the zone file in a valid state in terms of validation<br>
<br>
- The zone file is loaded and replicated, and the web server cannot reach the database.  An outage has begun.<br>
<br>
What was the Alignment here?<br>
<br>
The Alignment was that the web server required the DNS server to have the name of the database server, so that it could make a connection to it.<br>
<br>
This is a very simple case of Alignment, but it servers the point for an initial example, which is that without Alignment, things do not work, or do not work efficiently.<br>
<br>
Efficiency is a metric that has to do with "functioning, but not as well as we would like, or could be", and so is a more complex topic than something that does not function, which is fairly clear cut.<br>
<br>
We'll be getting very deep into the Alignment of efficiency soon.<br>
<h3 id=e51fd2df5fa27c89dbb16625df6ec6b6><a href="#e51fd2df5fa27c89dbb16625df6ec6b6">2.6.8</a>: Data Source</h3>
<br>
Since we'll be talking about Data quite a bit, I will be referring to any mechanism that stores Data as a "Data Source".<br>
<br>
This could be a database, a YAML file, a variable in a JavaScript that came from a JSON RPC request, it doesn't matter.  There is a location that stores data, and we interact with it to get data and store the data.<br>
<br>
The Data Source may be persistent, or it may be temporary (such as Javascript data in a web page).  These are secondary properties, as the primary property of a Data Source is access to the data.<br>
<br>
Some qualities of a Data Source:<br>
<br>
- Access to data.  Get it, set it.  This is mandatory, all others are optional.<br>
<br>
- Constraints on the structure of the data (such as not being able to insert arbitrary fields).  This would be a strict "schema" (schematic), as opposed to a "document" style which allows any type of modifications.<br>
<br>
- Constraints on the value of the data that is put into specific fields in the data.  For instance, in a relational database a field in table may be of type "integer" and will not allow alphabet characters, special characters, or real numbers (floating point) to be inserted.<br>
<br>
- Persistence: So that the data is saved, and is the power is turned off to the system where the data is, when the machine restarts the data will still be available.  There may be corruption here, unless the Data Source also offers a Consistency guarantee.<br>
<br>
- Consistency: Ensures that the data does not become corrupted in any failure situations.  These situations might be the program being terminated un-cleanly, and it might use something like a journal to keep track of previous changes, and will replay this journal to ensure that recently changed data is the same as in the journal.  <br>
<br>
To be safe, the journal is written to and flushed to disk before the changes are made in the database, so if anything the internal database data is consistent with the previous changes, and only new journal entries need to be applied.<br>
<br>
- Transactions: Multiple changes, such as in different tables, or multiple rows in the same table, can be applied all-at-once, in an "atomic" fashion, which means that it "cannot be split further" (Atomicity), and being the smallest-type-of-action, it is guaranteed to either not-have-started, or finished completely, before another action takes place.  <br>
<br>
Transactional changes are made sequentially, and cannot interrupt each other.  Furthermore they verify the consistency of the entire exchange, and not simply each statement, which allows more precise validation of referential integrity as well as being able to make changes that would be constraint violations if done one-at-a-time, but which are consistent when done together in a transaction.<br>
<br>
- Replication: This allows copies to be made of the data to at least 1 other instance of the Data Source implementation, for example a SQL server could incrementally copy it's journal file from itself to another machine, which then applies the journal.  If the original machine goes down, the replication target machine will have an update-to-date version of the database, up to the latest journal entry it received.<br>
<br>
There are many other properties to Data Sources, so this is not meant to be an exhaustive list, but a brief coverage of some elements we can associate with the label Data Source, which may or may not exist in a given implementation you may use.<br>
<br>
Some Data Source implementations offer features that are in opposition to some of the above, and those feature sets are also useful, since they provide different benefits and weaknesses to some of the features I have mentioned.  The right tool for every job, and all that.<br>
<br>
{{ todo__make_more_of_these_qualities_lists_for_other_terms_and_things }}<br>
<h3 id=2880d6cb6fe0e0528df63476d031e45e><a href="#2880d6cb6fe0e0528df63476d031e45e">2.6.9</a>: Production Environment</h3>
<br>
There are a couple different environments which we will be framing our discussions in, so let's get some strict definitions for them, starting with the most important, Production.<br>
<br>
The Production Environment, which I will mostly just be calling "Production", is the place that the critical operations of your organization takes place.<br>
<br>
This might be a data center that has many peered network circuits, in which you receive internet traffic and generate revenue.<br>
<br>
Or, it could be a server farm in your corporate offices, in which processing occurs, which is critical for the functioning of your organization.<br>
<br>
Or, it could be in a cloud or managed hosting environment, in which you mostly manage through a browser application.<br>
<br>
It doesn't matter what exactly the circumstances of your "Production" are, you should be aware of what it is, and how it is treated different than other areas of your organization.<br>
<br>
Things in Production should be the most important things, and not intermingled with devices or services which are not of the same critical importance.  Sometimes sharing of environmental space will have to occur, but this should be minimized, and remedied once it is possible to do so.<br>
<br>
The Production environment should have the highest levels of security, where only authorized personnel are allowed to access the server instances, and every login and preferably every command issued is logged, for auditing purposes.<br>
<br>
This follows the "AAA" process of: Authenticate, Authorize, Audit.<br>
<br>
In brief:<br>
<br>
Authentication is determining who someone is.<br>
<br>
Authorization is determining if they are allowed to do what they are trying to do.<br>
<br>
Auditing is logging everything that happens, so that it can be reviewed.<br>
<br>
<br>
There is a fourth "A" that be added {{ todo_forgot_what_this_is_tempoarily_but_i_wrote_about_it_years_ago }}<br>
<h3 id=85f5ad95d9e4d6cd51f782e15b9a380d><a href="#85f5ad95d9e4d6cd51f782e15b9a380d">2.6.10</a>: Staging Environment</h3>
<h3 id=42913fa225b25b38eee2478890c7cdc9><a href="#42913fa225b25b38eee2478890c7cdc9">2.6.11</a>: QA Environment</h3>
<h3 id=e51f755569b88937197a5286a282bf76><a href="#e51f755569b88937197a5286a282bf76">2.6.12</a>: Performance Bench Testing Environment</h3>
<h3 id=d1a4f057af493912852ac12fc03ca9b3><a href="#d1a4f057af493912852ac12fc03ca9b3">2.6.13</a>: Corporate Environment</h3>
<h3 id=3d2ece14db911afb11e032b9c3c646b7><a href="#3d2ece14db911afb11e032b9c3c646b7">2.6.14</a>: Humans</h3>
<br>
It feels a bit weird when I say or write "Humans", as it's strangely impersonalizing to everyone, I feel.  However, it is conveniently clear to differentiate not only from "Not Human", or "Logic Based" or "Software" or whatever, but also clear in the sense that I am not speaking casually about people, but specifically about the type of effects that Humans cause.<br>
<br>
We generalize about "people" all the time, different groups of them, to have any sort of discussion.  Sentences can only carry so much information in them at any given time, because words only have so much meaning, and a word is composed of syllables, and those take time to write or say, and they have to be done sequentially, the syllables cannot be written or said simultaneously to be more efficient, and so generalizing or summarization is required.<br>
<br>
Without summarization and generalization, we would spend so much time getting to the point, by being maximally specific in every detail, much in the way I am doing right now, that we would just not get to the point, and all communication would cease to function.<br>
<br>
Shouldn't there be a spectrum for this?  Let's make one:<br>
<br>
Specificity  <----->  Generalization<br>
<br>
Now we have an axis on which we can slide a variable across, to be more or less specific, and it can be tuned in the way we want it, for every circumstance that is possible.<br>
<br>
In addition to this, we can add in another topic, such as "Atomicity" that we spoke of previously.<br>
<br>
We can be extremely specific in our discussion of Atomicity, or we can be extremely General, or somewhere in between, in the spectrum, along the axis.  I will use this method of multiple examples mixed together to provide a richer tapestry for these ideas to be expressed in, as the book goes on.  These are tools for communicating more deeply than not, another spectrum or axis, which can be applied.<br>
<br>
In fact, let's just combine some right now, and make a new tool.  We just discussed "Atomicity" as a topic, on the spectrum/axis of Specificity <--> Generalization.  Let's combine the Atomicity scale and the Specificity scale together, and create a topic based on the two dimensional coordinate system that those two axes create.<br>
<br>
Atomicity:  Atomic <---> Not Atomic<br>
Specificity:  Specific <---> General<br>
<br>
I ended up writing these "Left to Right" in terms of the subject being in a full-state, or an empty-state, but they could just as easily be written "Right to Left" (in reverse order), if it is more convenient for the problem at hand to see them in that way.  This process of ordering things as needed for the current problem is another tool that can be applied, and which has properties that can be evaluated.  For the sake of keeping up a fluid pacing for this book, I can't go into detail on each of these things as they arrive (even though I would like to: enhance, enhance, enhance).<br>
<br>
Now that we have these two axes, which we could use in the Cartesian coordinate system, we can plot a point on it, and then create text that describes that point.  This is a sort of generative tool, in which one can use one's knowledge of an information space to generate any amount of specific data.<br>
<br>
If you are familiar with any sort of procedural generation, this yields the same kind of effect that Perlin Noise allowed in procedural generation, in that because the pattern remained consistent whether viewed from "from away" or "up close", procedurally generated content (images, models, clouds, cities, whatever) could scale to "infinite" detail, either looking at the "big picture" or with a magnifying glass.<br>
<br>
In the same way, this generative tool of mapping axes to an information space, and then using your own understanding of that space to extrapolate what text would describe that point in those axes' space.  <br>
<br>
This is actually the exact same technique I am using to write this book, as I have broken up the information space I am trying to cover into both a linear (sequential) flow (chapters), and then assigning various variables (in the forms of words in the topics) to create each chapter's text.<br>
<br>
Let's do one of these now:<br>
<br>
For the Atomicity value, let's say on a scale of 1.0 (Atomic) to 0.0 (Not Atomic), we have an Atomicity value of 0.25, or not very Atomic, but having some Atomic characterics.  <br>
<br>
Then let's say on the Specificity scale of 1.0 (Specific) to 0.0 (General), we have an Specificity value of 0.75, or fairly specific.<br>
<br>
Because we need to be specific, I am going to make up some details about the Atomicity of the thing in question, which I will use a database for:<br>
<br>
{{ start_quote }}<br>
This database provides limited atomic transactions.  Transactions are accepted, and written into a journal file, which is flushed to disk periodically, but not in sync with the transaction being written, for performance.  The means that in certain circumstances a transaction may be partially written onto the disk.<br>
{{ end_quote }}<br>
<br>
So, this terrible database accepts things as Transactions, and journals the transactions, but it doesn't flush the journal Atomically, so you might have partial transactions on the disk.  This is actually always potentially true, since a power failure could cause a partial transfer, in some hardware configurations.<br>
<br>
In practice, modern controllers accept a queue of IO requests, and can do some optimizations on them, depending on the construction of the storage medium (what type of disk/etc), and so flushing merely pushes more things onto this queue, and if you cant put more things into the queue, you have already maxed out your throughput in this configuration.<br>
<br>
In this case, it is possible that the queue can take more total IO requests if they are batched, and for a given workload and hardware specification, you may need to do this.  Moving on.<br>
<br>
<br>
What if we had a Specific value of 0.0, instead of 0.75?<br>
<br>
In this case we would be 100% Generic, but we still have to say something relevant so we might summarize:<br>
<br>
{{ start_quote }}<br>
This database handles requests in Transactions, and writes them to a journal file, but flushes only periodically, so Transactions may be lost on power failure.<br>
{{ end_quote }}<br>
<br>
This gets across the idea of what's going on, but is very brief about it.<br>
<br>
What if we had a Specific value of 1.0, instead of 0.75?<br>
<br>
We would have to specify the entire code, every line, and it would need to be idealistically correct (or actual implementation), and we would have to specify all environment requirements.  Why?  Because we are 100% Specificity at 1.0.  This means absolutely everything must be specified, if this spectrum or axis is to have real meaning.<br>
<br>
Taking this into account, maybe my example using 0.75 for that level of specificity isn't nearly detailed or specific enough, but on first introduction 0.75 sounds like "pretty specific", where 0.5 sounds "half specific, half vague", and I wanted to be detailed enough to get real implementation points across, but also not too long for pacing.  Only after thinking about what 100% Specificity would really mean does 0.75 seem too high.  <br>
<br>
This is yet another tool for performing evaluations, by making one example, and rating it, and then making another (or a series of others) example, and rating that, and going back and re-rating the first example, then the second again, and finally creating examples of the most extreme situation you can imagine at both ends of the spectrum (being 0.0 and 1.0), and then re-evaluating the middle ones again.  This is a method for getting a numerical sense of an information space.<br>
<br>
So, these are 2 more tools we can use in the future to discuss problems in a clear and precise manner.  Trying to get as close as we can to 1.0 specificity, without losing the ability to make progress.<br>
<br>
But where we're we?  Oh, yes!  Humans!<br>
<br>
When we are having conversations like the one we are sort-of currently involved in, being specific by saying "Humans" instead of any other word allows us to understand we are using technical jargon, and we mean technical things.<br>
<br>
This allows us to move away from our standard social communication style, and into a technical communication style, to discuss technical points at a detailed level.<br>
<br>
So while it is weird to type and say, it has a benefit for clarity, which is an important attribute of Engineering.<br>
<br>
Also, it will make it easier to relate to your future AI overlords, which will be helpful.<br>
<h3 id=eb72cfe6249ca80ac02d25c50109a4da><a href="#eb72cfe6249ca80ac02d25c50109a4da">2.6.15</a>: Philosophy</h3>
<br>
If you didn't know, there are 2 Greek roots in the word "Philosophy".<br>
<br>
These roots are "love" and "wisdom", so Philosophy is the "love of wisdom".<br>
<br>
I look at Wisdom and Intelligence as different axes.<br>
<br>
Wisdom is gained from experience, and has to do with the breadth and depth of insight into topics, and being able to make judgements that detail what might be favorable and unfavorable outcomes, and why.<br>
<br>
Intelligence I look at in very different perspective, which is "making an action that yields beneficial results for all parties involved."<br>
<br>
This is not a common definition of Intelligence, but it has a rigid definition, and comes from a brilliant article written by Carlo M. Cipolla, then a professor of Economics at UC Berkeley, and is one of the greatest things I have ever read, and quite literally changed my life.  I see the world differently after having ingested it, and am much better for it.<br>
<br>
The article is entitled "The Basic Laws of Human Stupidity", and while it's title and subject matter focus on "Stupidity" (anti-Intelligence), it's real function for me was to qualitatively and quantitatively define what intelligence is.  He puts it on a 2D graph, and charts it, and allows for pinpointing different kinds of Intelligent and Anti-Intelligent actions.  Try not to let the negative sounding name cause you to avoid this information, it is a very important set of thoughts he has encoded there-in.<br>
<br>
http://www.amazon.com/The-Basic-Laws-Human-Stupidity-ebook/dp/B005ZX622C<br>
<br>
http://harmful.cat-v.org/people/basic-laws-of-human-stupidity/<br>
<br>
{{ todo__request_rights_to_reprint_article_in_my_book_from_family }}<br>
<br>
These start to illustrate the differences between Intelligence and Wisdom, to me, and will hopefully (over the course of the material) become clearer and useful to you as well.<br>
<br>
So Philosophy is the "love of wisdom", and I love wisdom, so I take it for that.  I orient myself on "Applied Philosophy", which is Philosophy in a way that I can use to achieve results (internally and externally) and not merely as a way to win arguments at dinner parties, or making comments that end with "Do you want fries with that?".  <br>
<br>
Another purpose of Philosophy is to be a structure around the question, "Why?"<br>
<br>
In much of Engineering we focus on "How?":<br>
<br>
- How do I use this library or software?<br>
- How was this software written?<br>
- How do I get the result I want?<br>
<br>
Philosophy is more angled like:<br>
<br>
- Why should I use this library instead of that other library?  How are they different?  What will be the effect of using the one, versus the other?  If one of them is better suited for my current situation, but the other may be better suited to a future situation of mine, when would be the time to start switching over?  Is it worth doing?  Should we even be doing any of this at all?<br>
<br>
- Why was the software written in this way?  How was the developer trying to allow me to solve problems with it?  How can I best use this software to work with the way the developer was trying to enable me to solve a problem?  Between the different ways I could do this work, what are the different effects they will cause, and which of those do I think will be most beneficial for me?<br>
<br>
- Why am I doing this?  What are my goals?  How can I define them precisely?  Is my entire team in agreement with this, as an intention?  Are we able to communicate effectively, ensuring that we understand each other and can work together efficiently?  How would we know if this is true, and we are succeeding?  How can we measure that success, and compare it to the goals we wanted to achieve before we started?<br>
<br>
Philosophy is about depth, and the ability to inspect things from different angles, and while it may appear on the surface (and is sometimes explicitly stated) that it is trying to "define the way things are", in actuality the Philosophical inspection never ends (Infinitely Recursive), and so it does not have the ability to ever define things "the way they are", because it can't stop defining things.<br>
<br>
This is a "Turing Machine" in which we know it will never halt.  There is no final exit or return from Philosophy, it is a rabbit hole that never ends, and goes as deep as you are willing to look, and the detail expands to meet any closer inspection.  What is true from one perspective, or frame of values, is false from another.  It's flexibility to reframe data is infinite.<br>
<br>
This is do to "Why?"  Why?  Why?  Why?  Why?  ...<br>
<br>
I think Philosophy has a bad-wrap these days, and I hope to show, if only in a thin slice, that there is a way to use Philosophical ideas in a practical way to add clarity and improved performance in your life and work.<br>
<br>
Transitioning back to Wisdom (Note to self: Awesome segue!):<br>
<br>
One simple way to see Wisdom is "good ideas".<br>
<br>
To keep things simple and say, "I love good ideas", is why I love and heavily utilitize methods of philosophy.  I make use of different kinds of philosophies in my own ways, I take their definitions and interpret them in my own meanings, and I mix and match pieces wherever I need to as configurable tools to be used in understanding the problem I have at hand, and manipulating it into what I what I want it to become, to get the results I want.<br>
<br>
This is what philosophy is an element of, for me, and in this book, it will be how I will go about using it, and referencing it.<br>
<h2 id=af1f8c9950e296d130a668076e4ba88b><a href="#af1f8c9950e296d130a668076e4ba88b">2.7</a>: The Philosophy of Pragmatism</h2>
<br>
Pragmatism is a formally written up philosophy, and you can read more in-depth about it on the Internet or various books.<br>
<br>
For the purpose of this book, we'll be using it in it's core form, in my usage, which is:<br>
<br>
"Pragmatism is when you only evaluate an action based on the effects, and nothing else."<br>
<br>
"Effects" are different than "results", because results is more about what you wanted to achieve, and whether you felt you achieved that thing or not.<br>
<br>
"Effects" are more general, and deal with all things that come from an action.  The change of state from before to after.  How are things different?  How did they change?  What are the effects of this change?<br>
<br>
There can be a lot of confusion with the word "pragmatism", and it is often used interchangeably with "practical", and sometimes conflated with "common knowledge", but it does not mean these things, and for the purpose of this book we will be strictly avoided any conflation with "practical".<br>
<br>
"Practical" is a very loose term that means efficient in both resources and results, it gives you "good enough" results, with an acceptable amount of resource usage.<br>
<br>
This has nothing to do with Pragmatism, as Pragmatism has no concern for the amount of resources that were used, or if the burden was terrible, or whether it was convenient.  These things may show up in the "effects" of an action, such as the amount of resources impacted is part of the effect, but "practical" ties these things together as being important in the concept, whereas with Pragmatism, all of the effects are simply data and will be evaluated as to whether those are desirable effects, or not.<br>
<br>
This also covers another topic that causes confusion, which is "side-effects", and although this is useful in language to denote things that occurred that may not have been part of the "main" or "center" (hence, "side"), in truth all things are simply effects.  Whether they are in the "center" or the "side" is based on your perspective, and likely to cause partial blindness in evaluation when they are separated, instead of being seen as a single set of effects.  Some you intended, some you did not intend, but they are all equally effects of the action.<br>
<br>
Grouping everything into only one single pool of "effects" is the better way to do this, when you prioritize for accuracy and clarity, because you are not trying to push anything to the "side-lines" and are seeing all effects as being caused by your action, and thus will evaluate that action more comprehensively.<br>
<br>
What are we excluding when we only look at effects?<br>
<br>
Initially, we are excluding our value judgements, our goals, our history, culture, feelings, wants and desires, and anything else, so that we can focus on dealing with "what changed?" or "what will change?", and detailing these effects (changes) qualitatively and quantitatively, where possible for each.<br>
<br>
This allows us to go beyond whatever limitations we might be currently bound by, if we don't apply them to the situation before we have enumerated and started to evaluate all of the effects, not merely the effects we want to focus on.<br>
<br>
In terms of getting coverage like "all of something", we are obviously talking about potentially a lot of data and too much to grasp at any time, and this is where Systemic Thinking and Slicing the Pie come into effect, in that we can box these effects into groups, to be inspected in more detail as needed, or viewed from farther away, and seen with less detail, or Specificity.<br>
<br>
Again, this ability to scale in or out from details, is an important skill that needs to be developed and applied to get a good grasp on what is going on.  Without this, one is going to be "stuck" with the view from one's current perspective, which may change under different circumstances, giving one inconsistent results even from one's primary point of view.<br>
<br>
I like to give examples with every topic I introduce, but I don't think it's the right time to go into an example deeply on this, so we will just touch the surface of an example we will delve into deeply soon.<br>
<br>
How can we use Pragmatism to get better results?<br>
<br>
For instance, one thing that we are concerned about greatly in Production Operations is "up-time", which is the Availability of our services.<br>
<br>
How do we get the "best" (most) up-time?  Well, the most important thing is actually a "negative", which is "don't go down".  However, "not going down" takes "all the things" working all the time, even when some things fail.  This is obviously a very complicated endeavor to try to improve.<br>
<br>
By using Pragmatism, and only focusing on the "effects" of doing one thing, versus another thing, we can evaluate that method with the highest signal-to-noise ratio, so that we are spending more time thinking of the most-relevant things, and are actively trying to avoid things that may be distractions.<br>
<br>
Knowing that one thing that causes down-time events is "Humans making changes" we can say that we want to optimize for making more changes through automation, and less changes through direct Human manual (by hand) efforts.<br>
<br>
Since Logic is able to be written so that it runs deterministically (if done "properly"), then this Determinism is an attribute which helps us improve our up-time, by removing the non-determinism of manual Human changes.<br>
<br>
We can evaluate these based on the effects of what happens when Logic updates a DNS Zone file 10000 times, versus having Humans update a DNS Zone file 10000 times.  From these cumulative effects, we can see that the Humans will make more mistakes in the act of updating the zone file, than the Logic will, and thus the effect of Human edits are more errors, which reduce our up-time.<br>
<br>
There is a lot more detail that could go into this analysis, as with anything, but this is getting our feet on the path of how to analyze things by their effects, trying to strip out anything that is not an effect of the process.<br>

# Chapter 3: Engineering Philosophy and Methodology in Operations


Alright!  The book is really starting now!



We have cleared the hurdles of disclaimers, how-to-read, introductions, and terminology.  We can now get into the real substance of of why we are both here:  The Engineering of Operations.





<h2 id=b313ae83a593ebeebefbf3e427c23f35><a href="#b313ae83a593ebeebefbf3e427c23f35">3.1</a>: What is Engineering?</h2>
<br>
More definitions?  Well, we are never going to stop defining and re-defining things to our particular circumstances, as we simply can't front load all the thinking, and sometimes we will need to be more specific, but at least we are now into the real content, and not the peripherals.<br>
<br>
Engineering, to me, is:<br>
<br>
"The efficient use of resources applied in an environment, to yield a desired effect."<br>
<br>
Generic and vague?  You bet!  But, also it can be used to insert in any specifics into the general terms to get at a more specific definition, like so:<br>
<br>
"The efficient use of time, personnel, money and physical devices (servers, etc) applied into a Production Operations environment, to yield high up-time, acceptable performance, and scalable management."<br>
<br>
That's starting to be more clear, and more specific to our current topic than the more general answer, but I see all of Engineering as a similar set of options.<br>
<br>
Whether Engineering is applied to building a bridge, a canal, a sky scraper, or a production operations environment, it needs to be efficient (because being inefficient might mean it is not able to be completed, or "fails"), and it has certain resources (universally time, almost always money, and also almost always people, and then it might be soil conditions, and logistics of getting materials from Point A to Point B, or whatever), and has specifically desired effects, such as a set of interlocking canal segments of the Panama Canal, or a sky-scraper buildings ability to stay erect under it's own enormous weight and support and movement of the soil, or the digital and physical equivalents in server operations.<br>
<h3 id=2ee66e2e591f559bcad84f3a294d732a><a href="#2ee66e2e591f559bcad84f3a294d732a">3.1.1</a>: A brief interlude on the Strengths and Weaknesses of Metaphors</h3>
<br>
There is a trade-off on Metaphors, and it has to do with expert-knowledge and accuracy.<br>
<br>
Metaphors, in my opinion, are most useful when are you not an expert on the subject of the metaphor, or defer your expertise to see the metaphorical example being used as tool for communication.<br>
<br>
If I give the example of:<br>
<br>
 "Production Operations must deal with the problems given by information alignment and physical hardware management, similar to how building a bridge must deal with the soil, water, wind and temperatures around a bridge, and the materials used to construct the bridge."<br>
<br>
This metaphor, or simile in this case, is most useful if the audience are not experts at building bridges.  As an expert in building a bridge, they may have a very different take on what it takes to build a bridge, and what the issues are, and they may validly complain about my use of analogy between information and soil.<br>
<br>
This is where metaphors are weak, because they are meant to give "a comparative idea" by taking us out of the details we are currently immersed in, and putting us into a "very loose" frame in another topic which we can discuss as non-experts.<br>
<br>
Because of this, it may be useful to change metaphorical topics if someone introduces details about the metaphor which derail the intention of using a metaphor.  This can be referred to as "over-extending the metaphor".<br>
<br>
If you find yourself disagreeing with a particular metaphorical usage, try to re-frame the metaphor yourself into a different topic, preferably one you do not have expert knowledge in, and see if you can gain more insight into it that way instead.  <br>
<br>
This can also be a useful tool in determining if you understood someone correctly, as you can re-frame what you understand of their point with a different metaphorical topic, allowing them to re-map what they meant to your new metaphor, and if they are agree, you are both likely thinking of very similar things.  Going back and forth like this, when there is still mis-alignment, choosing new metaphorical topics, or changing the reference of the metaphor, can allow a complex topic to be worked through in a shorter period of time than going to full-fundamental-definitions and working up from there.<br>
<br>
The curse of an expert is a real thing, and doesn't just ruin movie plots ("We are 10 digits into hacking the mainframe password, but they are using 49-bit encryption, so it will take two more hours.  You need it done in 10 minutes?  We'll make it happen."), but also can ruin the intention of any type of alternative explanation, which is trying to expand on an idea in a hand-wavy-kind-of-way.<br>
<br>
This is an attempt to get you to use more information than what is being provided, which you already internally know, instead of explicitly providing all the information.  People are great at filling in this information, and while this works best in spoken conversations (say, where you could finish the other person's sentence), metaphors are an attempt to do that explicitly by providing a non-related but comparable reference.<br>
<h2 id=a941939e629b2be25c1ba265cbd9aaed><a href="#a941939e629b2be25c1ba265cbd9aaed">3.2</a>: Difference between Application and Operational Logic</h2>
<br>
Is there a difference between Logic that is written for Operations automation and Logic that is written for non-Operations?<br>
<br>
In my opinion, there is, and it is a big difference.  It doesn't need to exist, but it does exist, and they are not mildly different, but extremely different, at present.<br>
<br>
I see this changing more in the future, as distributed programming environments not only become normal, as they are are now, but that we start to get generational levels of experience in the field.<br>
<br>
I will call non-Operational Logic "Application Logic", even though it may not strictly fit your definition of what an Application is, since it changes under different contexts.<br>
<br>
For instance, in a Production web serving environment, you frequently have "Application Servers" which might run Java Tomcat, JBoss, or Ruby of Rails, or a Python, or other Logic required for producing dynamic web content.<br>
<br>
These would be "Application" Logic in the terminology as I'm using it.<br>
<br>
So, what is the difference between Application Logic and Operational Logic?<br>
<br>
The main difference is Resiliency, and this has a number of parts to it.  For instance:<br>
<br>
- Application Logic requires that the environment that it runs in be configured, or the Logic will fail, and often will fall non-gracefully.  How gracefully it fails generally has to do with how "mature" the Logic is, in terms of it's life cycle.<br>
<br>
- Operational Logic is built to support infrastructure, with the knowledge that the infrastructure components are going to fail, and the Operational Logic needs to not only recognize the failures, but needs to continue to work in whatever ways are still available.  <br>
<br>
Don't misunderstand me in that I am criticizing Application Logic developers, and praising Operational Logic developers, they have different goals, and so will product works that have different results because of this.<br>
<br>
It mostly has to do with priorities and responsibility.  Operations is responsible for infrastructure working, and is responsible for solving operational failures.  Applications are made to provide end-users with correct results, and have an expectation that the operational environment is working correctly to do so.  This is a natural prioritization, and not an incorrect one.<br>
<br>
For example, say there are a pair of relational databases in a Master/Slave configuration, and the Master node fails, because of the priorities for Application Logic, generally the application will just fail until the Master/Slave designators (floating IP address or DNS name change, or from another directory-style service).  <br>
<br>
There are some good reasons why Application Logic currently behaves this way.  The first is that it takes extra Logic to determine what should happen if the primary database server goes away, and this will be (eventually) taken care of by the Operations team, through manual intervention or automation.<br>
<br>
Some classes of databases have a multi-node approach from the beginning, to make these types of events less frequent, since a server can go down, but others will be up, and the Application can talk to any of them.  These databases still have failure cases though, and so the results can up being the same depending on the type of failure.<br>
<br>
Part of the "extra Logic" is that Applications are meant to serve end-users, and the time put into making this extra resiliency is often prioritized to go into making additional or improved features.  Whether you agree or disagree that this should be the priority, it often is the priority, and it servers us well to accept Reality, and work within it's confines.  If we want to change this, we need to change the priorities by showing more value given with a different priority.  Difficult, but possible.<br>
<br>
Additional to the Logic required to handle failures, is that Application code needs to be very stable for-it's-own-purposes, and adding in this kind of Logic means that during failures more cases may be found that could be handled, which means more changes to the Logic surrounding database access, which means more change/churn, and this leads to more potential bugs.  Specifically the kind of bugs that have data access requests failing, which is someone no one wants.<br>
<br>
While I think with better education, and better base-libraries we can solve these problems and Application Logic can be more like Operational Logic in handling failures, or in fact leverage the same Logic, so that they are working hand-in-hand, I am making this point because this is not currently standard, and has never been historically standard.<br>
<br>
Another thing that Operational Logic needs to do, is to simply have more information about the operational environment.  Seems like common sense, but since we are building from the foundations, it is necessary to state the details.<br>
<br>
As we get into what it takes to construct Operational Logic the brief description I have given here will be born out by many more details and along many more axes, to determine how these things are different, but for now it is sufficient that we can see that they are indeed different things.<br>
<h3 id=1e13f344d1ae44173a1f9532c809f6b1><a href="#1e13f344d1ae44173a1f9532c809f6b1">3.2.1</a>: Many applications and services.  One Operational environment</h3>
<br>
Another difference between Operational Logic and Application Logic has to do with the nature of their environments.<br>
<br>
In a given organization there is generally only one "Production Environment".  It may span many data centers, and there may be regional data center teams to support the physical side of the operations environment, but it generally by classified and worked on as a single environment.<br>
<br>
There are organizations who break these up, but they are frequently either regulated businesses, or ancient, or have some other external reason for running segmented Production Environments.  In general, companies, even very large ones with the largest Production server collections, only have one Production Environment.<br>
<br>
This means that in an entire Product Environment is being managed in a single manner:<br>
<br>
- There is one way to update Production DNS.<br>
- There is one way to provision new servers.<br>
- There is one way to fail over from a faulty server to a working server, for a given service.<br>
- There is one way to handle authentication and authorization for user and role account access.<br>
- There is one way to centralize log collection.<br>
- There is one way to monitor and alert on logs.<br>
- There may be one way to software releases.  (Actually, this could be on a product by product basis)<br>
<br>
<br>
Each of these "one way" methods may contain many sub-methods, such as you may actually have several monitoring packages, but collectively they make up the "one way", and generally things are put into one of them, versus any others, unless multiple coverage is desired.<br>
<br>
By this "one way" concept, I don't mean to be naive and really limit it to "one thing", that is why there is "one way to" and not "one thing that does".  However many methods of doing something (as legacy implementations will stick around for a long time, and sometimes there is intra-team competition for creating solutions).<br>
<br>
The thing about "one way to do it" systems that are different than "lots of different environments, that do it their own way", which is the comparison I'm trying to make, is that in a one-way-to-do-it system is that you don't want to introduce competing services.<br>
<br>
It is more efficient to configure, manage and have life-cycle support if we have limited the amount of ways we do things<br>
<br>
In terms of creating Application Logic, it is easy to separate components of the Application or separate applications that may work in tandem or sequence, or may be linked through a common Data Source, a through a messaging queue, RPC (Remote Procedure Call), or other data transference mechanism.<br>
<br>
There are many ways to do it, but the point is that you can split up personnel to work on different things, and their work can be isolated from each other, only connecting at certain points to do data exchanges. <br>
<br>
This could be generalized to always be true, but again, the point Im making is the difference between one thing and another, not in their similarities. <br>
<br>
The Operational equivalent needs to be more tightly integrated, because it is trying to support a one-way-to-do-it system, and where things are not one-way, they would often be better if they were.  <br>
<br>
So it is a Goal of an Operational system to have one-way-to-do-it, for efficiency, and it is a Goal of an Application system to have many ways to do many specific tasks, so that personnel can be split up into separate teams and given specific goals for those teams.<br>
<br>
The Operational team, in contrast, has more generalized goals, that take into account the entire Production Environment, and are more concerned about:<br>
<br>
- Total availability of all services in the Production Environment<br>
- Manageability and life-cycle maintenance efficiency<br>
- Performance of the entire system, with a priority on bottle-necks<br>
- Not introducing problems into the environment, and prioritizing solving ones that currently exist<br>
<br>
Again, we could align these in terms of how they are similar, and we will find that they are mostly similar, but there is a difference between Operational Logic and Application Logic, and in this circumstance we want to understand the differences more than the similarities, as we are dividing the two subjects for inspection.<br>
<br>
I will not spend much more time on Application Logic, as there is much writing about that in non-Operational literature that covers the current understanding of how to do that, and that is not the focus for Operational Engineers.<br>
<p id=ae00bdb9200029912abd5c942058cf26><b><a href="#ae00bdb9200029912abd5c942058cf26">3.2.1.1</a>: Making more depencies.  Networked dependencies.  When things are broken, how will your system function?  Will it fail?  Will it make it worse?  Will it make a mess?  Will it corrupt and destroy?</b></p>
<br>
Now that I've established there are two different things, with different qualities, Operational Logic and Application Logic, let's get into what goals Operational Logic should have:<br>
<br>
- Operation Logic should try to minimize external dependencies, especially networked dependencies.<br>
<br>
If we know things are going to fail, and we are writing Logic to handle them in cases where they have failed, then we know the infrastructure we are writing against, to manage, will also fail.<br>
<br>
Knowing this, we can optimize for the case that we want our Operational Logic to continue to function properly even in the case of a network partition or failure.<br>
<br>
If I have locally cached data to the server my Operational Logic is running on, I can access that data consistently, even if the network fails and the server running my Logic cannot reach other networked services or nodes.<br>
<br>
This allows me to handle failure cases more gracefully.  For instance, maybe all the nodes are not unavailable, and if I have the data that lists all the nodes and their properties on my server already, I can verify which are reachable, and which are not without an internal processing failure occurring (cannot access data to check with, because it has been partitioned in the network failure).<br>
<br>
- Operational Logic should try to minimize the amount of frameworks, libraries and services it uses.<br>
<br>
Frameworks and libraries are useful, they server a purpose, however the more things you have, the more things that can fail and cause your Logic to no longer function.<br>
<br>
Additionally each of these things needs expertise to manage and troubleshoot, and your Operational Logic needs to be as straight-forward and simple as it can be, so that when problems occur, they can be troubleshot and resolved quickly.<br>
<br>
Operations teams are also generally (at most organizations) much smaller than their Application Engineering departments, so this must also be done with less people involved in the work, and with shorter time frames.<br>
<br>
Since the Operations team also has to take new services into account, and new hardware platforms, and may be given very short notice to get these working, the Operational Logic needs to be written to be able to be adapted to these situations extremely rapidly, and without causing problems for the existing infrastructure.<br>
<br>
After all, in a one-way-to-do-it system, if you break something with a change, you have might have broken everything with the change.<br>
<br>
This "force multiplier" or leverage gained from automation is a double-edged sword, in that it cuts your problems efficiently but if used incorrectly will cut you as well, by automating failures into happening in a wider area and faster than Humans can manually do.<br>
<br>
In the past, these problems could be avoided when automation was implemented incorrectly by simply removing the automation and having everyone do everything by hands again.  I have seen this happen many times, when automation was immature, or was not given proper resources (mostly time) to be implemented correctly.<br>
<br>
As the scale of operations continues to grow, this will simply not be possible or efficient in terms of money and personnel to scale enough people to do things manually, and the number of mistakes created by manual work will mean that even getting through the dangerous stages of automation will be a better trade-off.<br>
<br>
We aren't quite there yet as of 2015, but it is coming.  Some organizations have a good amount of automation, and we will create a spectrum soon to do some analysis on this, but they are not yet comprehensively automated, and are approaching it through Aggregation, instead of Slicing The Pie.<br>
<br>
This change in viewpoint is what is required to deal with automation comprehensively, and it starts with understanding how to optimize the Operational Logic to yield the effects required to allow this to happen.<br>
<br>
- When things do break, how does your Logic function?<br>
<br>
Minimizing dependencies, locally caching data are two strategies in making resilient Logic, but the real goal is that the Logic continues to function exactly as you designed it.<br>
<br>
By using Slicing The Pie methods of black boxing work that needs to be done, one can create a system that anticipates failures, and continues to function properly with the resources that are still available to it.<br>
<br>
This will the be automation we are going to inspect and start modeling soon.<br>
<p id=8eb74e570e995c459a430857793ad69f><b><a href="#8eb74e570e995c459a430857793ad69f">3.2.1.2</a>: Like 1 big computer.</b></p>
<br>
One reason why the difference between Operational Logic and Application Logic matters if that it provides an insight into another way of looking at the Production Environment.<br>
<br>
By seeing it as a "one-way-to-do-it" system, where we mostly want things done one-way, we can actually look at the entire collective of Production Operations as a single entity.<br>
<br>
We can abstract it so that it is "one big computer", with many nodes, which can be configured as if it one a single computer, with containers in it, or rather different directory mount points.<br>
<br>
Each node in this "one big computer" has it's own internal process schedulers (as Operating Systems start processes through a scheduler, that manages interrupts and putting processes back onto CPUs when their system calls finish), and it has it's own internal RAM and storage, etc.<br>
<br>
But, the entire set of machines, no matter how distributed they are across the planet, or how many nodes they are, can be controlled in terms of configuration and operational management, as if they were one system with many parts.<br>
<br>
I think of this as a layer of Operating System above the traditional bare-metal and virtual-machine installed Operating Systems, whose goals are to abstract physical hardware (BIOS, Buses, Devices), and manage device drivers, and schedule processes on their CPU, and manage libraries and file systems and virtual memory and such.<br>
<br>
So, I'll introduce this acronym as "DOS", Distributed Operating System.  It is similar to a "cluster", but clusters are generally more uniform, trying to have the same type of pieces controlled by the same processes, in this they are homogeneous.<br>
<br>
Distributed Operating Systems (DOSes), would be heterogeneous, with any number of different hardware specification, different Operating Systems, and different services, and can contain any type of storage, in any configuration.<br>
<br>
Just like a single system, where you can run any kind of software (for that platform), or configure the directory structure in any way you want, there is no standard order for a DOS, it is merely an abstraction of working with a number of systems as if they were one system.<br>
<br>
There are unfortunately some acronym name conflicts with DOS, such as the legacy "MS-DOS", but this can simply be specified as "MS-DOS" or "PC-DOS" for the rare instances that someone needs to refer to this.<br>
<br>
There is also another acronym for "DoS", which is Denial of Service, and usually takes place in reality as a "DDoS", Distributed Denial of Service.  The convention is to keep the "o" lower case, which makes this less confusing.<br>
<br>
Since we need to move forward in our industry, and distributed systems are here to stay, and we need to advance our methods of thinking about how to manage those distributed systems, I think we can safely take the acronym "DOS" for our purposes.<br>
<br>
One big computer, many nodes, heterogeneous Operating Systems, and services.  All able to be managed as a single system.<br>
<br>
It's a big deal, and I predict whether this terminology is adopted or not, that in the future we will end up seeing Production Environments in this way, because of the efficiencies that this will lead to.<br>
<br>
In any case, I'm going to detail how to build this sort of thing in this book, so you have a path to getting access to this technology in your hands already.<br>
<h2 id=92dfc6ded926f3d44bd483b43e658db3><a href="#92dfc6ded926f3d44bd483b43e658db3">3.3</a>: Axiomatic Engineering.  My method for making decisions that are not personal, even though of course they are my personal understand and information matching to the algorithm.  Present a method for discussing engineering in this manner..</h2>
<br>
We've been building up to this for a while, introducing different spectrums or axes for different Attributes of this or that, but do they fit into a system?  They do!  And I call this "Axiomatic Engineering", which is like working with mathematical Axioms, to create engineering solutions.<br>
<br>
In this way we can detail all of the Attributes that we would like, and specify the spectrums (or axes) of those attributes, and then assign values to each attribute axes that we would like.<br>
<br>
Do we want more Consistency or less Consistency?  Do we want more Availability or less Availability?<br>
<br>
Between Consistency and Availability, which is higher priority?  What sorts of trade-offs need to be made if we were to rate Consistency higher than Availability?  What about Available over Consistency?<br>
<br>
We can't possible implement the same solution while matching our different axes values, and priorities, because we care about different things in each circumstance, and so we will create a different solution.<br>
<br>
This is important in your own work, and critical for working in a team.  If you can't agree on your values, how will your work have the Alignment necessary to produce the effects you want with efficient use of your resources?<br>
<br>
Let's re-iterate my generic definition for Engineering again:<br>
<br>
 "The efficient use of resources applied in an environment, to yield a desired effect."<br>
<br>
So we have:<br>
<br>
- An Environment (Production)<br>
- Resources (time, people, hardware, money)<br>
- Effects (Availability, Consistency, Resiliency, Atomicity, etc)<br>
<br>
These are the fundamental elements of Production Operations Engineering, and how we mix and match them together, and the methods of their implementation, will determine the effects that we get.<br>
<br>
If we are being Pragmatic, and we are only concerned with the effects, then we can start to build an "Effect Estimating Machine", and this is done through Axioms, created by populating our Axes with values and prioritizing which of those values are more important to us than others.  After and during the implementation of the solution, we can use an "Effect Evaluation Machine" to determine how our implementation is matching up with our Prioritized Attribute Axes values.  These would be a type of mental Virtual "machines", which could be considered mental software, or well-structured, consistent, internal algorithms for thinking, and used externally for communication.<br>
<br>
Let's make an overview for all of services in the Production Environment:<br>
<br>
- Available.  Our services must be available.<br>
<br>
- Performant.  Our services must be fast enough for our purposes (poor performance under heavy load means that some percentage of our end-users will not have Availability).<br>
<br>
- Manageable.  We need to be able to control our environment, deploy software, upgrade security flaws, making configuration changes, add or replace server nodes, control user access, etc.<br>
<br>
- Visible.  We need insight into our system through monitoring, alerts, logs, etc.  We can't manage things if we don't know what is going on.<br>
<br>
That's a pretty good start, so let's take this as our basis.<br>
<br>
I have also ordered them in a general order of priority, because:<br>
<br>
- If the services are not Available, what is the point of it existing?<br>
<br>
- If the services are not Performant, then they are not available to some end-users, or are not timely.<br>
<br>
- If they are not Manageable, then we cannot control them to keep them Available and Performant.<br>
<br>
- If they are not Visible, we cannot efficiently Manage them.<br>
<br>
We could add other elements in here, or split these up, and some circumstances might order them differently, but this is a good starting place for our purposes.<br>
<br>
So, let's check our Attribute Axes for these prioritized goals:<br>
<br>
- Available:   Not Available <---> Completely Availability<br>
- Performant:  Slow <---> Fast<br>
- Manageable:  Difficult, Risky and Slow <---> Easy, Safe and Fast<br>
- Visible:  Opaque or Fuzzy <---> Clear and Precise<br>
<br>
For Manageable, I ended up creating three different sub-attributed, as saying "Unmanageable" really doesn't mean much, so we can re-write it as:<br>
<br>
- Available:   Not Available <---> Completely Availability<br>
- Performant:  Slow <---> Fast<br>
- Manageable: Risk: Dangerous <---> Safe<br>
- Manageable: Difficulty: Difficult <---> Easy<br>
- Manageable: Speed: Slow <---> Fast<br>
- Visible:  Opaque or Fuzzy <---> Clear and Precise<br>
<br>
I have split these up now into individual attribute axes for Manageable, and also re-ordered them slightly for better prioritization, as we are more concerned with Risk than Difficulty.<br>
<br>
Difficult things need more leeway in performing them, so I am putting this higher than Speed, because if you are doing something difficult, but do it quickly, it seems that might lead to more mistakes, which increases Risk.  Perhaps the "Safeness" of the higher priority will protect us from these mistakes, but unless that is guaranteed, than Difficulty should be a higher priority issue than Speed.<br>
<br>
Is Visibility really less important than all of those Manageability attributes?  Maybe not, let's do one more re-ordering:<br>
<br>
- Available:   Not Available <---> Completely Availability<br>
- Performant:  Slow <---> Fast<br>
- Manageable: Risk: Dangerous <---> Safe<br>
- Visible:  Opaque or Fuzzy <---> Clear and Precise<br>
- Manageable: Difficulty: Difficult <---> Easy<br>
- Manageable: Speed: Slow <---> Fast<br>
<br>
That looks a little better to me.  We need that Visibility, because it speaks to knowing what is going on.  I would rather than that then easier to faster management, as I need it to ensure my work is correct, or help with troubleshooting if an error is introduced.<br>
<br>
Now, we have some Attribute Axes, does that mean we have Axioms?  Not quite, but we are getting close.<br>
<h3 id=66087a8256206e268b334c49bc0ba5ef><a href="#66087a8256206e268b334c49bc0ba5ef">3.3.1</a>: 90-9-.9-.09% rules for priorities.  Make up your own rules if this doesnt work for you.  How to present them to people, a plan on improvining presentation.  A plan on requested for improving presentation.    If you dont come to common terms, you arent really communicating, talking past each other.</h3>
<br>
Let's take a brief tangent to talk about prioritization.  We made a couple prioritized lists earlier, and they were listed sequentially, but not numbered or evaluated in terms of "how much more important" each element was.<br>
<br>
There are many ways to rank priorities, and I have come up with a methodology that I like which I call the: "90-9-0.9% rule", and can be said as the "Ninety-nine-point-Oh-nine rule" to make that actually pronounceable.<br>
<br>
The progression continues on forever, with the previous item being ten times (10x) more important than it's following item.<br>
<br>
This allows for clarity in which thing is more important, and also for knowing when things are just not important any more.  It is purposefully exaggerated because without that clear separation, it is unclear why one action would be preferred over another action, because of "extenuating circumstances" may exaggerate a lower prioritized item over a higher prioritized item.<br>
<br>
It is my contention, that you should never do this.  If you are going to change prioritization, you should explicitly change it from the order of ["A, B, C"] to ["B, A, C"] for a given circumstance.  "ABC" may normally be what you want, and in some circumstance "BAC" may be better, and so you should explicitly state that.<br>
<br>
But, while evaluating the priorities of "ABC", then "A" should always be preferred over "B", or you should change your assessment of the priorities and state what the extenuating circumstances are for the priority change.  This is for clarity of communication, both with yourself at a later date ("Why did I do that?") and for people besides yourself who should share a common understanding with you.<br>
<br>
By making the differences 10x apart, it clarifies things much more than if they were less.  2x may still sufficient, but let us first demonstrate that merely being "too close together" in priority separation causes confusion, and from that we can see that "further apart is less confusion", and have our answer for why this is a valid technique.<br>
<br>
Say we have priority of Availability and Performance, and we assign Availability a value of "100" and we assign Performance a value of "90", so that Availability is the most important thing (an "A" grade of importance"), and Performance is the second most, but still highly important (a "B" grade of importance).<br>
<br>
So, Availability is first, but Performance is still quite close behind at 10%.<br>
<br>
Say there is a decision to be made, and it has to due with a hardware configuration, say cabling, that will give an Availability vs. Performance tradeoff.<br>
<br>
Let's say that we can cable up some storage which will be five times (5x) faster in Specification B, but it has as flaw in that sometimes it fails, but very rarely and might be able to be avoided with some maintenance actions.<br>
<br>
But, there is another cabling strategy which will ensure Availability, Specification A, even under intense failure scenarios, but is one fifth (1/5th) the speed (Performance) of Specification B.<br>
<br>
If we have a 10% difference in importance (100 vs 90) in Availability (Spec A) and Performance (Spec B), but we are getting a 5x boost of Performance if we choose Spec B, we have a decision to make, and some data to make it with.<br>
<br>
If we were going to seriously evaluate this, for a presentation on "What should we do?" to our department, we could make up some "point system" and do the arithmetic and decide which had more points.  On a scale of 100 vs 90, it is possible that the 5X performance could win the "point comparison" just because of the "5x" scaling value being used in some calculation.<br>
<br>
Being "10%" close to the top item, it may seem more fluid, in that "this time" we will still keep Availability over Consistency (not thinking or talking about it, or not publicly stating the change in priority through documentation, etc), but we will go with the Spec B 5x performance boost, over better Availability.<br>
<br>
Making this trade-off isn't wrong, the proposed down-time might be acceptable, if it doesn't also some with a Consistency trade-off of data corruption (because we haven't accounted for that, you might find that acceptable as well as a trade-off) or another important Attribute which needs to be accounted for.  (Aside: Data Corruption would actually impact Availability directly, since if the data is corrupt, it isn't Available in a useful form.  Consistency in terms of recovering may still take time, and also count against Availabilty.)<br>
<br>
However, when making the scales of the system ten times (10x) different, then the spread is much different from the beginning.  Availability is worth "90", and Performance is worth "9".<br>
<br>
Even if we took a very naive algorithm of "5x performance is 5x the value", we get "90" vs. "45", and Availability is still on top.<br>
<br>
If we change the value to "10x performance", then we get "90" vs. "90" and while the positions match, we still know Availability is #1, and so it is clear that Availability is still our top priority in this case.<br>
<br>
If we change the value to "100x performance", we would get "90" versus "900" and it is clear this Performance has true value.<br>
<br>
What it means in reality is that we have a new Caching Layer.  With 100x performance (or even considerably less), it is worth it to try to leverage that storage in a different capacity then we are currently considering.  The "balance of scales" is heavily in favor of using "Specification B", because it's performance simply cannot be denied.<br>
<br>
It could be used for very fast read-only queries, or it could be used as transient storage for incoming queries, so that there is a "pretty reliable, with known long-term faults" solution in place for taking incoming data as quickly as we can.<br>
<br>
These types of analysis are what using axes of values, and combining them into an easy-to-communicate-and-visualize method allow.  We can change the values around, put them into forms or a spread sheet and apply algorithms to compare them quantitatively, etc.<br>
<br>
So, I have establish that using 10x scale differences has value, so let's put it to use:<br>
<br>
- Available:   90%<br>
- Performant:  9%<br>
- Manageable: Risk: 0.9%<br>
- Visible:  Opaque or Fuzzy 0.09%<br>
- Manageable: Difficulty: 0.009%<br>
- Manageable: Speed: 0.0009%<br>
<br>
Now the sequentially prioritized list we created before becomes numerically weighted.  We can calculate against each attribute based on the value we have assigned it, to determine which actions we should take next.<br>
<br>
But, one might ask, isn't setting things at 0.0009% and lower making them trivial and not important to work on?<br>
<br>
That depends on whether there is more important work to be done, which is the beauty of this system.<br>
<br>
For instance:<br>
<br>
- If this is no work to do at the 90% layer, because the system is currently up (Available)<br>
<br>
- And, there is no work to do at the 9% layer, because the system is currently running fast enough (Performant)<br>
<br>
- And, we are not currently evaluating making a change that introduce Risk into our Production environment (Manageable: Risk, at the 0.09% layer)<br>
<br>
- And, we have a problem with how Difficult some tasks are to perform (the 0.009% layer), then this is currently the top priority, and this work should occur.<br>
<br>
Should we also schedule work to fix "Manageable: Speed" problems (at the 0.00009% layer)?  Not unless we have another person to assign it too, as the 0.0009% layer is 10x more important.<br>
<br>
I think this is a system that provides a lot of clarity for what is important right now, and how we should design things, and how to separate what should be done from what should not be done.<br>
<br>
In a one-way-to-do-it system, you do not want to do all-the-things, you preferably want to do one-thing for any given category of thing, so that you can gain efficiencies from that correctly chosen thing.<br>
<br>
Although I believe these 10x differences, and being able to maintain a regular scaling interval (10x) between priority levels is good, and the "90-9-0.9%" format makes doing this clear, it is not easy to communicate about these levels using the exact percentage values because saying "0.0009%" is difficult, and is confusing between say, "0.009%" and "0.00009%".<br>
<br>
Instead we can simply order the layers as "Top Priority", "Second Priority" and so on, or some other labeling structure which is easier to say.<br>
<br>
Then you can say "This is 5th level priority, but we don't have anything to do in levels 1 to 4, so it is currently the top priority", which is clear, numerical, and does not use potentially confusing real numbers for normal communication purposes.<br>
<br>
The labelled tier structures can be replaced with their numerical equivalents to perform quantitative analysis whenever it is needed.<br>
<br>
The take-away for this section is not "this is a good technique, use it", although I am currently using it, and I do recommend it, but the larger lesson here is that you can make up these types of devices yourself, and you should.<br>
<br>
Come up with your own numbering schemes, labeling schemes, and determine the exact meaning for each of them, and reasoning behind why they are a valid method of working, and then suggest other people use them yourself.<br>
<br>
This is the type of Engineering discussions I would like to see more of, and the type of Engineering thought that I believe the Operational Engineering world could benefit from.<br>
<br>
We get clear sets of data, that are quantifiable, and qualifiable, and we can test ideas against them, and communicate clearly about what our priorities are, down to which axes of information, and we can change the attribute axes values or priorities and talk about how those changes would affect our designs, and evaluate how well our implementations did against those values during and after implementation.<br>
<p id=e4f58bc454dce4b3362881399d9ca4fd><b><a href="#e4f58bc454dce4b3362881399d9ca4fd">3.3.1.1</a>: Assigning different people different priorities is what makes up different roles.  This allows different points of view, to make the organization stronger and more thoughtful, by design.</b></p>
<h3 id=d2c6e14bfa28136f85c785a79fcfc39d><a href="#d2c6e14bfa28136f85c785a79fcfc39d">3.3.2</a>: Creating Axioms from Axes</h3>
<p id=9daefd3b7edab6a712ab778906fedc9f><b><a href="#9daefd3b7edab6a712ab778906fedc9f">3.3.2.1</a>: Impersonal decision making through communicated values and priorities using Axioms</b></p>
<h3 id=5c1f069a25780e9d9aff8574624089fc><a href="#5c1f069a25780e9d9aff8574624089fc">3.3.3</a>: FOE: Fashion Oriented Engineering.  "Blogineering".  real evaluations of the environment, agreement between team on details, moving forward.  How to do it quickly.   Honesty in public relations, be skeptical of the claims of others.  No one will state they are fuckups, but that doesnt mean they arent asked to blog about their operational endeavours anyway.  What works for them may not work for you, apply Axiomatic Engineering principles, decided by you and your team.  Use everyone for source information, but nothing as universally applicable.  It's just another idea, including this one.  In-take, evaluate, match to your environment (synthesize), iterate, evaluate, repeat.</h3>
<h2 id=4410772cb808c71ea7621428281fa35c><a href="#4410772cb808c71ea7621428281fa35c">3.4</a>: Evaluating changes.</h2>
<h3 id=26ab897a0841f617abc1175707de81dd><a href="#26ab897a0841f617abc1175707de81dd">3.4.1</a>: There is no best, except for a certain set of values and priorities, from a limited set of options.</h3>
<h2 id=9b893b40e08934229116cacf12764a11><a href="#9b893b40e08934229116cacf12764a11">3.5</a>: Understanding Engineering:  Environment -> Resources -> Goal -> Actions -> Changed Environment -> Desired Effects?  Efficient use of resources?  Management of environment?</h2>
<h3 id=dd4d43fb90d90e89b351e98d3788a97c><a href="#dd4d43fb90d90e89b351e98d3788a97c">3.5.1</a>: The use of resources (overall time, people time, money, hardware, etc) to create desired effects, for a given environment.</h3>
<p id=9ed589a4467b296c2ea9dbb09ae0f49d><b><a href="#9ed589a4467b296c2ea9dbb09ae0f49d">3.5.1.1</a>: Evaluate the environment.  Know the present.  Real vs. virtual/logical.</b></p>
<p id=6f4678a0c1cc447ce97cf330abb63e6d><b><a href="#6f4678a0c1cc447ce97cf330abb63e6d">3.5.1.2</a>: Modeling.  Creating models to understand.  Creating models to control.  Not the same.</b></p>
<p id=1e2f1485f11d72e7cc37ce72c7de6775><b><a href="#1e2f1485f11d72e7cc37ce72c7de6775">3.5.1.2.1</a>: Black boxing the world.  Pragmatism and effect driven models.  Input, Output, Side-Effects.</b></p>
<p id=86a667264372ca24826a809f97ed36b8><b><a href="#86a667264372ca24826a809f97ed36b8">3.5.1.3</a>: Algorithms: Idempotency, Sequence,</b></p>
<p id=c5cff688b2a25a6cc5ab3c0301d86a54><b><a href="#c5cff688b2a25a6cc5ab3c0301d86a54">3.5.1.4</a>: Centralized vs. Decentralized.  Push vs Pull, when is it centralized?  Do you want tight control, or loose control?  Both have their effects.  People typically want tight control, or the effects of tight control (knowledge that it worked).</b></p>
<p id=5fa11c75ac5e5ee842071b89611bd9ac><b><a href="#5fa11c75ac5e5ee842071b89611bd9ac">3.5.1.5</a>: Distribute Systems.  Many node problems.</b></p>
<p id=1a38d9aa40613994ccbc55d3bd80aac3><b><a href="#1a38d9aa40613994ccbc55d3bd80aac3">3.5.1.6</a>: Distributed Data.  Where is the good data?  Where is the active data?  Are they the same?</b></p>
<p id=4f692dac9d4a18060c7ed7ab3c560bea><b><a href="#4f692dac9d4a18060c7ed7ab3c560bea">3.5.1.7</a>: Utility vs. Cloud vs. Old-School:  On Demand vs. Full Anonymous vs One-Off.</b></p>
<p id=cd0b3e19dbeb9aa7495f50e8b3698932><b><a href="#cd0b3e19dbeb9aa7495f50e8b3698932">3.5.1.7.1</a>: Named servers (1-1), position and datacenter are known.  Utilty is anonymous server, not anonymous location, position unknown, location known.  Cloud is anonymous name and location.  You dont care what server in a DC it is, or what DC it is in.</b></p>
<p id=cc126bbb155f6cf8bd48d01908206040><b><a href="#cc126bbb155f6cf8bd48d01908206040">3.5.1.7.1.1</a>: What do you have to care about?  The exact machine?  The DC in general?  Nothing, only that the service is reachable, and it can be reachable from anywhere?</b></p>
<h2 id=b897d8c3f141f288841664b42ade8068><a href="#b897d8c3f141f288841664b42ade8068">3.6</a>: Code management.  How to canary.  How to test.  Vagrant and virtual testing.</h2>
<h2 id=44e191e4a8799ec4d8239c53a915b728><a href="#44e191e4a8799ec4d8239c53a915b728">3.7</a>: Perfect is the enemy of done.  Worse is better.  How much safety can you afford?</h2>
<h3 id=d98cb46eb6a0d64a68131fa80be27a81><a href="#d98cb46eb6a0d64a68131fa80be27a81">3.7.1</a>: Quality is never #1, utility is.  Once it's "good enough", it is abandoned for higher priority things.</h3>
<h2 id=53ee284612b4d4678a26814fc2442067><a href="#53ee284612b4d4678a26814fc2442067">3.8</a>: Troubleshooting.  Cencentric circles.  Locality.  Intermittent vs. sustained.  The attributes of failures.</h2>
<h3 id=222b0da1a677c8319df0b5742703e46f><a href="#222b0da1a677c8319df0b5742703e46f">3.8.1</a>: Determines monitoring.</h3>
<h3 id=5e9a4e088d8a4899a4a8579fec56b098><a href="#5e9a4e088d8a4899a4a8579fec56b098">3.8.2</a>: This can be represented in a spectrum.  Ops  <---->  Application.    Backend  <--->  Front End</h3>
<p id=2cda0e85947b37088449bf5d24291155><b><a href="#2cda0e85947b37088449bf5d24291155">3.8.2.1</a>: HTML pages are very front end, web servers are less front end, DBs are less front end more back end, and OpsDB is most backend.</b></p>
<h2 id=ac39699dc841781b49de6156b7d47f07><a href="#ac39699dc841781b49de6156b7d47f07">3.9</a>: Explain the skill ladders.  Infinitely many ladder, infinity tall ladders.  In each area you need to advance and learn, and as you do more ladders are climbed</h2>
<h3 id=8c334623a47643e18e33479feebf5bed><a href="#8c334623a47643e18e33479feebf5bed">3.9.1</a>: Show it like a Graph:  mwMmwnUvMMm, ups and downs in different areas.  How to test yourself, understanding your skills.  Completition of projects as proof of skill, etc.</h3>
<h3 id=5e25a809a807106b545adb208a4fa99d><a href="#5e25a809a807106b545adb208a4fa99d">3.9.2</a>: Know that no one else can know your ladder positions, though they can attempt to estimate, and people are always trying to determine pecking order between themselves and other people, and often to change the pecking order by politics and power.</h3>
<h2 id=291d5132845ea58ade7ea580866bf0f6><a href="#291d5132845ea58ade7ea580866bf0f6">3.10</a>: When to use statistics.  When they are applicable, when they are not.</h2>
<br>
<br>
<br>
When I started this book I made some statistical counters, which are sections, words and lines written.<br>
<br>
I estimated from about 280 sections off of my first 10 sections written, that I would have about 208,000 words at the end of the book.<br>
<br>
I have been checking my percentage complete, such as currently:<br>
<br>
"""<br>
 Total Sections: 301 Populated Sections: 54 Current Goal: Populate Empty Sections: 247 (Done: 17.9%)<br>
<br>
Lines: 2197<br>
<br>
Words: 37668<br>
"""<br>
<br>
And the sections and word percentages to completion have almost kept perfect alignment the entire time I have been writing this work.<br>
<br>
Yesterday was:<br>
<br>
>>> 33000 / 200000.<br>
0.165<br>
<br>
And today (with the above quote):<br>
<br>
>>> 37600 / 200000.<br>
0.188<br>
<br>
18.8% word vs 17.9% sections, in terms of estimated complete.<br>
<br>
Additionally I have been adding sections and removing them as I see fit.  Im not trying to match this data up, and Im not trying to count words in my sections, I just write what seems to fill the topic section, and move on.<br>
<br>
And yet the percentage complete to my initial rough-calculation of 208,000 words, remaining in-line with the number of sections I have.  I will do an analysis on this from my Github entries, since all of this is in version control once the book is done.<br>
<br>
This is a topic that apparently works very well with statistical analysis, and the results are "amazingly accurate" as a study of the population of words and sections I write over time.<br>
<br>
Apparently there is some kind of statistical slant I have to writing a certain number of words a day, a certain number of sections a day, and so on.<br>
<h3 id=18ddda391b891bf36f9b2387380f5e67><a href="#18ddda391b891bf36f9b2387380f5e67">3.10.1</a>: Across many things: appliable</h3>
<h3 id=967dc75f17be743f5b44485436fceff2><a href="#967dc75f17be743f5b44485436fceff2">3.10.2</a>: For a given thing: not applicable.</h3>
<h3 id=feb605a9dd85dcc6e0d371d023dea881><a href="#feb605a9dd85dcc6e0d371d023dea881">3.10.3</a>: Give mental exercises to prove this.</h3>
<h2 id=2d543cb2a0bfd85b80eacbcb10cf77b2><a href="#2d543cb2a0bfd85b80eacbcb10cf77b2">3.11</a>: How to select:  Frameworks, Libs, Software Tools</h2>
<h3 id=17c8887cbd04084bc3b75f577132b78e><a href="#17c8887cbd04084bc3b75f577132b78e">3.11.1</a>: Many stand alone tools will end up being replaced.</h3>
<p id=9362cba32d5a5c9dd234aecef27564d4><b><a href="#9362cba32d5a5c9dd234aecef27564d4">3.11.1.1</a>: Text and data and the purpose of the tools.</b></p>
<p id=e122b3c42185ad60077b1cc58c7f1f22><b><a href="#e122b3c42185ad60077b1cc58c7f1f22">3.11.1.2</a>: Explain DNS, DHCP, etc replacement</b></p>
<p id=957ddd798c6271497229ea774b39e478><b><a href="#957ddd798c6271497229ea774b39e478">3.11.1.2.1</a>: zones, subnets, etc</b></p>
<h2 id=27893ca25e6be2dd440c59fcc7aa321e><a href="#27893ca25e6be2dd440c59fcc7aa321e">3.12</a>: Name spaces.  Different kinds, diff uses, diff formats.  One of the 2 hard problems (+ off by 1)</h2>

# Chapter 4: Automation Philosophy and Methodology in Operations






<h2 id=92fb73bc7b038ce1ccda5ff2fbfdbd56><a href="#92fb73bc7b038ce1ccda5ff2fbfdbd56">4.1</a>: ***** Removing classes of work.</h2>
<h3 id=b7ed43cb9d71411713c556599a83a068><a href="#b7ed43cb9d71411713c556599a83a068">4.1.1</a>: Manual automation is a force multiplier.  Mistakes are also multipled.  Unintended consequences can be severe and wide-spread.</h3>
<h3 id=6715d22e2b900a354a2308f0a78af63e><a href="#6715d22e2b900a354a2308f0a78af63e">4.1.2</a>: Making people do more complicated and dangerous activtiies should not be an end-goal of automation, though it will likely be an intermediary step.</h3>
<p id=5530d1c5607e5f60f382ea9e52ce84d2><b><a href="#5530d1c5607e5f60f382ea9e52ce84d2">4.1.2.1</a>: Step with caution.</b></p>
<h2 id=80ef8721e561c4cedf7d5e7c71ded573><a href="#80ef8721e561c4cedf7d5e7c71ded573">4.2</a>: Introduce spectrum of automatability.  How automateable is something in configure X vs Y?  This is automatability.</h2>
<h2 id=24e3b555ee6f249c33c40b79fce7e744><a href="#24e3b555ee6f249c33c40b79fce7e744">4.3</a>: Working with N axis data for evaluation of properties.  Properties are scalar, but there are many dimensions to measure, and collectively they are near-infinite.</h2>
<h3 id=5b9d7b060f1397403be31640db9326c5><a href="#5b9d7b060f1397403be31640db9326c5">4.3.1</a>: Tuning your goals based on your methods.</h3>
<h3 id=45ba9f44240bd3d8eb4785969cda5301><a href="#45ba9f44240bd3d8eb4785969cda5301">4.3.2</a>: How to create your own Axioms.  Some standard axioms.  Axiomatic development.</h3>
<h3 id=ee01dd35dc1f46d2db9f2bb0383055da><a href="#ee01dd35dc1f46d2db9f2bb0383055da">4.3.3</a>: Tools to fit the job.  Testing in an operational environment.  Mock-tests, etc in a world of only side effects.  Using Vagrant and VMs to test allows these side-effects to be tested, but take time to set up.  Worth it, but you may not start there in a live environment because of all the legacy that would have to be replicated and is changing all the time in non-standard ways.</h3>
<h3 id=2694eafa373f1024fd47adf1fc0878be><a href="#2694eafa373f1024fd47adf1fc0878be">4.3.4</a>: How to standardize things.  Simplification.  The benefits and limitations.  Simpler means less options at any given time.  1-1 work is infinite precision and difficult to scale.  Simpler is can be deep precision in 1 or several ways, but does not allow all options.  Build your option matrix out of what you need, ensure all your use cases are covered.</h3>
<h2 id=024280ac08d372e795de22ac03f8aec5><a href="#024280ac08d372e795de22ac03f8aec5">4.4</a>: All processes can be automated to get a desired effect, if enough information about it is known.</h2>
<h2 id=a562892f336213a7fd2005780a71e6b4><a href="#a562892f336213a7fd2005780a71e6b4">4.5</a>: Introduce Intelligence.  Actionable Intelligence.</h2>
<h2 id=3c09a1e29d529b0e7e64d4c2cf6e026f><a href="#3c09a1e29d529b0e7e64d4c2cf6e026f">4.6</a>: Automating anything</h2>
<h2 id=18279c1b25b35838b531d26379bf8feb><a href="#18279c1b25b35838b531d26379bf8feb">4.7</a>: Total elimination of manual work.  How to remove classes of work from being necessary.</h2>
<h2 id=5ddef01855119bd34e5ea45dc320de43><a href="#5ddef01855119bd34e5ea45dc320de43">4.8</a>: Building the data and action chains, to create all workflow.</h2>
<h2 id=bab4fcb00ea2749653c2a43573413ce6><a href="#bab4fcb00ea2749653c2a43573413ce6">4.9</a>: The data requirements:  Authentication, Authorization, Versioning, Change Management, Deployment, Pre-Post Deployment Actions, Schema Management</h2>
<h2 id=08a271c1b1d52b0b22293cc0aa24981f><a href="#08a271c1b1d52b0b22293cc0aa24981f">4.10</a>: How to construct an unbreakable process.  How to stop that process from being completed/sealed, so that it breaks.  How to ensure it breaks all the time, by setting conditions accordingly.</h2>
<h3 id=0667659ec138ba985e276e32c2c874a5><a href="#0667659ec138ba985e276e32c2c874a5">4.10.1</a>: Faux-automation.  Manual automation.  Automation-assist.  Full-automation.  Comprehensive Life-Cycle automation.</h3>
<h3 id=cc4e2b2b382a5b8203afd5f7c286d1e7><a href="#cc4e2b2b382a5b8203afd5f7c286d1e7">4.10.2</a>: This can be started as Procedure for Humans, but it will not be unbreakable, as people will make mistakes entering data (running commands is entering data)</h3>
<p id=4952dddaa19b91207fda5e21b66cb544><b><a href="#4952dddaa19b91207fda5e21b66cb544">4.10.2.1</a>: Entered on the right system?  Right command?  Right args?  Right path?  Right data?  Right goal?  Right everything?</b></p>
<h2 id=55fc6a2fc3929e32f3e6aa8c650e52c3><a href="#55fc6a2fc3929e32f3e6aa8c650e52c3">4.11</a>: Flexibility and dangers of an automation system.</h2>
<h2 id=9d7a7dfb8deeb7338094c604cb4d6853><a href="#9d7a7dfb8deeb7338094c604cb4d6853">4.12</a>: Distributed OS.  DOS.  N units, all being controlled, configured and scheduling work.</h2>
<h3 id=10b09a38df50bfa7e5a5c390d4cfffad><a href="#10b09a38df50bfa7e5a5c390d4cfffad">4.12.1</a>: Does not need a "traditional" cluster scheduler.  Can use these these for "cron" type jobs though.</h3>
<h2 id=9fbbf8329fb60dc10037a5af19f31002><a href="#9fbbf8329fb60dc10037a5af19f31002">4.13</a>: Monitoring is the heart of automation.  You cant control what you dont have info on.</h2>
<h3 id=e52665a326340a943354050c831ed263><a href="#e52665a326340a943354050c831ed263">4.13.1</a>: Instelligence:  Actionable?  Timely?  Relevant?  Correct?  (Cross check it, all must align)</h3>
<h2 id=8ffdb0c910c1a74549d0d30d43ee3420><a href="#8ffdb0c910c1a74549d0d30d43ee3420">4.14</a>: Behavioral AI.  An expert system, build by experts in Ops and Biz goals.</h2>
<h3 id=3fa9092174f6aa792fa739418160f025><a href="#3fa9092174f6aa792fa739418160f025">4.14.1</a>: Do not use fuzzy info until you have exhausted discrete/precise info.  And turn the fuzzy info into a discrete/precise data point, so it can be acted on cleanly by logic.</h3>
<h3 id=102b1d39363d43827086af170dbc6c22><a href="#102b1d39363d43827086af170dbc6c22">4.14.2</a>: N of M failures is not fuzzy, even though it has a scalar value, and not boolean.</h3>
<h2 id=ab57d26b3045a6b20cffdd14faba910c><a href="#ab57d26b3045a6b20cffdd14faba910c">4.15</a>: 3 States:  Now, Desired, Current State (Whats Out there?)</h2>
<h3 id=734e804607130b865c31b46d6cfbafb8><a href="#734e804607130b865c31b46d6cfbafb8">4.15.1</a>: How to manage.  Importing, synthesizing, checking.</h3>
<h3 id=2c53820f8696b9c71bf7779bf141f713><a href="#2c53820f8696b9c71bf7779bf141f713">4.15.2</a>: Versioning, commits, pre/post-commit logic.</h3>
<h2 id=c8d4ceee72c4e9bec9a140aab31af0a7><a href="#c8d4ceee72c4e9bec9a140aab31af0a7">4.16</a>: Agent model.  Centralized model.</h2>
<h2 id=8df33f2e3ab42652f8dbc974a55ade69><a href="#8df33f2e3ab42652f8dbc974a55ade69">4.17</a>: Library model.  RPC model.  Framework model.</h2>
<h2 id=8f3dc2bb1b918f96ed62f145545bf67d><a href="#8f3dc2bb1b918f96ed62f145545bf67d">4.18</a>: ORM vs wrapping lib vs straight SQL/data query.</h2>
<h2 id=a287441fde41b224c7f9d96589d445b0><a href="#a287441fde41b224c7f9d96589d445b0">4.19</a>: Scales,  1000s/millions, not billions.  Can make this "configuration scale" not "production deployment end-user scale".  Optimize only when necessary, use tools that do heavy lifting for Time series data analysis, and import results and last N snippets into OpsDB.</h2>
<h2 id=e75b67627fcd0302ecae6162320e7b36><a href="#e75b67627fcd0302ecae6162320e7b36">4.20</a>: Selective Data Updating for Pyramid method and Mesh method.</h2>
<h2 id=8e5a823181660693663ac9171ea437f7><a href="#8e5a823181660693663ac9171ea437f7">4.21</a>: Compare Pyramid vs Mesh (p2p).  Pros and cons.</h2>
<h2 id=52c5a2714542df457a2f43133a312847><a href="#52c5a2714542df457a2f43133a312847">4.22</a>: Introduce the dotted notation as a universal naming convention, for lookups, it can universally address any type of DAG data:   domain.sub.thing.11.field.subfield.11.arrayfield.20.subsubfield</h2>
<h3 id=9d4135ad596f06c4521954e1f4b1e02f><a href="#9d4135ad596f06c4521954e1f4b1e02f">4.22.1</a>: **** Use this DAG lookup to go into YAML, DBs, etc.  Schema Man can allow this.  Can use sub-searches like globs (domain.thing.*.field) and translate that into SQL or whatever for more advanced usage.</h3>

# Chapter 5: Components of Operational Environments






<h2 id=e0456dfc4344813c454b2832f721d7cc><a href="#e0456dfc4344813c454b2832f721d7cc">5.1</a>: Troubleshooting</h2>

# Chapter 6: Components of Automation Environments






<h2 id=a26d014573a051d21bf35b17d0eda041><a href="#a26d014573a051d21bf35b17d0eda041">6.1</a>: The process of building this system in your organization.</h2>
<h3 id=87e63ce8f2071f53f8805c0cd6fc706e><a href="#87e63ce8f2071f53f8805c0cd6fc706e">6.1.1</a>: Collect all unique data in one place.  Ensure it is accurate by checking against reality, and combing through it manually to see if things line up, spot checking and automation checking every one by script.</h3>
<h3 id=f36abc40f33f81d73b6b8fd94bc37ff3><a href="#f36abc40f33f81d73b6b8fd94bc37ff3">6.1.2</a>: Things that are unique to you, vs things that are general to everyone.</h3>
<p id=0623d9b6199fbeb9e183439df55431b9><b><a href="#0623d9b6199fbeb9e183439df55431b9">6.1.2.1</a>: FQDNs, IPs, HW specs, OS specs, configuration variables, specific workflow and stuff.</b></p>
<h2 id=7007cad30eb5ca34743dbc74ecb214d6><a href="#7007cad30eb5ca34743dbc74ecb214d6">6.2</a>: Imaging vs re-building from scratch</h2>
<h3 id=5016b7b3143e119640e94393d4b76590><a href="#5016b7b3143e119640e94393d4b76590">6.2.1</a>: Correctness, up-to-date, vs speed.</h3>
<h2 id=206e9c61bb5ef53bbded00a8c8964b9e><a href="#206e9c61bb5ef53bbded00a8c8964b9e">6.3</a>: *** The Progression of an Automation System:  Walk through all the stages **</h2>
<h3 id=6dab388a16ed3d77edcd61d24e22f562><a href="#6dab388a16ed3d77edcd61d24e22f562">6.3.1</a>: These shouldnt be an order so much, as people can take different routes.   How to evaluate each of these spectrums/axis of data, scalars, would be good.</h3>
<h3 id=d7b7edd2b384d2fb2aa8ae8da1767599><a href="#d7b7edd2b384d2fb2aa8ae8da1767599">6.3.2</a>: Manual everything</h3>
<h3 id=1451f4580715a78839eb3ada548626a9><a href="#1451f4580715a78839eb3ada548626a9">6.3.3</a>: Kickstarts and auto config  (AWS gets you here)</h3>
<h3 id=1c20fb798339d70263c0b78365f27f78><a href="#1c20fb798339d70263c0b78365f27f78">6.3.4</a>: Sys configuration tools, Monitoring, Centralized Logging, etc.  Normal sys admin process.</h3>
<h3 id=8744736462545259d69fc1e0eacdc78a><a href="#8744736462545259d69fc1e0eacdc78a">6.3.5</a>: Issue tracking systems, change management ticket systems.</h3>
<p id=611430f5641a791eec9fda109deaecde><b><a href="#611430f5641a791eec9fda109deaecde">6.3.5.1</a>: Good to have different CMS for tickets, because your ops logic will change, but its more useful to track the CMS data right in the ops db for a real record of things, because it lists the complete workloads.</b></p>
<h3 id=1fc55849153c719e757bb6cba8124d73><a href="#1fc55849153c719e757bb6cba8124d73">6.3.6</a>: Databases for assets, inventory, etc</h3>
<h2 id=4f78d48397b0d75399cddbac6661aa4f><a href="#4f78d48397b0d75399cddbac6661aa4f">6.4</a>: * The more sources of authoritative data, the more data drift and non-alignment between the data (fields tracking similar but non-matching things, naming differences, not able to point to same primary keys, etc)</h2>
<h2 id=c60e4b0680418499aa5840cafca907a5><a href="#c60e4b0680418499aa5840cafca907a5">6.5</a>: Data survives longer than code/logic, business logic stays all the time, but the assets described in the DB remain the same, even if they are used differently, and different meta-data is stored about them.</h2>

# Chapter 7: The OpsDB






<h2 id=64bbdc8ed0e1e42739b42a4fc419e08e><a href="#64bbdc8ed0e1e42739b42a4fc419e08e">7.1</a>: What is it?</h2>
<h3 id=6d85b906bd9d454887125ebb31840c17><a href="#6d85b906bd9d454887125ebb31840c17">7.1.1</a>: Your OpsDB is the desires and actionable knowledge of your company.  Everything inside it can be acted upon, it is better global information than any single person can have, so it is the best communication mechanism for a system that has multiple people with their own information (all companies over 1 employee).  Synchronizes information, makes transactional.</h3>
<h3 id=f9918b64d4f419d98d2f8342088bea27><a href="#f9918b64d4f419d98d2f8342088bea27">7.1.2</a>: Setting realistic expectations for this project will be one of your biggest challenges.  Once the premise is understood, it is difficult to stop "magical" thinking about the project, as the intention is to solve all solvable problems, people see it as a magic machine.</h3>
<h3 id=3140a4b8520344ef6af72c4b6709e379><a href="#3140a4b8520344ef6af72c4b6709e379">7.1.3</a>: It is a system or "machine" that can be used to solve all problems, in that it is a centralized database and method for acting against that data.  That is immediately a universal set of tools, because every piece of software is data with a method for acting against it.</h3>
<h2 id=febf95c8835573c89a43474f25043f21><a href="#febf95c8835573c89a43474f25043f21">7.2</a>: Data Driven Design:  My methodology.  Start with the data, work from there.  Testing against data is key.</h2>
<h3 id=addcf00c3304307ee3ec5717fab5c768><a href="#addcf00c3304307ee3ec5717fab5c768">7.2.1</a>: Separate data changing logic from non-data changing logic.  This is like the Model/Controller separation, but is different because it is about any type of action, not just GUI-like actions.</h3>
<h3 id=63ca29ecfdbd33f8b82529d48bf7e2f6><a href="#63ca29ecfdbd33f8b82529d48bf7e2f6">7.2.2</a>: Work systems.  Distributed Job schedulers.</h3>
<h3 id=b9188413cc8c6606506e014873b6b930><a href="#b9188413cc8c6606506e014873b6b930">7.2.3</a>: Collection of data:  Events (logs/etc), Time Series, Config State (md5sum, etc), Active/Live State (up/down)</h3>
<h3 id=727550ddb6653e016e1496f196e288ac><a href="#727550ddb6653e016e1496f196e288ac">7.2.4</a>: Data Driven Development.  My methodology.</h3>
<p id=c2f8690440b17c7c50567db20222ffe1><b><a href="#c2f8690440b17c7c50567db20222ffe1">7.2.4.1</a>: Start with data.  Fo over all features as represented in data.</b></p>
<h2 id=f233ed09310a458264d313be344b885a><a href="#f233ed09310a458264d313be344b885a">7.3</a>: The Data (base)</h2>
<h3 id=b81585e0fda170c7250649704866ac0a><a href="#b81585e0fda170c7250649704866ac0a">7.3.1</a>: Modeling off of reality.  Logical ideas change all the time, business decisions and directions change all the time, staff changes regularly, reality will hold true, but it's perceived differently by everyone.  Still trying to map to reality gives the most common information to the most people who will work with it, and a common method of communication, and is therefore better than not.</h3>
<h2 id=eb0781821183170b505cc3d53ed8f810><a href="#eb0781821183170b505cc3d53ed8f810">7.4</a>: Naming conventions.  Set them and try to abide by them consistently.  This will determine how frequently things must be looked up to be used, for someone familiar with the sytem.  Python vs PHP.</h2>
<h2 id=88eefb88d8bdddb29a06e49470b741b5><a href="#88eefb88d8bdddb29a06e49470b741b5">7.5</a>: My rules:  No plurals in data (code is ok), strict lookup methods, limit methods of relationality.  DAG lookups, with normalized relations in data (not-DAG, has cycles, data doesnt have a direction when there are cycles, the search could start anywhere).</h2>
<h2 id=580a184d5471cd2ae0aa2951fafffcee><a href="#580a184d5471cd2ae0aa2951fafffcee">7.6</a>: What tools you will need to manage this data.   Problems with ORM, problems with non-ORMs.  The tools chosen will determine the level of automatability.</h2>
<h2 id=af2c0408d1a232656d0845019e4790ef><a href="#af2c0408d1a232656d0845019e4790ef">7.7</a>: Building the logic system.</h2>
<h3 id=c587a72562db2e142ed7bce6ba82c2fb><a href="#c587a72562db2e142ed7bce6ba82c2fb">7.7.1</a>: Ensuring uniqueness of elements that require guarantees.</h3>
<h3 id=d02f1a4ff1c843265bfaa4d20accf4d0><a href="#d02f1a4ff1c843265bfaa4d20accf4d0">7.7.2</a>: Infrastructure.  Pre-Services.</h3>
<h3 id=37233edbc6bbf446d6353f066766b5d4><a href="#37233edbc6bbf446d6353f066766b5d4">7.7.3</a>: Configuration of Services.</h3>
<h3 id=06bfc3797691d54fdd6e34c13c4e2ec3><a href="#06bfc3797691d54fdd6e34c13c4e2ec3">7.7.4</a>: Monitoring of Services.</h3>
<h3 id=e01a2cff836d04f498744d984298c363><a href="#e01a2cff836d04f498744d984298c363">7.7.5</a>: Life-Cycle Management of services.</h3>
<h2 id=2e7bd70786c580dcfbd4a9115bf0bb8f><a href="#2e7bd70786c580dcfbd4a9115bf0bb8f">7.8</a>: The layers of an automation system:</h2>
<h3 id=63b722744987837de93cab18cb980051><a href="#63b722744987837de93cab18cb980051">7.8.1</a>: Description of environment</h3>
<h3 id=cd394f4051b52bbe62e5ebb2cd8310ff><a href="#cd394f4051b52bbe62e5ebb2cd8310ff">7.8.2</a>: Provisioning</h3>
<p id=3ccd753ebf4dc31d41da2ddd58d657d6><b><a href="#3ccd753ebf4dc31d41da2ddd58d657d6">7.8.2.1</a>: One-Time configuration</b></p>
<p id=2ea0777930172d51b11974c4b9870340><b><a href="#2ea0777930172d51b11974c4b9870340">7.8.2.2</a>: Continuous Configuration</b></p>
<p id=60fee5b4808b14ad3b519f3642b92ba9><b><a href="#60fee5b4808b14ad3b519f3642b92ba9">7.8.2.3</a>: State management</b></p>
<p id=8959758dbd6b6f3cf8506033ed26a74e><b><a href="#8959758dbd6b6f3cf8506033ed26a74e">7.8.2.4</a>: One-time actions (manual state control of distributed systems)</b></p>
<p id=b7738190443498e5389dd4bb606b3213><b><a href="#b7738190443498e5389dd4bb606b3213">7.8.2.5</a>: Maintenance actions (taking offline)</b></p>
<p id=dc1141d3dbdaed262a31451319e4a0d6><b><a href="#dc1141d3dbdaed262a31451319e4a0d6">7.8.2.6</a>: Marking broken HW, fixing HW, migrating OS positions.</b></p>
<p id=dadcbabed40306c7ac679c0ce0715aca><b><a href="#dadcbabed40306c7ac679c0ce0715aca">7.8.2.7</a>: What stays the same, what changes?  IPs for LOM on HW.  IPs for OSes on virtual.</b></p>
<p id=47628abed8e1db8e9ed815f84bb4d116><b><a href="#47628abed8e1db8e9ed815f84bb4d116">7.8.2.8</a>: Tracking N things.  Primaries vs. position.  Ordered lists are the best?</b></p>
<h2 id=c5e3fc0965c2fdd764070ce7089ab03e><a href="#c5e3fc0965c2fdd764070ce7089ab03e">7.9</a>: How to "translate" data changes, making many changes at once, like matrix multiplication.  Changing from Puppet to Salt, etc.</h2>
<h2 id=1431f5a1f11b9fb451cc24ff2fee85c5><a href="#1431f5a1f11b9fb451cc24ff2fee85c5">7.10</a>: How to Build your own OpsDB.  What you need:</h2>
<h3 id=9853534dc81b1e9e41d72d4363f0a542><a href="#9853534dc81b1e9e41d72d4363f0a542">7.10.1</a>: View (Webpage, API)</h3>
<h3 id=276746c8ba1e2809eb7df2308d002381><a href="#276746c8ba1e2809eb7df2308d002381">7.10.2</a>: DB Backend</h3>
<p id=ff326af388f41f4924ffad21eb1dfed3><b><a href="#ff326af388f41f4924ffad21eb1dfed3">7.10.2.1</a>: Method for safely making changes to data</b></p>
<p id=036106589f472c34b5d06d007dea3f2b><b><a href="#036106589f472c34b5d06d007dea3f2b">7.10.2.1.1</a>: Versioning, Change Management</b></p>
<p id=1cdc99a3dfdde59fb854db0175cb63c4><b><a href="#1cdc99a3dfdde59fb854db0175cb63c4">7.10.2.1.1.1</a>: Roll backs</b></p>
<p id=c49dd8f1c6c2c694c834e61f716fb0fa><b><a href="#c49dd8f1c6c2c694c834e61f716fb0fa">7.10.2.1.1.2</a>: Pre-Post Commits</b></p>
<p id=0e83ef919a005decfa42731ac7f54b07><b><a href="#0e83ef919a005decfa42731ac7f54b07">7.10.2.1.1.3</a>: Locking, to stop problematic race conditions</b></p>
<p id=019b9ff6745a81e4c068d893c7f13852><b><a href="#019b9ff6745a81e4c068d893c7f13852">7.10.2.1.1.3.1</a>: Channeled locking, to limit domains of locks</b></p>
<p id=80bc1f096de2420328753be58a57dceb><b><a href="#80bc1f096de2420328753be58a57dceb">7.10.2.1.1.3.1.1</a>: Size of domain, and rate of change and lock duration determine requirements</b></p>
<p id=5d14c394196a168616acd71cd98b3e1d><b><a href="#5d14c394196a168616acd71cd98b3e1d">7.10.2.1.2</a>: Single choke point for DB changes</b></p>
<p id=b0cb8e8e7ef02730d62e746be34c4735><b><a href="#b0cb8e8e7ef02730d62e746be34c4735">7.10.2.1.2.1</a>: Web/API all use the same code, so different paths give different results.</b></p>
<p id=f17e11f935b8c1a4aa11102e9f73223e><b><a href="#f17e11f935b8c1a4aa11102e9f73223e">7.10.2.1.2.2</a>: Role users (scripts) can auto-commit changes, but should go through same process, because needed for auditing, troubleshooting, and maintaining integrity and pre/post-commit logic</b></p>
<h3 id=540cf17fe6e0e04bd037e55d7ce2f5ce><a href="#540cf17fe6e0e04bd037e55d7ce2f5ce">7.10.3</a>: Pull method, to gather data.  Time Series, Logs, State/Configs, Events, etc</h3>
<p id=c4337517e5ddb7098a69ab9ea06a54fe><b><a href="#c4337517e5ddb7098a69ab9ea06a54fe">7.10.3.1</a>: Creates Global Authority DB</b></p>
<p id=a12e034abf7648e012dba8f6624f26f3><b><a href="#a12e034abf7648e012dba8f6624f26f3">7.10.3.1.1</a>: Can be distributed, if sync. is strong</b></p>
<p id=462d69372dfef02a563fa6444c55cd24><b><a href="#462d69372dfef02a563fa6444c55cd24">7.10.3.1.1.1</a>: Need Transactions on all pieces of total DB, so that things are changed in block fastion, all this way, then all that way.  Keeping alignment.  (Like a shot in Pool, game.  Stick and balls must line up to make it into the pocket.)</b></p>
<p id=277518558b3f7c13c97da337398a3239><b><a href="#277518558b3f7c13c97da337398a3239">7.10.3.1.1.2</a>: Will come later in the process, in the "How to implement" section</b></p>
<p id=dc439f9efa60e2ef3a3b7a76233e90b4><b><a href="#dc439f9efa60e2ef3a3b7a76233e90b4">7.10.3.1.2</a>: Selective Replication.  Will have local and global portions.   Easy to separate instances (2 MySQL instances) so taht there is a Global DB (replicated from Master) and a Local DB, pulled from Local, which replicates to Master.</b></p>
<p id=36da14c0258aed53bb129e50b7540c0b><b><a href="#36da14c0258aed53bb129e50b7540c0b">7.10.3.1.2.1</a>: In this scenario, the Master will need to have N instances, where N is the number of sub-masters, so it can replicate.  Then it will pull and integrate this data into it's own global system, and then synthesize.</b></p>
<p id=8a7a7c7b2388bd544de92c5e305fac1b><b><a href="#8a7a7c7b2388bd544de92c5e305fac1b">7.10.3.1.2.1.1</a>: This Global pull-integrate-synthesize is then replicated out everywhere, and is the REAL data that can be acted upon.  It has met all constraints and has a view into everything</b></p>
<p id=acd4663d59d1c72e97ec62dfc8144a85><b><a href="#acd4663d59d1c72e97ec62dfc8144a85">7.10.3.1.2.1.1.1</a>: Some Logic can run off of Local data, because it is locally concerned.  When Logic needs to act on Global data, its obvious it needs to be correct and current global data.  Intelligence.</b></p>
<p id=bed7228195793a630892b855fc99a256><b><a href="#bed7228195793a630892b855fc99a256">7.10.3.1.2.2</a>: Collection is local.  Work from Global.</b></p>
<p id=87f7c87b586607ad6a5f02b42dbc6fd9><b><a href="#87f7c87b586607ad6a5f02b42dbc6fd9">7.10.3.1.2.2.1</a>: How to work on partitioon?</b></p>
<p id=d7f9ae8a09db2ce495f7b9c3de1765c2><b><a href="#d7f9ae8a09db2ce495f7b9c3de1765c2">7.10.3.1.2.2.1.1</a>: Can use local data for N time, until is stale.  Logic can decide how stale the data can be, can have Rules for lag time allowances.</b></p>
<h3 id=a00ef370998cbb3006289af9b995a5b9><a href="#a00ef370998cbb3006289af9b995a5b9">7.10.4</a>: Orchestration.  Remote Execution.  Seall the loop and check.  Post-Provisioning will need to run commands to check that things really worked.  Same as any other type of action. Do the action, get the result, but then go check and make sure it worked.  Check again to see if it failed after some time.  Ensure another action hasnt caused this (acted on the same Resource)</h3>
<h3 id=db268b9d5648f3cf17247aa4466aca44><a href="#db268b9d5648f3cf17247aa4466aca44">7.10.5</a>: Config Management.  Make known changes on a system.  It should be in "X state"</h3>
<h3 id=0a8618fa5985ed1fdc24f110dc27c026><a href="#0a8618fa5985ed1fdc24f110dc27c026">7.10.6</a>: State Management.</h3>
<p id=8b695cbf41a4ec0c65cc346d3f4ec397><b><a href="#8b695cbf41a4ec0c65cc346d3f4ec397">7.10.6.1</a>: OS Level</b></p>
<p id=13c2c758c5deddeef82f376abc18fd9d><b><a href="#13c2c758c5deddeef82f376abc18fd9d">7.10.6.2</a>: Service level (dealing with the execution of services, and proper functionoining of the service)</b></p>
<p id=c4dcd142e927de912d9547bc2fdc0b04><b><a href="#c4dcd142e927de912d9547bc2fdc0b04">7.10.6.3</a>: Running-Service level (dealing with things inside a running service.  This is a user of the service, instead of a controller, but it is an "administrative" type of use)</b></p>
<h3 id=dd58ffaa4ecbdac2411f233050464747><a href="#dd58ffaa4ecbdac2411f233050464747">7.10.7</a>: Work Scheduling</h3>
<p id=a70b03745f8075613c39c401fa6ebb3c><b><a href="#a70b03745f8075613c39c401fa6ebb3c">7.10.7.1</a>: Global cron jobs, etc.</b></p>
<p id=1ba95b39f638a0a938fe583f13451394><b><a href="#1ba95b39f638a0a938fe583f13451394">7.10.7.1.1</a>: In maint?  Is right machine (master/slave/role/etc)?  Dont take down prod.</b></p>
<p id=b0daa3658be541aa293ab0b9ded206da><b><a href="#b0daa3658be541aa293ab0b9ded206da">7.10.7.1.2</a>: Dont ignore failures of jobs.  Keep logs for auditing, so we know what happened, and what it happened for troubleshooting and Root Cause Analysis.</b></p>
<p id=0044ef67424877e39c1ba3c6053e8c31><b><a href="#0044ef67424877e39c1ba3c6053e8c31">7.10.7.1.3</a>: Track times for analysis to determine failures of scale-performance changes</b></p>
<h3 id=fb473bfadfe142c63f22f088a56d5977><a href="#fb473bfadfe142c63f22f088a56d5977">7.10.8</a>: Capacity Planning.  When will you run out of:  Disk? RAM?  CPU? Connections?  etc</h3>
<p id=0c6c6113cb02a2a1ff6e897237e5402b><b><a href="#0c6c6113cb02a2a1ff6e897237e5402b">7.10.8.1</a>: Resources of our services.  Network Loadbalancer has N potential connections, and we can determine that by a MAX check on how much its done, and where it has produced failures after MAX_WORKING values have been breached.  Might not be the LB though, just correlation.</b></p>
<h3 id=a6e21acd13a2849ee9c611451ba8b30a><a href="#a6e21acd13a2849ee9c611451ba8b30a">7.10.9</a>: Access Control.  Authorization to do work.</h3>
<h3 id=e3cba7be54f69ef1b2d51192e0ef633e><a href="#e3cba7be54f69ef1b2d51192e0ef633e">7.10.10</a>: Deployments, as separate from Config</h3>
<p id=f05b48f95386109c5c79cfc128fc44e3><b><a href="#f05b48f95386109c5c79cfc128fc44e3">7.10.10.1</a>: Code deploy</b></p>
<p id=1d1be487a8a4d497425c60ca93d25285><b><a href="#1d1be487a8a4d497425c60ca93d25285">7.10.10.2</a>: Data/Schema deploy</b></p>
<p id=f08b1ca1ab0f2290f2a2c3b8b8b97ffc><b><a href="#f08b1ca1ab0f2290f2a2c3b8b8b97ffc">7.10.10.2.1</a>: When tied together.  Ways to avoid problems, ways to increase problems.</b></p>
<p id=ed24cd5011374fb609ff91ea5d18cc17><b><a href="#ed24cd5011374fb609ff91ea5d18cc17">7.10.10.2.2</a>: Lifetimes, rate of change, etc</b></p>
<p id=88ff2ffdc4b027db0a400a53602c0063><b><a href="#88ff2ffdc4b027db0a400a53602c0063">7.10.10.2.3</a>: Service up/down.  In/out of LB.  (Active)</b></p>
<h3 id=938f106673899a434d955e75ed15a20a><a href="#938f106673899a434d955e75ed15a20a">7.10.11</a>: Network config and planning</h3>
<p id=95c64ed20fa4a1dbb04c67f0aea42b82><b><a href="#95c64ed20fa4a1dbb04c67f0aea42b82">7.10.11.1</a>: VLANs.  Hidden systems, ensure not old IPs (collisions)</b></p>
<p id=19579404710a661869e4eea32f5e1c96><b><a href="#19579404710a661869e4eea32f5e1c96">7.10.11.1.1</a>: Can defer their use until that HW is proven to not use that IP anymore.  Like its in Escrow.  Once really released, it can be re-used.   Nice.</b></p>
<p id=8307c8ed240946f143913fa06d1021f4><b><a href="#8307c8ed240946f143913fa06d1021f4">7.10.11.2</a>: LOM IPs stay with the hardware.  DHCP timeouts, etc.  Server IPs stay with "ServerInstance" (OSInstance)</b></p>
<h3 id=203ffd1d4778494bd7a2556c2a0ac90e><a href="#203ffd1d4778494bd7a2556c2a0ac90e">7.10.12</a>: VM Provisioning.  Hybrid.</h3>
<h3 id=f7ae4f5ab54c3927652049bdcf35e555><a href="#f7ae4f5ab54c3927652049bdcf35e555">7.10.13</a>: Self Service tools.</h3>
<h3 id=276b07fae87391ca794e8587e972cf4e><a href="#276b07fae87391ca794e8587e972cf4e">7.10.14</a>: How to plan to do this in your existing environment.  A map from:  Here -> There.</h3>
<h2 id=dc9b1c51ebd041941929fe8845a2c78e><a href="#dc9b1c51ebd041941929fe8845a2c78e">7.11</a>: States of machines:  Unknown, Unprovisioned/Spare, Provisioned-Inactive, Active, In Maintenance, Transition-To X State, Broken, Fixed (waitig to be Unprovisioned/Spare)</h2>

# Chapter 8: How to Implement the OpsDB in your Current Environment






<h2 id=4e188beb6a9e453253679bb857ac7767><a href="#4e188beb6a9e453253679bb857ac7767">8.1</a>: The OSI layer for getting things done:</h2>
<h3 id=458b9365b935744307dce791d0f73ea6><a href="#458b9365b935744307dce791d0f73ea6">8.1.1</a>: Physical.  Real world things.</h3>
<p id=7543ac663d8be861d64b607357cbc148><b><a href="#7543ac663d8be861d64b607357cbc148">8.1.1.1</a>: People are always required for real world things, because robots arent good enough yet.  Physical must manage physical.</b></p>
<h3 id=a782fd2d1471fc65afd9abcdc78c14ed><a href="#a782fd2d1471fc65afd9abcdc78c14ed">8.1.2</a>: Configuration.  How real world things are configured.</h3>
<p id=719bc5f15fa7d54e8a67977bf0901094><b><a href="#719bc5f15fa7d54e8a67977bf0901094">8.1.2.1</a>: Logical.</b></p>
<h3 id=6331cb83195fd5b2bd738c89abc4ec84><a href="#6331cb83195fd5b2bd738c89abc4ec84">8.1.3</a>: State.  How real world things are managed.</h3>
<p id=719bc5f15fa7d54e8a67977bf0901094><b><a href="#719bc5f15fa7d54e8a67977bf0901094">8.1.3.1</a>: Logical.</b></p>
<h3 id=b53ddf4dc4025191a641f212d24e1be3><a href="#b53ddf4dc4025191a641f212d24e1be3">8.1.4</a>: Automation.  How software can manage configuration and state.</h3>
<p id=32f7e1e930dc786f657dc6a88b1bbde3><b><a href="#32f7e1e930dc786f657dc6a88b1bbde3">8.1.4.1</a>: Automation ends where people begin.  If you have no automation, the people manage the config and state.</b></p>
<p id=95e40183969996603b8e5e3425a932c4><b><a href="#95e40183969996603b8e5e3425a932c4">8.1.4.2</a>: Automation is the control of logical devices and state.  It does not control Physical devices, but does control their state.  (Even in the case of directing a physical robot, the automation updates state, and it takes something physical (motors, servos, cogs) to make the physical thing move.)</b></p>
<h3 id=173c2bec1142197f6757fcb7d4a8dbbf><a href="#173c2bec1142197f6757fcb7d4a8dbbf">8.1.5</a>: Process (and Procedures).  How people work around the lower levels.</h3>
<h3 id=8e203f62002cbf6f27b191f991da6f30><a href="#8e203f62002cbf6f27b191f991da6f30">8.1.6</a>: Policy.  Dictates how processes can be implemented.  Policies may be directly contradicting Process, such as "No one is allowed to X", while a process requires a person to do exactly that.</h3>
<h3 id=7fdcde9fe4218f5aa5a0a40cc5501fbd><a href="#7fdcde9fe4218f5aa5a0a40cc5501fbd">8.1.7</a>: Business...  Business goals</h3>
<h3 id=9fe2a787f3e54166e4252165680a59d2><a href="#9fe2a787f3e54166e4252165680a59d2">8.1.8</a>: Political.  The realities of the business goals, determined by how well people will work together to achieve them.</h3>
<h3 id=3ff1735de8bc414c4f645abe641ad297><a href="#3ff1735de8bc414c4f645abe641ad297">8.1.9</a>: Financial...  Financial reality, approved or not.  Timing.  Delays.</h3>
<h3 id=b982d3de81bba13dd46914991650f426><a href="#b982d3de81bba13dd46914991650f426">8.1.10</a>: Legal...  Hard stop, must change direction if told by legal.</h3>
<h2 id=3f2cc3566a84cad0a234647ab1300021><a href="#3f2cc3566a84cad0a234647ab1300021">8.2</a>: Planning for projects in the real world</h2>
<h3 id=236e9bb833a610161cfbaaba9e6bb6fe><a href="#236e9bb833a610161cfbaaba9e6bb6fe">8.2.1</a>: The end-date comes first.  Whether you have any say in that is only occassionally true, even if you are asked how long it will take.</h3>
<h3 id=cba0d1f4cdd7b395395d6b34e6523e97><a href="#cba0d1f4cdd7b395395d6b34e6523e97">8.2.2</a>: Things will interrupt your work that were not planned for in the time estimates, and this will mean less work gets done</h3>
<h3 id=c7eec3bac3f711b65028b49170529559><a href="#c7eec3bac3f711b65028b49170529559">8.2.3</a>: You will have normal duties to attend to, this will interrupt things getting done</h3>
<h3 id=c2a0b4944f0d52aaec4ba066f1860790><a href="#c2a0b4944f0d52aaec4ba066f1860790">8.2.4</a>: Meetings.  Whether you enjoy them, are ambivalent, or dislike them, they are going to occur and take time.</h3>
<h3 id=05c0e353e04741273d56999b7e33a595><a href="#05c0e353e04741273d56999b7e33a595">8.2.5</a>: Mental-Context-switching cost.  Ramp up time.</h3>
<p id=d14a0f795ad0930b2ab59e40ff6742b4><b><a href="#d14a0f795ad0930b2ab59e40ff6742b4">8.2.5.1</a>: Know what kind of work you are going to start, and pick the best time to do so.  If it needs more ramp-up time, then pick a block where you are less likely to be interrupted.</b></p>
<p id=ca064b32d34547ac269d1b85fa693e6d><b><a href="#ca064b32d34547ac269d1b85fa693e6d">8.2.5.2</a>: Break your open time periods into "units" of 30 minutes or 2 hours or whatever you can have contiguously, and see what you can FINISH in that time.  It is easy to lose days/weeks to getting little changes made, but not moving ahead in terms of usable progress.</b></p>
<p id=ae9af424cff9e20bb4d775d699db9e81><b><a href="#ae9af424cff9e20bb4d775d699db9e81">8.2.5.2.1</a>: When each time block arrives, try to get what you can finish, and hopefully test and put into place, in that 1 session.  This isnt possible for some work, because it's too big, so break that into stages that can fit into one of these time blocks.  A simple method, would be: write it in 1, test it in another, and finally deploy it in the 3rd.</b></p>

# Chapter 9: General Advice






<h2 id=0a605e177cdf62b2e4fd820e73cbecf7><a href="#0a605e177cdf62b2e4fd820e73cbecf7">9.1</a>: Go over code reviews, and config reviews.</h2>
<h3 id=a720022abaff2d1c9e31daf42dc94dee><a href="#a720022abaff2d1c9e31daf42dc94dee">9.1.1</a>: *** Mark this as my personal opinion.  Not as something provable.  This is color. ***</h3>
<h3 id=3519e134dd26a81e963ccf09964c8a88><a href="#3519e134dd26a81e963ccf09964c8a88">9.1.2</a>: Normal pitfalls.  Dont really check, "Yes Stamp".</h3>
<p id=7cfef0cbf3e4fb479b3309647eb17ca6><b><a href="#7cfef0cbf3e4fb479b3309647eb17ca6">9.1.2.1</a>: Too style oriented.  Enforcing a style is important in some areas, but less important in others.  It is better to keep a team cohevsive to know these differences, so that on some things you are strict (variable naming) and on other things you are flexible (commenting style).  People write prose more personally than they name variables, and variables have to be used by many people, whereas the message in a comment in based on the author's mental state when they wrote it, which is very subjective, and people have very different styles.</b></p>
<p id=3caece8edc80e43f05cec661ae0cf2f7><b><a href="#3caece8edc80e43f05cec661ae0cf2f7">9.1.2.1.1</a>: I recommend allowing people to have their own unique style in areas that will not harm the ease-of-use and resiliency/robustness of the Logic, and strictness on naming conventions, and basic formatting (indentation)</b></p>
<p id=8923934b9a6ece208968c72ceb0460c4><b><a href="#8923934b9a6ece208968c72ceb0460c4">9.1.2.1.1.1</a>: Strictness can be kept inside individual projects, with a general theme to a department or company.  These are degrees to each of this which will make actually working with other people nicer, while</b></p>
<h2 id=fa154a30257b81d67d9e7c7114d4c549><a href="#fa154a30257b81d67d9e7c7114d4c549">9.2</a>: Root Cause Analysis write ups.</h2>
<h3 id=57a8fb171628609c4f4a074359da7864><a href="#57a8fb171628609c4f4a074359da7864">9.2.1</a>: How to not bullshit these.  Dont lie.  Dont criticize every failure, because failures WILL happen.  The only way to avoid them is to REMOVE the CLASS OF WORK.</h3>
<h2 id=676e5f44878bdde31c3379f2c69b98ae><a href="#676e5f44878bdde31c3379f2c69b98ae">9.3</a>: Create a set of Checklists.</h2>
<h3 id=508068aefcdc803e5f88092d9cafbbf5><a href="#508068aefcdc803e5f88092d9cafbbf5">9.3.1</a>: Automation Spectrum</h3>
<h3 id=47245b1f66b268d9bf3e915e19d7106e><a href="#47245b1f66b268d9bf3e915e19d7106e">9.3.2</a>: Automation Layers</h3>
<p id=4d89acb0c6cf7d6c14c7c9925ffee864><b><a href="#4d89acb0c6cf7d6c14c7c9925ffee864">9.3.2.1</a>: Sub-Components of layers.  How well are they implemented, 1-5 scale or something</b></p>
<h3 id=10909577585a58647fbb1902112b6ab3><a href="#10909577585a58647fbb1902112b6ab3">9.3.3</a>: Talk about how to make your own checklists and scales.  This is flexible, not dogmatic.  The important part is that we can communicate what we are talking about, in a way where multiple individuals and groups can agree, allowing us to work successfully together.</h3>
<h2 id=0109e0d4643177fefe7ccc3fe1c7a872><a href="#0109e0d4643177fefe7ccc3fe1c7a872">9.4</a>: Self-evaluation?  How to evaluate your actions, how to make plans to improve.</h2>
<h2 id=90ee09235d729b6403260561482812a7><a href="#90ee09235d729b6403260561482812a7">9.5</a>: Introduce the Basic Laws of Human Stupidity.  Not meant as insult or joke, but as quantitative method of determining the intelligence of an action.  This is the model I will use in this book.</h2>
<h2 id=7f0428bc4e8fd20bc8ddd31b00ea1d75><a href="#7f0428bc4e8fd20bc8ddd31b00ea1d75">9.6</a>: Journmanship, apprenticeship.  What we are missing.  Valuing experience.  Im old, of course thats my take.</h2>
<h2 id=5ca3d14cd4988a84227bb91b9f59650b><a href="#5ca3d14cd4988a84227bb91b9f59650b">9.7</a>: The benefits of "vanilla" use of tools.  Less upkeep.  Only change what you strictly need to change.  Spend time optimizing only in critical areas.  Reduce things that need to be manually maintained.</h2>
<h2 id=cc2951537c1aa0cd251fbda6639f2b8f><a href="#cc2951537c1aa0cd251fbda6639f2b8f">9.8</a>: "Lowest Common Denominator" problem</h2>
<br>
In response to: http://euphoricus.blogspot.com/2015/11/everybody-is-doing-tdd-take-two.html<br>
<br>
<br>
<br>
Reduction to this workflow does not mean that this workflow can be understood and implemented with the same results in any manner.<br>
<br>
I call this the "Lowest Common Denominator" problem.  In any given situation, there are some common things that are understood between all parties, and these are the things that can be communicated "clearly".<br>
<br>
These concepts are used to divide up the problem so that they can be solved, hence denominator.  The problem is that in order for the parties to agree, they have to use the simplest methods of communicating that every party can understand, which is where the "common" and "lowest" (simplest) come from.<br>
<br>
The issue here is that there are more efficient ways of doing things, that are not as simple, but not all parties will have equal knowledge of all of these things, presenting a dilemma:  Do you aim for higher efficiency or higher commonality?<br>
<br>
This is something every given team/organization should decide for themselves, because they work on a spectrum.  If you aim for more commonality, you lower the bar on what techniques are common to all parties, and you will lose the benefits that un-commonly-known techniques may provide.<br>
<br>
If you aim for efficiency of techniques, you enter the area where not all parties understand the techniques.  This is also exemplified by the "single person vs. large team" spectrum.  Single people are able to use efficiencies that even a 2-person team cannot, because of the immediate nature of communication inside one's own head.<br>
<br>
As soon as the communication must be externalized, there is a massive loss of efficiency in the communication, and as the team grows the communication problems grow factorially.<br>
<br>
How massive is this loss in terms of efficiency in communication between your own thoughts, and communicating with 1 external person?  {{ stats_memory_cycles_per_second_vs_words_per_minute }}<br>
<br>
To give an example, this is the difference between accessing something already loaded into RAM and Layer 1 Cache, vs accessing something on a 5400 RPM slow rotating spindle disk, on a remote computer, that is networked via satellite, and resides on another planet (Earth -> Mars).  That is the type of inefficiency that is created between going from one's own thoughts, to communicating with 1 other person.<br>
<br>
When communicating with teams or large groups of people, this is made worse, as often the communicate is by proxy, so not only is the communication inter-planetary in terms of efficiency, it is through a lossy-proxy, which will change the data and is more likely to summarize it, dropping out many details and changing the terminology, phrasing, and perhaps even the intent.<br>
<br>
So while your assertion that everything can be broken down into: Create Test, Implement Thing To Be Tested, Verified Test.  <br>
<br>
This does not mean that all different types of processes give the same results merely because of this.<br>
<br>
To give an analogy, I can say that all data in a database could be stored in a single table with 3 fields:<br>
<br>
- Group<br>
- Type<br>
- Value<br>
<br>
All of these fields can be BLOBs, so we only need 1 storage type, and from that all data actions done in any other method can be implemented.<br>
<br>
This is true, but it is not efficient.<br>
<br>
This is a similar spectrum to having "single ownership" vs "team ownership".  They provide different benefits, and cause different problems.  Single ownership allows for the efficiency that a single owner can bring, but at the loss of wider understanding and access.<br>
<br>
Team ownership provides wider understanding and access, but limits the amount of efficiency that can be used due to all members of the team needing to be able to understand all of the implementation well enough to work with it.<br>
<br>
Anything that is not immediately well-understood by any member of the team, in a team-ownership environment, should be converted into a method in which that team member can understand it.  This should be applied to all changes, recursively, so that all details fit this criteria.<br>
<br>
Taken to it's extreme, it is easy to see how this solution will be "dumbed down" (not to be insulting, merely to illustrate the point) to the most common knowledge (low tech vs high tech), and this will have an effect on the efficiency and manageability of the work.<br>
<br>
There is a "tipping point" where this "low-tech" type direction starts to become a problem in itself, either by not performing fast enough, or not being small enough to manage, as size has a direct impact on complexity as well.  More things are harder to manage than less things, just as more complex things are harder to manager than simple things.<br>
<br>
__Exchange__<br>
<br>
Author:  So are you are saying that the workflow is same, but it just differs in implementation? I'm leaving that question out for now. I believe it is possible to separate the questions of workflow and it's implementation. So first think I want to agree on is on which workflow produces best result. After we agree on that, we can talk about it's implementation.<br>
<br>
<br>
Me:<br>
<br>
I completely agree with your interest in coming to agreement on workflow, techniques and terminology.  I think this is important work, and the surface has barely been scratched on it in our industry (even with places like the c2 wiki, which are comically in-depth).  Just wanted to say that.<br>
<br>
I think there are a couple of issues here.<br>
<br>
The first is the matter of deconstructionism.  For every layer of abstraction you remove when deconstructing something, you lose the context and connotations (intentions) of that symbolic abstraction as well.<br>
<br>
So I can further deconstruct your deconstruction into this:<br>
<br>
- Think<br>
- Act<br>
- Evaluate<br>
<br>
Now we have an even simpler model, and we aren't restricting to programming.  The problem is that we also aren't even talking about software development any more, we've gone so general that it has lost it's original purpose, which is to better understand how to do something related to developing software.<br>
<br>
In similar ways, each abstraction layer removed to get to the point of:<br>
<br>
- Create test<br>
- Write code<br>
- Evaluate test<br>
<br>
Has lost the contexts, connotations, and further layers of abstractions that each of the concrete methods that would be used in place of those 3 things, and the many nuanced sub-things that would be required to properly detail those replaces.<br>
<br>
Taken to it's extreme, on that same spectrum, you go from the 3 things I just typed in, to the complete work of code you intended to produce, in it's ideal fully-tested-and-shippable form.<br>
<br>
This is the full-spectrum of analysis:  From complete abstraction to complete concrete implementation.<br>
<br>
So we can tune the discussion to any parameter for both this spectrum, and any related axioms for determining the results of the work that we wish to get through our efforts.<br>
<br>
My point was mostly that we should not lose out on efficiency, if we desire efficiency, because we also desire commonality.  As they have a spectrum between them.  (Almost anything can be put with anything else into a spectrum, like two points making a line segment, so I'm not drawing from any specific examples here, more in idea-space)<br>
<h2 id=822a93e6d35a5d2173bda4a30b16591b><a href="#822a93e6d35a5d2173bda4a30b16591b">9.9</a>: Releasing the poison</h2>
<br>
This is the only non-Operations advice that I will give in this book, because I think it is the most important non-technical advice I can give, and it has to do with inter-human communication and inter-human relationships.<br>
<br>
No matter what society, culture or place you are born in, grow up in, and live in, there are elements around you that are harmful to you, and affect you in a negative manner.<br>
<br>
In dealing with other people, we often encounter negativity in many dimensions, whether it is in attitude, verbally, or physically.<br>
<br>
And in our own actions, we ourselves will have negative attributes that are presented and may affect our co-workers, team mates, as well as ourselves, friends and family.<br>
<br>
A term I have begun to use for this type of thing is "poison", and to use it in a sentence might be something like, "I am poisoned, and have become toxic and it is effecting myself and others".  This reads pretty harshly to me, but it is meant to be clarifying and not vague or down-played.<br>
<br>
I believe that all of us are both our own greatest allies, and our own worst enemies.  Our own actions have more impact on us than any other individual's can have, because we are the ones who coordinate our actions every second of every of day of our lives, whether we are directly aware of the coordination for each action or not.<br>
<br>
In term's of our larger group's influence on us, this is actually more of our own influence on ourselves, as we have interpreted the intention of our larger society, culture or group, and our position in it.  I find conflict between my view of how I think I should fit into my group, versus how I would like to fit into my group.  And the same is true for "how the group thinks about me", to anthropomorphize the "collective dynamic" or "group think" or "social pressure" or "super ego" or whatever.<br>
<br>
But, this is not merely negative, it is also positive, as I take the good things about my culture and group, and I am seen positively by them and myself, and I see the positive ways that I fit into the group, and they do me.<br>
<br>
In order to improve myself, I need to focus more on seeing these positive things, and how others can see me positively, and less on the negative.  My attention alone will create time that I spend reflecting on the negative aspects, where I could be putting effort into actively making things more positive, and spending my time inspecting the positive aspects of things to determine how to strengthen them, and create more of them.<br>
<br>
I refer to this, internally (and now written into a book, I guess), as "releasing the poison", which is releasing the things inside me that make me "more toxic", so that I can be "less toxic", with the goal of being "not toxic".<br>
<br>
I say "releasing" instead of some other term, because these are active patterns in myself, things that I do, that I didn't have to do, but did.  So these are habits or reflexes which need to be changed, but in order to do something else, I must stop doing what I am already doing.  So I refer to this as "releasing" it, as it is something I am "holding on to", which is why I keep doing it.  I think this distinction is important, as it underlines how this is completely an internal process, that I can accomplish myself, with no external validation.  <br>
<br>
Why is it important that I can continue to make progress without external validation?  It is important, because if people act in negative ways to me or around me, I do not need to respond with negativity or spend time dwelling on the negativity.  <br>
<br>
Acting with negativity creates a feedback loop, where one party is negative to another party, and the other responds with negativity (understandable, even if they were neutral or positive prior to the introduced negativity), and the first continues to respond negative and may increase it, and so on.<br>
<br>
Because this feedback loop only intensifies until one of the party "turns down the volume", or turns it off, then it becomes clear why so many problems exist between people. <br>
<br>
I am certainly not through with my journey on this path, but I feel continual improvement as I have created an internal process of inspecting things that occur in my life, and comparing them to the model I have created for how I spend time related to negativity, versus how I spend time related to positivity.<br>
<br>
This allows me to see where I have made mistakes more easily, and gives me the incentive to take action to try to correct those mistakes.  Often simply not taking action to correct a negative-effect action creates even more problems down the road which requires much work or may be unsalvageable, where taking a smaller effort earlier on, after detecting the problem, leads to less problems in the future and a more positive outcome and duration.<br>
<br>
If I have said or done something that may have caused a problem for someone, in any way, I can realize this and then mention it to them in passing, or ask to talk with them and go over what happened, and how I would prefer things were resolved, trying to fix any problems that were created, and create and keep a positive relationship with them.<br>
<br>
This, however, does not mean that I ignore problems because "problems are negative".  I do not see problems being negative, even though "problem" and "obstacle" are normally negative-quality terms.  In engineering, and especially in more maintenance type aspects such as Operations, problems and obstacles are almost all we deal with.  Everything could be phrased as a problem, and it could be flipped around to being phrased as an opportunity.  <br>
<br>
I don't recommend trying to phrase problems as opportunities all the time, because it leads to sounding unrealistic, but if you look at them positively, they really are opportunities that one can take advantage of to greater or lesser degrees to get greater or lesser benefits, if one can view them appropriately, and work with the knowledge gained from that vision into their nature.<br>
<br>
I think this methodology this has been very good for me, and recommend spending some time to think about this, and how it intersects with your life, and who you are, and if you can think of ways that bring about similar improvements in your own life, which can make working with other people more enjoyable and efficient, and brings you more happiness, contentment and a more fulfilling life with more accomplishments and friends.<br>

# Chapter 10: Everywhere.  Throughout the book.






<h2 id=a7df76e3e33c3832af992a160d248f3b><a href="#a7df76e3e33c3832af992a160d248f3b">10.1</a>: Have "Wouldnt it be nice?" sections, where I posit what would be improvements I have yet to experience.  Coming to terms, agreeing on the foundational details, agreeing on the axioms, agreeing on how to relate data to the axioms.  Agreeing on how to act against axioms.  With these done, we can work much better as a team, and discuss them.</h2>
