# Google Cloud Storage (GCS) Performance Tips and Trics

## Summary

* Use sharding and optimize threading for large file downloads [#1](#1-large-file-performance)
* Profile Your Workflow When Using GCS Downloads/Uploads [#2](#2-profile-your-workflow-when-using-gcs-downloadsuploads)

### Useful Links:
#### 1. Large File Performance
[Source](https://medium.com/@duhroach/gcs-read-performance-of-large-files-bd53cfca4410)  
* Use sharding which splits the file and downloads in parallel and combines.
* Sharding requires `crcmod` to be installed (for cheksum of shards). Instructions [here](https://cloud.google.com/storage/docs/gsutil/addlhelp/CRC32CandInstallingcrcmod).
* Optimize n_processes and n_threads because by default it is optimized for many small files.
* Be careful with your local disk's performance if using sharding or downloading many files. Slow seek times may cause parallel downloads to be slower, compared to turning off sharding (which is on by default).
![](https://miro.medium.com/max/1400/1*uQ6h2gkUe-Z5vDg3t4Xcgg.png)

#### 2. Profile Your Workflow When Using GCS Downloads/Uploads
[Source](https://medium.com/@duhroach/google-cloud-storage-performance-4cfcec8bad72)
* It is complicated to test because there are a lot of moving parts.
* `gsutil perfdiag` is a tool to test this, within reason.
* Google Cloud Performance Atlas YT playlist [here](https://www.youtube.com/playlist?list=PLIivdWyY5sqK5zce0-fd1Vam7oPY-s_8X)