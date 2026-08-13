---
layout: page
title: Open Dataset
description: The Uganda Web Design Directory publishes its listings as an open machine-readable dataset. Download the company data as JSON.
permalink: /data/
---
# Open Dataset

The directory's listings are published as an open, machine-readable dataset.

**Download:** [companies.json](/data/companies.json)

## What it contains

The dataset is a JSON file with a small amount of metadata followed by a `companies` array. Each company entry uses a stable set of fields:

| Field | Description |
| --- | --- |
| `name` | Company name |
| `location` | City / town and country |
| `services` | List of services offered |
| `website` | Official website URL |
| `bestFor` | What the company is best suited for |
| `lastReviewed` | Date the listing was last reviewed |
| `sources` | Public sources used for the listing |

## Why we publish it

Publishing the data openly means the directory can be reused, cited and verified. It also lets developers build tools on top of it, and gives journalists and researchers a structured reference to Uganda's digital agency market.

## How to use it

- **Schema:** each entry follows the fields above; the schema may evolve, and additions are documented in the repository's commit history
- **License:** the dataset is released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — reuse it with attribution
- **Repository:** source and history live in the [GitHub repository](https://github.com/kiwanacollins/uganda-web-design-directory)

<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Dataset",
  "name": "Uganda Web Design Directory company listings",
  "description": "An open dataset of website design, web development, e-commerce, SEO and digital marketing companies serving Uganda.",
  "url": "{{ '/data/companies.json' | absolute_url }}",
  "dateModified": "2026-08-13",
  "license": "https://creativecommons.org/licenses/by/4.0/",
  "creator": {
    "@type": "Organization",
    "name": "Kico Web Design",
    "url": "https://kicowebdesign.com"
  },
  "distribution": {
    "@type": "DataDownload",
    "encodingFormat": "application/json",
    "contentUrl": "{{ '/data/companies.json' | absolute_url }}"
  }
}
</script>
