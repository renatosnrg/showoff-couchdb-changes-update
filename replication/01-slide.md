<!SLIDE section>

# Continuous Replication #

<!SLIDE bullets>

# Continuous Replication #

* It’ll not stop after replicating all missing documents from the source to the target
* “continuous”:true
* Listen _changes to replicate


<!SLIDE commandline>

# Continuous Replication #

	curl -X POST http://127.0.0.1:5984/_replicate -d \
	'{"source":"db", "target":"db-replica", "continuous":true}'
	
