---
description: 'Generic Analytics Pack Report: run every available KPI and summarize
  the results.'
allowed-tools: mcp__mis-mcp-generic-analytics__describe_data, mcp__mis-mcp-generic-analytics__list_business_concepts,
  mcp__mis-mcp-generic-analytics__describe_schema, mcp__mis-mcp-generic-analytics__get_data_profile, mcp__mis-mcp-generic-analytics__get_value_set,
  mcp__mis-mcp-generic-analytics__list_kpis, mcp__mis-mcp-generic-analytics__get_kpi, mcp__mis-mcp-generic-analytics__explain_metric,
  mcp__mis-mcp-generic-analytics__compare_kpi, mcp__mis-mcp-generic-analytics__rank_entities, mcp__mis-mcp-generic-analytics__breakdown_metric,
  mcp__mis-mcp-generic-analytics__query_metric, mcp__mis-mcp-generic-analytics__search_records, mcp__mis-mcp-generic-analytics__get_record,
  mcp__mis-mcp-generic-analytics__get_related_records, mcp__mis-mcp-generic-analytics__render_chart, mcp__mis-mcp-generic-analytics__run_safe_query
---

Use this skill for questions about this business's data and its KPIs.

1. Call get_kpi("average_measure") - Average of Primary Measure.
2. Call get_kpi("sum_measure") - Sum of Primary Measure.
3. Call get_kpi("total_records") - Total Records.
4. Call get_kpi("trend_by_month") - Trend by Month.
5. Summarize the results in plain business language, calling out anything unusual.
