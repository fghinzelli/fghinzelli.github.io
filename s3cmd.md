# s3cmd - Cheat sheet
- List all buckets: ``` s3cmd ls ```
- Info of bucket: ``` s3cmd du -H s3://<bucket> ```
- More info: ``` s3cmd info s3://<bucket> ```
- Lifecycle: ``` s3cmd lifecycle s3://<bucket> ```


 Generate a hash sha256 from terminal:  ``` echo -n '<string>' | sha256sum ```
