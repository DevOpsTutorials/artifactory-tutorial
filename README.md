# artifactory-tutorial

## Install Artifactory

```
$ sudo -i
# wget https://bintray.com/jfrog/artifactory-rpms/rpm -O bintray-jfrog-artifactory-rpms.repo
# mv bintray-jfrog-artifactory-rpms.repo /etc/yum.repos.d/
# yum install -y jfrog-artifactory-oss
# service artifactory start
```

Check the Artifactory UI on the browser at `http://IP-ADDRESS:8081`, and, login as `admin` with password `password`.

## Setup a repository

Navigate `Admin` -> `Repositories` -> `Local`.

Click on `New`. Pick `Generic` for `Select Package Type`.

Enter `bootcamp` as `Repository Key`. Click `Save & Finish` to create the new repository.

## Upload/Download files

On the main menu on the right pane, click on `Artifacts`.

Click `Deploy` on the top-right. 
- From the pop-up dialog for uploading select a file from your laptop. 
- Select `Target Repository` as `bootcamp`.
- Enter a relative path to the repo in `Target Path`. Multi-level directories are supported, for example try `first/second/YOUR-FILENAME`.
- Click `Deploy`. This uploads the local file to the specified target path in the repo `bootcamp`.

Following the last steps upload another file with `Target Path` set to `first`.

Following `Artifacts` -> `Tree` -> `bootcamp`, browse the files uploaded in the last steps in remote folders.

Highlight on one of files on the left pane, on the right pane `Info` -> `Name` click on the file icon to copy the URL of that file. Sample path could like `http://34.212.154.26:8081/artifactory/bootcamp/first/IMG_7600.jpg`

Using such URL the file could be downloaded from a script using `curl` or `url`:
```
$ wget http://34.212.154.26:8081/artifactory/bootcamp/first/IMG_7600.jpg
$ curl http://34.212.154.26:8081/artifactory/bootcamp/first/IMG_7600.jpg -o IMG_7600.jpg
```

A file could be uploaded also using the REST API support provided by Artifactory:
```
$ curl -vi -u admin:password -X PUT  http://34.212.154.26:8081/artifactory/bootcamp/first/2018-02-10.csv -T ~/Downloads/2018-02-10.csv
```

Type of repositories and local caching.

Artifacts replication between Artifactory instances.

Artifactory maintenance.


