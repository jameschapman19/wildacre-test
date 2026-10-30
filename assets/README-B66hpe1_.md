# Soft ground

Load `?skins=skins/default,examples/soft-ground` to replace the map's ground-detail artwork independently of its palette, wildlife and simulation. This is a minimal public skin, not a renderer branch. It replaces the default material atlas with an 8×8 RGBA utility data tile whose every channel is 128; nearly centred detail has no visible grain. The tiny tile contains no external artwork.

Copy this pack and point `ground_detail` at your own pack-relative static PNG. Channels are fine grass (R), coarse grass (G), soil (B), gravel (A), with neutral detail around 0.5. The shader reads channels as data, not a transparent picture or habitat colour. The default atlas's sources and licence are recorded in `assets/MANIFEST.md`.
