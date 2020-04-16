# SOEN363S_PHASE2
DBMS Cassandra project

You can download the Dataset from:
https://open.canada.ca/data/en/dataset/b7c7d526-c0a8-4ccb-8ffa-8df36c9eefe4

Dataset size: 583 M CSV file

Once the data has been dowloaded it needs to the file needs to be cleaned up by running it through the Parser.

Database Creation:
```
CREATE KEYSPACE populationcomponent WITH replication = {'class':'SimpleStrategy', 'replication_factor' : 1};

CREATE TABLE populationcomponent.population (
	ref_date text,
	vector text,
	agegroup text,
	componentsofgrowth text,
	coordinate text,
	decimals text,
	dguid text,
	geo text,
	scalar_factor text,
	scalar_id text,
	sex text,
	status text,
	symbol text,
	terminated text,
	uom text,
	uom_id text,
	value varint,
	PRIMARY KEY (ref_date, vector)
) WITH CLUSTERING ORDER BY (vector ASC)
	AND additional_write_policy = '99PERCENTILE'
	AND bloom_filter_fp_chance = 0.01
	AND caching = {'keys': 'ALL', 'rows_per_partition': 'NONE'}
	AND comment = ''
	AND compaction = {'class': 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold': '32', 'min_threshold': '4'}
	AND compression = {'chunk_length_in_kb': '64', 'class': 'org.apache.cassandra.io.compress.LZ4Compressor'}
	AND crc_check_chance = 1.0
	AND default_time_to_live = 0
	AND gc_grace_seconds = 864000
	AND max_index_interval = 2048
	AND memtable_flush_period_in_ms = 0
        	AND min_index_interval = 128
	AND nodesync = {'enabled': 'true', 'incremental': 'true'}
	AND read_repair = 'BLOCKING'
	AND speculative_retry = '99PERCENTILE';
 
//Secondary indexing
CREATE CUSTOM INDEX componentsofgrowth ON populationcomponent.population (componentsofgrowth) USING 'org.apache.cassandra.index.sasi.SASIIndex';
CREATE CUSTOM INDEX geo ON populationcomponent.population (geo) USING 'org.apache.cassandra.index.sasi.SASIIndex';
CREATE CUSTOM INDEX agegroup ON populationcomponent.population (agegroup) USING 'org.apache.cassandra.index.sasi.SASIIndex';
 
CREATE CUSTOM INDEX sex ON populationcomponent.population (sex) USING 'org.apache.cassandra.index.sasi.SASIIndex';
```


