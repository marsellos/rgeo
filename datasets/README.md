# R-GEO book — dataset archive

Authentic copies of the public datasets used in *R-GEO* (Earth & Sustainability Data
Analytics with R), saved per chapter so readers can reproduce the book's results even
if a live source changes or goes offline. Each entry lists the **source**, the
**verified license/terms**, and the **attribution** to use.

Verified 2026-06-18. The book code itself was **not changed**; these are standalone copies.

> Large/derived items are linked rather than re-hosted: the **GRACE** NetCDF (already
> archived on Zenodo) and the **elevatr** DEMs (assembled on demand from AWS Terrain
> Tiles). See notes below.

---

## Licensing summary

| Dataset | Source | License / terms | Re-host? |
|---|---|---|---|
| USGS groundwater | U.S. Geological Survey (NWIS) | Public domain (U.S. Gov work) | ✅ yes |
| NOAA GHCN-Daily (JFK) | NOAA NCEI | Public domain (U.S. Gov; US station) | ✅ yes |
| GPS NYCI | Nevada Geodetic Lab, UNR | Open, attribution requested | ✅ yes (attribute) |
| World Bank WDI (GHG, pop) | World Bank | **CC BY 4.0** | ✅ yes (attribute) |
| Natural Earth countries | Natural Earth | Public domain | ✅ yes |
| GRACE mascons | NASA/JPL (PO.DAAC) | Public domain (U.S. Gov) | 🔗 link Zenodo |
| Elevation/bathymetry DEM | elevatr → AWS Terrain Tiles | Open, attribution to sources | 🔗 reproduce (see note) |
| volcano, nottem, airquality | R `datasets` package | GPL (base R) | ✅ yes |
| **volcano_db.csv** | plotly/datasets → **Smithsonian GVP** | ⚠️ MIT compile, but **GVP = non-commercial** | ⚠️ link, do not re-host (see below) |
| **NYS Civil Boundaries** | NYS GIS Program Office | ⚠️ **No explicit license**; "as-is, planning use" | ⚠️ your call (see below) |

---

## chapter2-data/
- **`usgs_groundwater_well-404416073491801_param-62610_2000-2025.rdb`**
  - Source: USGS National Water Information System, daily values service. Well 404416073491801, parameter 62610 (groundwater level, ft above NGVD 1929), 2000-02-01 to 2025-02-10.
  - License: **Public domain** (U.S. Geological Survey; U.S. Government work). Dataset DOI 10.5066/P9X4L3GE.
  - Attribution: "U.S. Geological Survey, National Water Information System (NWIS)."
- **`ghcn-daily_USW00094789_JFK.csv`**
  - Source: NOAA NCEI, Global Historical Climatology Network – Daily. Station USW00094789 (JFK International Airport, NY). Full station record (PRCP used by the book).
  - License: **Public domain** (NOAA / U.S. Government; US station). Dataset DOI 10.7289/V5D21VHZ.
  - Attribution: "NOAA National Centers for Environmental Information, GHCN-Daily."

## chapter5-modeling/
- **`nottem.csv`**, **`airquality.csv`** — R built-in `datasets` package. `nottem` = monthly mean air temperature, Nottingham Castle, 1920–1939 (°F). `airquality` = New York air quality measurements, May–Sep 1973. License: GPL (ships with base R). Freely redistributable.

## chapter1-intro/
- **`volcano.csv`** — R built-in `datasets::volcano` (topographic grid of Maungawhau / Mt Eden, Auckland; 87×61). License: GPL (base R).

## chapter6-casestudies/
- **`gps_NYCI.tenv3`**
  - Source: Nevada Geodetic Laboratory, University of Nevada, Reno — station NYCI, IGS20 tenv3 daily positions.
  - License: **Open**; attribution requested. Cite Blewitt, Hammond & Kreemer (2018), *Eos* 99, doi:10.1029/2018EO104623.
  - Attribution: "Nevada Geodetic Laboratory, University of Nevada, Reno."
- **GRACE mascons (NetCDF)** — NOT re-hosted (large, already archived).
  - Source/DOI: NASA/JPL GRACE/GRACE-FO mascons, PO.DAAC doi:10.5067/TEMSC-3JC634.
  - Author's archived copy: **Zenodo doi:10.5281/zenodo.20535360** (the book downloads from here). License: public domain (U.S. Gov). Link to the Zenodo record from the website.
- Long Island counties + DEM — shared with chapter 3 (see below).

## chapter3-spatial/
- **Elevation / bathymetry DEM** — NOT re-hosted (assembled on demand).
  - Source: `elevatr::get_elev_raster()` → **AWS Terrain Tiles** (open data, built from SRTM/USGS NED and other public DEMs). Reproduce with the chapter's bounding box and zoom (`z`); the tiles are open with attribution to the underlying sources.
  - Attribution: "Elevation from AWS Terrain Tiles via the elevatr R package."

---

## ⚠️ Pending your decision — `_review_licensing/`

These two are downloaded but **kept out of the published chapter folders** until you decide, because their terms are not a clean re-host.

### `volcano_db.csv` (chapter 3)
- Source: `plotly/datasets` GitHub (MIT) — but the **content is Smithsonian Global Volcanism Program** data (confirmed: the rows carry GVP volcano numbers like `0803-001`).
- Terms: Smithsonian GVP Terms of Use = **personal/educational/non-commercial only**, with required citation and a link back to the SI site; commercial use (selling, or products incorporating the content) is **not** permitted.
- Conflict: the book is sold, so re-hosting GVP-derived data on its commercial website is the one real risk.
- Note: raw factual data (volcano coordinates/elevations) is generally **not copyrightable** in the U.S. (Feist), so practical risk is low — but **linking** to the plotly source (and citing Smithsonian GVP) avoids the GVP non-commercial policy entirely.
- **Recommendation: link, do not re-host.** Keep the attribution already in the book.

### `nys_long_island_counties.geojson` (chapters 3 & 6)
- Source: NYS GIS Program Office, NYS Civil Boundaries service (counties layer); the four Long Island counties (Kings, Queens, Nassau, Suffolk).
- Terms: **No explicit license** is published (data.gov lists "no license information"). It is public NY-State government data, freely downloadable in GeoJSON, marked "for planning and general use only," provided "as is" with no warranty.
- **Recommendation: re-host is low-risk WITH attribution + the as-is/planning disclaimer**, or link to the NYS GIS Clearinghouse to be fully safe. Your call.
- Attribution if hosted: "New York State GIS Program Office, NYS Civil Boundaries. For planning/general use only; provided as-is."

Sources consulted: NYS GIS Clearinghouse (gis.ny.gov/civil-boundaries), data.gov NYS Civil Boundaries, plotly/datasets (github.com/plotly/datasets), Smithsonian GVP Terms of Use (volcano.si.edu/gvp_termsofuse.cfm).
