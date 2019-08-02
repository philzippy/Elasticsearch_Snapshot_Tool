Document Name
Markdown
Preview
Toggle Mode

<p class="has-line-data" data-line-start="0" data-line-end="1">Elasticsearch Snapshot Tool</p>
<ol>
<li class="has-line-data" data-line-start="1" data-line-end="17">Configure Elasticsearch for index snapshots<br>
a) Navigate to the Elasticsearch directory<br>
Windows: C:\Elastic\elasticsearch-2.4.0<br>
Linux: /var/lib/elasticsearch/<br>
b) Create a subfolder for the Elasticsearch snapshot repository, for example: es_backup_folder<br>
c) Make note of the entire path for the snapshot folder path, for example…<br>
Windows: C:\Temp\es_backup_folder<br>
Linux: /tmp/es_backup_folder<br>
d) Navigate to the path where the “elasticsearch.yml” file is located. For example…<br>
Windows: &lt;drive&gt;\Elastic\elasticsearch-2.4.0\config\elasticsearch.yml<br>
Linux: /etc/elasticsearch/elasticsearch.yml<br>
e) Open the “elasticsearch.yml” for editing<br>
f) Using the path from Steps 4c, add the following line in the “elasticsearch.yml” file…<br>
If using Windows: path.repo: C:\Elastic\elasticsearch-2.4.0\es_backup_folder<br>
If using Linux: path.repo: /var/lib/elasticsearch/es_backup_folder<br>
g) Restart the Elasticsearch service</li>
<li class="has-line-data" data-line-start="17" data-line-end="18">Check Index Health – Red=Bad, Yellow=normal for single node environments, green=normal for an instance with no indicies or cluster</li>
<li class="has-line-data" data-line-start="18" data-line-end="19">Index Version – Lists the version of the current indices</li>
<li class="has-line-data" data-line-start="19" data-line-end="37">Create the Elasticsearch Snapshot (backup)<br>
a) Populate the Elasticsearch URL with the source server name and port. For example: <a href="http://localhost:9200">http://localhost:9200</a><br>
b) Populate the Backup Repo Path with the path collected in Step 4f<br>
If using Windows, massage the snapshot path by replacing back-slashes () with forward-slashes (/). For example…<br>
C:/Temp/es_backup_folder<br>
If using Linux, the path can be as it is, for example: /tmp/es_backup_folder<br>
c) Click “Get Current Indexes”. The Results window should show at least one index which will look similar to…<br>
yellow open mqm_5k8wj5v97d2ovf9o9gl210qd2_index Lgk8aHhLQHaHq2xZqgAXsA 5 1 8342 28<br>
If no indexes are displayed make sure the correct Elasticsearch server (URL) has been specified<br>
d) Click “Check Index Health”. The Results window should show the health of the indexes. Mind that a “yellow” status is normal in single-node ES enviornments.<br>
e) Verify the path specified in the “Backup Repo Path” at the top of the utility. This must be exact. Refer to Step 5b just above<br>
f) Click “Create Backup Repo”. This Results window should display: “acknowledged”:true<br>
g) Click “Create Snapshot”. It may take some time for the Snapshot to create. The Results window should display: &quot;:{“total”:5,“failed”:0,“successful”:5}}}<br>
The results clarified. 5 total shards, zero failed, 5 succeeded<br>
h) Click “Check Snapshot”. This verifies the integrity of the Snapshot. The Results window should display a similar message as in Step 5g: &quot;:{“total”:5,“failed”:0,“successful”:5}}}<br>
The results clarified. 5 total shards, zero failed, 5 succeeded<br>
The above results exemplify a healthy Snapshot<br>
i) Close the Elasticsearch Snapshot Tool</li>
<li class="has-line-data" data-line-start="37" data-line-end="51">Restore the Elasticsearch Snapshot<br>
a) On the target Elasticsearch server repeat Steps 3 and 4 including all sub-steps<br>
b) Start the Elastisearch Snapshot tool<br>
c) Populate the Elasticsearch URL with the source server name and port. For example: <a href="http://localhost:9200">http://localhost:9200</a><br>
d) Populate the Backup Repo Path with the path collected in Step 4f<br>
If using Windows, massage the snapshot path by replacing back-slashes () with forward-slashes (/). For example…<br>
C:/Temp/es_backup_folder<br>
If using Linux, the path can be as it is, for example: /tmp/es_backup_folder<br>
e) Click “Create Backup Repository”<br>
f) Copy the entire contents of the es_backup_folder from the source ES server to the target ES server<br>
g) Click “Check Snapshot” to verify the snapshot<br>
h) Click “Restore Snapshot” to restore the snapshot from the source ES server. This may take some time.<br>
i) Click “Get Current Indexes”, then “Check Index Health”<br>
Note: Be careful when using “Delete Indexes” and “Delete Snapshot” as these will delete those items. Make sure proper backups are maintained before using!!!</li>
<li class="has-line-data" data-line-start="51" data-line-end="52">Disable Shard Allocation – Used for upgrading Elasticsearch Indexes</li>
<li class="has-line-data" data-line-start="52" data-line-end="53">Enable Shard Allocation - Used for upgrading Elasticsearch Indexes</li>
<li class="has-line-data" data-line-start="53" data-line-end="54">Synced Flush – Used of upgrading Elastisearch Indexes</li>
<li class="has-line-data" data-line-start="54" data-line-end="55">Delete Indexes – double confirmed in the utility – Use with discretion!</li>
<li class="has-line-data" data-line-start="55" data-line-end="57">Delete Snapshot – singled confirmed in the utility – Use with discretion!</li>
</ol>

