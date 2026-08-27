# insta-s3-uploads

Drop files into `images/`, push to `main`, and GitHub Actions uploads them to S3.

## How it works

1. Add any files under `images/`.
2. Commit and push to `main`.
3. The **Upload images to S3** workflow runs and uploads **only files added or changed in that push**.
4. Older files already in the bucket are left alone. If you uploaded `pic1.jpg` an hour ago and now add `pic2.jpg`, only `pic2.jpg` is uploaded.
5. If a file with the same name already exists in S3, the job **fails** with: change the image name and upload again. It will not overwrite.
6. The job prints a public URL for each new file: `https://assets.instaservice.com/<filename>`. Spaces in filenames are replaced with `-` (`my photo.jpg` → `https://assets.instaservice.com/my-photo.jpg`).
