## Copilot instructions for Google Cloud Storage documentation

### Repository overview
Product: Google Cloud Storage (managed through NetApp Console)

This repository contains documentation for managing Google Cloud Storage buckets through the NetApp Console, including discovering buckets, adding and configuring buckets, and integrating buckets with NetApp data services.

### Repository structure
- `task-viewing-gcp-storage.adoc` – How to discover and view Google Cloud Storage buckets in NetApp Console after installing a Console agent
- `task-add-gcp-bucket.adoc` – Step-by-step instructions for adding new buckets, including project, location, storage class, protection, and encryption settings
- `task-change-gcp-bucket-settings.adoc` – How to change editable bucket properties (storage class, labels, turbo replication) from the Console
- `task-gcp-enable-data-services.adoc` – How to use NetApp data services (Backup and Recovery, Cloud Tiering, Copy and Sync) with Google Cloud Storage buckets
- `task-support-registration.adoc` – How to register for NetApp support
- `task-get-help.adoc` – How to get help and open support cases
- `whats-new.adoc` – Release notes landing page that includes content from `_whatsnew/`
- `_whatsnew/` – Release notes content fragments included by `whats-new.adoc`; one file per release date
- `_include/` – Reusable AsciiDoc content fragments shared across pages
- `media/` – Screenshots and button images referenced by documentation pages
- `_index.yml` – Landing page tile configuration
- `project.yml` – Site settings and sidebar navigation structure

### Product-specific context

**Architecture and components:**
- *NetApp Console* is the central management platform (formerly BlueXP) through which users discover and manage Google Cloud Storage; all Console operations are performed from the Console UI
- *Console agent* is a software component installed in a Google Cloud account; it enables the NetApp Console to automatically discover Google Cloud Storage buckets in that account
- *Google Cloud Storage system* is the representation of a discovered Google Cloud account's storage within the NetApp Console Systems page
- NetApp data services connect to a Google Cloud Storage system by drag-and-drop on the Systems page or through the Services panel

**Key concepts:**
- *Bucket discovery* occurs automatically after a Console agent is installed in the Google Cloud account; no manual import is needed
- *Storage class* controls cost and retrieval behavior for objects; options are Standard, Nearline, Coldline, Archive, and Autoclass (which adjusts the class automatically based on access patterns)
- *Location type* determines geographic redundancy: Region (single), Dual-region (two regions within a continent), or Multi-region (broad geographic area)
- *Turbo replication* is a dual-region option that guarantees geo-redundancy for newly written objects within 15 minutes; only available for dual-region buckets
- *Object versioning* and *retention policy* are mutually exclusive data protection tools that cannot be enabled simultaneously on the same bucket
- *Customer-managed encryption keys (CMEK)* can replace the default Google-managed encryption keys; keys must be created in Google Cloud before bucket creation

**Naming conventions and terminology:**
- The management platform is called *NetApp Console* (not BlueXP, which was the former name)
- The agent installed in Google Cloud is called *Console agent* (not Connector or BlueXP Connector)
- The collection of discovered GCS resources appears as a *Google Cloud Storage system* on the Systems page
- *Labels* in Google Cloud Storage are key:value metadata pairs (maximum 10 per bucket); the term "tag" is not used for this concept in GCS
- NetApp data services referenced in this documentation: *NetApp Backup and Recovery*, *NetApp Cloud Tiering*, *NetApp Copy and Sync*
- The three-dot action menu is referred to as the *more button* (image: `button-horizontal-more.gif`)

**Technical constraints:**
- Bucket name, Google project, and protection settings cannot be changed after bucket creation
- Object versioning and retention policy cannot be enabled on the same bucket simultaneously
- Turbo replication is only available for dual-region location types
- Storage class cannot be changed to Autoclass if a non-Autoclass storage class was selected at creation, and cannot be changed from Autoclass to another class unless Autoclass is first disabled

### Typical user workflows

**Discover and view Google Cloud Storage buckets:** Install Console agent in Google Cloud account → Open NetApp Console → Navigate to Storage > Management → Google Cloud Storage system appears automatically → Select system to view bucket details

**Add a new bucket:** Open Google Cloud Storage system in NetApp Console → Click *Add bucket* → Enter project details (name, Google project, labels) → Select location type and region(s) → Select storage class → Configure protection and encryption settings → Click *Add*

**Change bucket settings:** Open Google Cloud Storage system → Click the more button for a bucket → Select *Edit bucket details* → Modify storage class, labels, or turbo replication → Save changes

**Enable a NetApp data service for GCS:** Open Systems page in NetApp Console → Drag and drop source/target system onto the Google Cloud Storage system → Follow service-specific setup steps for Backup and Recovery, Cloud Tiering, or Copy and Sync
