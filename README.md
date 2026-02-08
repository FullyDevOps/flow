GitHub can render Mermaid diagrams directly in Markdown when you wrap the diagram in a fenced code block labeled `mermaid`. ([GitHub Docs][1])
If you publish via **GitHub Pages (Jekyll)**, Mermaid may not render by default and you may see the raw code unless you add a Mermaid renderer step. ([GitHub Discussion][2])

Below are **paste-ready Mermaid charts** you can copy into `README.md` or any `.md` file in your repo.

> **Mermaid reliability rules (prevents parse errors):**
>
> * One arrow/statement per line
> * Keep node labels on a single line
> * Prefer quoted labels: `A["text"]`
> * Avoid special characters inside labels (use `m3` instead of `m³`, avoid `+` where possible)

---

## Chart 1 — End-to-end overview (Friend vs You) 🧭

```mermaid
flowchart TD
  A["Brand owner (You) - Indiana USA"] --> B["Define SKU specs, labels, and claims rules"]
  B --> C["Select providers: broker, forwarder, lab, FSVP, 3PL/prep"]
  C --> D["Create FSVP program per SKU"]
  D --> E["Send purchase order and approved artwork to India"]

  subgraph INDIA["Friend (India) - Manufacturer and exporter"]
    I1["Business setup and registrations"] --> I2["Facility, equipment, GMP, SSOP"]
    I2 --> I3["Raw sourcing (conventional or organic)"]
    I3 --> I4["Manufacture and pack retail-ready (pouch or jar)"]
    I4 --> I5["Lot coding, COA testing, QA release"]
    I5 --> I6["Export documents and handover to forwarder"]
  end

  E --> I1
  I6 --> U1["Transit (ocean or air)"]
  U1 --> U2["US import: broker entry and Prior Notice"]
  U2 --> U3["Indiana receiving and QC check"]
  U3 --> U4["Distribution: store, 3PL, or Amazon FBA"]
  U4 --> U5["Sales, complaints, recall readiness loop"]
```

---

## Chart 2 — Manufacturing SOP (Beetroot master flow) 🏭

```mermaid
flowchart LR
  R1["Receiving"] --> R2["Wash"]
  R2 --> R3["Sort and trim"]
  R3 --> R4["Slice 3 to 6 mm"]
  R4 --> D1{"Blanch?"}

  D1 -->|Yes| B1["Blanch or steam"]
  D1 -->|No| DY["Dry"]

  B1 --> DY
  DY --> M1["Mill or grind"]
  M1 --> S1["Sieve (mesh spec)"]
  S1 --> F1["Magnet(s)"]
  F1 --> MD["Metal detector"]

  MD --> P0{"Pack format?"}

  P0 -->|Pouch| P1["Fill pouch"]
  P1 --> P1A["Optional nitrogen flush"]
  P1A --> P1B["Seal pouch"]

  P0 -->|Jar| P2["Fill jar"]
  P2 --> P2A["Cap jar"]
  P2A --> P2B["Optional induction seal"]

  P1B --> C1["Print lot and best-by"]
  P2B --> C1

  C1 --> CP["Case pack"]
  CP --> PL["Palletize and stage"]
  PL --> QH["QA hold pending COA"]
```

---

## Chart 3 — SKU process differences (decision logic) 🍋🍊

```mermaid
flowchart TD
  A["Select SKU"] --> B{"SKU type?"}

  B --> BR["Beetroot"]
  B --> CR["Carrot"]
  B --> GI["Ginger"]
  B --> OR{"Orange option?"}
  B --> LE{"Lemon option?"}

  BR --> BR1["Color sensitive; control heat and oxygen"]
  CR --> CR1["Optional blanch for color stability"]
  GI --> GI1["Higher soil risk; tighten washing and screening"]

  OR --> ORW["Whole fruit powder"]
  OR --> ORP["Peel powder"]
  ORW --> ORW1["Higher sugar; higher clump risk; use high barrier pouch"]
  ORP --> ORP1["Residue risk higher; increase pesticide testing frequency"]

  LE --> LEW["Whole or juice-solids type"]
  LE --> LEP["Peel powder"]
  LEW --> LEW1["Control browning and aroma; validate drying profile"]
  LEP --> LEP1["Residue risk higher; oils can affect sealing; keep mesh moderate"]

  LEW --> LES{"Juice solids carrier?"}
  LES -->|Yes| LES1["Carrier used; ingredient list and nutrition facts change"]
  LES -->|No| LES2["No carrier; standard single-ingredient label path"]
```

---

