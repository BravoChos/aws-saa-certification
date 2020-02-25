# Instance Store
An Instance Store provides temporary block-level storage for your instance. This storage is located on disks that are physically attached to the host computer. Instance store is ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temprary content, or for data that is replicated across a fleet of instaces, such as a load-balanced pool of web servers.

## Instance Store lifetime
You can specify instance store volumes for an instance only when you launch it. You can't detach an instance volume from one instace and attach it to a differnt instance.

The data in an instance store persists only during the lifetime of its associated instance. If an instance reboots(intentionally or unintentionally), data in the instance store persists. However, data in the instance store is lost under any of the following circumstances:

- The underlying disk drive fails
- The instance stops running
- The instance terminates

**Note:**
Some instance types do not support instant store volumes.