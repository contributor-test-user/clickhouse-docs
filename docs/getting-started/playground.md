---
description: 'The ClickHouse Playground allows people to experiment with ClickHouse
  by running queries instantly, without setting up their server or cluster.'
keywords: ['clickhouse', 'playground', 'getting', 'started', 'docs']
sidebar_label: 'ClickHouse Playground'
slug: /getting-started/playground
title: 'ClickHouse Playground'
---

# ClickHouse playground

[ClickHouse Playground](https://sql.clickhouse.com) allows people to experiment with ClickHouse by running queries instantly, without setting up their server or cluster.
Several example datasets are available in Playground.

You can make queries to Playground using any HTTP client, for example [curl](https://curl.haxx.se) or [wget](https://www.gnu.org/software/wget/), or set up a connection using [JDBC](../interfaces/jdbc.md) or [ODBC](../interfaces/odbc.md) drivers. More information about software products that support ClickHouse is available [here](../integrations/index.mdx).

## Credentials {#credentials}

| Parameter           | Value                              |
|:--------------------|:-----------------------------------|
| HTTPS endpoint      | `https://play.clickhouse.com:443/` |
| Native TCP endpoint | `play.clickhouse.com:9440`         |
| User                | `explorer` or `play`               |
| Password            | (empty)                            |

## Limitations {#limitations}

The queries are executed as a read-only user. It implies some limitations:

- DDL queries are not allowed
- INSERT queries are not allowed

The service also have quotas on its usage.

## Examples {#examples}

HTTPS endpoint example with `curl`:

```bash
curl "https://play.clickhouse.com/?user=explorer" --data-binary "SELECT 'Play ClickHouse'"
```

TCP endpoint example with [CLI](../interfaces/cli.md):

```bash
clickhouse client --secure --host play.clickhouse.com --user explorer
```

## Playground specifications {#specifications}

our ClickHouse Playground is running with the following specifications:

- Hosted on Google Cloud (GCE) in the US Central region (US-Central-1)
- 3-replica setup
- 256 GiB of storage and 59 virtual CPUs each.
