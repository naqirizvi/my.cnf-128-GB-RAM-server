# my.cnf

# 128-GB-RAM-server
This is my.cnf configuration for onw of our running 128 GB server, If any one want to follow this cofiguration or point out the issues is appreciated

#MariadB
[mysqld]
datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock
symbolic-links=0
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid
local-infile=0
innodb=on
max_connections = 5000
max_user_connections=1000
key_buffer_size = 512M
myisam_sort_buffer_size = 128M
read_buffer_size = 1M
table_open_cache = 5000
thread_cache_size = 100
wait_timeout = 30
connect_timeout = 30
tmp_table_size = 2G
max_heap_table_size = 2G
max_allowed_packet = 32M
net_buffer_length = 2M
max_connect_errors = 100
concurrent_insert = 2
read_rnd_buffer_size = 2M
bulk_insert_buffer_size = 2G
query_cache_limit = 1M
query_cache_size = 128M
query_cache_type = 1
query_prealloc_size = 128M
query_alloc_block_size = 128M
transaction_alloc_block_size = 128M
transaction_prealloc_size = 128M
max_write_lock_count = 16
slow_query_log
log-error
external-locking=FALSE
open_files_limit=50000
character-set-server = utf8
collation-server = utf8_general_ci

[client]
socket = /var/lib/mysql/mysql.sock
default-character-set = utf8

[mysqld_safe]
nice = -15

[mysqldump]
quick
quote-names
max_allowed_packet = 128M

[isamchk]
key_buffer = 384M
sort_buffer = 384M
read_buffer = 256M
write_buffer = 256M

[myisamchk]
key_buffer = 384M
sort_buffer = 384M
read_buffer = 256M
write_buffer = 256M

## Table cache settings
table_cache = 512
table_open_cache = 512
tmpdir = /tmp

## Thread settings
thread_concurrency = 16
thread_cache_size = 100

## Table and TMP settings
max_heap_table_size = 2G
bulk_insert_buffer_size = 2G
tmp_table_size = 2G

## MyISAM Engine
key_buffer = 1M
myisam_sort_buffer_size = 128M
myisam_max_sort_file_size = 256M
myisam_repair_threads = 4
myisam_recover = BACKUP


#### Per connection configuration ####
sort_buffer_size = 2M
join_buffer_size = 2M
thread_stack = 512K
read_buffer_size = 2M
read_rnd_buffer_size = 2M
binlog_cache_size = 128K

## Binlog sync settings
XA transactions = 1
sync_binlog = 1

## InnoDB Plugin Independent Settings
innodb_data_home_dir = /var/lib/mysql
innodb_data_file_path = ibdata1:128M;ibdata2:10M:autoextend
innodb_log_file_size = 768M
innodb_log_files_in_group = 4
innodb_buffer_pool_size = 72G
innodb_additional_mem_pool_size = 4M
#innodb_status_file
#innodb_file_per_table
innodb_flush_log_at_trx_commit = 2
innodb_table_locks = 0
innodb_log_buffer_size = 256M
innodb_lock_wait_timeout = 60
innodb_thread_concurrency = 16
innodb_commit_concurrency = 16
innodb_flush_method = O_DIRECT
#O_DIRECT = local/DAS
#O_DSYNC = SAN/iSCSI
innodb_support_xa = 0
#skip-innodb-doublewrite
#
# include all files from the config directory
#
!includedir /etc/my.cnf.d
