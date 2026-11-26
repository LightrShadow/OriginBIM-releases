# ConstructCraft Components attribution

Original component definitions: **ConstructCraft Components contributors**.

Source: https://github.com/francisreboucas/constructcraft-components

Pinned revision: `0cd86f89eaa9d31e8b5a02f5690081e3902d973e`.

License: **Creative Commons Attribution 4.0 International**, https://creativecommons.org/licenses/by/4.0/ . Full upstream licence text: https://github.com/francisreboucas/constructcraft-components/blob/0cd86f89eaa9d31e8b5a02f5690081e3902d973e/LICENSE .

The source component JSON is retained in `constructcraft-data.mts`. Changes made for OriginBIM: evaluate arithmetic parameters with a restricted parser; convert supported boxes, cylinders and planar profiles into normalized editable members; subtract supported voids; convert Y to plan-down coordinates; retain per-item materials, type parameters, opening metadata, MEP values and connectors. Unsupported primitive/type combinations are excluded with explicit reasons rather than replaced by bounding proxies.

The geometry is the upstream library's simplified parametric design. Neither importing it nor placing it in IFC certifies manufacturer dimensions, fabrication details or engineering compliance. MEP fixture/device values retain their source Brazilian-standard context and are not applied as universal local sizing requirements.

Attribution can be shown in About / Third-party notices and distributed source documentation; it does not need to occupy the main modelling Properties panel. Preserve this notice and source/change metadata with redistributed derived component data.


# OpenCalque

Parts of the drawing workspace follow OpenCalque (https://github.com/laurent512/opencalque): the light and dark canvas colours and the way the dark canvas turns the drawing's lightness over, the grid steps and their translucent lines, the origin axes, the magenta snap signs with their names (such as "Lined up"), the length and angle tags shown while drawing, and typing a length while a wall is drawn. They were rewritten for OriginBIM's own editor.

MIT License

Copyright (c) 2026 OpenCalque contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.


# PDF.js

PDF plans are read for tracing with PDF.js 4.10.38 by Mozilla (https://github.com/mozilla/pdf.js), unmodified, in vendor/pdf.min.mjs and vendor/pdf.worker.min.mjs. Licensed under the Apache License 2.0 (vendor/PDFJS-LICENSE.txt).
