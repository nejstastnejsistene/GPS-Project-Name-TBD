GPS-Project-Name-TBD
====================

An ambitious project idea I dreamt up while hiking in the [beautiful mountains of Norway](https://www.google.com/search?q=besseggen&tbm=isch) one summer. This project is essentially described in [this article](http://www.navsys.com/In%20the%20News/NAVSYS_GNSS_Signal_Simulator_GPS_World_May_2012.pdf), but I'd like to replace the [GPS Signal Architect](http://www.navsys.com/products/signal_architect_simulator_software.htm)/[SatGen Scenario Simulator](http://www.labsat.co.uk/index.php/en/products/satgen-simulator-software) with my own software.

#### Input
- Almanac of current GPS constellation information ([current almanac available here](http://www.navcen.uscg.gov/?pageName=currentAlmanac&format=sem)).
- GPX trip data (i.e., an ordered list of `(position, elevation, timestamp)` pairs).

#### Output
- GPS radio transmission that would convince a stationary GPS receiver that it is travelling along the path described by the trip data input.

#### Components
- Simulate GPS orbits given almanac data.
- Simulate GPS satellite broadcasts given almanac data.
- Encode satellite signals with PRN and then modulate onto carrier frequency (checkout [GNU Radio](http://gnuradio.org/)).
- Determine which satellites are visible from a given location.
- Figure out what a GPS signal "looks like" given that both the satellite and receiver are move.
  - Need to estimate how long the transmission takes to arrive. It travels through both space and the atmosphere.
  - Timing is especially important because it's used for [trilateration](https://en.wikipedia.org/wiki/Trilateration) so a few milliseconds could make big differences in accuracy.
  - Note that the satellite, the Earth, and the GPS receiver are moving.
  - Might need to take into account the Doppler effect and/or [general and special relativity](http://www.astronomy.ohio-state.edu/~pogge/Ast162/Unit5/gps.html).
- Sum the generated signals (again, [GNU Radio](http://gnuradio.org/)) for the whole trip and put it through a [USRP](https://en.wikipedia.org/wiki/Universal_Software_Radio_Peripheral) ($$$$$)
  - I'll probably want to do this in a Faraday cage so I don't [commit any felonies](http://www.cnet.com/news/truck-driver-has-gps-jammer-accidentally-jams-newark-airport/).

#### Name ideas
I'm looking for a play on the idea that this project "moves the Earth" around the GPS receiver, instead of the usual moving the GPS receiver around the Earth.

- Aristarchus (first astronomer to realize the Earth moves around the Sun and not the other way around)
- Some reference to Carole King ([I love this song](https://www.youtube.com/watch?v=wbQ4m-NqeF8))
- Gjende/Besseggen (The lake and mountain that I think was hiking on when I came up with this project)
