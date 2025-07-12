# ✅ cryo-kmod: Exotic Kernel Filesystem Ticket List

---

## 📦 Phase 1: Kernel Module Bootstrapping

- [ ] Set up kernel module build with `Makefile`
- [ ] Register filesystem with VFS (`file_system_type`)
- [ ] Implement `myfs_mount()` using `mount_bdev()`
- [ ] Implement `myfs_fill_super()` to load the superblock
- [ ] Define `super_operations`, `inode_operations`, `file_operations`
- [ ] Implement dummy root inode + dentry

---

## 🧱 Phase 2: Disk I/O Layer

- [ ] Implement block read/write abstraction with `sb_bread()` and `sb_getblk()`
- [ ] Support block sizes: 4K and 64K (runtime tunable)
- [ ] Implement block bitmap allocator (alloc, free)
- [ ] Create `fs_structs.h` with `superblock_t`, `inode_t`, `dir_entry_t`

---

## 📂 Phase 3: Inode Management

- [ ] Implement inode allocator and free list
- [ ] Add `myfs_iget()` to load inode from disk
- [ ] Implement inode flags, sizes, timestamps, UID/GID
- [ ] Add support for symbolic links and sockets
- [ ] Track per-inode journaling mode (full/meta/none)

---

## 📁 Phase 4: Directory System

- [ ] Implement fixed-size dir entry format
- [ ] Add `lookup()`, `create()`, `mkdir()`, `rmdir()`, `unlink()`
- [ ] Add parent directory backlink (cycle detection)
- [ ] Hash-based directory indexing (HTree-style)
- [ ] Add Bloom filter for directory lookups

---

## 📄 Phase 5: File Data I/O

- [ ] Implement `read_iter`, `write_iter` using buffer_heads
- [ ] Add indirect block support for large files
- [ ] Support extent-based allocation for contiguous files
- [ ] Add inline small file support (store in inode if small)
- [ ] Add truncate, seek, and partial read/write support
- [ ] Add compression support (zstd/lz4, per-block)
- [ ] Add sparse file support with hole punching

---

## 🧾 Phase 6: Journaling & Transaction System

- [ ] Design journal entry format (WAL-style)
- [ ] Implement `start_tx()`, `log_op()`, `commit_tx()`
- [ ] Add journal replay on mount
- [ ] Add per-inode journaling level flag
- [ ] Implement journal ring buffer variant (low write amp)

---

## ⚙️ Phase 7: Advanced Block Layout & Metadata

- [ ] Add hybrid extents + indirect pointer format
- [ ] Implement self-healing allocator: track extents with red-black tree
- [ ] Implement block-type tagging (inode/data/journal/etc.)
- [ ] Implement persistent slab allocator for metadata regions
- [ ] Add Merkle tree generation per file
- [ ] Add per-block checksums and integrity verification

---

## 🧪 Phase 8: Caching, Metrics, and Background Tasks

- [ ] Implement adaptive LRU-K block cache
- [ ] Add read-ahead for sequential file reads
- [ ] Add write-behind buffering with delayed allocation
- [ ] Add live metrics exposed via `/proc/myfs/stats`
- [ ] Add block reuse tracking and mount-time analytics
- [ ] Add background defragmentation daemon

---

## 🔁 Phase 9: Copy-on-Write + Snapshot Features

- [ ] Implement block-level reference counting
- [ ] Add snapshot table and snapshot creation system call
- [ ] Copy-on-write updates for snapshot-tracked blocks
- [ ] Time-travel recovery for files from snapshot diffs

---

## 🌀 Phase 10: Deduplication, Quotas, Encryption

- [ ] Add transparent deduplication (SHA-256 per-block)
- [ ] Maintain block hash table with reference count
- [ ] Add per-user UID/GID quota support
- [ ] Implement basic block-level encryption (XOR or ChaCha20)
- [ ] Encrypt inode metadata per user

---

## 🧩 Phase 11: Experimental Features

- [ ] Pluggable metadata backend (B+Tree, LSM-tree, HashMap)
- [ ] Preallocated file templates for fast log file creation
- [ ] Custom inode layout schema per user-defined type
- [ ] Journaling configuration override per directory
- [ ] Tiered storage simulation: hot/cold file movement

---

## 🧰 Phase 12: Tools, Testing, and Utilities

- [ ] Write `mkmyfs` formatting tool to build superblock and root inode
- [ ] Write `fsck.myfs` to verify and repair structures
- [ ] Add file fuzzing test tool (`fs_fuzz`) for lookup/corruption testing
- [ ] Add test harness that mounts/unmounts and verifies block state
- [ ] Add benchmarking tool: `fsbench` (files/sec, ops/sec, write amp)

---

## 🧪 Bonus Features for Bragging Rights

- [ ] Time-travel file recovery
- [ ] Filesystem scrubbing daemon
- [ ] Filesystem visualizer (graph block allocation)
- [ ] Built-in telemetry + debugging shell
- [ ] Filesystem event tracing + journaling log viewer
- [ ] Crash simulation/recovery tester with snapshot rewind

