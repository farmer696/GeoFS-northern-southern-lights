I though it would be cool to have a northern lights addon for GeoFS and i didnt find any and didnt find anyone making one, so i made my own...


GeoFS Aurora is a userscript for Tampermonkey (or any userscript manager) that adds northern and southern lights to GeoFS. In its default mode it puts the aurora where it is actually happening on Earth right now. You can also switch to a custom mode and build your own shape. 


What you see
The aurora is drawn as tall, glowing curtains in the night sky, floating 100 km up. The tops reach 230–450 km in live mode, depending on how active the aurora is.
Colour by altitude: the bottom edge has a thin pink fringe and is sharp and bright. Above it is a green body (the classic aurora colour), with violet and a faint red tint toward the top.
Motion: the curtains fold back and forth, giving broad bright and dark bands. Fine vertical rays drift along them, each reaching a different height. The whole thing pulses slowly and flickers slightly.
Edges: the ends of each curtain fade out softly.
Horizon: the globe hides curtains that are below the horizon, so distant ones sit low and half-hidden, as in real life.
Live mode (default)
Data source: it downloads NOAA’s aurora nowcast (the OVATION model), a world grid of aurora probability. It refreshes every 10 minutes.
Placement: around your camera it searches in 120 directions, out to 1100 km, for the strongest aurora in each direction. It then connects the strong spots into curtains that follow the real auroral oval. Up to 4 curtain sections are drawn, each with a second, fainter layer just poleward of it.
Strength: stronger activity makes taller, brighter curtains.
Where you’ll see it: if you’re near the oval, for example over northern Canada, Alaska, Iceland or Scandinavia, it appears in the real direction and distance. At mid-latitudes on a quiet night you’ll see nothing, because nothing is there to see.
Fallback: if GeoFS blocks the NOAA request, it uses a rough estimate of the oval (about Kp 3). The panel says “Estimated oval” when that happens.
Night only
The aurora fades in as the sun drops between 4° and 12° below your horizon and is hidden in daylight. This uses the Cesium clock. If GeoFS doesn’t drive that clock, the sun check may not match the in-game time, so I haven’t confirmed this works. The Show in daylight option overrides it.


Custom mode (Live unticked)
Custom mode ignores real data and places a shape of your choice relative to you.
Shapes: curtain, arc, ring, spiral, wave.
Direction: poleward, north, east, south, west, or “where I’m looking”.
Distance: 80–800 km.
Size: 0.3×–3×.
Height: 200–500 km.
Layers: 1–3.


Controls
Bottom-bar button: a moon icon that opens a popover.
Bonsai settings: a section is added if you use Bonsai UI.
Floating button: a small button appears if neither of the above is found after about 3 seconds.
Alt+A: toggles the aurora from the keyboard.
Brightness slider: 10%–150%.
Status lines: they show the data source and forecast time, how many curtains are in range and how far away the nearest is, and whether the sun is up.
Console commands: GeoFSAurora.toggle(), .enable(), .disable(), .rebuild(), .probe(), .destroy() and .cfg for tweaking values.
Your settings are saved in the browser and restored next time. Reinstalling or re-running the script cleans up the old copy first.
Under the hood
Rendering: the curtains are Cesium wall shapes with a custom shader, blended additively so they glow. They are depth-tested against the globe, which is why the horizon hides them.
Rebuilds: they are rebuilt when you move more than 60 km, when new data arrives, or when you change mode or shape settings.
Performance: GeoFS only redraws on demand, so the script asks for a redraw every frame while enabled. That adds a small constant cost.
Lightning script: it uses its own IDs and storage key, so it can run alongside your lightning script.
Limits
It needs internet access to services.swpc.noaa.gov for real data.
OVATION is a probability forecast for roughly the next 30 minutes, not a photograph.
Curtains can visibly pop when they rebuild after a long flight.
GeoFS clouds aren’t specially handled. The aurora sits far above them and is drawn through them like any distant object.

