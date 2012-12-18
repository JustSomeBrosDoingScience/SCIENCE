#Challenges faced by Mars Aerobots

Some notes on the challenges faced by Martian Aerobots in contrast to Dave
Barnes' notes on [Challenges faced by titan aerobots](http://www.aber.ac.uk/~dcswww/Dept/Teaching/CourseNotes/current/CS36510/Titan%20Aerobot%20Notes.pdf).

In no particular order:
* *Entry Descent and Deployment (EDD)* - more is known about the surface of Mars
  than the surface of Titan in general. There are quite a lot of suitable
  landing spots in the Northern hemisphere of the planet, although the southern
  hemisphere is cratered and more dangerous to land on. Deployment after
  landing is potentially a better option than deployment during descent. Mars
  has a significantly thinner atmosphere than Earth (less than 1% relatively
  speaking) and gravity is approximately 1/3rd of the strength of Earthern
  gravity on the planet. Lower gravity means less lift is required to get a
  balloon airbourne but a less dense atmosphere means a larger envelope is
  required.
* *Localisation* of a Martian aerobot presents significantly less of a
  challenge than on titan. There are several comprehensive maps of the martian
  surface since the atmosphere is a lot easier to penetrate. Therefore,
  terrain-based localisation is an option. The problem of Martian localisation
  has already been solved very effectively using NASA'S MER Localisation
  solution. The algorithm developed by Ron Li is used to capture stereo images
  of terrain and process this data to extract 'interesting points.' The rover
  then circles the rocks gathering more image data of the same rocks from
  different angles and storing data on each rock to form an *analytical rock
  model.* The rover can use rock matching before and after traversing different
  rock distributions and localise itself relative to each site in it's memory.
* Navigation
* Communication
* Longevity and survivability
