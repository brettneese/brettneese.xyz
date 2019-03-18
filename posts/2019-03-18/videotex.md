Tags: art, shorts, research, hackery, ideas

# Shorts: Videotex 

From [Wikipedia](https://en.wikipedia.org/wiki/Videotex): 


	Videotex (or "interactive videotex") was one of the 
	earliest implementations of an end-user information system

Videotex is interesting to me, not just because of its aesthetic qualities, but because it attempted to adapt existing systems -- the broadcast TV and telephone systems -- to new, interactive uses. 

Several systems of interest are:

- [Minitel](https://en.wikipedia.org/wiki/Minitel) in France, by far the most popular and widely adopted system. It was unique in that it was somewhat decentralized.
- [Prestel](https://en.wikipedia.org/wiki/Prestel) in the UK, which was operated by the General Post Office. It has some really intriguing implementation details outlined on the Wikipedia page.
- [Viewtron](https://en.wikipedia.org/wiki/Viewtron) in the US, which was operated by AT&T and Knight-Ridder publishing. It was a dismal failure, but produced an aesthetic af video:

https://www.youtube.com/watch?v=sgYkpk9nJnE&app=desktop

The Viewtron interface, in particular, is intriguing to me. It used a language called [NAPLPS](https://en.wikipedia.org/wiki/NAPLPS), an extremely low-bandwidth graphics language that could produce complex graphics using terse object commands. I would love to get my hands on an implementation of this language and do something with it. 

Another interesting avenue of research is the Singapore [Teleview system](https://en.wikipedia.org/wiki/Singapore_Teleview), which transmitted imagery via "Full Field Teletext transmissions from dedicated data inserters/UHF TV Transmitters." My understanding is this means imagery was transmitted the same way TV signals were transmitted! I'd love to reimplement this. 

Finally, [TELSTAR](https://glasstty.com/wiki/index.php/The_TELSTAR_Videotex_System) seems to be a re-implementation of a PRESTEL-like server, which can apparently be accessed fromRISC OS running on a Raspberry Pi (another thing I learned, Raspberry Pis can run RISC OS.) Another project might be building a traditional modem interface to a system like TELSTAR on top of Twilio or similar. 