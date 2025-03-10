# Storage & Databases on AWS
## 1. Storage

### Storage Types on AWS

**Block Storage vs. Object Storage:**

- There are two main types of storage:
    - **Block Storage:** Files are split into fixed-size chunks (blocks). This allows for easy updates, as you can change just the block that needs modification.
    - **Object Storage:** Each file is treated as a single unit. To change a file, the entire file must be updated, which can be less efficient for frequent changes.

- Usage Recommendations:
    - Object Storage is suitable for static data (like photos) that is accessed often but modified rarely.
    - Block Storage is better for frequently updated data or high transaction rates (like application files).