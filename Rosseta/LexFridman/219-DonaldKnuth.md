# Lex and Donald


Introduction

the following is a conversation with donald knuth his second time on this podcast
don is a legendary computer scientist touring award winner father of algorithm analysis
author of the art of computer programming creator of tech that led to
late tech and one of the kindest and most fascinating human beings i've ever
got a chance to talk to i wrote him a letter a long time ago he responded and the rest as they say is
history we've interacted many times since then and every time it's been joyful and inspiring
to support this podcast please check out our sponsors in the description this is the lex friedman podcast and
here is my conversation with donald knuth your first large-scale program you wrote
First programs
it in ibm 650 assembler in the summer of 1957. i wrote it in decimal machine
language i didn't know about assembler until a year later but the year 1957 the
year and the program yeah i might have learned about it assembler later that summary i probably
did in 1957 hardly anybody had heard of assemblers you looked at the user manuals
how did you write a program for this machine it would be it would it would say um
you know you would say 69 which meant load the distributor and and then you would give the address of the number you
wanted to load into the distributor uh yesterday uh my friend that
doug spicer at the computer history museum sent me a link to something that just went on youtube it
was the ibm's progress report from 1956 which is you
know very contemporary with 1957 yes and in 1956 ibm had donated to stanford
university on ibm 650 one of the first ones when they showed a picture of the
assembly line for ibm 650s and they said you know this is number 500 or something coming off the assembly line and i had
never seen so many ibm 650s i did in this movie that was a it's on youtube now
um and and it showed the picture from stanford
uh that that you know they they said look you know we donated one of these to
stanford one to mit and they mentioned one other another college and in in december of 56 they donated to
to my university case tech but anyway they showed a picture then
a class session where a guy was teaching programming and on the blackboard it said 69
8 000 i mean he it was he was teaching them how to write
uh code for this ibm 650 which was in decimal numbers
so so the instructions were tended ten decimal digits you had two digits that
said what what to do for they just say uh uh what to do it too
and four more digits to say where to get your next instruction and there's a manual that describes what
each of the numbers mean and the manual was actually one if the manual had been well written i
probably never would have gone into computer science but it was so badly written i figured that i must have a talent for it because
i'm only a freshman and i and i could write a better manual uh and that he did
and so i i started working at the computer center um
and and uh wrote some manuals then but but yeah but
but this was uh but this was the way we did it and and my first program then was june of 1957
the tic-tac-toe no that was the second program the first the third program the first program was
factoring a number okay so you dial a number on the on the um
uh their switches that means you sat at this big mainframe and
and you turn the dials and set a number and and then it would punch out uh the
factors of that number on on cars so that's the input is the number the input
was yeah the input what was the number yeah attended a number and
and uh and the output was uh its factors and and and i wrote that program
uh i still have a copy of it somewhere and um how many lines of code do you
remember well yeah it started out as about 20 but then i kept having to debug it
and i i discovered debugging of course when i wrote my first program and what does uh debugging look like
on a program with just all numbers well you sit there and you uh i don't
remember how i got it into the machine but i but i think there was a way to punch punch it on cards so each each instruction would would be one
one card or maybe i could get seven instructions on the card eight instructions i don't know but anyway
so i'm sitting there at the console of the machine i mean i'm doing this at night when nobody else is around of course um and
and so you have one set of switches where you can dial the number i'm inputting but there's another switch
that's it that you know that says okay now execute one instruction and show me what you thought what you did
or or you or you there was another four switches and say stop if you get to those if if you get
to that instruction so so i can say now go until you get there again and watch okay so i could
watch you know it he would take that number and it would divide it by two and if
it's you know there's no remainder then okay two is a factor so
so then i work on the but if if not divisible by two divide by three okay
keep trying and you know until you know you're you're at the end
and uh you would find a bug if uh if you were just surprised that something weird happened
well certainly i mean first of all i might have it you know try to divide by one instead of
two you off by one errors that people make all the time you know but but maybe i go to the wrong instruction maybe i
you might maybe i uh i left left something in a register that i shouldn't have done but the first bugs
were pretty you know i i i probably on the first night i was able to i was
able to get the factors of 30 you know as equal to two three and five okay um so you're sorry to interrupt you were
so you're sitting there late at night yeah so it feels like you spent many years late
at night working on a computer oh yeah so like what what's that like so most
the world is sleeping and you have to be there at night because that's when you get access to
the computer between my freshman sophomore year i didn't need sleep you know i used to do all-nighters when i was in
high school i used to i used to do the uh the whole student newspaper every
monday night i would i would you know i would just stay up all night and and it would be done on tuesday morning
um that was because i i didn't get ulcers and stuff like that until later you know
but but but uh well the uh i don't know if you know rodney brooks rod brooks of
course yeah he he he told he told me a story that he really you're you know he really
looked up to you he was actually afraid of you vice versa i must say
but when he tells a story when you were working on tech that they screwed up something with a
machine i think this might have been mit i don't know and you were waiting for them to fix the
machine so you can get back to work late at night oh oh that happened all the time
he was really intimidated he's like dr newt is not happy with this that's interesting but no no the the
machine at stanford ai lab was uh uh i
was down an awful lot because we they had they had many talented programmers
changing the operating system every day and so operating system was getting better every day but
it was also crashing so so so i i wrote almost the entire manual for tech during
down time [Music] that much but that's another story okay well he was saying they uh it's a
hardware problem they they uh they tried to fix it and they reinserted something and smoke was everywhere because he was
hurt well that didn't happen as often as the operation coming from but yeah and it was it's a funny story because
you're saying there's this tall uh don knuth that i look up to and
there was pressure to i think it's the computer well it's funny
okay the kind of things we remember that stick in our memory well okay yeah well i i i could tell you a bunch of rod
brooks stories too but let's let's let let's go back to the 650. so so um
so i'm debugging this my first program and and i i i had more bugs in it than a number of
lines of code i i mean the number of lines of code kept growing and let me explain so so i had to punch
the answers on cards all right so so suppose i suppose i'm factoring the number 30 then i got then it i got a
i got to put two somewhere on the card i got to put a three somewhere on the card i got to put
a five somewhere on the card right and and you know what my i was my first program i i probably screwed up and you
know it it fell off the edge of the card or something like that but but i didn't
realize that there are some tentative numbers that have that have more than eight um factors
and the card has only 80 columns and so i need 10 columns for every factor so my first program didn't take account
for the fact that i would have to punch more than one card my first program you know just line the stuff up in memory and then it punched
the card but but after you know so by the time i finished i had to i had to deal with lots of lots of things also i
uh uh if you if you put a large prime number in there my program might have sat there
for for 10 minutes the 650 was pretty slow and so it would sit there spinning its wheels and you wouldn't know if it
was in a loop or whatever you said ten digit ten digits yeah so i think the largest
is sort of nine nine nine nine nine nine nine nine nine seven or something like that and that would you know that that would take
me a while uh for that first one anyway that was my first program well what was your goal
with that program well there's something you were hoping to find a large prime maybe or no
the opposite you know my goal was to see the lights flashing and understand how how this magical machine
would be able to do something that took so long by hand so what was your second program my second program was
uh was a converted number from from binary to decimal or something like
that it was much much simpler it didn't have that many bugs in it my third program was tic-tac-toe yeah
and he had some machi so the the the tic-tac-toe program is interesting on many levels but one of
them is that it has some you can call machine learning in it that's
yeah that's right uh uh i don't know how long it's going to be before
the name of our field has changed from computer science to machine learning but
but anyway uh uh it it was my first experience with machine learning because
okay so here we had yeah how does the program well first of all what is the problem you were solving
what is tic tac toe what are we talking about and then um right how was it designed
right so so you got a three by three grid and each each each
each could be in three states it can be empty or it can have an x or an o yeah right so three to the ninth is a
uh well what is how big is it i should know um but it's 80
81 times 81 times three so um
anyway eight is like two to the third and so that would be uh that would be like two to the sixth
um uh and then uh but that would be 64 then you have to anyway i love how you're
doing the calculation anyway the three comes from the fact
that it's either empty an x or an o right and
the 650 what was it was a machine that had only uh two thousand
ten digit words you go from zero zero zero zero to one nine nine nine and that's it
and and in each word you have a ten digit number so that's not many bits i mean i gotta
have three in order to have a memory of every position i've seen i need three to the ninth bits
okay but it was a decimal machine too it didn't have bits but but but it did have it it did have
strange instruction where if if you had a tentative number that but all the digits were either
eight or nine uh you you'd be eight nine nine eight or
something like that that would uh you you could make a test whether it was eight or nine that was one of the
strange things ibm engineers put into to the machine i have no idea what well um
hardly ever used but anyway i i needed one digit for every every position i'd seen
uh zero meant it was a bad position i meant it was good position i i think i started out at five or six
you know but if you if you win a game then you uh then you increase the value of that
position for you but you decrease it for your opponent uh uh so but but i i i
could i had that much total memory for every every possible position was one digit
and i had a total of 20 000 digits which had which had to also include my program
yes and all the logic and everything including how to how to ask
the user what the moves are and things like this okay so so i think i had to work it out because get every every
position in tic-tac-toe it is equivalent to roughly eight others because you you you
can rotate the board um which gives you factor four and you can also flip it over
and that's another factor two so so i might you know so i might have needed only three to the ninth over eight
positions about you know plus plus a little bit uh so i had but anyway that was
that was a a part of the program to to squeeze it into this tiny so you tried to find an efficient
representation that took account for that kind of rotation i had to otherwise i couldn't do the learning
uh wow so so but but i had three parts to my tic-tac-toe program
uh and i called it brain one brain two and brain three so brain one
just played a um let's see
at random okay it's your turn okay you gotta put an x somewhere he has to go in an empty space
but that's that's it okay choose to choose one and and play it uh
brain two uh had a canned routine
and i think it was it also maybe it had maybe it assumed you were the first
player or maybe it allowed you to be first i think you were odd to be either first of a second but had a canned
built-in strategy known to be optimum for tic-tac-toe [Music] before i forget by the way
i learned uh many years later that charles babbage had had planned to
had thought about programming tic-tac-toe for his for his dream machine that he that he
was never able to finish wow so that was the program he thought about more than a hundred years ago yeah yeah he had he
he did that okay and i had but and and i had however been influenced by a
demonstration at the at the museum of science and industry in chicago it's like it's like boston's science museum i
think bell labs had had prepared a special exhibit about
telephones and relay technology and they had a tic-tac-toe playing uh
machine as part of that exhibit so that had been one of my uh you know something i'd seen
before i was a freshman in college and and inspired me to see if i could write a program for
okay so so anyway i had brain one random you know uh
knowing nothing brain two knowing everything then brain three was the learning one and and i could
i i could play brain one against brain one brain one against brain two and so on and so uh
you could also play against the user against the live members but but uh so so i started going the the
learning thing and i said okay you know take two random random people uh just playing uh uh
tic-tac-toe uh uh knowing nothing um and after about i i forget the number now
but but it converged after about 600 games uh uh to a safe draw
the way my program learned was actually it learned how not to make mistakes because
you know how to it didn't try to do anything for winning it just tried to yeah drop
losing and not lose so that was probably because of the way i did i designed the learning thing i could have you know
had a different uh reinforcement function that that would that would reward brilliant play but
anyway it didn't and uh and and if if i took a novice against the uh
you know the skilled player uh it it was able to learn uh how to play a good game
so that was that and that was really mike but after i finished that i i felt i i
understood programming was there um did you
did a curiosity and interest in learning systems persist for you
so why why did you want brain three to learn
yeah i i think naturally it's we're talking about rod brooks like
he he was teaching all kinds of very small devices to to learn stuff
um if a leaf drops off of a tree uh uh
you know it he was saying something well it learns if there's wind or not but but i i mean he pushed that a little
bit too far but he said he could probably train some little mini bugs to to scour out dishes
if he had enough financial support i don't know can i can i ask you about that because
he he also mentioned that during those years there was discussion about
inspired by touring about computation you know of what is computation
yeah and yeah i never thought about any stuff like that that was
that that was way too philosophical i mean i i was a
i was a freshman after all i mean i i didn't
i was pretty much a machine so it's almost like yeah i got you it's a tinkering mindset
uh not a philosophical mindset it was just exciting to me to
be able to control something but not but not but not to say hmm am i solving a big
problem or something like that or is is this a step for humankind right no no way
when did you first start thinking about computation in the big sense
you know like the universal turing machine well i mean i had to pass an ex i
had to take i had to take uh classes on computability when i was a senior
so you know we read this book by martin davis and yeah this is cool stuff but you know i i
learned about it because i you know i needed to pass the exams but i didn't i didn't invent any of that before stuff
but but i i had great fun playing with the machine you know i um i wrote
program because it was fun to write programs and and and get
this i i mean it was like watching miracles happen
you mentioned in in an interview that when reading a program you can tell when
the author of the program changed oh okay uh
how the heck can you do that like what makes a distinct style for a programmer do you think
you know there's different hemingway has a style of writing versus james joyce or something
well those are pretty yeah those are pretty easy to imitate but it's the same with music and whatever
you can i i i i found uh well during the pandemic i
spent a lot more time playing the piano and i i found something that i'd had i i had it right when i was taking
lessons uh you know before i was a teenager and uh it was
yankee doodle uh played in the style of you know and
i you had you had beethoven and you had wc and chopin and you know and the last
one was gershwin and and i played over and over again i thought
it was so brilliant because but but it was so easy but also to appreciate how
this uh this author mario somebody or other had had been able to uh reverse engineer
the styles of of those components so but now specifically uh to your question i
mean there would be there it was it was pretty obvious in this program i
was reading it was it was a compiler uh and it had been written by a team
at at carnegie mellon and uh i have no idea which program
was responsible for but but it you would get to a part where the guy would just not know how he how to move things
between registers very efficiently and so and so everything that that could be done in one instruction
would take three or something like that that would be a pretty obvious uh change in style but there were but then
there were also you know flashes of brilliance where you could do in one instruction normally i used two because
because you knew enough about the way the machine worked that you could that that you could accomplish two goals
in one step so it was mostly the the brilliance of the concept more than the
uh semicolons and uh or the the you know the use of short sentences versus long sentences something like
that so you would see the idea in the code and you can see the the different style of thinking experience right it
was yeah so it was stylistic i mean like i could identify authors by
their by the amount of technical aptitude they had but not by
styling the sense of rhythm or something like that so if you
think about mozart beethoven bach if somebody looked at don knuth code would
Literate programming
they be able to tell that this is a distinct style of thinking going on
here what do you think and what what would be the defining uh
characteristic of the style well my code now is it
is literate programming so i'm it's a combination of english and c mostly but
but but if you just looked at the c part of it you would also probably notice that i don't
got it you know that i use a lot of global variables that other people don't and and and i expand things inline more than
instead of calling anyway i have different subset of c that i use okay but this
that's a little bit stylistic yeah but but with literate programming you alternate between english and
and c or whatever and um and by the way people listening to
this should look up literate programming it's very interesting uh concept that you
uh you proposed and developed over the years yeah yeah i'm
that's the most significant thing
i think to come out of the tech project is it is that i uh
i i realized that uh my programs
were to be read by people and not not just by computers and and that typography could
massively enhance that and and and so uh i mean it
they're just wonderful if they're gonna look it up that they should also look up this book by
called physically based rendering by matt farr and
anyway it got an academy award but it's but but but all the if
on the graphic effects you see in movies uh like you know are accomplished by algorithms
and this book it is the whole book is a literate program it tells you not only how you do all the shading and
and uh bringing images in that you need for animation and textures and so on but it
also uh you can run the code uh so uh and
and so uh i find it uh an extension of the way i
uh of of how to teach programming is it is but by by telling a story
as part of the program so it's uh it works as a program but it's also
readable by humans yes and especially by me
yeah a week later or a year later that's a good test if you yourself understand the code yeah
easily a week or more or a year later yeah so it it it's uh
what's this piece it's the greatest thing since sliced bread programming or literate literate program okay
uh you heard it here first okay you uh dodged this question in an interview i
Beauty in programming
listened to uh so let me ask you again here uh what makes for a beautiful program
what makes for a beautiful program yeah what are the characteristics you see like you just said literate programming
what are the characteristics you see in a program that make you sit back and say that's pretty good
well the reason i didn't answer is because there are there are dozens and dozens of answers to that because
because each you can define beauty the same personal defined beauty a
different way from hour to hour i mean it depends on what and what you're looking for at one level you it's it's beautiful
just if it works at all another level it's beautiful if it's if it uh
uh uh it can be understood easily it's beautiful if it
if it's illiterate programming it's beautiful it makes you laugh i mean yeah i'm actually so i'm with you i
think beauty if it's readable readable yeah if you understand what's
going on and also understand the elegance of thought behind it
and then also as you said wit and humor i was always uh i remember having this
conversation i had this conversation on stack overflow whether humor is good in comments
and i think it is whether huma is good in comments like uh when you add comments in code yeah
i always thought a little bit of humor is good it shows personality
it shows character shows wit and fun and all those kinds of things of the personality of the programmers
yeah okay so uh a couple days ago i received
a wonderful present from my former editor at aston wesley he he's downsizing his house and he found
uh that somebody at the company had had found all that all of their internal
files about the art of computer programming from the 1960s and they gave it to him
uh and then you know before throwing string in the garbage and then so he said oh yeah he
he planned to keep it for posterity but now he realized that posterity is a bit too much for him to handle so he
sent it to me and so and so i just received uh
this big big stack of of letters uh some of which i had written to them but
but many of which they had written to early guinea pigs who were telling them whether they should publish
or not you know and one of the things was uh uh in in the uh in the comments to volume
one uh uh the the major the major reader was was
bob floyd uh who is my great
uh co-worker in the 60s um died early unfortunately but but uh
and and he he commented about the humor
so we had you know he ran it by me you know says you know keep this joke in or not you know um
they also sent it out to focus groups what do you think about humor in
a book about computer programming what's the conclusion and i stated my philosophy is it said you know the ideal
thing is uh that it's it's it's something where
the reader knows that there's probably a joke here if you only understood it and this is a motivation
to understand to think about it a little bit um but anyway it it it's a very delicate humor
i mean it's it's it's really uh each each century invents a different kind of humor too i mean
and different cultures have different different kinds of humor um yeah like uh
we met we talked about russia a little bit offline uh you know there's dark humor
and you know what when a country goes to something different right any of that life and
stuff like this yo and jack benny i mean
steve allen wrote this book about humor and it was the most boring book but he was one of my idols but
but uh yeah it's called the funny men or something like that but yeah okay so anyway i i
think it's important to know that that this is part of life and and it should be fun and not yeah and and so
you know i wrote this this organ composition which uh uh is based on the bible but i didn't refrain
from putting little jokes in it also in the music it's hidden in the
music it's it's it's there yeah a little humor is okay yeah i mean
not egregious humor so in in this correspondence you know there were
there were things i said yeah i really shouldn't have i i really shouldn't have done that
but uh but other ones i could you know i insisted on and i've got jokes in there
that no that nobody has figured out you in fact in volume 2
i've got a cryptogram a message in cypher and in order to decipher it you're going
to have to have to break an rsa key which is larger than people know how to break
uh and so you know if computers keep getting faster and faster then you know might be
100 years but somebody will figure out what this message is and they will laugh i mean i've got a joke in there
so that one you really have to work for uh i i don't know if you've heard about this
OpenAI
let me explain it maybe you'll find it interesting so open ai is a company that
does uh ai work and they have this language model it's a neural network that can generate
language pretty well but they also of on top of that develop something
called openai codex and together with github they developed
a system called openai copilot let me explain what it does
there's echoes of literate programming in it so what you do is you start writing code
and it completes the code for you so for example you start let's go to
your factoring program you start you write in javascript and python in any language
that it trained on uh you start you write the first line and some
comments like what this code does and it generates the function for you and it does an incredibly good job like
it's not provably right but it often does a really good job of completing the code for you i see whether
but how do you know whether it did a good job or not you could see a lot of examples where he did a good job
and so you it it's not a thing that generates the code for you it starts
it gives you uh so it puts the human in the seat of fixing
issues versus writing from scratch do you find that kind of idea at all interesting
every year we're going to be losing more and more control over what machines are doing and
people are saying well it seemed to like when i was a professor at caltech
uh in this in the 60s we had this this guy who
who talked a good game he could give inspiring lectures and you'd think well
certainly things he was talking about an hour later you said well what did he say um
but what but but he really felt that it didn't matter whether computers got the right answer or not it just mattered whether it made
you happy or not in other words if you you know if if if your boss paid for it uh he
you know then you had a job you could you know you could you could take care of your wife happiness is more important than truth
exactly he didn't believe in truth but he was a philosopher i like it and somehow you you see uh
we're going that way i mean so many more things are are taken over by saying well this seems to work
and so and when there's when there is uh competing interests involved neither side understands
why the decision is being made you know we realize now that it's that
is bad but but consider what happens five private ten year year down the line
when things get even more further detached and each thing is based on something
from the previous year yeah so you start to lose the more you automate the more
you start to lose track of uh some deep experimentally exponentially but so that's the dark
side the positive side is the more you automate the more you let
humans do what humans do best so maybe programming
this you know maybe humans should focus on a small part of programming that requires that genius
the magic of the human mind and the mess you let the machine generate yeah i mean they're that's the
that's the positive but of course it does come with the darkness like automation
what what's better correct i'm never going to try to write a book about that uh i'm never going to recommend to any
of my students to work for them so you you're on the side of i'm on the
side i'm on the side of honor happiness understanding i understand and i i think these things are really
marvelous if they if if what they do is you know all of a sudden we have a better medical
diagnosis or or or you know it will help guide some scientific experiment or something like this uh
you know you know curing diseases or what whatever but but when it
when it affects people's lives in a serious way uh uh so if you're writing if you're writing
code for geeky oh yeah here this is great this will make a slaughter bot okay
so i see so you have to be very careful
like right now it seems like fun and games it's useful to write a little javascript program that helps you with
the website but like you said one year passes two years passes five years and you forget
you start building on top of it and then all of a sudden you have autonomous weapon systems
based well we're all dead it doesn't matter in that sense
well in the end the this whole thing ends anyway so
um but it it there is a heat death of the universe
predicted but i i'm trying to postpone that for for a little bit
well it'd be nice that at the end as we approach the heat death of the universe there's
still some kind of consciousness there to to to to appreciate it
hopefully human consciousness i'll settle for 10 to the 10 to the 10 to the 10th year some finite number but
but things like this might be the reason we don't pick up any signals from
extraterrestrial they don't want anything to do with us oh because they because they
they invented it too and
so you you do have a little bit of worry on the existential threats of
ai and automation so like like removing the human from the picture et cetera yeah people have more
more potential to to do harm now than by far than they did a 100 years ago
but are you optimistic about so the humans are good at creating destructive
things but also humans are good at solving problems yeah i mean there's half empty and have full you know that
so how yeah we have full or what i can go yeah so so let me let me put it this way
because because it's the only way i can be optimistic but but but
think of um of
things that have changed because of civilization you know they don't occur just in nature
so just uh just imagine that the room we're in for example
okay some you know we've got pencils we've got books we've got tables we've got microphones
clothing food all these things were added somebody invented them one by one and
millions of things uh that we inherit okay and
it's inconceivable that that so many millions of billions of things uh wouldn't have problems and
we we get it all right um and and each one would have no
negative effects and so on so it it's very
amazing that it much works as does work it's it's incredibly amazing
and actually that's the source of my optimism as well including for artificial intelligence
so we we drive over bridges we we use all kinds of technology we
don't know how it works and there's millions of brilliant people involved in building a small part of that and it
doesn't go wrong and it works and i mean that it it works and it doesn't go go wrong
often enough to suffer and we can identify things that aren't working and
and try to improve on them in a sub often suboptimal way oh
absolutely but it's but but the the kind of things that
i know how to improve require human beings to be rational and i i'm losing my confidence that human
beings are rational yeah yeah now here you go again with the worst case uh worst case analysis
they may not be rational but they're um they're they're
clever and uh beautiful in their own kind of way yeah i tend to think that most people
um have the desire and the capacity to be good to each other and love will ultimately win out like if
they're given the opportunity that's where they lean in the art of computer programming you
Optimization
wrote the real problem is that programmers have spent far too much time worrying about efficiency in the wrong
places and at the wrong times premature optimization is the root of
all evil in parentheses or at least most of it in programming
can you uh explain this idea uh what's the wrong time what is the
wrong place for our optimization so first of all the word optimization i i
started out writing software uh and optimization was i was a compiler writer
so optimization meant uh making the uh
making a better translation it it so that it would run faster on it on a machine instead of an optimized program
it's just like you know you you you run a program and you set the optimization level uh for
the compiler so that's one word for optimization um and at that time i
i happened to be looking in an unabridged dictionary uh for some reason or other and i came
to work optimizing what's the meaning of the word optimized and it says to view with optimism
and you look in webster's dictionary of english language in 1960 early 1960s
that's what optimized me meant okay
so people started doing cost optimization other kinds of things uh
you know whole subfields of of algorithms and economics and whatever
are are based on what they call optimization now but but to me optimization when i was saying
that was saying uh uh changing a program to make it more
tuned to the machine and i found out that uh
when a person writes a program uh he
he or she tends to think that the parts that were hardest to write are going to be hardest for the computer to
execute so maybe i have 10 pages of code but
i i had to work a week writing this page i i mentally think that when the
computer gets to that page it's going to slow down right uh it's chris oh i don't understand what i'm doing i better
be more anyway this is of course silly but it's it's something that we
that we that we don't know when we write a piece of code we don't know what what whether the computer is actually
going to be executing that code very much so so people had had a very
poor understanding of of what the computer was actually doing
i i made one test where where we studied a fortran compiler
and it was spending more than 80 of its time reading the comments card [Music]
but as a programmer we were really concerned about how fast it could take a complicated expression that had lots of
levels of parenthesis and and and and convert that in into something but that was just you
know less than one percent of the uh so if we optimized that
uh we didn't know what we were doing but but but if if we knew that it was spending eighty percent of his time on
the comments card you know in ten minutes we could we could make the the compiler run more
than twice as fast and you can only do that once you've completed the program and then you empirically study where i
had some kind of profiling that i knew what was important yeah so
you don't think the supplies generally i mean there's something that rings true to this across the board i'm glad that
it applied generally but but it was it was only my good luck i said it but you know but but i did but
i said it in limited context and not and and i'm glad if it makes people think about stuff because i
i but it applies in another sense too that is
sometimes i will do optimization in a way that does help
the the actual running time but makes the program impossible to
change next week because i've changed my data structure of something that
that made it less adaptable so one of the great uh principles of computer science is
is it is laziness or whatever you call it the late binding uh you know don't
hold off decisions when you can um and and and you know and we understand now
quantitatively how valuable that is what do you mean we understand so you mean people
people have written thesis about how you can how late binding will it will improve the i mean you know just
in time manufacturing or whatever you can make you can defer a decision
instead of doing your advanced planning and say i'm gonna allocate thirty percent to this and fifty percent so in
all kinds of domains there's an optimality to laziness in many cases decision is not made in advance so
instead you you design in order to be flexible uh uh to to
change with the uh uh with the way the wind is blowing yeah but so the reason that line resonated
with a lot of people is because uh there's something about the programmer's mind
that wants that enjoys optimization so it's a constant struggle
to balance laziness and lay binding with
the desire to optimize the elegance of a well-optimized code is
something that's compelling to programming yeah it's a another concept of beauty
Consciousness
let me ask you a weird question so roger penrose
has talked about computation computers and
he proposed that the way the human mind discovers mathematical ideas is something more
than a computer that that a universal turing machine cannot
do everything that a human mind can do now this includes discovering mathematical ideas and it
also includes he's written a book about it consciousness so i don't know if you know roger but
yeah my uh my daughter's kids played with his kids in oxford
nice so do you think there is such a limit to the computer do you think consciousness
is more than a computation do you think the human mind the way it thinks is more
than a computation i i mean like i i can say yes or no but but but i don't i have no reason
i mean so you don't find it useful to have an intuition in one way or the other like
when you think about algorithms do you isn't it unanswerable question in my opinion is
is no better than anybody else you think it's unanswerable so you don't think eventually science angels can dance on the head i mean i
don't know but angels anyway there are lots of things that are
beyond that that we can speculate about but i don't want somebody to say oh yeah canoe said this and and so he's he's
he's smart and so he so that must be i mean i say it's something that uh
we'll never know interesting okay that's a strong statement i i don't
i personally think it's something we will know eventually like there's no reason to me why the the workings of the
human mind are not within the reach of science that's absolutely possible and i'm not
denying it yeah uh but right now you don't have a good intuition i mean that's also possible
you know that and ai you know created the universe you know intelligent design
has all been done by an ai yes this is i mean all these things are but
but but but you're asking me to to pronounce on it and and i don't have any expertise i i i i'm a teacher that
passes on knowledge but i don't but i don't know the fact that i
that i vote yes or no on well you do have expertise as a human
not as a not as a teacher or a scholar of computer science
i mean that's ultimately the realm of where the discussion of human thought yeah well i know we're in consciousness
he might even thought he proved it but no he doesn't he doesn't prove it he is following intuition but
but i mean you have to ask john mccarthy john mccarthy i think
uh we're totally unimpressed by these statements so you don't think so even like the
touring paper on uh on the touring test that
you know starts by asking can machines think oh um you don't think these kind of um
touring doesn't like that question yeah i don't consider it important let's put
it that way because it it's in the category of things that
it it it would be nice you know but i think it's beyond knowledge and so i don't
i'm not i'm more interested in knowing about the riemann hypothesis or something
so when you say it's an interesting statement beyond knowledge yeah i think what you mean
is it's not sufficiently well it's not even known well enough to be able to formalize it
in order to ask a clear question yeah and so that's why it's beyond knowledge but that doesn't mean it's not
eventually going to be formalized yeah yeah maybe consciousness will be understood some some day but uh the last
time i checked uh it it was still 200 years away
i haven't been specializing in this by any means but but but i went to lectures about it 20 years ago when i was
uh there was there was a symposium at the american academy in in cambridge and
it started out by saying essentially everything that's been written about consciousness is
is hogwash i tend to
i tend to disagree with that a little bit so well it's so consciousness for the longest time
still is in the realm of philosophy so it's just conversations without any basis and
yeah understanding still i think once you start creating artificial
intelligence systems that interact with humans and they have personality
they have identity you start flirting with the question of consciousness not
from a philosophical perspective but from an engineering perspective and then starts becoming much more
like i feel like yeah yeah don't misunderstand me i i i i i certainly don't disagree with
that at all um and even at these lectures that we had you know 20 years ago there were
neurologists pointing out that that human beings had actually decided
to do something before they were conscious of making that decision yeah uh
i mean they could tell that you know that signals were being sent to their arms before they before their they
knew that they were anything like this are true and and uh my uh you know less valiant has
an architecture for the brain and more recently uh uh christus papadomitrio uh
in the academy science proceedings a year ago uh with with two other people but i know chris
does very well uh and and he's got this uh uh this model of uh
this architecture by which you could uh create a uh things that
that correlate well with the uh with experiments that are done on consciousness uh
and and and and he he actually you know has a a machine language that in which you can
you can write code and and test hypotheses
uh and so it it might you know we might have a big breakthrough my personal
feeling is that consciousness the the best model i
i've heard of uh to explain the the miracle of consciousness uh is
that that that somehow inside of our
brains we're having a a continual survival for the fittest
competition as i'm speaking to you uh all the possible things i might be
wanting to say are all in there and there's like a voting going on yeah right and
one of them is is winning and and that's affecting the you know
the next sentence and so on yeah uh and uh there was this book
machine intelligence or unintelligent on intelligence yeah bill atkinson uh was what was it what was a
total devotee of that book well i like
whether it's consciousness or something else i like the storytelling part that we it feels like uh for us
humans it feels like there's a concrete it's almost like literary programming i don't know what the programming going on
on the inside but i'm getting a nice story here about what happened and it feels like i'm in
control and i'm getting a nice clear story so but it's also possible there's a computation going on
that's really messy there's a bunch of different competing ideas and in the end it just kind of generates
a story for you to uh a consistent story for you to believe and that makes it all nice yeah and so
i prefer to talk about things that i have some expertise and then things for which i which i'm only a
uh you know on the sideline so there's a tricky thing i don't know
Conway's game of life
if you have any expertise in this you might be a little bit on the sideline it'd be interesting to ask though
what are your thoughts on cellular automata and the game of life have you ever played with those kind of
little uh games i think uh the game of life uh it is
it is wonderful and uh uh and
and shows all kind of stuff about how things can evolve without the creator
understanding anything more than the power of learning things in a way but to me the
most important thing about the game of life is that is is how it
focused for me what what it meant to have free will or not
because the game of life is obviously totally deterministic yes and i i i find
it hard to believe that anybody who's ever had children cannot believe in free will
right on the other hand this makes it crystal clear
john conway said he wondered whether it was
immoral to shut the computer off after he got into a particularly interesting play of the game of life um wow yeah so
there is to me the reason i love the game of life is exactly as you said a clear
illustration that from simple initial conditions with simple rules you know exactly
how the system is operating is deterministic and yet if you let yourself
if if you allow yourself to lose that knowledge a little bit
enough to see the bigger organisms that emerge and then all of a sudden
they seem conscious they seem not conscious but living if if the universe is finite
we're all living in the game of life to slow down i mean it's sped up a lot
but do you think technically some of the ideas that you used for
analysis of algorithms can be used to analyze the game of life can we make sense of it or is it too
weird yeah i mean i i i've got i've got a dozen exercises in volume
for fascicle six uh that actually worked rather well for that
purpose but bill gospers came up with the
with the algorithm that that allows that allowed golly to uh to
you know to run thousands and thousands of times faster to you know the website called golly
g-o-l-l-y it simulates the cellular automata like game of life yeah you got
you got to check it out yeah can i ask about john conway yes in fact i i i'm just reading now the
the issue of mathematical intelligence or that came in last last week it's a whole issue devoted to to
uh you know remembrance of of him did you know him
i i slept overnight in his house several times i
yeah he recently passed away yeah he got he died a year ago
may i think it was i've covered
what are you what are some memories of him of his work that stand out for you
is did uh on a technical level did any of his work
inspire you on a personal level that did he himself inspire you in some way
you know absolutely to all of those things but let's see when did i first meet him i guess i first met him at oxford in like
1967 when i was wow okay that's a long time ago yeah yeah
you were minus 20 years old or something i don't know 1967. but but uh
there was a conference where uh and i think i spoke
i was speaking about something that known as the canoes bendix algorithm now
but but he he gave it famous talk about knots and and at the end i didn't know at the
time but but anyway that talk had now the source of thousands and thousands of
papers since then uh and it was he was reported on something that
he had done in high school uh you know almost ten years earlier
[Music] before this conference but he never published it and and he climaxed his
stock by building some nozzle you have these lit these little plastic
things that you that you could stick together uh it's it's it's it's something like lego but easier
and so he made a whole bunch of knots in front of the audience and so on and then disassembled it
so it was a dramatic lecture before he had learned how to give even
more dramatic lectures later so all right and were you at that lecture and i was there
yeah because i had to i was at the same conference um for some reason i was i i happened to be
in in calgary uh at the same day that he was visiting calgary
and it was a spring of of 72 i'm pretty sure and
and we had lunch together and he wrote down during the lunch on a
napkin uh all of the facts about what he called numbers
um and i and and he covered the napkin with with the
theorems about his his idea of numbers
and i thought which was incredibly beautiful um and
and later in 1972 my sabbatical year began and i went to norway
and and in december of that year uh in the middle of the night
the thought came to me you know conway's theory about numbers would be a great
thing to teach students how to invent research and what the joys are of research
and and i and so i said and i had also
read a book in dialogue by by alfred rennie
uh where he was kind of a socratic thing where the two characters were talking to each other about mathematics and so i
and so at the end in the morning i i woke up my wife and said
jill i think i want to write a book about conway's theory
and um you know you know i'm supposed to be writing the
art of computer programming doing all this other stuff but i got but i really want to write this other book
and so we made this plan but i said i thought i could write it in a week
and we made the plan then so in january i i rented a room in a hotel in downtown
austin we were in sabbatical in norway uh and i ran at the hotel in in downtown
oslo and um did nothing else except write
up conway's theory and and i i changed the name to surreal numbers that so this
book is now published as surreal number and um and
you know we figured out we'd always wonder what what what would he like to have an affair in a hotel room so so we
figured out that she would visit me twice during the week things like this you know we would
you know try to sneak in this was hotel was was run by a mission organization these
ladies were probably very strict but anyway so yeah so uh and the wild week
in every way but the thing is i had lost that i had lost that napkin in which you wrote the theory but but i i
i looked for it but i couldn't find it so i tried to recreate from memory what he
told me at that luncheon uh in calgary and and as i as i wrote the book i i was
going through exactly what i what the characters in the book were supposed to be doing so i start with the
with the two axioms that start out the whole thing and everything is defined it flows from that but you have to discover
why and and as a every mistake that i make as i'm trying to discover it i uh my
characters make two right you know and and and so it was it's a long long story
and i but but i worked through this week uh uh and and it and it was
it it was one of the most exciting intense weeks of my life and and
and i i described it in other places but but but anyway uh
after six days i i finished it and on the seventh day i rested and and i sent the right to my secretary to
type it it was flowing as i was writing it uh faster than i could think almost
but but but after i finished it uh and tried to write a letter to my secretary
telling her how to type it i couldn't write it anymore he gave it the muse had left me
completely can you explain how that week could have happened like why is that seems like
such a magical week i have no idea but anyway there was some it it was almost as if i was channeling
so so the book was typed they sent it to conway and and he said well don you got the
axiom the one axiom wrong there is a difference between
um less than or equal and not greater than i don't know
the opposite of being greater than yeah and less than or equal but anyway
technically it can make a difference when you're developing a logical theory and the way i had chosen
was harder to do than john's original so um and we visited him at his house in
cambridge in april we took a boat actually from norway over to across the channel and and so on
and stayed with him for some days and and uh oh he told he talked we talked about all kinds of
uh of of things he has he had puzzles that i'd never heard of before
he had a great way to to solve the game of solitaire many of the
common interests that we you know he'd never written up and but but anyway
uh then in the summer time i took another week off and went to a
a place in in in the mountains of norway and and rewrote the book
using the correct axiom and so so that was the most intensive connection with
with conway uh after that uh it started with a napkin it started with an app
connect but but but we would run into each other all that well yeah
the next really impo i was giving lectures in montreal
uh i i was giving a series of um
of of seven lectures about the topic called stable marriages and
and and he arrived in montreal uh uh between my sixth and seventh lecture
and and we met at a party and uh i i started telling him about the topic i
was doing and uh he sat and thought about it he came up with a beautiful theory
to show that the uh i mean in technical terms it's it's that the that the set of all stable marriages it
forms a lattice and and there was a simple way to find the greatest lower bound
of of two stable pairings and and least upper bound of two stable married and so i could use it in my
lecture the next day and he came up with this theorem you know during the party
uh and it it it's a brilliant yeah it's a distributive lesson i mean it it's uh you know
uh it it added greatly to the theory of of stable matching
Stable marriage
so you mentioned your wife jill you mentioned stable marriage can you tell the story of how you two
met so we celebrated 60 years of wedded bliss uh last month
and and we met because uh uh i was dating her roommate
this this was my sophomore year her freshman year i i was dating her roommate and
i wanted her advice on strategy or something like this and anyway i
found i enjoyed her advice better than i enjoyed a roommate
you guys were majoring the same thing no no no because because i read something about
working on a computer in grad school on a difficult computer science topic
so so she's an artist and i'm okay and i'm a you know geek and what was she doing
with a computer science book all right i read the was it the manual that she was reading what was she reading i wrote the
manual that she had had she had to take a class in computer science okay
and and uh you're the tutor no no yeah no we yeah we
there were tearful times uh you know trying to learn certain concepts but i
learned art from her and so we we worked together you know occasionally in design
projects but but every year we write a christmas card and and we each have to
compromise our our own notions of beauty yes uh when did you
fall in love with her that day that i asked her about her her roommate
okay i mean no i i okay so i i don't mind telling these things
depending on how you for how far you go but [Laughter] but let me promise
let me tell you this that i i never really enjoyed kissing uh
until i found how she did it
and 60 years yeah is there a secret you can uh you can say
in terms of stable marriages of how you stayed together so long the topic stable marriage by the way is
not it is is the technical term uh yes
it's [Music]
different people will have to learn how to compromise and and and
work together and and and you're going to have ups and downs and and
and crises and so on um and so as long as you don't set your expectation on
having 24 hours of bliss then there's a lot of hope for stability
but if you if if you decide that it's that that there's going to be no frustration
[Music] so you're going to have to compromise on your notions of beauty when you write
christmas cards that's it uh you uh you mentioned that richard
Richard Feynman
feynman was someone you looked up to yep um probably you've met him in
caltech well we knew each other yeah at cal tech for sure yeah
uh you are one of the seminal personalities of computer science he's one for physics
have you ever is there specific things you picked up from him by way of inspiration or uh
so we used to go to each other's lectures and and uh
but but if i saw him sitting in the front row i would throw me for a loop actually and
i i i would i would miss a few a few sentences
what unique story do i have about i mean i i i i often refer to his
his time in brazil where he uh essentially
said they were teaching all the physics students the wrong way they were just they were just learning how to pass exams and not learning any physics
and he said you know if you want me to prove it you know
here i'll turn to any page of this textbook and i'll tell you what's wrong with this page and and he did so and
and the textbook had been written by his host and and it was a big embarrassing
incident but he had previously asked his host if if he was supposed to tell the truth
um but but anyway it epitomizes the way
education goes wrong uh in all kinds of fields uh and has to periodically
be brought back from from from a process of giving credentials to
a process of giving knowledge that's probably a story that continues to this day in a bunch of places where
it's too easy for educational institutions to fall into
credentialism versus uh inspirationalism
i don't know if those are words but sort of uh yeah understanding versus just giving a little um
it would be plaque and you know it's it's very much like what we were talking about if you want
the computer to if you want to be able to believe the answer computer is sure it's doing that
one of the things bob floyd showed me in the 60s there was a uh he loved this cartoon there was a
there were two guys standing in front of in those days the computer was a big thing you know
and and the first guy says to the other guy he said this machine can do in one second what it would take
uh a million people to do in a hundred years and the other guy says oh so how do you
know it's right [Laughter] that's a good line uh
is there some interesting distinction between physics and math to you have you looked at physics much to like
speak university feynman so the difference between the physics community the physics way of thinking
the physics intuition versus the computer science the theoretical computer science the mathematical
sciences do you see that as a gap are they strongly overlapping
it's quite different in my opinion i um i started as a physics major and i switched into math
and probably the reason was that i could i could get a plus on the physics exam but
i like i never had any idea why i would have been able to come up with the problems that were on
those exams but but in math i i i knew
you know why the teacher set those problems and i thought of other problems that i could set too
and i believe it's quite a different mentality is it it has to do with your philosophy
of geek geekdom i mean some of my computer scientist friends
are really good at physics and others are not and and i i'm uh you know i'm really good at algebra
but not at geometry you talk about different parts of mathematics you know i just it's
so they're different kind of physical but physicists think of things in terms of waves and
i can think of things in terms of waves but it's like a dog walking on hind legs if i'm thinking
about it so you basically you like to see the world in in uh
in discrete ways and then this is more continuous yeah i i i'm not sure
if turing would been a great physicist i think it was a pretty good
chemist i don't know but but uh but anyway i see things
i i i believe that computer science is largely
driven by uh a people who have brains who work
who are good at resonating with certain kind of of of concepts
and like quantum computers it takes a different kind of brain yeah that's interesting yeah it's it's well quantum computers is
almost like at the intersection in terms of brain uh between computer science and physics
because they it involves both at least at this at this time
but there is like the physicists i've known they have incredibly powerful intuition
and and there's a lot i mean statistical mechanics so i i study
uh statistical mechanics and you know i mean random processes uh uh are
related to algorithms in a lot of a lot of ways and so but there's lots of different flavors of flavors of physics
as there are different flavors of mathematics as well um but but the thing is that i i don't
see well actually when they talk to physicists
use a completely different language than when they're talking to when they're writing expository papers
so i didn't understand quantum mechanics at all from reading about it in scientific american
but but when i read you know how they described it to each other talking about eigen eigenvalues
and various mathematical terms that
that made sense then it made sense to me but but hawking said that
every formula you put in a book you lose half of your readers and so he didn't put any formulas into the book so i couldn't understand his book at all
you could say you understood it but i really i really didn't
um well feynman also spoke in this way so feynman
i think prided himself on a really strong intuition but at the same time he was hiding all the the really good the
the deep computation he was doing so so there was one thing that that uh
that i i was never able to uh yeah i wish i had more time to to work out with
him but i guess i could describe it for you there's there's something that got my name
attached to it called knuth arrow notation but it's a notation for very large numbers
and so uh it i find out that that somebody invented it in in 1830s
it's fairly easy to to understand anyway so you start with
x plus x plus x plus x n times and and you can call that x n
so x n is multiplication then you take x times x times x times x and n time that gives
you exponentiation x to the nth power so that's one arrow x
so x n with no arrows is multiplication x arrow n is x to the nth power yes just
to clarify for the uh so x times x times x n times is
obviously x n and x x plus x plus x n times
oh yeah okay and then uh xn multiplication is x to the n uh and then
and then here the arrow is when you're doing the same kind of repetitive operation for the exponential so i so i
put in one arrow and i get x to the nth power now i put in two arrows and that makes takes x to the x to the x to the x
to the x n times pi so in other words if if if it's two
uh double arrow uh three that would be
that would be 2 to the 2 to the 2 so that would be 2 to the fourth power that'd be 16 okay okay so so so that's
the double arrow and now you can do a triple arrow
uh of course uh and and so on and
and i i had this this paper called uh well
essentially big numbers uh you know you yeah you try to impress your friend but by saying a number
they've never thought of before yeah and and and i i gave a special name
for it we designed a font for it that has script k and so on but it but it really is 10
i think like 10 quadruple aero 3 or something like that and i claim that that number if it
is so mind-boggling that you can't comprehend how large it is but anyway fine
i talked to feynman about this and he said oh let's just let's just use double arrow
but instead of taking integers let's consider complex numbers right so
you know you have that means x to the x
x but what about x x double arrow two 2.5 well that's not too hard to figure
out that's interpolate between those but what what what x double arrow
i or one plus i or some complex number uh and
and uh so he claimed that that that there was no analytic
function that would that would do that would do the job uh but i i i i didn't know how he could
claim that that was that wasn't true and his next question was did then have
a complex number of arrows [Laughter]
yeah okay wow okay okay so so that's that's fine uh that's
fine can you describe what the [Music] uh new morris pratt algorithm does
Knuth-Morris-Pratt Algorithm
and how did you come to develop it one of the many things that you're known for and has your name attached to it yeah
all right so it should be actually morris pratt knuth
but we decided to use alphabetical order when we published the paper the problem is
uh something that everybody knows now if they're if they're using a search engine
uh you have a a large collection of text
and you want to know if if the word canoeist appears anywhere in the text to
say or or some some other word that's less interesting than
but anyway that's the most interesting thing or something mega morris right so we have we have
a large piece of text and it it's all one long one-dimensional thing you know
first or second letter et cetera et cetera et cetera and so uh the question you would like to be able
to do this um and the obvious way is that let's say
we're looking for morris they don't know that so we would we would go through and
wait till we get to letter m then we look at the next word and sure enough it's an o and then an r but then that oh
too bad um yeah the next letter is is e
so we missed we missed out on morris and so we go back and start looking for another
okay all over again so that's the obvious way to do it all right um
and and jim morris noticed there was a more clever way
to do it the obvious way would have started let's say you know we found that let letter m at
character position one thousand so it was started next at character position 1001
[Music] but but he but he said no look we we already read the o and the r
and we know that they aren't m's so we could we could start
we don't have to read those over again all right so uh and this gets pretty tricky when
when the word isn't morris but it's more like abracadabra where you have patterns that
are occurring uh like repeating patterns at the beginning at the middle right
right so so um he worked it out and he put it into the system software
at berkeley i think it was where he was he was writing some berkeley unix i think was some routine i was supposed to
find occurrences of patterns in texas and and
we didn't explain it and and so he found out that several months later somebody had
had looked at it didn't look right and so they ripped it out so he had this this algorithm but it
didn't make it through you know because he what wasn't understood
nobody knew about this particularly von pratt also had independently
discovered it a year or two later i forget why
i think vaughn was studying some technical problem
about palindromes or something like that he wasn't really it juan wasn't working on
on text searching but he was working on on an abstract problem that
that was related well at that time steve cook was a professor at berkeley uh
and uh uh it was the greatest mistake that
berkeley cs department made was not to give him tenure and so steve went to
went to toronto but um but i but i knew steve while he was at berkeley
and he had come up with a with a very peculiar theorem uh
about a technical concept called a stack automaton and a stack automaton it is a machine
that that it can't do everything a turing machine can do but it
it can only look at something on at the top of a stack or it can put more things on the stack or or it can take
things off the stack like it can't remember a long string of symbols but but it can remember them in
reverse order so so if you tell a stack of thomas on
it can tell you afterwards edcba you know it doesn't have any other
memory except except this one thing that it can see and steve cook proved this amazing thing
that says if a stack automaton can recognize a language
where the strings of the language are length n in any um amount of time whatsoever so the stack
automaton you might use a zillion steps a regular computer can recognize that
same language in time n log n so steve had a way of transforming
a a computation that goes on and on and on and on into using different data structures
into something that you can do on a regular computer uh fast the stack of timezone goes slow but
but but but somehow the fact that it can do it at all means that there has to be a fast way
so i thought this was a pretty you know cool theorem and so i tried it out on
on a problem where i knew a stack automaton could do it
but i couldn't figure out a fast way to do it on a regular computer i thought i was a pretty good programmer
but but by golly i couldn't think of any way to recognize this language
efficiently so i went through steve cook's construction i filled my blackboard
with all the everything that stack thomas undone did you know i i i wrote down and and
then i tried to see patterns in that and
and how did he convert that into a computer program on a regular machine um and
finally i psyched it out what was what was the thing i was missing so that i could
say oh yeah this is what i should do in my program uh and now i have an efficient program
and and so i uh i i would never have thought about
like that if i hadn't had his theorem which was purely abstract thing
actually to try to intuit how to use the stack automaton for the the string matching
problem yeah so so so the problem i i had
started with was not the string matching part but then i realized that the string matching problem was another thing which
would also be could be done by a stack of automatons and and so when when i looked at what
that told me then i had a nice algorithm for this string matching problem uh
and and it told me exactly what i should remember as i'm as i'm going through the string
and i worked it out and and i wrote this little paper called automata theory can be useful
and and the reason was that it was first i mean i had been reading all kinds of papers about automated theory
but it never taught me it never improved my programming for for everyday problems
uh it was something that you published in journals and and and you know it was it was interesting stuff but it but here
was a case where i couldn't figure out how to write the program i had a theorem from automated theory then i knew how to
write the program so this was for me uh
you know a change in life i started to say maybe i should learn more about thomas
and and and and i i showed this note to vaughn pratt and he said
that's similar to something i was working on um and then uh
and jim morris was at berkeley too at the time anyway he
he he's had an illustrious career but i haven't kept track of jim but one is my colleague at
stanford and my student uh later but but this was before vaughn
ron was still a graduate student and hadn't come to stanford yet so we found out that we'd all been working on the
same thing so so it was our algorithm we each discovered it independently but each of us had discovered a different
a different part of the elephant you know a different aspect of it and so we could put our
our our things together it was my job to write the paper how did the elephants bring to life
spring to life was because i i had drafted this paper
autonomous theory oh it can be useful which was seen by vaughn and then by jim and then then
then we combined because maybe they had also been thinking of writing something up
about it about specifically history problem
Hardest problem
let me ask a ridiculous question uh last time we talked you told me what the most beautiful algorithm is
actually uh for strongly connected graphs what is the hardest problem
puzzle idea in computer science for you personally that you had to work through
just something that was just the hardest thing that i've ever been involved with yeah
okay well yeah that's i don't know how to answer questions like that but in this case uh it's pretty clear
okay because it's uh called the the birth of the giant component okay so
now let me explain that because this is actually gets gets into physics too
and it gets into something called bose einstein statistics but but but anyway
it's got some interesting stories and it connected with berkeley again
so start with the idea of a random graph now this is
here we we just say we have n points that are totally unconnected
and and there's no geometry involved there's no saying some points are further apart
than others all points are exactly are exactly alike and
let's say we have 100 points and and we number them from zero zero to nine nine
all right now let's let's take pi uh the digits of pi so
two at a time so so we had 31 41 59 26 we we can look go go through pi
and so so we take the first two 31 41 and let's
let's put a connection between point 31 and point 41
that's an edge in the graph so then we take 5 9 2 6
and make another edge and the graph gets bigger it gets more
and more connected as we add these things one at a time okay so we start out with end points
and and we add uh m edges okay now each edge is completely
we forgot about edges we had before we make an edge twice we might get an edge from a point
to its selfie but um you know maybe pi is going to have a run of four digits in there
so we're gonna but anyway we're evolving a graph at random
um and a magical thing happens when the number of edges
is like point four nine and uh
so maybe n is a million and i have uh you know 490 000 edges
uh then it almost all the time it it consists of isolated trees
not even any loops right it's a very small number of veggies so far
a little less than half n and right but if i had point five one inches so a
little more than half in so it's you know million points 510 000 edges
now it probably has a
one component that's much bigger than the others um and we call that the giant component
is that can you clap so can you clarify so is there a name for this kind of random
super cool pie random graph well i i call it
part the pie graph no no i the pie graph is actually
my pie graph is based on on binary representation of pi not the decimal representation of pi but but but
but anyway let's suppose i was rolling dice instead what's that so sorry so it doesn't it
doesn't have to be pi any source the point is every step
choose totally at random one of those endpoints and choose totally at random another one
of the end points make that an edge that's the process yeah
so there's there's nothing magical about pi they you're no no i was using pi to sort of saying pi is sort of random that
nobody knows a pattern in exactly got it i got it but it's not yeah i i could have just as well drawn
straws or something um this was a concept invented by erdogan rainey and
they called evolution of random graphs and if you start out with with a large number n
and you and you repeat this process all of a sudden a big bang happens at one half n there'll be two points together
then maybe we'll have half have three uh and then
you know then they maybe branch out a little bit but but they'll all be separate until we get to one half end
and we pass one half in and all of a sudden there's substance to it that
there are there's a big clump of stuff that's all joined together so it's almost like a phase
transition of some kind it's exactly it it's a phase transition but it's actually it's a double phase transition
and turns out it it it happens there's actually two things going on at
once at this phase transition which uh which is very remarkable about okay
so so um a lot of the most important algorithms are based on random processes and so i
wanted to you know i want to understand random processes now so there are data structures that sort
of grow this way okay so so dick carp one of the leading
experts on on random randomized algorithms had his students working looking at this
at berkeley and we heard a rumor that the students had found something interesting happening
the students are are generating this or simulating this random evolution of
graphs and under taking stat snapshots
every so often take a look at what the graph is and the rumor was that every time they
looked that there was only one component that had loops in it almost always they do a
million experience and only three or four times did they ever ever
happen to see a loop at at this point no more than one component with the loop
so they want you to keep till the graph gets completely full uh so it starts out totally empty and gets
more and more more and more edges all the time uh and and so okay
certainly a loop comes along once but but now all the loops stay somehow joined to that one
they're there never were two guys with loops wow okay in this experiment okay so anyway
this one almost always certainly not always yeah but but but with high very high
probability that seemed to be true so so we heard about this rumor at stanford
and we said if if that's true then must you know a lot more must also be true so there's
a whole bunch there's a whole theory out there waiting to be discovered that we haven't ever thought about so so let's
take a look at it and so we look closer and we find out no it actually it's not true
but but in fact it's almost true namely
there's a very short interval of time when it's true and and if you don't happen to look at
it during that short interval of time then you miss it
so that in other words there'll be a period where they're two or three components
have loops but they join together pretty soon okay
so so if you don't have a real fast shutter speed you're going
to miss you're going to miss that instant so separate loops don't exist for long that's that's it yeah you know i started
looking at this to make it quantitative and uh basic problem was to slow down the big
bang so that i could watch it happening yeah i i think i can explain it actually
in fairly elementary terms deep even without writing a formula that's right like hawking would do uh and and
and so uh let's let's watch the evolution and and at first uh these edges are coming along
and they're just making things without loops which we call trees okay so then all of
a sudden the loop first appears so at that point i have one component that has a loop
all right now now i say that the complexity of a component
is the number of edges minus the number of vertices so if i have a loop i have like a loop
of length five it has five edges and five vertices
um or or i could put a tail on that and that would be another edge another vertex like a zero one two complexity
kind of thing so so if the if the complexity is zero we have one one loop i call it a cycle or i call a
cyclic component so so cyclic component looks like a
a wheel to which you attach fibers
or trees they go branching but there's no more loops there's only one loop and
everything else feeds into that loop okay and that has complexity zero
but but a tree itself has complexity minus one because it has uh uh you know
like like it might have ten vertices and nine edges to tie the time together so nine
minus ten is minus one so so complexity minus one is a tree
it's gotta be connected that's what i mean by a component it's gotta be connected so so so if if i have ten
things connected i have to have nine edges can you clarify
why when complexity goes uh you can go above zero i'm a little yes
right so the complexity plus one is the number of loops so if complexity is zero i have one loop
if if if complexity is one that means i have one more edge then i have vertex
so i might have like 11 edges and 10 vertices
it's so it turns we call that a bicycle because it it it's got two loops and it's got to have two loops in it
why can't it be trees just going off of the loop that i would need more edges than
all right right okay so so every time i get another loop i i get
another excess of edges over vertices i got you okay so in other words uh
we start out and after i have one loop i have one component that has
a cycle in it not now the the next step uh according to the rumor would be that
at the next step i would have a bicycle
in the evolution of almost all graphs it would go from cycle to a bicycle but in
fact there's a certain probability it goes from cycle to two you know
to two different cycles all right um and i worked out the probability it
was something like five out of twenty four that was pretty high it was substantial yeah
uh but still soon they're going to merge together almost okay so
that's so cool but but then it splits again after you have either either two or one
one uh the next step is you either have three or you have two one or you have
one on one okay and so i worked out the probability
for for those transitions and i worked it out up to up to the first five transitions
and i had these so i had these strange numbers five twenty fours and i stayed up all night and about three a.m
i i had the numbers computed and i looked at them and here were the denominator was something like
20 2 3 0 2 3. so
the probability was something over 2 3 0 2 3. i don't know how you worked that out but i had a formula of that you know i could
calculate the probability yeah and and i could find the limiting probability as n goes to infinity and and it turned out
to be this number but the denominator was 2 0 and i and i looked at the denominator and i said wait a minute
this number factors because 1001 is equal to 7 times 11 times 13. i
had learned that in my first computer program so so so
so 23023 yeah is 7 times 11 times 13 times 23.
that's not a random number there has to be a reason why those small primes appear in the
denominator but my think so all of a sudden that suggested um
another way of looking at the problem where small prime factors would occur
so what would that be so that said oh yeah let me take the logarithm of this
formula and and sure enough it's going to simplify and and it happened
so and i wouldn't have noticed it except for this factorization okay so i go to bed and i say okay this
is this looks like i'm slowing down the big bang i can figure out what's going on here and
the next day it turned out bill gates comes to stanford to visit uh they're trying to sell him on donating money to
uh for a new computer science building sure and and they and uh so they gave me an
appointment to talk to bill and i and i wrote down on the blackboard this
this evolutionary diagram you're going from one to two five twenty fourths in all this business yeah
and i wrote it down and anyway at the end of the day the uh he was discussing people with the
with the uh development office and he said boy i was really impressed with what professor knuth said
about this giant component and uh and so uh you know i i love this
story because it shows that theoretical computer science has is really worthwhile you know
does bill have you ever talked to bill gates about it uh since then yeah
that's a cool yeah that's a cool little moment in history yeah but but anyway he happened to visit on exactly the day
after i had i i had found this pattern and that allowed me to to crack the problem
so you know so that i could develop the uh the theory some more and understand
what's happening in the big but uh because i could i could now write down
explicit formulas for stuff right and so it would you know it would work not only the first few
steps but also they'll study the whole process and and i worked further and further and i
with two authors co-authors and we finally figured out that the probability
that the rumor was true in other words look at the evolution of a of a random graph going
from zero zero to to complete and say what's the probability that at
every point in time there was only one component with a cycle we started with this rumor saying
there's only one site there's only one component with the cycle and and uh
so it's a hundred percent the rumor was that was 100
it turned out the actual numbers was like percent or i i don't know i should
remember the number but i do but i don't have it with me but but anyway but but the but the number
it it turned out to be like 12 over pi squared or anything
it was a nice it related to pi yeah um and we could never have
done that with but so that's the hardest problem i ever saw in my life was to prove that this probability is is it was proven
the probability was proven yeah i was able to prove this that this and and and this should shed light on a
whole bunch of other things about random graphs that that was sort of the the major
thing we were asked after that's super cool what was the connection to physics that you mentioned
well bose einstein statistics is the study of how molecules uh
bond together without geometry without distance
Open source
you created the tech type setting system and released it as open source
just on that little aspect why did you release it as open source
what is your vision for open source no okay well that the word open source
didn't exist at that time but we but i i didn't want proprietary rights over it
because i saw how proprietary rights were holding things
back in the late 50s people at ibm developed the language called fortran they could have
kept it proprietary they could have said only ibm can use this language everybody else has to but but they didn't
they said anybody who can write who can translate fortran into the
into the language of their machines uh is allowed to make fortran compilers too
um on the other hand in the typography industry i had
seen a lot of languages that were developed for composing pages
and each manufacturer had his own language for composing pages
and that was holding everything back because people were tied to a particular manufacturer
and and then a new equipment is invented a year later but printing printing machines they have to
expect to amortize the cost over 20 30 years so you didn't want that for tech
i didn't need the income okay i already i i already had
uh a good job and you know
my books were people were buying enough books that i
that that it would bring me plenty of supplemental income for
everything my kids needed for education whatever so there was no reason for me to try to
maximize income any further income is sort of a threshold function
if you don't have if you don't have enough you're starving but if if you get over the threshold
then you start thinking about philanthropy or else or you're trying to take it with you but uh
but anyway there's a i had my income was over the threshold so
so that i i didn't need to keep it and so i specifically could see the advantage of
of of making it open for everybody do you think uh most software should be
open so i think that people should charge for non-trivial
software but not for trivial software yeah you give an example of i think
adobe photoshop versus on linux as photoshop has value which so
it's definitely worth paying paying for all the stuff i mean
and i mean well they keep adding adding stuff that just
that my wife and i don't care about but somebody does but i mean but they have
built in a fantastic uh uh undo feature for example
in photoshop where you you you can go through a sequence of a thousand complicated steps
on graphics and it can take you back anywhere in that sequence yeah
with really beautiful algorithms i mean yeah it's it's oh that's interesting i didn't think about what algorithm it
must be some kind of efficient representation really yeah i know i mean there's a lot of really subtle
nobel prize class like creation of intellectual property in in
there and uh
and with patents uh you've got a limited time to uh i mean eventually the idea of patents
is that you publish so that it's not secret it's not a trade secret
that said you you've said that i currently use ubuntu linux on a standalone laptop
it has no internet connection i occasionally carry flash memory drives between the machine and the macs that i
use for network surfing and graphics but i trust my family jewels only to
linux why do you love linux the version of linux that i use is
stable i i i actually i i'm gonna have to upgrade one of these days but
to a newer version of ubuntu yeah i'll stick with ubuntu but but uh right now i'm running
something that doesn't support a lot of the new software
the last stability i don't remember the number like 14 anyway it's it's quite
and i'm going to get a new computer um i'm getting new um solid-state memory
instead of kind of a hard disk and the basics well let me ask you
Favorite symbols
um sticking on the topic of tech um
when thinking about beautiful typography what is your favorite letter number or
symbol i know i know ridiculous question but is
there some let me show you there
or look at the last page
at the very end of the index what is that
there's a book by dr seuss called on beyond zebra and he gave a name to that
did you say dr seuss gave a name to that dr seuss this is uh s-e-u-s-s he he
wrote children's books in the 50s 40s and 50s
wait are you talking about cat in the hat doctor yeah that's it yeah i like how you hit this
on on beyond zebra did he did did it get to soviet union
[Laughter] yeah doctors no we did dr seuss did not come to the soviet
union but since you oh actually i think he did actually a little bit when we were
um that that was a uh his maybe cat in the hat or or green
eggs and ham i think was used to learn english oh okay so i think it made it
that way my my okay i i didn't like those as much
as bartholomew cubbins but but i used to know bartholomew covens by heart when i was
young so what the heck is this symbol we're looking at there's so much going on he has a name
for it at the end of his book on beyond zebra who made it he did he did
so there's it looks like a bunch of vines uh well is that symbol of existence
by the way he he made a movie in the early 50s um i don't remember the name of the
movie now you can probably find it on easily enough but it it features uh
dozens and dozens of pianos all playing together at the same time and but but the all the scenery is sort of
based on the kind of artwork that was in his books and uh the fantasy big
you know based of zeus land or so and i saw the movie only once or twice
but it's but it's quite i'd like to see it again
that's that's really fascinating that you gave him they gave him shout out here
okay is there some elegant basic symbol that you're attracted to some
uh give something that gives you pleasure something used a lot
pi pi of course uh i try to use pi
i as often as i can when i need a random example [Music]
because it doesn't have any known characters so for
so for instance i i don't have it here to show you but
do you do you know the put the uh the the game called masu m-a-s-y-u
no it's it it's a great recreation i mean
sudoku is easier to understand but matthew is it it is more addictive uh uh
you you have black and white stones like like on a go board and you have to draw a path that
goes straight through a white stone and makes a right angle turn at the black stone
um and it turns out to be really really nice puzzle because it
doesn't involve numbers but with this visual but it's 3d pleasant to to play with
so so i wanted to use it as example in art of computer programming and i have
i have exercise on how to design cool massive puzzles and uh you can find that on wikipedia
certainly uh as an example m-a-s-y-u um and and so i and so i decided i would
take pi the actual image of it and it
had pixels and i i would put a stone wherever it belongs in the letter pi in the greek
letter pi and and but the problem was find a way to make some of the stones
white some of the stones black so that there's a unique solution to the mossview puzzle
that was a good test case for my algorithm on how to design master puzzles because i i
insisted in advance that the stones had to be placed in exactly the positions that make the
letter pie make a juice letter okay all right that's cool and and
i saw you know and it turned out there was a a a unique way to do that
um and so so pi is a source of
of examples where i can where i can prove that i'm starting with something that isn't canned
and most most recently i was writing about something called graceful graphs
uh graceful graphs is the following you have a graph that has
m edges to it all right and you attach numbers to every vertex
in the following way so every time you have an edge between vertices you take the difference between those
numbers and and that difference is it's got to be
tell you what edge it is so so one edge two numbers will be one apart there'll be another edge where the
numbers are two apart and so uh great computer problem can you find a graceful
way to label a graph so i started with a so i started with a
graph that i use for an organic graph not not a
mathematically symmetric graph or anything and i take this i take the 49 states of the united states
uh the edges that go from one state to the next state so for example california be
next to oregon nevada arizona okay and and
and i include this district of columbia uh so i have 49 i can't get at la alaska
and hawaii in there because they don't touch you have to be able to drive from one to the other so is there a graceful
labeling of of the united states each state gets a number
and then if california is number 30 and oregon is number 11. that edge is going to be number
19. the difference between those right okay so is there a way to do this for for all
the states and at that and so i was i was thinking of having a contest uh
for people to to get it as graceful as they could uh but my friend tamara kiki
actually solved the problem by proving that i mean i was able i was able to get it down
within seven or something like that he was able to get a perfect solution the actual solution or to prove that a
solution exists more precisely i i had figured out a way to put labels on so that
all the all the uh all the edges were labeled somewhere between one and 117
but but there were some some get some gaps in there because i should really have gone from one to 105 or what the whatever the number is
so i gave myself too much you know a lot of slack he did it without any slack whatsoever a
perfect grace for labeling and and so i you know i call out the contest uh because the
problem is already solid and too easy in a sense because tom was able to do it in an afternoon
um he sorry he did the algorithm or for this particular uh for the stick united
states for the united states this problem is this problem is incredibly hard i mean for the general generally okay
but it's like it's like coloring but it was very lucky that we worked for the united states sure um i think but but i
mean the theory is still very uncomplete but but but anyway then tom came back a
couple days later and he had been able to not only find a graceful labeling but he
but the label of washington was 31. the label of
of idaho was 41 following the digits of pi
yeah going across the topic of the united states he has the digits of pipeline did he do it on
purpose he was able to still get a graceful labeling with that with
it's a miracle okay but yeah but um i i i
i like to use pie in my book you see and this is all roads lead to pie yeah somehow um
somehow often hidden uh in the middle of like the the most difficult problems
Productivity
can i ask you about uh productivity productivity yeah you said that quote my
scheduling principle is to do the thing i hate most uh on my to-do list
by week's end i'm very happy can you explain this process to a
productive life oh i see well but all the time i'm working out and what i want i what i don't want to do
but still i'm glad to have all those unpleasant tasks finished yes is that something you would advise to others
well i yeah i i i don't know how to say it
during the pandemic i feel my productivity actually went down by half um
because i have to um i have to communicate by
writing which is slow i have to i mean i i don't like to send out a bad sentence so i
you know i go through and reread what i've written and edit and fix it so so everything takes a long a lot longer
when i'm when i'm communicating by by text messages um
instead of just you know together with somebody in the room and it's also
slower because the libraries are closed and stuff but there's another thing about scheduling that i learned from my mother
that i should probably tell you and that is um it's different from what people in
robotics field do which is called planning so she had this principle
that was see something that needs to be done and do it
you know i would just instead of saying i'm going to do this first and do this first
just you know just do it oh yeah pick this up you know
but you're at any one moment there's a set of tasks that you can do and you're saying a good heuristic
is to do the the one you want to do least right the one i haven't got any good reason
i think that i'll never be able to do it any better than i am now
i mean there are some things that that i know if i do something else first i'll be able to do
that one better yeah but but but there's some that are going to be harder because you know
i i i i've forgotten some of the groundwork that went into it or something like that
so so i just finished uh a pretty tough part of the book and uh
and so and so now i'm you know doing the parts that are more fun but but but the the other thing is as
i'm writing the book of course i want the reader to think that i'm happy all
the time i'm writing the book i i'm you know that it's upbeat i i i can have humor i can you know i can i can say
this is cool you know wow this uh i have to i have to disguise the
fact that it was painful in any way to come up the road to that excitement is painful yeah
it's laden with pain okay is is there um you've given some advice to people before
but can you um can you you give me too too much credit but anyway this is my this is my turn to
just not to say things that that that i believe but but i want to preface it by saying um
i also believe that other people do a lot of these things much better than i do so i can only tell
you my side of it so
can i ask you to give advice to young people today to high school
students to college students whether they're geeks or the other kind
about how to live a life that they can be proud of how to have a successful career how to have a successful life
it's always the same as i've said before i guess not to
do something because you because it's trendy but but it's something that you personally
feel that you were called to do right rather than somebody else expects you to do
how do you know you're called to do something you try it and it works or you or it
took or it doesn't work i mean you you learn about yourself life is a binary search you try
something and you find out oh yeah i have a background that helped me with this or
or or maybe maybe i i could do this if i worked a little bit harder but you try something else and
you say wait i have really no intuition for this and it looks like uh
you know it looks like it doesn't have my name on it it was there advice along the way that
you got about what you should and shouldn't work on or do you just try to listen to
yourself yeah i probably overreacted another way when something when i see everybody else
do going some way i probably i i'd probably say not too much
competition but yeah but but uh
but mostly i i played with things that were interesting to me and then later on i found
oh actually the most important thing i learned was how to be interested in almost anything yeah i mean not to be
bored it hurts it makes me very sad when i when i see kids talking
to each other and they say that was boring
and to me a person should feel
upset if he would help if he had to admit that he wasn't able to find something interesting
so uh uh you know the skill they they say i haven't learned how to
how to enjoy life i have to have somebody entertain me instead of right that's really interesting it is a skill
uh david foster wallace i really like the thing he says about this which is
the key to life is to be unborable and i do really like you saying that
it's a skill because i think that's a really good that's really good advice which is if
you find something boring that's not i don't believe it's because
it's boring it's because you haven't developed i have learned how to how to find the beauty and how to find the fun
in it yeah that's a that's a really really good point you know sometimes it's
more difficult than others to do this but i mean during the covet
lots of days when i did when i never saw another human being but um
but i i i still find other ways to
it still was a pretty fun time yeah yeah i came earlier i came a few minutes
early today and i walked around foster city i didn't want you know i didn't know
what was going on in foster city i saw a beautiful some beautiful flowers at the nursery at home depot a few blocks away
life is amazing it's full of amazing things like this yeah i just sometimes i'll i'll sit there and just stare at a
tree nature is beautiful uh let me ask you the big ridiculous
question i don't think i asked you last time i have to ask this time in case you have a good answer what is the meaning of life
Meaning of life
our existence here on earth the whole thing [Laughter]
no no you can't you can't i will not allow you to uh to try to escape answering this question you have to
answer definitively uh because they're they're surely surely don knuth there must be an answer
what is the answer is it 42 or wherever yeah well i don't think it's the numerical that's that's
okay but all right so so anyway um it's only for me and
but i but i personally think of my belief that
that god exists although i have no idea what that means
but i believe that there is some
something beyond human uh capabilities
um and it might be uh uh it might be some ai
but but whatever it is but but whatever i but i do believe that
that there is something that goes beyond
the realm of human understanding but but that that i can
try to learn more about how to resonate with whatever that
being would like me to do so do you think you can have occasional glimpses of that being i
i strive for that not that i
ever think i'm going to get close to it but but it's not it's not for me it's it's saying what
should i do that that big being wants me to do that's that's you know i i'm trying to
ask what that
i mean does that being want me to to be talking to lex friedman right now you know and i said yes okay but thank you
well thank you but yeah what i'm trying to say is
i'm not trying to say what of all the strategies i could choose or something which one
i i try to do it not not strategically but i try to
to imagine that i'm following somebody's wishes even though
you're not smart enough to to know what they are yeah but that funny little dance well i i i
mean this ai or whatever is it probably is it is smart enough to help to give me
clues and uh
to make the whole journey from clue to clue a fun one yeah i mean it's as so many
people have said it's the journey not the destination and people live
live through crises help each other all these things come up
history repeats itself you try to say in the world today
is there any government that's working i i read history i i know that things were
they they were they were there were a lot worse in many ways there's a lot of bad things
all the time and i read about you know i i look at
things and people had good ideas and they were working on great projects and then i know that it didn't succeed though in the end
uh but but the new insight i've gotten him actually in that way was i i was reading
uh what what book was i reading now recently it was it was by ken follett and it was called
the man from saint petersburg but it but but it was talking about the prequel to
world war one and winston churchill according to this book uh sees that
that germany has been spending all its gold reserves uh building up a huge military
and there's no question that if germany would attack england that england would be wiped out
um so he wants russia to help uh to attack germany from the other side
because germany doesn't have enough of an army to to be fighting two wars at one
okay now then there's an anarchist in russia
who sees that wars are
something that leaders start but actually people get killed and so he
wants to stop any alliance between england and russia
because that would mean that a thousand thousand people of russia would would be killed that wouldn't be
otherwise killed all right and so his his life's goal
is to assassinate a russian prince who's visiting england
because that will make will mean the czar will not form the alliance all right
so we have this question about what should the government do
should it actually do something that will lead to you know is is the war inevitable or is
there a way to have peace and and this just did and it struck me that if i were
in a position of responsibility work for people's lives in most cases i wouldn't have i wouldn't
have any confidence that any of my decisions were good that that that these these questions are
too hard probably for any human being but certainly for me
well i think i think coupling the not being sure
that the decisions are right so that that's actually a really good thing
coupled with the fact that you do have to make a decision and carry the burden of that and
ultimately i have faith in human beings and the great leaders to arise
uh and help build a better world i mean that's the hope of democracy that's done
yeah enhance their abilities with uh
with algorithms [Laughter]
uh well put done it's such a huge honor i've you've been an inspiration to me and to millions for
such a long time um thank you for spending your really valuable time with me once again
it's a huge honor i really enjoyed this conversation thanks for listening to this conversation with donald knuth to
support this podcast please check out our sponsors in the description and now let me leave you with some words
from don knuth himself science is what we understand well enough to explain to a computer art is
everything else we do thank you for listening i hope to see you next time

