---
title: SQL Persistence
summary: A persister that targets relational databases, including SQL Server, Oracle. MySQL, and PostgreSQL
component: SqlPersistence
related:
 - samples/sql-persistence/simple
 - samples/sql-persistence/transitioning-correlation-ids
 - samples/saga/sql-sagafinder
 - samples/saga/migration
 - persistence/upgrades/sql-2to3
 - persistence/upgrades/sql-1to2
 - persistence/upgrades/sql-1.0.0-1.0.1
reviewed: 2018-10-12
---


Stores NServiceBus data in various relational database engines, without the need for an intermediate ORM, using only a configured `DbConnection`.


## Highlights

* Supports [multiple database engines](#supported-sql-implementations).
* No ORM dependency: can be used with Entity Framework, Dapper, etc.
* Independent tables for each endpoint. No "noisy neighbor" problems.
* [Generates DDL scripts at compile time](controlling-script-generation.md) in the build output directory.
* Generated scripts can be [promoted outside the build directory ](controlling-script-generation.md#promotion) and:
  * Added to source control.
  * Compared using a diff viewer.
  * Inspected by DBAs.
  * Treated as first-class citizens in operations workflows for [installation and deployment](install.md).
* Sagas are:
  * Stored using [Json.NET](http://www.newtonsoft.com/json) to serialize complex data structures, with no need to manage complex table structures.
  * Built to be [version-aware](saga.md#json-net-settings-custom-settings-version-specific-type-specific-deserialization-settings) with support for data evolution.
  * Built to [allow changing the `CorrelationId` over time](saga.md#correlation-ids).


## Supported SQL implementations

partial: supportedimpls


## NuGet Packages

partial: nugets


## Script creation

SQL installation scripts are created as a compile-time output alongside a project's binary outputs. Additionally, these scripts can be promoted to a directory under source control so that differences can be easily tracked and analyzed. To learn more, see [Controlling Script Generation](/persistence/sql/controlling-script-generation.md).
