# ⚙️ Project: High-Performance, Bespoke Filesystem in C

A custom block-based filesystem with exotic, bleeding-edge ideas for performance, resilience, and innovation.

---

## 📦 Phase 1: Disk Abstraction & Utilities

- [ ] Implement low-level block I/O over a file using `pread`/`pwrite`
- [ ] Support block sizes of 512B, 4KB, and 64KB with runtime selection
- [ ] Add sector-alignment verification
- [ ] Implement `mkfs` utility to create a clean FS image
- [ ] Add debug tools to dump block contents (`dumpfs`)

---

## 🌲 Phase 2: On-Disk Format and Structures

- [ ] Design a superblock with space for plugin hooks, feature flags, UUID, label
- [ ] Define inode format with:
  - direct blocks
  - indirect, double-indirect blocks
  - extents (start, len) support
- [ ] Design support for inline files (small files stored inside inode)
- [ ] Add type-safe tagged union for different inode types: file, dir, symlink, socket
- [ ] Implement `dir_entry_t` structure with hash-based indexing for fast lookups

---

## 🔢 Phase 3: Block / Inode Allocation

- [ ] Bitmap-based allocator for both blocks and inodes
- [ ] Next-fit allocator fallback for fragmentation reduction
- [ ] Implement persistent allocation log (append-only)
- [ ] Add high-entropy randomization for block placement (anti-fragmentation under load)
- [ ] Group allocator support: allocate in block groups with locality hints

---

## 🧾 Phase 4: Journaling and Transaction System

- [ ] Implement Write-Ahead Log (WAL) with:
  - Ordered metadata journaling
  - Data+metadata full journaling mode
- [ ] Add journal transaction batching
- [ ] Crash consistency recovery from unclean shutdown
- [ ] Redo log and checkpoint system

---

## 🔍 Phase 5: Directory System

- [ ] Implement scalable hash-based directories (HTree-style)
- [ ] Add support for collision resolution via chaining
- [ ] Optimize directory scan with bloom filter pre-check
- [ ] Support long filename entries and UTF-8 encoding
- [ ] Add parent-backlink pointer to detect cycles and repair

---

## 🧠 Phase 6: File Data I/O

- [ ] Read/write API with bounds and indirect resolution
- [ ] Memory-mapped read mode using `mmap` for fast I/O
- [ ] Async prefetching for sequential reads (read-ahead)
- [ ] Write buffering and journaling integration
- [ ] Support large sparse files with hole punching

---

## 📁 Phase 7: Feature-Rich Filesystem API

- [ ] `open`, `read`, `write`, `close`, `truncate`, `mkdir`, `unlink`, `rename`
- [ ] Add `stat`, `fstat`, and `lstat` support
- [ ] Implement symbolic links (fast path in inode)
- [ ] Add FUSE integration for full user-space mounting
- [ ] Optional POSIX ACL support in extended attributes

---

## 🧬 Phase 8: Performance Optimizations

- [ ] LRU-based inode/block cache with clock sweep eviction
- [ ] Extent-based allocation: contiguous block runs to reduce seek
- [ ] Delayed allocation for small writes
- [ ] Adaptive compression (per-file LZ4, ZSTD with thresholds)
- [ ] Alignment-aware IO for NVMe drives

---

## 🧩 Phase 9: Bespoke & Exotic Features

- [ ] **Deduplication engine**: detect and merge duplicate blocks
- [ ] **Inode versioning**: keep historical snapshots of files
- [ ] **Merkle tree for integrity**: detect corruption with per-file hashes
- [ ] **Hybrid extent+indirect pointer model** for flexible scaling
- [ ] **Transactional snapshot**: atomic snapshot via COW block remap
- [ ] **User-defined file metadata** schema (key-value indexing)
- [ ] **Per-directory compression policies**
- [ ] **Self-healing inode tables** with CRC checks and rebuild
- [ ] **Per-inode journaling levels** (some files journaled, some not)
- [ ] **Speculative prefetching** using branch-predicted file access patterns

---

## 🌐 Phase 10: Scalability & Distributed Hooks

- [ ] Add support for remote block fetch (future: cluster FS)
- [ ] Add checkpointable block replay log for distributed sync
- [ ] Design plugin hooks for networking or remote inode resolution

---

## 🧪 Phase 11: Tooling and Testing

- [ ] CLI `fsck` tool to verify and repair image
- [ ] File-based unit test coverage for allocator, journal, inode
- [ ] Fuzzer for path resolution and directory tree corruption
- [ ] Performance benchmark: write/read 100k files with profiling
- [ ] Integration with `strace`/`perf` to inspect syscall overhead

---

## 📦 Phase 12: Packaging and Docs

- [ ] Provide static `mkfs`, `fsck`, `mount-fuse` binaries
- [ ] Add JSON output for FS tools for scripting integration
- [ ] Full design spec documentation (`docs/spec.md`)
- [ ] Blog or whitepaper-style writeup on performance design
- [ ] Run comparison against ext4, XFS, btrfs (benchmark suite)
