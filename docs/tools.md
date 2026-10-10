# Hosted tool reference

This inventory covers tools exposed by the hosted user endpoint at `https://mcp.rudderstack.com/mcp`. Availability depends on your RudderStack plan, workspace permissions, enabled products, and server configuration.

## Classifications

- **Read** — inspects RudderStack configuration, metadata, metrics, or documentation without persisting a control-plane change.
- **Sensitive execution** — does not persist control-plane configuration, but executes transformation code or submits temporary warehouse work. Review inputs and outputs carefully.
- **Write** — persists session state or changes RudderStack control-plane configuration. MCP clients should request confirmation before invocation.

The hosted service also provides a separately controlled read-only web surface. Its allow-list includes the tools marked **Read** or **Sensitive execution** below except `user_details`; write tools are excluded.

## User and workspace

| Tool | Access | Purpose |
| --- | --- | --- |
| `user_details` | Read | Get the current user, accessible workspaces, and active workspace context. |
| `user_switch_workspace` | **Write** | Change and persist the active workspace for the MCP session. |
| `get_workspace_settings` | Read | Get details and settings for the current workspace. |
| `list_connections` | Read | List source-to-destination connections. |
| `get_billing_details` | Read | Get contract volume, plan, organization, and owner information. |

## Sources

| Tool | Access | Purpose |
| --- | --- | --- |
| `list_sources` | Read | List configured event-stream and Reverse ETL sources. |
| `get_source` | Read | Get source configuration, tracking plans, and connected destinations. |
| `get_source_definitions` | Read | Get source-definition metadata, schemas, and capabilities. |
| `get_source_event_schemas` | Read | Get incoming event schemas for a source. |
| `get_source_event_metrics` | Read | Get source event-volume and filtering metrics. |
| `get_source_tracking_plans_and_versions` | Read | Get a source's tracking-plan associations and versions. |
| `get_source_tracking_plan_event_metrics` | Read | Get tracking-plan validation and violation metrics. |
| `get_source_tracking_plan_event_violations` | Read | Get tracking-plan validation failures and redacted samples when available. |
| `get_source_event_names_similarity` | Read | Find similar or duplicate source event names. |
| `get_source_event_properties` | Read | Get observed property types and frequency for an event. |

## Destinations

| Tool | Access | Purpose |
| --- | --- | --- |
| `list_destinations` | Read | List workspace destinations. |
| `get_destination` | Read | Get destination configuration, connected sources, and transformations. |
| `get_destinations_errors` | Read | Get delivery failures and redacted samples when available. |
| `get_destination_event_metrics` | Read | Get delivery success, failure, and filtering metrics. |
| `get_destination_definitions` | Read | Get destination-definition metadata, schemas, and capabilities. |
| `get_destination_latency_metrics` | Read | Get destination latency over time. |

## Transformations and libraries

| Tool | Access | Purpose |
| --- | --- | --- |
| `transformation_test_new` | **Sensitive execution** | Execute unsaved JavaScript or Python transformation code against supplied events without saving it. |
| `transformation_test_existing` | **Sensitive execution** | Execute a saved transformation against supplied events without changing it. |
| `sample_transformations` | Read | Browse pre-built transformation templates. |
| `upsert_transformation` | **Write** | Create or update a JavaScript or Python transformation. |
| `connect_transformation_destination` | **Write** | Attach a transformation to a destination. |
| `list_transformations` | Read | List transformations and their destination connections. |
| `get_transformation` | Read | Get transformation details, source code, and configuration. |
| `get_transformation_event_metrics` | Read | Get transformation volumes, outcomes, and errors over time. |
| `get_transformation_latency_metrics` | Read | Get transformation latency over time. |
| `list_transformation_libraries` | Read | List custom workspace transformation libraries. |
| `get_transformation_library` | Read | Get a custom transformation library, including source code. |
| `list_rudderstack_transformation_libraries` | Read | List pre-built RudderStack transformation libraries. |

## Warehouse, Reverse ETL, tracking plans, and data catalog

| Tool | Access | Purpose |
| --- | --- | --- |
| `get_warehouse_uploads` | Read | Get warehouse upload history, status, and optional table details. |
| `get_warehouse_upload_with_tables` | Read | Get table-level details for one warehouse upload. |
| `get_retl_source_syncs` | Read | Get Reverse ETL sync results, metrics, and timing. |
| `list_tracking_plans` | Read | List tracking plans and governance rules. |
| `list_tracking_plan_events` | Read | List tracking-plan events and optional schemas. |
| `list_data_catalog_events` | Read | List events in the data catalog. |
| `list_data_catalog_properties` | Read | List event properties in the data catalog. |

## Live events and profiles

| Tool | Access | Purpose |
| --- | --- | --- |
| `get_live_events` | Read | Poll real-time source, destination, and transformation events. Live event content can be sensitive even when fields are redacted or hashed. |
| `list_profiles` | Read | List profile projects for the workspace. |
| `get_profile_details` | Read | Get profile models, statistics, cohort features, or history. |
| `get_profile_artifacts` | Read | List task artifacts or retrieve artifact-file content. |

## Audit and audiences

| Tool | Access | Purpose |
| --- | --- | --- |
| `audit_logs` | Read | List workspace audit-log entries. |
| `list_audience_subjects` | Read | List data-graph entities that can be audience subjects. |
| `get_audience_model_context` | Read | Get model attributes, relationships, neighbors, and peer audiences. |
| `load_audience_skill` | Read | Load the audience-expression grammar used to construct valid requests. |
| `create_audience` | **Write** | Create and persist a data-graph audience. |
| `update_audience` | **Write** | Update a persisted data-graph audience. |
| `get_audience` | Read | Get an audience and its stored expression and metadata. |
| `preview_audience` | **Sensitive execution** | Submit temporary warehouse preview work to estimate audience size. |

## Activation

| Tool | Access | Purpose |
| --- | --- | --- |
| `get_audience_destination_schema` | Read | Discover valid destination fields and destination-side audiences. |
| `connect_audience_destination` | **Write** | Persist an audience-to-destination activation connection. |

## Documentation and service status

These tools are registered only when the corresponding hosted integration is configured.

| Tool | Access | Purpose |
| --- | --- | --- |
| `search_docs` | Read | Search RudderStack documentation. |
| `ask_docs` | Read | Get a documentation-grounded answer with citations. |
| `list_statuspage_incidents` | Read | List recent RudderStack status-page incidents. |
| `get_statuspage_incident` | Read | Get one incident, its updates, and affected components. |

## Inventory summary

When all optional integrations are configured, the endpoint exposes **58 tools**: 49 read tools, 3 sensitive-execution tools, and 6 write tools. Four read tools are conditional, so a typical workspace may expose fewer tools.

Feature-flag administration is not part of this hosted user endpoint. In particular, there is no `set_feature_flag` tool on `/mcp`; feature-flag controls belong to a separate administrative surface.
