# HIMALAYAN AIRFIELD — FINAL SUBMISSION RULES

## PROJECT

Unity project: HimalayanAirfield
Unity version: 6.0.58f2
Render Pipeline: URP
Main gameplay scene: 02_Airfield
Main menu scene: 01_MainMenu

This project is under an extremely tight submission deadline.

The goal is NOT to redesign the project.

The goal is to transform the existing working project into a polished, lively, submission-ready Himalayan airport/flight game as quickly and safely as possible.

---

# ABSOLUTE SAFETY RULE

Existing working gameplay must NOT be broken.

Before modifying anything:

1. Locate the actual 02_Airfield scene file.
2. Duplicate ONLY the `.unity` scene into a new scene called:

`02_Airfield_Final.unity`

Do NOT duplicate/copy the original `.meta` file.

Allow Unity to generate a unique meta/GUID for the duplicated scene.

All major environment and airport-life changes must be made to the FINAL scene.

The original 02_Airfield scene must remain available as a working backup.

---

# WORKING SYSTEMS — PRESERVE

Do NOT rewrite, replace, redesign or significantly refactor these working systems unless compilation absolutely requires it:

* HybridAircraftController
* AircraftEffects
* PlaneOrbitCamera
* player aircraft enter/exit system
* aircraft engine/throttle system
* aircraft takeoff
* aircraft flight
* aircraft landing
* aircraft crash/reset
* aircraft audio
* existing player FPS controller
* existing AirportShuttleController
* existing BusDoorController

Do not attach player aircraft scripts to NPC aircraft.

Do not alter player aircraft handling values.

Do not replace the existing player aircraft.

---

# CURRENT WORLD

The game already contains:

* Himalayan airfield
* terminal
* hangar
* control tower
* runway
* taxiway
* apron
* runway/taxiway lights
* working player
* working player aircraft
* working airport shuttle
* nine connected terrain tiles
* mountain flight environment
* predefined flight-route guide objects

The terrain layout and mountain sculpting are considered complete.

Do NOT regenerate the terrain.

Only decorate it.

---

# AVAILABLE CHARACTER ASSETS

Existing character prefabs can be found under the project's character prefab folders.

Visible available character types include:

* Beach
* Casual
* Casual_2
* Formal
* Suit

Use these for civilians/passengers/airport visitors.

Reuse characters where necessary with randomized:

* scale
* rotation
* clothing/prefab choice
* starting positions

Do not create complex character customization.

---

# AVAILABLE TREE ASSETS

A free tree package exists under approximately:

`Assets/Darth_Artisan/Free_Trees/Prefabs`

Available tree prefabs include:

* Fir_Tree
* Oak_Tree
* Poplar_Tree
* Palm_Tree

For the Himalayan environment:

USE:

* Fir_Tree
* Oak_Tree
* Poplar_Tree

DO NOT use Palm_Tree unless a later instruction explicitly asks for it.

---

# AVAILABLE AIRCRAFT ASSETS

Extra aircraft prefabs/models exist under approximately:

`Assets/ThirdParty/Aircraft`

Visible aircraft include:

* basicPlane
* stuntPlane

The existing PLAYER aircraft remains unchanged.

Additional aircraft created for background airport traffic MUST use a new lightweight NPC traffic controller.

They must NOT use HybridAircraftController.

---

# FINAL GAME TARGET

The final game should feel like an active small Himalayan airport.

Required final features:

1. lively airport traffic
2. passenger activity
3. shuttle passenger transport
4. multiple background aircraft
5. background aircraft takeoff/flying/landing loops
6. forests around the mountain terrain
7. scenic ponds/lakes
8. environmental decoration
9. simple player flight mission
10. polished but performant presentation
11. stable final Windows build

---

# NPC AIRCRAFT TRAFFIC

Create FIVE background NPC aircraft.

These are NOT physics aircraft.

They should use lightweight deterministic waypoint/path movement.

Each aircraft should have a staggered schedule so they do not all move together.

The visual lifecycle should be:

PARKED
→ BOARDING
→ TAXI OUT
→ RUNWAY
→ TAKEOFF
→ CLIMB
→ MOUNTAIN FLIGHT LOOP
→ APPROACH
→ LAND
→ TAXI IN
→ PARK
→ WAIT
→ REPEAT

Create broad smooth waypoint routes.

Movement should visually interpolate position and rotation.

Takeoff/climb/approach should be represented with 3D waypoints of increasing/decreasing altitude.

Avoid sudden rotations.

Avoid teleporting aircraft while visible.

NPC aircraft should ignore physics and must not interfere with the player aircraft.

Where practical, disable unnecessary colliders on airborne NPC traffic.

Create staggered starting delays so at any moment the player can see different aircraft performing different operations.

Approximate desired activity:

* one parked/boarding
* one taxiing
* one taking off or climbing
* one flying through the valley
* one returning/landing

Do not require perfect real-world ATC simulation.

Visual believability and stability are more important.

---

# AIRPORT PASSENGER LIFE SYSTEM

Create reusable simple passenger NPC behaviour.

Do NOT build an overly complicated AI framework.

Use a deterministic state machine.

Desired passenger lifecycle:

WAIT_AT_TERMINAL
→ WALK_TO_BUS
→ BOARD_BUS
→ RIDE_BUS
→ EXIT_BUS
→ WALK_TO_ASSIGNED_PLANE
→ BOARD_PLANE
→ FINISHED/HIDDEN

Passengers should visibly walk while outside vehicles.

When a passenger reaches the bus door:

* hide or attach them inside the bus
* do not simulate walking through the bus interior

