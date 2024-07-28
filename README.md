# OsmAndRailwayStyles
Railway-focused offline map styles for the OsmAnd App (https://osmand.net/) adapting the colour scheme of OpenRailwayMap (https://www.openrailwaymap.org/).

<div>
<img src="https://github.com/fuzzysolutions/OsmAndRailwayStyles/blob/master/Screenshots/praha v1.png" alt="Screenshot of v1.0" width="300" hspace="10"/> 
<img src="https://github.com/fuzzysolutions/OsmAndRailwayStyles/blob/master/Screenshots/leipzig - v2.png" alt="Screenshot of v2.0" width="300" hspace="10"/>
</div>

# Status of Development
In v2.0, I realised line styling as well as line labeling. I will later add nodes their labels.

Feel free to contribute. Note that I copied some snippets of interest from the OsmAnd default style in order to work on them later.

# Setup
1. Download the [latest release](https://github.com/fuzzysolutions/OsmAndRailwayStyles/releases/latest) of the RailwayInfra.render.xml file
2. Open OsmAnd menu&mdash;"Maps and Resources"&mdash;"Local"&mdash;"Display Styles"
3. Open the 'three dots' menu to the top right&mdash;"Import"&mdash;Navigate to the file and import it
4. Open OsmAnd menu, choose "Configure Map"&mdash;"Map Style" (you need to scroll down a bit, to find "Map Style") and select "RailwayInfra"

# Visible Features
Not every topic of interest for railway mapping is contained within the standard *.obf files provided by OsmAnd.
This map style is designed to work with the standard maps, so many features had to be omitted.

You can create your own *.obf files with the features you're interested (https://osmand.net/help-online#map_creator) and adapt this style.

The list below shows some OSM keys of interest (compare https://wiki.openstreetmap.org/wiki/OpenRailwayMap/Tagging) and whether they are included into standard *.obf files, altered or not included.
Note that many keys (e.g. `service`) are taken to the detailed maps only, the generalized "World Base Map" contains almost bare `railway` lines.

Key | Value | Included? (+ Comment)
--- | ------| ----------
`railway` | `rail, narrow_gauge, tram, light_rail, subway, miniature, funicular, monorail, abandoned, disused, construction, proposed` | Yes
`railway` | `preserved` | Yes, but this key/value is actually not recommended to use as no other information on the type of railway can be stored then. Recommended tagging is `railway:preserved=yes`, but OsmAnd prefers this one, see below.
`railway` | `razed, dismantled` | Is converted to `railway=abandoned` under obf creation.
`railway:xxx` | _any_ | Generally, sub-tags of railway are not included.
`railway:preserved` | `yes` | Is converted to `railway=preserved` which means that other information on the railway type is being overwritten.
`railway` | `platform` | Is converted to `public_transport=platform`
`service` | `spur` | Yes
`service` | `crossover, siding` | Is converted to `service=spur`
`service` | `yard` | No
`usage` | _any_ | No (which is quite sad)
`highspeed` | _any_ | No (workaround with Maxspeeds over 160?)
`electrified` | `rail, contact_line` | Is converted to `electrified=yes`.
`frequency` | _any_ | No
`voltage` | _any_ | No
`rack` | _any_ | No
`maxspeed` | _any_ | Yes
`railway` | `buffer_stop, crossing, halt, level_crossing, station, yard, subway_entrance, tram_stop, turntable` | Yes
`railway` | `switch, signal` | No
`bridge, tunnel` | _any_ | Yes
`landuse` | `railway` | Yes
`operator` | _any_ | Yes, but may overlap with `route=*` operators


# License
This code is licensed under GPLv3.
It contains some Code from the OsmAnd Default style (prepared to alter it according to railway map display) and some parts of the OpenRailwayMap colour scheme, both licensed under GPLv3.
