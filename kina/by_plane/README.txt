DATA:           2013 Labor Day Flight tracks
SOURCE:         Public web site
CLASSIFICATION: None (but follow scraper ethics)
WRANGLER:       Craig Ulmer / cdulmer@sandia.gov

INFO:

Over the labor day weekend, I set an offsite machine to
scrape data from a popular flight-tracking service. I
grabbed a full dataset every 6 minutes, from about 8am
to 11pm Pacific. The original captures have a good bit
of info (plane type, src/dst, ETA, altitude change). 
This dataset is reformatted to track specific planes
over time. As such, you'll notice that in several of
the tracks, a plane lands, waits, and takes off again.

The data is arranged so that a flight is listed, followed
by multiple track points. A single track looks like this:

FLIGHT	 8A02F1 	 MES	DPS
1377742574	3.598300	98.862700	1750
1377742937	3.273100	99.253600	14925
1377743300	2.814900	99.778800	26775
1377743665	2.259600	100.320700	34600
1377744022	1.701400	100.802500	35000
1377749104	-6.559300	106.808200	23750
1377749456	-6.804200	107.342200	12475
1377749828	-6.984500	107.729700	5925
1377750124	-6.897800	107.568200	0

The FLIGHT line is the record header and has basic info:
FLIGHT  : just a marker to signify a new record
8A02F1  : an id for a plane
MES/DPS : Airport codes used for src/dst at some point 
          in the flight. Note: likely to only be one
          leg of the journey.

The track data is:
int64   : Seconds since epoch that data was captured
float   : Latitude
float   : Longitude
int     : Altitude (ft)

   
