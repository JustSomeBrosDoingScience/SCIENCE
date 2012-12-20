#Challenges faced by Mars Aerobots

Some notes on the challenges faced by Martian Aerobots in contrast to Dave
Barnes' notes on [Challenges faced by titan aerobots](http://www.aber.ac.uk/~dcswww/Dept/Teaching/CourseNotes/current/CS36510/Titan%20Aerobot%20Notes.pdf).

In no particular order:

## Entry Descent and Deployment (EDD)

More is known about the surface of Mars than the surface of Titan in general.
There are quite a lot of suitable landing spots in the Northern hemisphere of
the planet, although the southern hemisphere is cratered and more dangerous to
land on. Deployment after landing is potentially a better option than
deployment during descent. Mars has a significantly thinner atmosphere than
Earth (less than 1% relatively speaking) and gravity is approximately 1/3rd of
the strength of Earthern gravity on the planet. Lower gravity means less lift
is required to get a balloon airbourne but a less dense atmosphere means a
larger envelope is required.

## Localisation

Localisation of a Martian aerobot presents significantly less of a challenge
than on titan. There are several comprehensive maps of the martian surface
since the atmosphere is a lot easier to penetrate. Therefore, terrain-based
localisation is an option. The problem of Martian localisation has already been
solved very effectively using NASA'S MER Localisation solution for rovers. A
variation on this technique could be build models of rock formations from above
the surface of the planet and use images of the terrain below to determine
where the aerobot currently is.

## Navigation

Navigation for a martian aerobot should be quite straight forward in terms of
current location and determination of a target location. However, propulsion
technology would be significantly more challenging to set up. Mars' thin
atmosphere means that a very large envelope would be needed for a balloon-based
aerobot or alternatively a high-yield motor or engine would need to be running
constantly on a fixed wing aircraft. 

## Communication 


Like on titan, an aerobot on Mars would also have trouble communicating with
Earth. There is a 9 minute time delay between Mars and Earth meaning that
realtime communication is not possible. There are also power concerns since
long range communications are very power hungry. Such comms are usually
offloaded to an orbiter by rovers. However, the mobile nature of an aerobot
makes communication with an orbiter more difficult. One possible solution could be
to deploy an array of orbiters so that the aerobot could communicate with the
closest device. Alternatively, a geo-stationary orbital device could be set up
and the aerobot could return to the orbiter when it needed to communicate with
earth.

## Longevity and survivability

The relative longevity and survivability of a martian aerobot in comparison to
a rover would be significantly shorter. A fixed wing aerobot would need
constant energy to keep moving in the thin atmosphere of Mars. Even with the
addition of Solar Panels, such a device owuld not be able to collect/generate
as much energy as it was using during its motion. An LTA balloon-based aerobot
could last for significantly longer than a fixed wing aerobot provided that
leakage from the envelope was minimal. There would still need to be a way of
collecting or generating energy since high-capacity batteries and RTG systems
are very heavy and would weigh an LTA device down significantly.