When the bus reaches an aircraft:

* passengers appear at appropriate bus exit positions
* walk toward aircraft boarding points
* when reaching aircraft boarding point, hide them and mark them boarded

This is visual simulation.

Do not create complex seating systems.

Use groups of approximately 3–6 passengers.

Use the existing character prefabs.

---

# AI SHUTTLE

Do NOT destabilize the existing working player's airport shuttle.

Prefer duplicating the shuttle visuals/hierarchy into a separate:

`AirportServiceBus_AI`

Create a dedicated simple waypoint shuttle controller for airport-life simulation.

AI shuttle loop:

TERMINAL
→ wait
→ passengers board
→ drive to active aircraft stand
→ wait
→ passengers exit
→ return to terminal
→ repeat

Use smooth waypoint steering.

The AI shuttle should never enter:

* runway
* player aircraft spawn
* player taxi path
* buildings

---

# FOREST GENERATION

Create an Editor tool for controlled terrain vegetation placement.

Prefer Unity Terrain tree instances rather than hundreds/thousands of individual tree GameObjects where practical.

Use:

* Fir_Tree heavily
* Oak_Tree moderately
* Poplar_Tree sparingly

Generate natural clusters rather than uniform grids.

Rules:

* dense vegetation on lower mountain slopes
* moderate vegetation on valley edges
* sparse vegetation at high elevation
* no trees on steep exposed cliffs
* no trees on runway
* no trees on taxiway
* no trees on apron
* no trees inside terminal/hangar
* preserve the main flight corridor

Use deterministic random seeds so generation can be reproduced.

Keep total vegetation reasonable for performance.

Do not fill every square metre with trees.

---

# WATER / PONDS

Create 2–3 scenic ponds/lakes in appropriate open terrain areas away from the airport infrastructure.

Use a simple lightweight URP-compatible water solution.

If no water asset exists:

* create a simple water plane/mesh
* generate/use a transparent blue-green URP material
* mild smoothness
* mild transparency
* no expensive simulation

Decorate pond borders using available:

* trees
* vegetation
* rocks if available

Do not create swimming mechanics.

Water exists as scenery and flight landmarks.

---

# PLAYER MISSION

Implement one simple flight mission.

Mission sequence:

1. Go to / enter the player aircraft.
2. Start flight.
3. Take off.
4. Fly through a short series of mountain checkpoint zones.
5. Return toward Himalayan Airfield.
6. Enter the landing zone.
7. Land successfully.
8. Display MISSION COMPLETE.

Use the existing flight-route guide objects where useful.

Mission UI should be small and readable.

Example objective text:

`OBJECTIVE: Take off from Himalayan Airfield`

then

`OBJECTIVE: Fly through Mountain Checkpoint 1`

then

`OBJECTIVE: Return to Himalayan Airfield`

then

`MISSION COMPLETE`

Avoid changing player aircraft scripts unless absolutely necessary.

Prefer independent trigger/checkpoint components.

---

# POLISH

Add modest environmental life where inexpensive:

* trees
* ponds
* rocks
* airport passengers
* moving background aircraft
* shuttle traffic
* appropriate ambient objects

Do not add:

* helicopters
* multiplayer
* economy
* dialogue systems
* weapons
* complex ATC
* weather simulation
* second full airport
* new player flight physics
* giant new frameworks

NO FEATURE CREEP.

---

# PERFORMANCE

This is a college submission.

Prioritize:

1. stability
2. visual impression
3. smooth gameplay
4. simplicity

Avoid huge runtime allocations.

Avoid thousands of independent animated GameObjects.

Use pooling/reuse where useful but do not overengineer.

Do not install unnecessary packages.

---

# UNITY EDITOR AUTOMATION

Where scene generation would require many repetitive manual steps, prefer writing a Unity Editor tool.

Preferred location:

`Assets/Project/Editor/`

Create a tool/menu such as:

`Himalayan Airfield/Build Final Airport`

The tool may:

* create NPC aircraft
* create NPC routes
* create AI shuttle
* create passenger spawn/wait/boarding points
* populate trees
* create ponds
* create mission checkpoints
* organize generated objects under clean parent GameObjects

Generated hierarchy should be organized approximately as:

`FINAL_AirportLife`
`FINAL_NPCAircraft`
`FINAL_Passengers`
`FINAL_AIShuttle`
`FINAL_Environment`
`FINAL_Forests`
`FINAL_Ponds`
`FINAL_Mission`

The builder MUST detect existing generated objects and avoid duplicating them every time it runs.

Make generation idempotent where possible.

---

# SAFE SCENE EDITING

Prefer Unity Editor APIs for major scene modifications rather than manually performing risky YAML surgery.

If the Unity executable can be reliably discovered, it is acceptable to run Unity in batch mode to execute an Editor builder.

If Unity cannot be run automatically:

create the Editor builder and clearly tell the user the SINGLE menu command they must click.

Do not pretend scene generation ran if it did not.

---

# FINAL ACCEPTANCE TEST

Before declaring work complete:

* project compiles
* no new serious Console errors
* player still moves
* player aircraft still works
* player can enter aircraft
* engine works
* aircraft can taxi
* aircraft can take off
* aircraft can fly
* aircraft can land/reset
* NPC planes visually cycle
* NPC passengers visibly move
* AI shuttle cycles
* forests exist
* ponds exist
* mission checkpoints work
* objective UI updates
* scene remains performant

Finally provide:

1. exact files created
2. exact files modified
3. remaining manual Unity steps
4. any Inspector references that still need assigning
5. known limitations
6. shortest final test procedure

Do not continue inventing features after these requirements are met.
