# Toolboxed BIM Product Plan

## Product goal

Toolboxed is a collaborative BIM application that helps professionals design, plan, coordinate, document, approve, and execute property development activities.

The central building model is the source of truth. Architecture is the foundation; specialist systems are coordinated overlays that remain connected to the architectural model.

## Product principles

1. **Architecture first** — establish the building's spatial and geometric foundation before adding specialist systems.
2. **One coordinated model** — plans, schedules, specifications, overlays, and construction information derive from connected model data.
3. **Views are generated outputs** — site plans, floor plans, elevations, sections, schedules, and 3D views should remain linked to the model.
4. **Controlled change** — visual updates may propagate automatically, while model changes affecting other disciplines require review.
5. **Traceable information** — preserve revisions, approvals, comments, decisions, and audit history.
6. **Professional execution** — support the project from early design through documentation and construction.

## Primary workflow

1. Create project.
2. Configure project, roles, units, standards, and phases.
3. Define site, survey information, constraints, and orientation.
4. Define levels, grids, and reference geometry.
5. Build the architectural model.
6. Review plans, elevations, sections, details, and 3D views.
7. Add annotations, schedules, specifications, and drawing information.
8. Add specialist system overlays.
9. Coordinate systems and review conflicts.
10. Manage project phases, revisions, and approvals.
11. Create sheets, drawing sets, and issue packages.
12. Review, approve, issue, and record project information.
13. Export, share, and support construction execution.

## Delivery phases

| Phase | Scope | Success measure |
|---|---|---|
| 1. Architecture foundation | Site, levels, rooms, walls, floors, roofs, doors, windows, ceilings, components, and core views | A professional can create and edit a basic building model |
| 2. Coordinated documentation | Sheets, annotations, schedules, specifications, revisions, publishing, and document control | A project can produce a coordinated drawing package |
| 3. Specialist overlays | Structural, electrical, plumbing, heating, energy, landscape, and finishes | Disciplines can coordinate against the architectural model |
| 4. Review and approvals | Issues, comments, permissions, approvals, and audit trail | Stakeholders can review and approve information |
| 5. Construction execution | Work packages, tasks, inspections, field updates, progress, and defects | The model supports construction delivery |
| 6. Advanced platform | AI assistance, analytics, mobile field tools, and integrations | Toolboxed supports the broader property-development lifecycle |

## Non-functional requirements

- Autosave without losing the current working state.
- Transaction-based undo and redo.
- Project snapshots and version history.
- Role-based access control.
- Clear change tracking and audit events.
- Model validation and coordination warnings.
- Exportable drawings, schedules, specifications, and issue packages.
- Accessible, responsive interfaces for office and field use.

## Initial success criteria

- Architecture can be modelled without disconnected duplicate data.
- Required views can be generated from the central model.
- Specialist overlays remain spatially related to rooms and building elements.
- Changes identify affected views, systems, documents, and approvals.
- Users can recover previous states through undo, redo, snapshots, and history.
- A project can progress from model creation to an issued construction information package.
