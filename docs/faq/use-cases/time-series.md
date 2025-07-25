---
slug: /faq/use-cases/time-series
title: 'Can I use ClickHouse as a time-series database?'
toc_hidden: true
toc_priority: 101
description: 'Page describing how to use ClickHouse as a time-series database'
---

# Can I use ClickHouse as a time-series database? {#can-i-use-clickhouse-as-a-time-series-database}

_Note: Please see the blog [Working with Time series data in ClickHouse](https://clickhouse.com/blog/working-with-time-series-data-and-functions-ClickHouse) for additional examples of using ClickHouse for time series analysis._

ClickHouse is a generic data storage solution for [OLAP](../../faq/general/olap.md) workloads, while there are many specialized [time-series database management systems](https://clickhouse.com/engineering-resources/what-is-time-series-database). Nevertheless, ClickHouse's [focus on query execution speed](../../concepts/why-clickhouse-is-so-fast.md) allows it to outperform specialized systems in many cases. There are many independent benchmarks on this topic out there, so we're not going to conduct one here. Instead, let's focus on ClickHouse features that are important to use if that's your use case.

First of all, there are **[specialized codecs](../../sql-reference/statements/create/table.md#specialized-codecs)** which make typical time-series. Either common algorithms like `DoubleDelta` and `Gorilla` or specific to ClickHouse like `T64`.

Second, time-series queries often hit only recent data, like one day or one week old. It makes sense to use servers that have both fast NVMe/SSD drives and high-capacity HDD drives. ClickHouse [TTL](/engines/table-engines/mergetree-family/mergetree#table_engine-mergetree-ttl) feature allows to configure keeping fresh hot data on fast drives and gradually move it to slower drives as it ages. Rollup or removal of even older data is also possible if your requirements demand it.

Even though it's against ClickHouse philosophy of storing and processing raw data, you can use [materialized views](../../sql-reference/statements/create/view.md) to fit into even tighter latency or costs requirements.
