# EHLC Curation Prototype

This prototype shows how [Nanobot](https://github.com/ontodev/nanobot.rs)
can be used to curate datasets for EHLC.

WARNING: Nanobot is "alpha" stage software,
still under active development and likely to change.

## Usage

1. clone this repository
2. download a `nanobot` binary for your platform
3. run `nanobot` and browse <http://localhost:3000>

For example:

```sh
git clone https://github.com/jamesaoverton/ehlc-curation-prototype.git
cd ehlc-curation-prototype
curl -L -o nanobot https://github.com/ontodev/nanobot.rs/releases/download/v2024-04-25/nanobot-v20240425-x86_64-linux
chmod +x nanobot
./nanobot serve --connection :memory:
```

This will create a temporary, in-memory SQLite database,
then load and validate all TSV files,
and start the web application at <http://localhost:3000>.
Inside the web application,
"Actions > Save" will save changes to the TSV files.
Press `Ctrl-C` to stop the web server.

You can create a persistent SQLite database file using `./nanobot init` first.
For example:

```sh
rm -f .nanobot.db && ./nanobot init && ./nanobot serve
```

This will also create a
[`nanobot.toml` configuration file](https://github.com/ontodev/nanobot.rs/blob/main/doc/config.md)
that you can modify.

## Files

- `geospatial.tsv` geospatial datasets (partial)
- `src/schema/` configuration and controlled terminology
  - `table.tsv`, `column.tsv`, `datatype.tsv`: table configuration
  - `*.tsv` controlled terminology
