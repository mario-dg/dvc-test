# Simple Repository that shows how DVC can be used to integrate large binary file tracking into git

## Setup DVC for Git Repo
Run
```bash
dvc init
```
inside the already initialized git repo.
Make sure that your large binary files are not added or committed to version control.

## Add binary files or directories containing binary files to DVC
```bash
dvc add /path/to/large_directory
```

## Setup a remote(Amazon S3, Google Cloud, Google Drive, SSH/SFTP Server) or local storage
```bash
dvc remote add -d storage_name path/to/storage
```

## Push large binary files to remote
```bash
dvc push
```

## Add all created DVC files to git version control
```bash
git add ./dvc/ .dvcignore /path/to/large_directory/*.dvc /path/to/large_directory/.gitignore
git commit -m "Initialized and setup DVC for large file tracking"
git push -u origin main
```

## Clone repository on other machine
```bash
git clone https://path/to/git_repo
```

## Fetch and Checkout large binary files from DVC
```bash
cd git_repo
dvc pull -R /path/to/large_directory
```

## Verify all binaries are downloaded to the specified directory and check if pipeline is up to date
```bash
dvc status
```
