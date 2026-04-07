---
tags:
  - citizenscience
  - viraj
  - roger
---
- **Use open metadata aggregators as the backbone**
    
    - **OpenAlex** for broad cross-disciplinary metadata, filtering, and bulk/snapshot access. It has an API, monthly snapshots, and now supports bulk full-text PDF / TEI XML downloads for many open-access works.
        
    - **Crossref** for DOI-centric metadata and links to text-and-data-mining or full-text URLs when publishers expose them. Crossref itself is mostly metadata, not the full text.
        
- **Use domain databases where they are strongest**
    
    - **PubMed / PMC / Europe PMC** are excellent if a big part of your corpus is biomedical / life science. PubMed E-utilities are meant for programmatic access; NCBI documents request limits of 3 requests/sec by default and up to 10/sec with an API key. PMC also provides article datasets and OA full text access pathways. Europe PMC exposes REST services and large full-text coverage for life sciences.
        
    - **Semantic Scholar** is also useful as a supplementary source because it has an API and dataset downloads.
        
- **Only go to publisher / journal websites for the last mile**
    
    - Individual journal scraping is possible in some cases, but it is the **worst default strategy**: every site has different HTML, anti-bot behavior, licensing, and access rules.
        
    - Better approach: use OpenAlex / Crossref / PubMed / Europe PMC to identify records first, then follow DOI / PMC / OA links only for papers you are actually allowed to retrieve.

- `id`
    
- `doi`
    
- `title`
    
- `abstract`
    
- `publication_year`
    
- `journal`
    
- `authors`
    
- `concepts`
    
- `cited_by_count`
    
- `open_access`
    
- `fulltext links`