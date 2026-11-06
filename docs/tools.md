# Hosted tool reference

This inventory covers tools exposed by the hosted user endpoint at `https://mcp.rudderstack.com/mcp`. Availability depends on your RudderStack plan, workspace permissions, enabled products, and server configuration.

Use `user_details` to find your accessible workspace IDs. Every workspace tool requires a `workspace_id` (or `workspaceId`) on each call; omitting it fails with `workspace_id is required`. The endpoint is stateless and does not use `Mcp-Session-Id`.

## Classifications

- **Read** — inspects RudderStack configuration, metadata, metrics, or documentation without persisting a control-plane change.
- **Sensitive execution** — does not persist control-plane configuration, but executes transformation code or submits temporary warehouse work. Review inputs and outputs carefully.
- **Write** — changes RudderStack control-plane configuration or triggers a sync. MCP clients should request confirmation before invocation.

The hosted service also provides a separately controlled read-only web surface. Its allow-list includes the tools marked **Read** or **Sensitive execution** below except `user_details`, `plan_audience_activation`, and `list_sync_runs`; write tools are excluded. The allow-list includes `get_retl_failed_records`.

## User and workspace

| Tool | Access | Purpose |
| --- | --- | --- |
| `user_details` | Read | Get the current user and accessible workspace IDs. |
| `get_workspace_settings` | Read | Get details and settings for the specified workspace. |
| `list_connections` | Read | List source-to-destination connections. |
| `get_billing_details` | Read | Get contract volume, plan, organization, and owner information. |

## Sources

| Tool | Access | Purpose |
| --- | --- | --- |
| `list_sources` | Read | List configured event-stream and Reverse ETL sources. |
| `get_source` | Read | Get source configuration, tracking plans, and connected destinations. |
| `get_source_definitions` | Read | Get source-definition metadata and capabilities, with configuration schemas when requested. |
| `get_source_event_schemas` | Read | List observed event types and names for a source, with counts and first/last seen times. |
| `get_source_event_metrics` | Read | Get source event-volume and filtering metrics. |
| `get_source_tracking_plans_and_versions` | Read | Get a source's tracking-plan associations and versions. |
| `get_source_tracking_plan_event_metrics` | Read | Get tracking-plan validation and violation metrics. |
| `get_source_tracking_plan_event_violations` | Read | Get tracking-plan validation failures, with optional sample events (values in `properties` and `traits` are hashed) and optional sample responses. |
| `get_source_event_names_similarity` | Read | Find similar or duplicate source event names. |
| `get_source_event_properties` | Read | Get observed property types and frequency for an event. |

## Destinations

| Tool | Access | Purpose |
| --- | --- | --- |
| `list_destinations` | Read | List workspace destinations. |
| `get_destination` | Read | Get destination configuration, connected sources, and transformations. |
| `get_destinations_errors` | Read | Get delivery failures, with optional sample events (request header and body values are hashed) and optional destination responses. |
| `get_destination_event_metrics` | Read | Get delivery success, failure, and filtering metrics. |
| `get_destination_definitions` | Read | Get destination-definition metadata and capabilities, with configuration schemas when requested. |
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
| `get_retl_failed_records` | **Sensitive execution** | Page and filter a finished Reverse ETL run's failed destination records (first 5,000 per run unless filtered). Errors may contain customer data; warehouse queries incur customer charges. |
| `list_tracking_plans` | Read | List tracking plans and governance rules. |
| `list_tracking_plan_events` | Read | List tracking-plan events and optional schemas. |
| `list_data_catalog_events` | Read | List events in the data catalog. |
| `list_data_catalog_properties` | Read | List event properties in the data catalog. |

## Live events and profiles

| Tool | Access | Purpose |
| --- | --- | --- |
| `get_live_events` | Read | Poll real-time events for the sources, destinations, or transformations you name. Turns on live-event capture for them and refreshes it while polling; capture stays on for about 5 minutes after the last refresh. |
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
| `preview_audience` | **Sensitive execution** | Submit temporary warehouse work to estimate matching rows, total subject rows, and audience percentage. |

## Activation

| Tool | Access | Purpose |
| --- | --- | --- |
| `get_audience_destination_schema` | Read | Discover destination identifier fields, existing audiences, and mapping guidance for activation. |
| `connect_audience_destination` | **Write** | Connect a data-graph audience to an existing destination audience with identifier mappings; mirrored syncs remove nonmembers from the destination audience. |

## Audience activation (rETL)

These four tools are available only for workspaces with audience activation enabled. They operate on SQL-defined Reverse ETL audience sources (`sql-audience`, discoverable with `list_sources`), not data-graph audiences. To connect a data-graph audience to a destination, use `connect_audience_destination`.

| Tool | Access | Purpose |
| --- | --- | --- |
| `plan_audience_activation` | **Sensitive execution** | Plan an audience activation and review the configuration before creation. Later planning steps run the audience's query on your warehouse to read its columns. |
| `create_audience_activation` | **Write** | Create a destination and Reverse ETL connection for an audience activation; mirrored syncs remove nonmembers from the chosen ad-platform audience. |
| `trigger_sync` | **Write** | Trigger an audience-activation sync; mirrored syncs remove people no longer in the audience from the ad-platform audience. |
| `list_sync_runs` | Read | List recent audience-activation sync runs and their results. |

## Documentation and service status

These tools are registered only when the corresponding hosted integration is configured.

| Tool | Access | Purpose |
| --- | --- | --- |
| `search_docs` | Read | Search RudderStack documentation. |
| `ask_docs` | Read | Get a documentation-grounded answer with citations. |
| `list_statuspage_incidents` | Read | List recent RudderStack status-page incidents. |
| `get_statuspage_incident` | Read | Get one incident, its updates, and affected components. |

## Inventory summary

With optional hosted integrations configured and audience activation enabled for the workspace, the endpoint exposes up to **62 tools**: 50 Read, 5 Sensitive execution, and 7 Write. Four Read tools depend on optional documentation and service-status integrations; another four tools (1 Read, 1 Sensitive execution, and 2 Write) depend on per-workspace audience activation.
