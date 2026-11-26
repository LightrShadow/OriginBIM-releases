# OpenSKP native writer vendor provenance

Upstream: https://github.com/iamahsanmehmood/openskp
Commit: c98561147ea502c6d4d53a257fa4581d0c6cde1d (2026-11-09)
License: MIT, copyright (c) 2024–2026 Ahsan Mehmood. See OPENSKP-LICENSE.txt.

Files:
- `openskp-create.mjs` derives from `packages/typescript/src/create.ts`.
- `openskp-scaffold.mjs` derives from `packages/typescript/src/scaffold.ts`.

Transformation: Node 24 `stripTypeScriptTypes(...,{mode:'transform'})`, then change the sole relative scaffold import to `./openskp-scaffold.mjs`. No writer algorithms or binary data were changed. This pair has no browser runtime dependency. Use `create()` and `builder.toBytes()`; `builder.save()` is Node/CommonJS-only.

The writer emits legacy native SketchUp 2017 `{17.0.1}` MFC CArchive files. Every coordinate and texture application dimension is in **inches**; convert metres with `metres / 0.0254`. Display units are scaffold defaults, not an API setting. Attribute dictionaries support string/number values; the high-level reader surfaces `dynamic_attributes` dictionaries. Keep a separate native OriginBIM project JSON for full semantic authoring and round trip.

The scaffold provenance is disclosed in the upstream file comments, retained here: a minimal blank v17 document was originally authored with Trimble's official SketchUp SDK during upstream research. Runtime writing uses only JavaScript and the embedded empty template; it does not call or distribute the proprietary SDK. This is not the fully clean-room GPL project skpwright.

Write ordering is significant: add every material first; then every layer; then every group/component definition; only then root-level faces, edges, instances or section planes. Using the wrong handles or adding definitions late throws. Filter degenerate triangles before `addFace`. Equal coordinates share edges/vertices within a definition. Group each OriginBIM object to preserve independent SketchUp editability; attach object IDs and IFC classes using attributes. Use `backMaterial` when the same face appearance is required on both sides.

Verification in the task workspace:
- `verify-fixture.mjs` wrote `fixture.skp`: 8,651 bytes; one named group; 12 triangular faces; AAC concrete color material; Walls tag; custom object ID / IFC class metadata; physical bounds 1 m cube. Parsed and built scene with independent npm installation `openskp@1.5.0` (different shipped reader module, same upstream project); all assertions pass.
- Independent GPL skpwright source at commit `073c10a4b0ed9cd0076c937ba02da77d08c864ce`, `tools/skpwalk.py`, successfully identifies `{17.0.1}`, group definition name, correct material RGBA/opacity, Walls tag and attribute records. Its heuristic geometry-run scanner did not recover this fixture's mesh. Its prototype continuous walker asserts on the scaffold's model-list assumptions. These limits are not evidence of invalid output, but are not a full independent geometric validation either.
- No SketchUp desktop or proprietary SDK validation was run in this environment. Do not describe this as app-certified round-trip. Faces/metadata can be checked by users in SketchUp; SDK compatibility is an upstream claim supported by upstream tests, not a new validation performed here.
