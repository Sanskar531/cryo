# 🧠 myfs-kmod Kernel Filesystem Ticket List

## Phase 1: Bootstrapping
- [ ] Set up kernel module build with `Makefile`
- [ ] Register filesystem type with VFS
- [ ] Implement `myfs_mount()` using `mount_bdev`
- [ ] Implement `myfs_fill_super()` to load superblock
- [ ] Define and assign `super_operations`

## Phase 2: Disk Access
- [ ] Use `sb_bread()` to read blocks
- [ ] Add block allocator using a free block bitmap
- [ ] Create simple on-disk `superblock` and `inode` structs
- [ ] Add helper functions for reading/writing inodes

## Phase 3: Inodes & Dentries
- [ ] Implement `myfs_iget()` to load inode from disk
- [ ] Assign `inode_operations` (e.g. lookup, create)
- [ ] Create simple `dentry` → `inode` path resolution

## Phase 4: File Operations
- [ ] Define `file_operations` with `read`, `write`
- [ ] Use `generic_file_read_iter`, `generic_file_write_iter`
- [ ] Implement `myfs_get_block()` for buffer_head mapping

## Phase 5: Directory Support
- [ ] Implement directory format using fixed-size entries
- [ ] Support `readdir`, `mkdir`, `rmdir`, `unlink`
- [ ] Add hashing for faster directory lookups

## Phase 6: Allocation
- [ ] Implement `alloc_inode()`, `free_inode()`
- [ ] Implement `alloc_block()`, `free_block()`
- [ ] Add journaling placeholder for future WAL

## Phase 7: Debugging & Testing
- [ ] Add `mkmyfs` userspace tool to format image or device
- [ ] Add `fsck` tool to check on-disk structures
- [ ] Use `dmesg` and `printk()` for trace-level logging
- [ ] Test with `mount -t myfs /dev/loop10 /mnt/myfs`

## Phase 8: Advanced Features
- [ ] Add extent-based allocation
- [ ] Add inline small file support in inodes
- [ ] Add journaling layer
- [ ] Add support for sparse files and indirect blocks
