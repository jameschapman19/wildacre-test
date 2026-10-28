# Independent logical and appearance packs

`heathland` adds a tenth land type through normal habitat conditions. `heathland-skin` supplies just its colour. Load the logical pack beside core and the appearance pack above the default skin. Neither duplicates the base estate, its rule profiles or its palette.

This is an original API example, not a calibrated heathland model. It approximates nutrient-poor, relatively dry, open dwarf-shrub vegetation using the existing generic shrub layer; it does not model heather species, acidity, fire or soil chemistry. The classification numbers demonstrate the format. Real heathland dynamics would need additional ecological detail and sources before being used in a balanced scenario.

Logic and appearance are independent: changing the companion colour leaves every simulation hash unchanged. Removing the companion skin produces a missing-appearance validation error for the new land type. Removing the logical pack produces an unsatisfied skin dependency. A logical mod can also edit an existing definition through explicit manifest replacements (see docs/modding.md).

Run the logical example headlessly from the repository root:

```sh
cargo run --release -p sim-cli -- --content content/core --content content/examples/heathland --years 30
```

For the web build, append `?content=core,examples/heathland&skins=skins/default,examples/heathland-skin` to its URL. The values select bundled pack roots under `/content`; the loader discovers them from the build's content files. Add a folder with a manifest to bundle another pack without changing loader code. Appearance layer order is explicit; content dependencies determine logical order.

`wildlife-coats` is an appearance-only example for an existing species: append `?skins=skins/default,examples/wildlife-coats` to change fox coat/scale while preserving the simulation and replay. Logical add-ons can supply the same optional illustration tables for their new species.

`fox-art` replaces the default fox PNG with an original silver-grey coat variant. Append `?skins=skins/default,examples/fox-art`; the state hash and replay remain unchanged. A skin can use the same `sprite` field for added species, herd kinds or group fallbacks. The PNGs and their Canvas generation source are original project content.


## Added management choices

`estate-tools` adds a regime and a water tool using the existing Hands-off and drain-blocking effects. `estate-tools-skin` supplies the added regime's colour independently. This is an example of extending the command palette with data; neither definition needs a renderer or UI special case.

Use `?content=core,examples/estate-tools&skins=skins/default,examples/estate-tools-skin` in the web build. Open Manage estate: Land includes Meadow recovery along the upper valley, and Water includes Floodplain drain works. The new actions use the same quotes, unlock validation and replay commands as core choices. The long regime name also exercises ordinary palette layout. The companion skin can be edited without changing the simulation's identity.

`valley-grazers` adds a managed herd kind using existing pony effects. Load `?content=core,examples/valley-grazers&skins=skins/default,examples/valley-grazers-skin` to give it an independent coat. The map figures, selectable herd standard and unit card share that appearance. Without the companion skin, the existing herd/animal fallback is used; ecological definitions and replays are unchanged by the skin choice.
