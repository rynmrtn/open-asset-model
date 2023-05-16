# Open Asset Model Specification

## Goals

The Open Asset Model is an effort to uniformly describe assets
that belong to both organizations and individuals.

Asset specifications have traditionally focused upon the technical,
infrastructure-specific things that can be discovered on the internet.
While this represents a potentially significant portion of an organization's
assets, it is also limiting. The Open Asset Model seeks to expand on
this and cover the breadth and depth of both physical and digital assets.

Open Asset Model defines not just the assets themselves, but also the
relationships within and across types of assets. This allows the model
to express the real-world interconnectedness that exist between assets.

## Non-Goals

[anything to include here?]

## Source & Data Provenance

When it comes to asset discovery, it is sometimes a bit of a mystery as to
how an asset was discovered.

Source can also imply the trustworthiness and/or accuracy of the data.

Another important reason for tracking the source of an asset is to
ensure modern data privacy requirements. Depending upon where you obtained
the information, there may exist restrictions with regard to how it is used
and who it can be shared with.

## Assets

### Domain

#### FQDN

| Property | Type | Required | Description |
| -------- | ---- | -------- | ----------- |
| `name` | string | true | Fully Qualitified Domain Name |

##### Outgoing Relationships

| Relationships | Type | Description |
| -------- | ---- | ----------- |
| `a_record` | `IPAddress` | IPv4 address that fqdn resolves to |
| `aaaa_record` | `IPAddress` | IPv6 address that fqdn resolves to |
| `cname_record` | `FQDN` | type = "CNAME" |
| `ns_record` | `FQDN` | ... |
| `cname_record` | `FQDN` | ... |


##### Incoming Relationships

| Relationship | Type | Description |
| ------------ | ---- | ----------- |
| `ns_record` | `FQDN` | ... |
| `cname_record` | `FQDN` | ... |

### Network

#### AutonomousSystem

| Property | Type | Required | Description |
| -------- | ---- | -------- | ----------- |
| `number` | int | true | Fully Qualitified Domain Name |

##### Outgoing Relationships

| Relationship | Type | Description |
| ------------ | ---- | ----------- |
| `accounces` | `Netblock` | ... |
| `managed_by` | `RIROrganization` | ... |

##### Incoming Relationships

| Relationship | Type | Description |
| ------------ | ---- | ----------- |
| No incoming relationships | |

#### IP Address

| Property | Type | Required | Description |
| -------- | ---- | -------- | ----------- |
| `address` | object | true | Address |
| `type` | string | true | IPV4 or IPV6 |

##### Outgoing Relationships

| Relationship | Type | Description |
| ------------ | ---- | ----------- |
| No outgoing relationships | |

##### Incoming Relationships

| Relationship | Type | Description |
| ------------ | ---- | ----------- |
| `a_record` | `FQDN` | ... |
| `aaaa_record` | `FQDN` | ... |
| `contains` | `Netblock` | ... |

#### Netblock

| Property | Type | Required | Description |
| -------- | ---- | -------- | ----------- |
| `cidr` | object | true | CIDR representation of an  IP block |
| `type` | string | true | IPV4 or IPV6 |

##### Outgoing Relationships

| Relationship | Type | Description |
| ------------ | ---- | ----------- |
| `contains` | `IPAddress` | ... |

##### Incoming Relationships

| Relationship | Type | Description |
| ------------ | ---- | ----------- |
| `accounces` | `AutonomousSystem` | ... |rir

#### RIROrganization

| Property | Type | Required | Description |
| -------- | ---- | -------- | ----------- |
| `name` | integer | Autonomous System Number |
| `rir_id` | string | the unique identifier of the RIR organization |
| `rir` | string | Regional Internet Registry |

##### Outgoing Relationships

| Relationship | Type | Description |
| ------------ | ---- | ----------- |
| No outgoing relationships | |


##### Incoming Relationships

| Relationship | Type | Description |
| ------------ | ---- | ----------- |
| `managed_by` | `AutonomousSystem` | ... |

