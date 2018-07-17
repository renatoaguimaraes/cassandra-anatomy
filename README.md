# cassandra-anatomy

### fqltool

```
dump -  Dump the contents of a full query log
  args: <path1> [<path2>...<pathN>] -  Path containing the full query logs to dump.
  option: [--roll-cycle] -  How often to roll the log file was rolled. May be necessary for Chronicle to correctly parse file names. (MINUTELY, HOURLY, DAILY). Default HOURLY.
  option: [--follow] -  Upon reacahing the end of the log continue indefinitely waiting for more records
```

### nodetool

```
assassinate -  Forcefully remove a dead node without re-replicating any data.  Use as a last resort if you cannot removenode
  args: <ip_address> -  IP address of the endpoint to assassinate
resume -  Resume bootstrap streaming
cleanup -  Triggers the immediate cleanup of keys no longer belonging to a node. By default, clean all keyspaces
  args: [<keyspace> <tables>...] -  The keyspace followed by one or many tables
  option: [-j, --jobs] -  Number of sstables to cleanup simultanously, set to 0 to use all available compaction threads
clearsnapshot -  Remove the snapshot with the given name from the given keyspaces. If no snapshotName is specified we will remove all snapshots
  args: [<keyspaces>...]  -  Remove snapshots from the given keyspaces
  option: [-t] -  Remove the snapshot with a given name
  option: [--all] -  Removes all snapshots
clientstats -  Print information about connected clients
  option: [--all] -  Lists all connections
  option: [--by-protocol] -  Lists most recent client connections by protocol version
  option: [--clear-history] -  Clear the history of connected clients
compact -  Force a (major) compaction on one or more tables or user-defined compaction on given SSTables
  args: [<keyspace> <tables>...] or <SSTable file>... -  The keyspace followed by one or many tables or list of SSTable data files when using --user-defined
  option: [-s, --split-output] -  Use -s to not create a single big file
  option: [--user-defined] -  Use --user-defined to submit listed files for user-defined compaction
  option: [-st, --start-token] -  Use -st to specify a token at which the compaction range starts
  option: [-et, --end-token] -  Use -et to specify a token at which compaction range ends
compactionhistory -  Print history of compaction
  option: [-F, --format] -  Output format (json, yaml)
compactionstats -  Print statistics on compactions
  option: [-H, --human-readable] -  Display bytes in human readable form, i.e. KiB, MiB, GiB, TiB
decommission -  Decommission the *node I am connecting to*
  option: [-f, --force] -  Force decommission of this node even when it reduces the number of replicas to below configured RF
describecluster -  Print the name, snitch, partitioner and schema version of a cluster
describering -  Shows the token ranges info of a given keyspace
  args:  -  The keyspace name
disableauditlog -  Disable the audit log
disableautocompaction -  Disable autocompaction for the given keyspace and table
  args: [<keyspace> <tables>...] -  The keyspace followed by one or many tables
disablebackup -  Disable incremental backup
disablebinary -  Disable native transport (binary protocol)
disablefullquerylog -  Disable the full query log
disablegossip -  Disable gossip (effectively marking the node down)
disablehandoff -  Disable storing hinted handoffs
disablehintsfordc -  Disable hints for a data center
  args: <datacenter> -  The data center to disable
drain -  Drain the node (stop accepting writes and flush all tables)
enableauditlog -  Enable the audit log
  option: [--logger] -  Logger name to be used for AuditLogging. Default BinAuditLogger. If not set the value from cassandra.yaml will be used
  option: [--included-keyspaces] -  Comma separated list of keyspaces to be included for audit log. If not set the value from cassandra.yaml will be used
  option: [--excluded-keyspaces] -  Comma separated list of keyspaces to be excluded for audit log. If not set the value from cassandra.yaml will be used
  option: [--included-categories] -  Comma separated list of Audit Log Categories to be included for audit log. If not set the value from cassandra.yaml will be used
  option: [--excluded-categories] -  Comma separated list of Audit Log Categories to be excluded for audit log. If not set the value from cassandra.yaml will be used
  option: [--included-users] -  Comma separated list of users to be included for audit log. If not set the value from cassandra.yaml will be used
  option: [--excluded-users] -  Comma separated list of users to be excluded for audit log. If not set the value from cassandra.yaml will be used
enableautocompaction -  Enable autocompaction for the given keyspace and table
  args: [<keyspace> <tables>...] -  The keyspace followed by one or many tables
enablebackup -  Enable incremental backup
enablebinary -  Reenable native transport (binary protocol)
enablefullquerylog -  Enable full query logging
  option: [--roll-cycle] -  How often to roll the log file (MINUTELY, HOURLY, DAILY). Default HOURLY.
  option: [--blocking] -  If the queue is full whether to block producers or drop samples. Default true.
  option: [--max-queue-weight] -  Maximum number of bytes of query data to queue to disk before blocking or dropping samples. Default 256 megabytes.
  option: [--max-log-size] -  How many bytes of log data to store before dropping segments. Might not be respected if a log file hasn't rolled so it can be deleted. Default 16 gigabytes.
  option: [--path] -  Path to store the full query log at. Will have it's contents recursively deleted. If not set the value from cassandra.yaml will be used.
enablegossip -  Reenable gossip
enablehandoff -  Reenable future hints storing on the current node
enablehintsfordc -  Enable hints for a data center that was previsouly disabled
  args: <datacenter> -  The data center to enable
failuredetector -  Shows the failure detector information for the cluster
flush -  Flush one or more tables
  args: [<keyspace> <tables>...] -  The keyspace followed by one or many tables
garbagecollect -  Remove deleted data from one or more tables
  args: [<keyspace> <tables>...] -  The keyspace followed by one or many tables
  option: [-g, --granularity] -  Granularity of garbage removal. ROW (default) removes deleted partitions and rows, CELL also removes overwritten or deleted cells.
  option: [-j, --jobs] -  Number of sstables to cleanup simultanously, set to 0 to use all available compaction threads
gcstats -  Print GC Statistics
getbatchlogreplaythrottle -  Print batchlog replay throttle in KB/s. This is reduced proportionally to the number of nodes in the cluster.
getcompactionthreshold -  Print min and max compaction thresholds for a given table
  args: <keyspace> <table> -  The keyspace with a table
getcompactionthroughput -  Print the MB/s throughput cap for compaction in the system
getconcurrentcompactors -  Get the number of concurrent compactors in the system.
getconcurrentviewbuilders -  Get the number of concurrent view builders in the system
getendpoints -  Print the end points that owns the key
  args: <keyspace> <table> <key> -  The keyspace, the table, and the partition key for which we need to find the endpoint
getinterdcstreamthroughput -  Print the Mb/s throughput cap for inter-datacenter streaming in the system
getlogginglevels -  Get the runtime logging levels
getmaxhintwindow -  Print the max hint window in ms
getsstables -  Print the sstable filenames that own the key
  option: [-hf, --hex-format] -  Specify the key in hexadecimal string format
  args: <keyspace> <cfname> <key> -  The keyspace, the column family, and the key
getseeds -  Get the currently in use seed node IP list excluding the node IP
getstreamthroughput -  Print the Mb/s throughput cap for streaming in the system
gettimeout -  Print the timeout of the given type in ms
  args: <timeout_type> -  The timeout type, one of (read, range, write, counterwrite, cascontention, truncate, misc (general rpc_timeout_in_ms))
gettraceprobability -  Print the current trace probability value
gossipinfo -  Shows the gossip information for the cluster
handoffwindow -  Print current hinted handoff window
import -  Import new SSTables to the system
  args: <keyspace> <table> <directory> ... -  The keyspace, table name and directories to import sstables from
  option: [-l, --keep-level] -  Keep the level on the new sstables
  option: [-r, --keep-repaired] -  Keep any repaired information from the sstables
  option: [-v, --no-verify] -  Don't verify new sstables
  option: [-t, --no-tokens] -  Don't verify that all tokens in the new sstable are owned by the current node
  option: [-c, --no-invalidate-caches] -  Don't invalidate the row cache when importing
  option: [-q, --quick] -  Do a quick import without verifying sstables, clearing row cache or checking in which data directory to put the file
  option: [-e, --extended-verify] -  Run an extended verify, verifying all values in the new sstables
info -  Print node information (uptime, load, ...)
  option: [-T, --tokens] -  Display all tokens
invalidatecountercache -  Invalidate the counter cache
invalidatekeycache -  Invalidate the key cache
invalidaterowcache -  Invalidate the row cache
join -  Join the ring
listsnapshots -  Lists all the snapshots along with the size on disk and true size.
move -  Move node on the token ring to a new token
  args: <new token> -  The new token.
netstats -  Print network information on provided host (connecting node by default)
  option: [-H, --human-readable] -  Display bytes in human readable form, i.e. KiB, MiB, GiB, TiB
pausehandoff -  Pause hints delivery process
proxyhistograms -  Print statistic histograms for network operations
rangekeysample -  Shows the sampled keys held across all keyspaces
rebuild -  Rebuild data by streaming from other nodes (similarly to bootstrap)
  args: <src-dc-name> -  Name of DC from which to select sources for streaming. By default, pick any DC
  option: [-ks, --keyspace] -  Use -ks to rebuild specific keyspace.
  option: [-ts, --tokens] -  Use -ts to rebuild specific token ranges, in the format of "(start_token_1,end_token_1],(start_token_2,end_token_2],...(start_token_n,end_token_n]".
  option: [-s, --sources] -  Use -s to specify hosts that this node should stream from when -ts is used. Multiple hosts should be separated using commas (e.g. 127.0.0.1,127.0.0.2,...)
rebuild_index -  A full rebuild of native secondary indexes for a given table
  args: <keyspace> <table> <indexName...> -  The keyspace and table name followed by a list of index names
refresh -  Load newly placed SSTables to the system without restart
  args: <keyspace> <table> -  The keyspace and table name
refreshsizeestimates -  Refresh system.size_estimates
reloadlocalschema -  Reload local node schema from system tables
reloadseeds -  Reload the seed node list from the seed node provider
reloadtriggers -  Reload trigger classes
relocatesstables -  Relocates sstables to the correct disk
  args: <keyspace> <table> -  The keyspace and table name
  option: [-j, --jobs] -  Number of sstables to relocate simultanously, set to 0 to use all available compaction threads
removenode -  Show status of current node removal, force completion of pending removal or remove provided ID
  args: <status>|<force>|<ID> -  Show status of current node removal, force completion of pending removal, or remove provided ID
repair -  Repair one or more tables
  args: [<keyspace> <tables>...] -  The keyspace followed by one or many tables
  option: [-seq, --sequential] -  Use -seq to carry out a sequential repair
  option: [-dcpar, --dc-parallel] -  Use -dcpar to repair data centers in parallel.
  option: [-local, --in-local-dc] -  Use -local to only repair against nodes in the same datacenter
  option: [-dc, --in-dc] -  Use -dc to repair specific datacenters
  option: [-hosts, --in-hosts] -  Use -hosts to repair specific hosts
  option: [-st, --start-token] -  Use -st to specify a token at which the repair range starts
  option: [-et, --end-token] -  Use -et to specify a token at which repair range ends
  option: [-pr, --partitioner-range] -  Use -pr to repair only the first range returned by the partitioner
  option: [-full, --full] -  Use -full to issue a full repair.
  option: [-force, --force] -  Use -force to filter out down endpoints
  option: [-prv, --preview] -  Determine ranges and amount of data to be streamed, but don't actually perform repair
  option: [-vd, --validate] -  Checks that repaired data is in sync between nodes. Out of sync repaired data indicates a full repair should be run.
  option: [-j, --job-threads] -  Number of threads to run repair jobs. Usually this means number of CFs to repair concurrently. WARNING: increasing this puts more load on repairing nodes, so be careful. (default: 1, max: 4)
  option: [-tr, --trace] -  Use -tr to trace the repair. Traces are logged to system_traces.events.
  option: [-pl, --pull] -  Use --pull to perform a one way repair where data is only streamed from a remote node to this node.
  option: [-os, --optimise-streams] -  Use --optimise-streams to try to reduce the number of streams we do (EXPERIMENTAL, see CASSANDRA-3200).
repair_admin -  list and fail incremental repair sessions
  option: [-l, --list] -  list repair sessions (default behavior)
  option: [-a, --all] -  include completed and failed sessions
  option: [-x, --cancel] -  cancel an incremental repair session
  option: [-f, --force] -  cancel repair session from a node other than the repair coordinator. Attempting to cancel FINALIZED or FAILED sessions is an error.
replaybatchlog -  Kick off batchlog replay and wait for finish
resetfullquerylog -  Stop the full query log and clean files in the configured full query log directory from cassandra.yaml as well as JMX
resetlocalschema -  Reset node's local schema and resync
resumehandoff -  Resume hints delivery process
ring -  Print information about the token ring
  args:  -  Specify a keyspace for accurate ownership information (topology awareness)
  option: [-r, --resolve-ip] -  Show node domain names instead of IPs
scrub -  Scrub (rebuild sstables for) one or more tables
  args: [<keyspace> <tables>...] -  The keyspace followed by one or many tables
  option: [-ns, --no-snapshot] -  Scrubbed CFs will be snapshotted first, if disableSnapshot is false. (default false)
  option: [-s, --skip-corrupted] -  Skip corrupted partitions even when scrubbing counter tables. (default false)
  option: [-n, --no-validate] -  Do not validate columns using column validator
  option: [-r, --reinsert-overflowed-ttl] -  Rewrites rows with overflowed expiration date affected by CASSANDRA-14092 with the maximum supported expiration date of 2038-01-19T03:14:06+00:00. The rows are rewritten with the original timestamp incremented by one millisecond to override/supersede any potential tombstone that may have been generated during compaction of the affected rows.
  option: [-j, --jobs] -  Number of sstables to scrub simultanously, set to 0 to use all available compaction threads
setbatchlogreplaythrottle -  Set batchlog replay throttle in KB per second, or 0 to disable throttling. This will be reduced proportionally to the number of nodes in the cluster.
  args: <value_in_kb_per_sec> -  Value in KB per second, 0 to disable throttling
setcachecapacity -  Set global key, row, and counter cache capacities (in MB units)
  args: <key-cache-capacity> <row-cache-capacity> <counter-cache-capacity> -  Key cache, row cache, and counter cache (in MB)
setcachekeystosave -  Set number of keys saved by each cache for faster post-restart warmup. 0 to disable
  args: <key-cache-keys-to-save> <row-cache-keys-to-save> <counter-cache-keys-to-save> -  The number of keys saved by each cache. 0 to disable
setcompactionthreshold -  Set min and max compaction thresholds for a given table
  args: <keyspace> <table> <minthreshold> <maxthreshold> -  The keyspace, the table, min and max threshold
setcompactionthroughput -  Set the MB/s throughput cap for compaction in the system, or 0 to disable throttling
  args: <value_in_mb> -  Value in MB, 0 to disable throttling
setconcurrentcompactors -  Set number of concurrent compactors in the system.
  args: <value> -  Number of concurrent compactors, greater than 0.
setconcurrentviewbuilders -  Set the number of concurrent view builders in the system
  args: <value> -  Number of concurrent view builders, greater than 0.
sethintedhandoffthrottlekb -  Set hinted handoff throttle in kb per second, per delivery thread.
  args: <value_in_kb_per_sec> -  Value in KB per second
setinterdcstreamthroughput -  Set the Mb/s throughput cap for inter-datacenter streaming in the system, or 0 to disable throttling
  args: <value_in_mb> -  Value in Mb, 0 to disable throttling
setlogginglevel -  Set the log level threshold for a given component or class. Will reset to the initial configuration if called with no parameters.
  args: <component|class> <level> -  The component or class to change the level for and the log level threshold to set. Will reset to initial level if omitted. Available components:  bootstrap, compaction, repair, streaming, cql, ring
setmaxhintwindow -  Set the specified max hint window in ms
  args: <value_in_ms> -  Value of maxhintwindow in ms
setstreamthroughput -  Set the Mb/s throughput cap for streaming in the system, or 0 to disable throttling
  args: <value_in_mb> -  Value in Mb, 0 to disable throttling
settimeout -  Set the specified timeout in ms, or 0 to disable timeout
  args: <timeout_type> <timeout_in_ms> -  Timeout type followed by value in ms (0 disables socket streaming timeout). Type should be one of (read, range, write, counterwrite, cascontention, truncate, misc (general rpc_timeout_in_ms))
settraceprobability -  Sets the probability for tracing any given request to value. 0 disables, 1 enables for all requests, 0 is the default
  args: <value> -  Trace probability between 0 and 1 (ex: 0.2)
snapshot -  Take a snapshot of specified keyspaces or a snapshot of the specified table
  args: [<keyspaces...>] -  List of keyspaces. By default, all keyspaces
  option: [-cf, --column-family, --table] -  The table name (you must specify one and only one keyspace for using this option)
  option: [-t, --tag] -  The name of the snapshot
  option: [-kt, --kt-list, -kc, --kc.list] -  The list of Keyspace.table to take snapshot.(you must not specify only keyspace)
  option: [-sf, --skip-flush] -  Do not flush memtables before snapshotting (snapshot will not contain unflushed data)
status -  Print cluster information (state, load, IDs, ...)
  args: [<keyspace>] -  The keyspace name
  option: [-r, --resolve-ip] -  Show node domain names instead of IPs
statusautocompaction -  status of autocompaction of the given keyspace and table
  args: [<keyspace> <tables>...] -  The keyspace followed by one or many tables
  option: [-a, --all] -  Show auto compaction status for each keyspace/table
statusbackup -  Status of incremental backup
statusbinary -  Status of native transport (binary protocol)
statusgossip -  Status of gossip
statushandoff -  Status of storing future hints on the current node
stop -  Stop compaction
  args: <compaction type> -  Supported types are COMPACTION, VALIDATION, CLEANUP, SCRUB, VERIFY, INDEX_BUILD
  option: [-id, --compaction-id] -  Use -id to stop a compaction by the specified id. Ids can be found in the transaction log files whose name starts with compaction_, located in the table transactions folder.
stopdaemon -  Stop cassandra daemon
tablehistograms -  Print statistic histograms for a given table
  args: [<keyspace> <table> | <keyspace.table>] -  The keyspace and table name
tablestats -  Print statistics on tables
  args: [<keyspace.table>...] -  List of tables (or keyspace) names
  option: [-i] -  Ignore the list of tables and display the remaining tables
  option: [-H, --human-readable] -  Display bytes in human readable form, i.e. KiB, MiB, GiB, TiB
  option: [-F, --format] -  Output format (json, yaml)
  option: [-s, --sort] -  Sort tables by specified sort key (average_live_cells_per_slice_last_five_minutes, average_tombstones_per_slice_last_five_minutes, bloom_filter_false_positives, bloom_filter_false_ratio, bloom_filter_off_heap_memory_used, bloom_filter_space_used, compacted_partition_maximum_bytes, compacted_partition_mean_bytes, compacted_partition_minimum_bytes, compression_metadata_off_heap_memory_used, dropped_mutations, full_name, index_summary_off_heap_memory_used, local_read_count, local_read_latency_ms, local_write_latency_ms, maximum_live_cells_per_slice_last_five_minutes, maximum_tombstones_per_slice_last_five_minutes, memtable_cell_count, memtable_data_size, memtable_off_heap_memory_used, memtable_switch_count, number_of_partitions_estimate, off_heap_memory_used_total, pending_flushes, percent_repaired, read_latency, reads, space_used_by_snapshots_total, space_used_live, space_used_total, sstable_compression_ratio, sstable_count, table_name, write_latency, writes)
  option: [-t, --top] -  Show only the top K tables for the sort key (specify the number K of tables to be shown
toppartitions -  Sample and print the most active partitions
  args: [keyspace table] [duration] -  The keyspace, table name, and duration in milliseconds
  option: [-s] -  Capacity of stream summary, closer to the actual cardinality of partitions will yield more accurate results (Default: 256)
  option: [-k] -  Number of the top partitions to list (Default: 10)
  option: [-a] -  Comma separated list of samplers to use (Default: all)
tpstats -  Print usage statistics of thread pools
  option: [-F, --format] -  Output format (json, yaml)
truncatehints -  Truncate all hints on the local node, or truncate hints for the endpoint(s) specified.
  args: [endpoint ... ] -  Endpoint address(es) to delete hints for, either ip address ("127.0.0.1") or hostname
upgradesstables -  Rewrite sstables (for the requested tables) that are not on the current version (thus upgrading them to said current version)
  args: [<keyspace> <tables>...] -  The keyspace followed by one or many tables
  option: [-a, --include-all-sstables] -  Use -a to include all sstables, even those already on the current version
  option: [-j, --jobs] -  Number of sstables to upgrade simultanously, set to 0 to use all available compaction threads
verify -  Verify (check data checksum for) one or more tables
  args: [<keyspace> <tables>...] -  The keyspace followed by one or many tables
  option: [-e, --extended-verify] -  Verify each cell data, beyond simply checking sstable checksums
  option: [-c, --check-version] -  Also check that all sstables are the latest version
  option: [-d, --dfp] -  Invoke the disk failure policy if a corrupt sstable is found
  option: [-r, --rsc] -  Mutate the repair status on corrupt sstables
  option: [-t, --check-tokens] -  Verify that all tokens in sstables are owned by this node
  option: [-q, --quick] -  Do a quick check - avoid reading all data to verify checksums
version -  Print cassandra version
viewbuildstatus -  Show progress of a materialized view build
  args: <keyspace> <view> | <keyspace.view> -  The keyspace and view name
```
