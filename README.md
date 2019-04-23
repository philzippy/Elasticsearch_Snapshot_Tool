Elasticsearch Snapshot Tool
1)	Configure Elasticsearch for index snapshots
a)	Navigate to the Elasticsearch directory
Windows: C:\Elastic\elasticsearch-2.4.0\
Linux: /var/lib/elasticsearch/
b)	Create a subfolder for the Elasticsearch snapshot repository, for example: es_backup_folder
c)	Make note of the entire path for the snapshot folder path, for example…
Windows: C:\Temp\es_backup_folder
Linux: /tmp/es_backup_folder
d)	Navigate to the path where the “elasticsearch.yml” file is located. For example…
Windows: <drive>\Elastic\elasticsearch-2.4.0\config\elasticsearch.yml
Linux: /etc/elasticsearch/elasticsearch.yml
e)	Open the “elasticsearch.yml” for editing
f)	Using the path from Steps 4c, add the following line in the “elasticsearch.yml” file…
If using Windows: path.repo: C:\Elastic\elasticsearch-2.4.0\es_backup_folder
If using Linux: path.repo: /var/lib/elasticsearch/es_backup_folder
g)	Restart the Elasticsearch service
2) Create the Elasticsearch Snapshot (backup)
a)	Populate the Elasticsearch URL with the source server name and port. For example: http://localhost:9200
b)	Populate the Backup Repo Path with the path collected in Step 4f
If using Windows, massage the snapshot path by replacing back-slashes (\) with forward-slashes (/). For example…
C:/Temp/es_backup_folder 
If using Linux, the path can be as it is, for example: /tmp/es_backup_folder
c)	Click “Get Current Indexes”. The Results window should show at least one index which will look similar to…
 yellow open   mqm_5k8wj5v97d2ovf9o9gl210qd2_index Lgk8aHhLQHaHq2xZqgAXsA   5   1       8342           28      
If no indexes are displayed make sure the correct Elasticsearch server (URL) has been specified
d)	Click “Check Index Health”. The Results window should show the health of the indexes. Mind that a “yellow” status is normal in single-node ES enviornments.
e)	Verify the path specified in the “Backup Repo Path” at the top of the utility. This must be exact. Refer to Step 5b just above
f)	Click “Create Backup Repo”. This Results window should display: "acknowledged":true
g)	Click “Create Snapshot”. It may take some time for the Snapshot to create. The Results window should display: ":{"total":5,"failed":0,"successful":5}}}
The results clarified. 5 total shards, zero failed, 5 succeeded
h)	Click “Check Snapshot”. This verifies the integrity of the Snapshot. The Results window should display a similar message as in Step 5g: ":{"total":5,"failed":0,"successful":5}}}
The results clarified. 5 total shards, zero failed, 5 succeeded
The above results exemplify a healthy Snapshot
i)	Close the Elasticsearch Snapshot Tool
3) Restore the Elasticsearch Snapshot
a)	On the target Elasticsearch server repeat Steps 3 and 4 including all sub-steps
b)	 Start the Elastisearch Snapshot tool
c)	Populate the Elasticsearch URL with the source server name and port. For example: http://localhost:9200
d)	Populate the Backup Repo Path with the path collected in Step 4f
If using Windows, massage the snapshot path by replacing back-slashes (\) with forward-slashes (/). For example…
C:/Temp/es_backup_folder
If using Linux, the path can be as it is, for example: /tmp/es_backup_folder
e)	Click “Create Backup Repository”
f)	Copy the entire contents of the es_backup_folder from the source ES server to the target ES server
g)	Click “Check Snapshot” to verify the snapshot
h)	Click “Restore Snapshot” to restore the snapshot from the source ES server. This may take some time.
i)	Click “Get Current Indexes”, then “Check Index Health”
Note: Be careful when using “Delete Indexes” and “Delete Snapshot” as these will delete those items. Make sure proper backups are maintained before using!!!

