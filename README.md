# dank-data

`dank-data` is AgentDank's public dataset repository.  We take public cannabis datasets, clean them, and publish them.  We use them to train our AgentDank models and to provide information to [our Model Context Procotol (MCP) server](https://github.com/AgentDank/dank-mcp) `dank-mcp`.  The data is sourced using `dank-mcp --dump` ([docs](https://github.com/AgentDank/dank-mcp)).

 * [Snapshots](#snapshots)
 * [Data Cleaning](#data-cleaning)
 * [Contribution and Conduct](#contribution-and-conduct)
 * [Credits and License](#credits-and-license)


Currently the following datasets are snapshotted:

 * [US CT Medical Marijuana and Adult Use Cannabis Brand Registry](https://data.ct.gov/Health-and-Human-Services/Medical-Marijuana-and-Adult-Use-Cannabis-Brand-Reg/egd5-wb6r/about_data)

## Snapshots

We have included our ["cleaned"](#data-cleaning) data snapshots of public datasets in the respository for the researcher's convience.  These may be found in the [`snapshots`](./snapshots/) directory.  Due to their size, the CSV and JSON and [DuckDB](https://duckdb.org) files are compressed with [ZStandard, `.zst`](https://en.wikipedia.org/wiki/Zstd).

The following [snapshots](./snapshots) are available:

  * `2025-04-03` US CT Brands ([CSV](./snapshots/us/ct/2025-04-03/us_ct_brands.csv.zst), [JSON](./snapshots/us/ct/2025-04-03/us_ct_brands.json.zst), [DuckDB](./snapshots/us/ct/2025-04-03/us_ct_brands.duckdb.zst))

## Data Cleaning

Because the upstream datasets are not perfect, we have to "clean" it.  Such practices are opinionated, but since this is Open Source, you can inspect how we clean it by examining [the data extractors and cleaners](https://github.com/AgentDank/dank-mcp/#data-cleaning) in `dank-mcp`.

Generally, we simply remove weird characters.  We treat detected "trace" amounts as 0 -- and even with that, there's a decision about what field entry actually means "trace".  

We also remove rows with riduclous data -- as much as I'd love a `90,385% THC product`, I don't think it really exists.  In that case, it was an incorrect decimal point (by looking at the label picture), but not every picture validates every error.  It's also a pain -- but maybe a multi-modal vision LLM can help with that?

--

## Contribution and Conduct

As [AgentDank](https://github.com/AgentTank) curates these datasets, pull requests are generally not welcome here.  If you want to contribute, please create an issue.

Either way, obey our [Code of Conduct](./CODE_OF_CONDUCT.md).  Be shady, but don't be a jerk.

## Credits and License

Copyright (c) 2025 Neomantra Corp.  Authored by Evan Wies for [AgentDank](https://github.com/agentdank).

Released under the [MIT License](https://en.wikipedia.org/wiki/MIT_License), see [LICENSE.txt](./LICENSE.txt).

----
Made with :herb: and :fire: by the team behind [AgentDank](https://github.com/AgentDank).
