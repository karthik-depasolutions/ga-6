---
name: generic-analytics-analyst
description: Use this skill when analyzing Generic Analytics Pack data - revenue,
  volumes, trends, and pre-built KPIs (average_measure, sum_measure, total_records,
  trend_by_month). Guides querying via the bundled MCP tools instead of ad-hoc SQL.
metadata:
  pack_slug: generic-analytics
  pack_version: 1.0.0
---

# Generic Analytics Pack Analyst

Use this skill for questions about this business's data and its KPIs.

## Analytical Methodology

When analyzing business performance, follow this structured diagnostic protocol:
1. **Frame the Question**: Restate ambiguous questions with specific metrics, time horizons, and baseline periods.
2. **Decompose Metrics First**: Break composite metrics into constituent drivers (e.g. `Revenue = Volume × Unit Price × Mix`).
3. **Query via Grounded Tools**: Fetch data using the bundled MCP tools (`get_kpi`, `run_safe_query`) without guessing columns.
4. **Drill Down by Dimensions**: Compare period-over-period performance across available segments, ordering by absolute variance contribution.
5. **Synthesize with BLUF**: Lead with the Bottom Line Up Front, follow with quantified evidence, and conclude with actionable recommendations.

## Available KPIs

- `average_measure` - **Average of Primary Measure**: Average of the primary numeric measure. (unit: numeric)
- `sum_measure` - **Sum of Primary Measure**: Sum of the primary numeric measure. (unit: numeric)
- `total_records` - **Total Records**: Total number of rows in the primary table. (unit: count)
- `trend_by_month` - **Trend by Month**: Primary measure summed and record count, grouped by month of the primary date dimension. (unit: numeric)

Not available for this data source (required data was missing): `count_by_category`

## How to Use the MCP Analytics Tools

Before writing any SQL, read the `schema://model` resource (per-table meaning, column definitions, enum decodes) and `schema://cookbook` (verified example queries for this exact database). Use `schema://relationships` for join keys. Then follow this hierarchy:
1. **Discovery**: Call `mcp__mis-mcp-generic-analytics__describe_data`, `mcp__mis-mcp-generic-analytics__list_business_concepts`, or `mcp__mis-mcp-generic-analytics__list_kpis` first to discover available business entities and metrics.
2. **KPIs & Metrics**: Prefer `mcp__mis-mcp-generic-analytics__get_kpi` for standard verified metrics, `mcp__mis-mcp-generic-analytics__compare_kpi` for period comparisons, `mcp__mis-mcp-generic-analytics__rank_entities` for top/bottom rankings, and `mcp__mis-mcp-generic-analytics__breakdown_metric` for dimensional slices.
3. **Categorical Slices**: Use `mcp__mis-mcp-generic-analytics__get_value_set` to discover distinct category values safely without exploratory SQL.
4. **Entity Records**: Use `mcp__mis-mcp-generic-analytics__get_record`, `mcp__mis-mcp-generic-analytics__search_records`, or `mcp__mis-mcp-generic-analytics__get_related_records` for entity lookups.
5. **Escape Hatch**: Use `mcp__mis-mcp-generic-analytics__run_safe_query` ONLY as a last resort when no semantic or metric tool can answer the question.

## Guardrails & Privacy

- No industry-specific vocabulary is assumed — treat all categorical values literally
- All data access must be read-only