## Chart 4 — Quality system (GMP, SSOP, Pest, Traceability) 🧼

```mermaid
flowchart TD
  Q0["Quality management system"] --> Q1["GMP program"]
  Q0 --> Q2["SSOP cleaning schedules"]
  Q0 --> Q3["Pest control and trending"]
  Q0 --> Q4["Traceability (1-up, 1-down)"]
  Q0 --> Q5["Batch coding and records"]
  Q0 --> Q6["CAPA and deviations"]
  Q0 --> Q7["Recall plan and mock recalls"]

  Q1 --> Z1["Hygiene zoning: wet to dry"]
  Q2 --> V1["Verification: logs and checks"]
  Q4 --> L1["Lot map: raw to WIP to finished to shipment"]
```

---

## Chart 5 — COA and Release workflow (per lot) 🧪

```mermaid
flowchart TD
  L0["Lot produced"] --> H1["Quarantine hold"]
  H1 --> S1["Composite sampling"]
  S1 --> T1["Lab testing"]
  T1 --> R1{"Meets spec?"}

  R1 -->|Yes| REL["QA release"]
  R1 -->|No| INV["Investigation"]

  INV --> CAPA["CAPA and corrective actions"]
  CAPA --> D1{"Rework possible?"}

  D1 -->|Yes| RW["Rework and re-test"]
  RW --> T1

  D1 -->|No| DIS["Dispose, downgrade, or reject"]

  REL --> SHIP["Eligible for export"]
```

---

## Chart 6 — Organic vs Conventional segregation controls 🌿

```mermaid
flowchart TD
  A["Production planning"] --> B{"Run type?"}

  B -->|Conventional| C1["Conventional staging"]
  B -->|Organic| O1["Organic staging"]

  O1 --> O2["Verify organic supplier documents"]
  O2 --> O3["Line clearance and cleaning"]
  O3 --> O4["Organic run"]
  O4 --> O5["Organic lot labels and segregated storage"]
  O5 --> O6["Organic transaction and chain-of-custody records"]

  C1 --> C2["Conventional run"]
  C2 --> C3["Conventional labels and storage"]
```

---

## Chart 7 — Export docs package (India) 📄

```mermaid
flowchart TD
  A["Shipment build plan"] --> B["Lot list and case/pallet map"]
  B --> C["Commercial invoice"]
  B --> D["Packing list"]
  B --> E["COAs per lot"]
  B --> F["Certificate of origin (if needed)"]
  B --> G["Bill of lading or airway bill (via carrier)"]
  B --> H["Insurance certificate (if CIF or DDP)"]

  C --> Z["Forwarder export filing"]
  D --> Z
  E --> Z
  F --> Z

  Z --> Y["Cargo handover to carrier"]
```

---

## Chart 8 — US import flow (Broker + Prior Notice) 🇺🇸

```mermaid
flowchart TD
  A["Pre-arrival"] --> B["ISF filed (ocean)"]
  A --> C["Prior Notice filed"]
  A --> D["Entry data prepared (invoice, packing list, BL/AWB, COA)"]

  B --> E["Arrival at US port"]
  C --> E
  D --> E

  E --> F{"CBP/FDA status?"}
  F -->|May proceed| G["Customs release"]
  F -->|Hold or exam| H["Respond: documents, samples, label review"]

  H --> I{"Cleared?"}
  I -->|Yes| G
  I -->|No| J["Refuse, destroy, or export back (rare)"]

  G --> K["Deliver to Indiana, 3PL, or prep center"]
```

---

## Chart 9 — Shipping method decision (Air vs Sea; LCL vs FCL) 🚢✈️

```mermaid
flowchart TD
  A["Monthly volume estimate"] --> B{"Volume (m3) and weight?"}

  B -->|Pilot or urgent| AIR["Air freight"]
  B -->|About 6 to 15 m3 per month| LCL["Sea LCL monthly"]
  B -->|High and stable| FCLQ{"Consider sea FCL?"}

  FCLQ -->|Yes, consistent pallets| FCLY["FCL (lower unit cost)"]
  FCLQ -->|No, inconsistent| LCL

  AIR --> P1["Higher cost, faster validation"]
  LCL --> P2["Balanced cost, steady supply"]
  FCLY --> P3["Best cost when scaled"]
```

---

## Chart 10 — Incoterms selection (beginner-safe) 📦

