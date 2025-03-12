# Storage & Databases on AWS
## 1. Storage

### Storage Types on AWS

- **File Storage:**
    - Organizes files in a hierarchical structure (like folders).
    - Ideal for centralized access and sharing among multiple computers.
    - Common use cases include large content repositories and development environments.
- **Block Storage:**
    - Splits files into fixed-size chunks called blocks, each with its own address.
    - Allows for efficient retrieval and modification of data.
    - Optimized for high-performance workloads, such as databases.
- **Object Storage:**
    - Stores data as objects in a flat structure, each with a unique identifier.
    - Easier to scale and suitable for large datasets and unstructured files.
    - Changing data requires updating the entire object.

**Block Storage vs. Object Storage:**
    - **Block Storage:** Files are split into fixed-size chunks (blocks). This allows for easy updates, as you can change just the block that needs modification.
    - **Object Storage:** Each file is treated as a single unit. To change a file, the entire file must be updated, which can be less efficient for frequent changes.

- Usage Recommendations:
    - Object Storage is suitable for static data (like photos) that is accessed often but modified rarely.
    - Block Storage is better for frequently updated data or high transaction rates (like application files).

### Amazon EC2 Instance Storage and Amazon Elastic Block Store

- **Block Storage Types:**
    - Instance Store:
        - Directly attached storage to the physical server.
        - Fast access but data is lost if the instance is stopped or terminated.
    - Amazon Elastic Block Store (EBS):
        - Network-attached storage that persists even if the EC2 instance is stopped or terminated.
        - Allows multiple EBS volumes to be attached to a single instance.
        - Supports EBS Multi-Attach for attaching to multiple instances simultaneously.
- **Data Backup:**
    - EBS volumes can be backed up using snapshots, which are incremental backups stored redundantly.

