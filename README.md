nfAddon
=======

Simple, statically-embedded World of Warcraft addon framework


Facilities
----------

nfAddon provides the following facilities:

- Will initialize your global namespace for you (named exactly as your addon folder name). No need to create some `init.lua` file filled with generic boilerplate. Provides some useful constants in that namespace: `.name`, `.version` (if found in TOC), `.path`, `.debuglog` (array of messages written to `:debug()` with timestamp).
- Provides API for registering events, timers and OnUpdates to callbacks, to reduce the boilerplate associated with setting up frames for these tasks. 
- Provides the following APIs that's generally useful for every addon: `:print()`, `:debug()` [write message to a debug log], `:argcheck()`, `:softerror()`. 


Why statically embedded?
------------------------

- Does not incur the nasty execution cap incidentally. Since each addon has its own event handler, one addon using up too much CPU time on an event like CLEU will not prevent other addons' callbacks from firing. 
- Accurate CPU profiling. Since all handlers are isolated per-addon, one addon cannot be "blamed" for the CPU usage of other addons just because its embedded copy of the lib got loaded first, like with Ace. 
- Why not? The design is simple, and the overhead is miniscule. 
- Think of nfAddon more as an addon stub with some included facilities, and it makes sense. I'm not trying to make the next Ace, because Ace is already good. I'm trying to go the simpler, less feature-packed route, because I find it more comfortable for smaller addon projects. 


Documentation
-------------

- Read the source. It's small, generously formatted and easy to understand. There's only a handful of functions to look at, and they're all pretty obvious. 