```mermaid
flowchart TD
  A["Choose incoterm"] --> B{"Beginner importer?"}

  B -->|Yes| FOB["FOB (recommended)"]
  B -->|No| C{"Need simplicity with a trusted provider?"}

  C -->|Yes| DDP["DDP (only with full cost transparency)"]
  C -->|No| CIF["CIF (supplier books freight and insurance)"]

  A --> EXW["EXW (avoid early on)"]
  EXW --> R1["High coordination risk in India"]
  FOB --> R2["Balanced control and cleaner responsibility split"]
  CIF --> R3["Less control; watch destination fees"]
  DDP --> R4["Can be opaque if poorly structured"]
```

---

## Chart 11 — Distribution Scenario A (Store + Amazon) 🏪📦

```mermaid
flowchart TD
  A["Shipment delivered to Indiana"] --> B["Receiving QC and lot/best-by verification"]
  B --> C["Inventory split"]
  C --> S["Store stock"]
  C --> P["Prep or 3PL for Amazon"]

  S --> S1["Retail storage (cool, dry, pest control)"]
  S1 --> S2["POS and sales tax process"]
  S2 --> S3["Customer returns and complaints handling"]

  P --> P1["FNSKU and carton labels"]
  P1 --> P2["Create FBA inbound shipment"]
  P2 --> P3["Amazon receiving"]
  P3 --> P4["Amazon sales and returns"]
```

---

## Chart 12 — Distribution Scenario B (Amazon-only) 📦

```mermaid
flowchart TD
  A["Shipment delivered"] --> B["Receiving QC and lot/best-by verification"]
  B --> C{"Route?"}

  C -->|Direct to prep center| P["Prep center"]
  C -->|Your warehouse first| W["Your warehouse"]

  W --> P
  P --> L1["FNSKU and best-by checks"]
  L1 --> L2["Case pack and carton labels"]
  L2 --> L3["FBA inbound"]
  L3 --> L4["Amazon receiving"]
  L4 --> L5["Sales, returns, defect monitoring"]
```

---

## Chart 13 — Amazon FBA expirable prep workflow 🏷️

```mermaid
flowchart TD
  A["Select expirable SKU"] --> B["Ensure unit shows best-by or expiration date"]
  B --> C["Apply FNSKU (if required)"]
  C --> D["Carton labels plus lot and best-by on cases"]
  D --> E["Create FBA shipment plan"]
  E --> F["Send to FBA"]
  F --> G{"FBA check-in result?"}
  G -->|Pass| H["Available for sale"]
  G -->|Fail| I["Rework, relabel, or remove order"]
```

---

## Chart 14 — Traceability + complaint to recall loop 🔁

```mermaid
flowchart TD
  A["Customer complaint"] --> B{"Food safety concern?"}

  B -->|Yes| C["Immediate triage and stop-ship"]
  B -->|No| D["Quality complaint handling"]

  C --> E["Identify lot, ASIN, UPC"]
  D --> E

  E --> F["Trace lot: raw to WIP to finished to shipments"]
  F --> G{"Scope known?"}

  G -->|Yes| H["Targeted recall or removal plan"]
  G -->|No| I["Expand investigation and testing"]

  H --> J["Notify channels: Amazon, store, 3PL"]
  J --> K["Execute retrieval and disposition"]
  K --> L["CAPA and prevention"]
```

---

## Chart 15 — Scale from 5 SKUs to 10 SKUs (no redesign) 📈

```mermaid
flowchart TD
  A["Current system: 5 SKUs"] --> B["Standardize spec sheets and COA templates"]
  B --> C["Standardize label system (SKU, size, format)"]
  C --> D["Add parallel raw bays (organic and conventional segregation)"]
  D --> E["Add capacity: dryer or mill hours, or upgrade dryer"]
  E --> F["Add QC capacity: faster moisture/aw and lab SLA"]
  F --> G["Expand to 10 SKUs"]
```

---

# Minimal usage in your GitHub repo 🧩

1. Paste any block into `README.md` or `docs/diagrams.md`:

````text
```mermaid
flowchart TD
  A --> B
```
````

2. GitHub renders Mermaid on GitHub.com automatically. ([GitHub Docs][1])
3. If GitHub Pages shows raw Mermaid, you need extra setup. ([GitHub Discussion][2])

If you want more charts next, I can add:

* Swimlane diagrams (Friend vs Forwarder vs Broker vs You vs Amazon)
* Sequence diagrams (Ocean LCL shipment, Air pilot shipment)
* State diagrams (Inventory lifecycle: quarantine → released → in transit → FBA → sold/returned)

[1]: https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams "Creating Mermaid diagrams"
[2]: https://github.com/orgs/community/discussions/65040 "Mermaid diagrams not showing in GitHub Pages discussion"
