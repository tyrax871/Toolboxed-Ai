# BIM Architecture Plan

## Architecture-first foundation

Architecture defines the primary spatial and geometric structure of the building. All other systems attach to, reference, analyse, or coordinate against this foundation.

## Core model entities

| Group | Entities |
|---|---|
| Project | Project, Site, Building, Phase, Stakeholder |
| Spatial | Level, Grid, Zone, Room, Space |
| Architecture | Wall, Floor, Roof, Ceiling, Door, Window, Opening, Stair |
| Components | Fixture, Appliance, Joinery, Component |
| Information | Material, Specification, Annotation, View, Sheet, Schedule |
| Coordination | System, Connection, Issue, Clash, Change Request |
| Governance | Revision, Approval, Permission, Audit Event |
| Construction | Work Package, Task, Inspection, Defect, Progress Record |

## Architecture model scope

The initial model must support:

- Site boundary, orientation, survey references, setbacks, and constraints.
- Levels, grids, reference planes, and project coordinates.
- Rooms and spaces with names, areas, zones, finishes, and occupancy information.
- Walls, floors, slabs, roofs, ceilings, openings, doors, and windows.
- Materials and assemblies with properties and specifications.
- Fixtures, appliances, joinery, stairs, and other architectural components.
- Existing, retained, demolished, new, proposed, relocated, temporary, and superseded statuses.
- Relationships between elements, rooms, levels, views, sheets, and documents.

## View browser

Required generated views include:

- Site Plan
- Floor Plan
- Roof Plan
- Elevations: North, South, East, and West
- Sections
- Reflected Ceiling Plan
- Electrical Plan
- Plumbing/Drainage Plan
- Details
- 3D/Perspective View
- Isometric/Axonometric View
- Demolition Plan
- Proposed Plan
- Landscape Plan

Views are outputs of the model. They must retain links to the model elements they display.

## Overlay systems

| System | Primary relationships |
|---|---|
| Structural | Walls, floors, roofs, openings, loads, trusses, footings, and ground conditions |
| Electrical | Rooms, ceilings, lighting, power, data, smoke detection, and equipment |
| Plumbing and drainage | Wet rooms, fixtures, supply, waste, stormwater, and legal discharge points |
| Heating and cooling | Rooms, zones, ducts, outlets, equipment, and roof-mounted units |
| Energy | Orientation, windows, glazing, wall construction, insulation, ceilings, shading, and thermal loads |
| Landscape | Site boundary, levels, paths, drainage, fencing, gates, and external works |
| Finishes and interiors | Rooms, floors, walls, ceilings, tiles, paint, fixtures, appliances, and joinery |
| Construction | Elements, phases, work packages, tasks, inspections, progress, and defects |

## Change propagation

| Change category | Behaviour |
|---|---|
| View-only change | Update the affected generated view automatically |
| Model change with local effects | Update dependent views and schedules automatically; record the change |
| Cross-discipline effect | Flag affected systems and create a coordination review |
| Approved controlled change | Apply the change, update dependencies, and preserve revision history |
| Rejected change | Keep the current approved model and record the decision |

Examples include moving a wall, changing a room boundary, relocating a window, changing a floor level, modifying roof geometry, and moving a specialist fixture.

## Model governance

The model must support:

- Autosave.
- Transaction-based undo and redo.
- Snapshots.
- Version history.
- Revisions and issue packages.
- Role-based permissions.
- Comments, issues, approvals, and audit events.
- Validation warnings and coordination status.
- Controlled publishing of drawings, schedules, and specifications.
