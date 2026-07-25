# Docker Repo
https://hub.docker.com/repository/docker/dbal7/is601_assignment12/general


# Setup

## Create project directory and clone project

### Create directory for assignment 12

```bash
mkdir assignment12
```

### Clone Module 12 github repo and copy files to project

```bash
git clone git@github.com:kaw393939/module12_is601.git
```

```bash
cp -r ~/module12_is601/.github/ .
cp -r ~/module12_is601/.gitignore .
cp -r ~/module12_is601/.vscode/ .
cp -r ~/module12_is601/Dockerfile .
cp -r ~/module12_is601/LICENSE .
cp -r ~/module12_is601/README.md .
cp -r ~/module12_is601/app/ .
cp -r ~/module12_is601/docker-compose.yml .
cp -r ~/module12_is601/pytest.ini .
cp -r ~/module12_is601/init-db.sh .
cp -r ~/module12_is601/requirements.txt .
cp -r ~/module12_is601/templates/ .
cp -r ~/module12_is601/tests/ .
```

**Check all files in directory**

```bash
ls -la

total 64
drwxr-xr-x  7 dbalicky dbalicky 4096 Jul 21 20:15 .
drwxr-xr-x 16 dbalicky dbalicky 4096 Jul 21 20:13 ..
drwxr-xr-x  3 dbalicky dbalicky 4096 Jul 21 20:14 .github
-rw-r--r--  1 dbalicky dbalicky   71 Jul 21 20:14 .gitignore
drwxr-xr-x  2 dbalicky dbalicky 4096 Jul 21 20:14 .vscode
-rw-r--r--  1 dbalicky dbalicky 1092 Jul 21 20:14 Dockerfile
-rw-r--r--  1 dbalicky dbalicky 1061 Jul 21 20:14 LICENSE
-rw-r--r--  1 dbalicky dbalicky 5162 Jul 21 20:14 README.md
drwxr-xr-x  7 dbalicky dbalicky 4096 Jul 21 20:14 app
-rw-r--r--  1 dbalicky dbalicky 1628 Jul 21 20:14 docker-compose.yml
-rwxr-xr-x  1 dbalicky dbalicky  158 Jul 21 20:15 init-db.sh
-rw-r--r--  1 dbalicky dbalicky 1009 Jul 21 20:15 pytest.ini
-rw-r--r--  1 dbalicky dbalicky  899 Jul 21 20:15 requirements.txt
drwxr-xr-x  2 dbalicky dbalicky 4096 Jul 21 20:15 templates
drwxr-xr-x  5 dbalicky dbalicky 4096 Jul 21 20:15 tests
```

### Open project directory in VSCode

```bash
code .
```

## Setting up venv and github repo

### Set python version to 3.10

```bash
pyenv local 3.10
```

### Create and activate venv

```bash
python3 -m venv venv

source venv/bin/activate
```

### Initialize git repo and set remote github repo

```bash
git init

git remote add origin git@github.com:dbalicky/IS601_assignment12.git
# or git remote set-url origin git@github.com:dbalicky/IS601_assignment12.git
```

### Initial commit and push

```bash
git add .

git commit -m 'Initial commit'

git push --set-upstream origin main
```

## Updating dependency versions

### Update dependency versions in requirements.txt

```bash
cffi==1.17.1 --> 2.0.0
cryptography==44.0.0 --> 48.0.1
fastapi==1.115.8 --> 1.139.0
h11==1.14.0 --> 1.16.0
httpcore==1.0.7 --> 1.0.9
pyasn1==0.6.1 --> 0.6.4
python-jose==3.3.0 --> 3.5.0
python-multipart==0.0.20 --> 0.0.30
# remove starlette
typing-extensions==4.12.2 --> 4.13.2
urllib3==2.3.0 --> 2.7.0
```

### Check for dependency conflicts and install different versions if necessary

```bash
pip install -r requirements.txt

pip check

pip install --upgrade -r requirements.txt
```

# Pushing to Dockerhub

**Create docker repo, then create and copy docker username and token to github secret keys**

## Building docker image

### Remove any currently running docker image
```bash
docker compose down -v
```

### Build docker image
```bash
docker compose up --build
```

**Update tags in test.yml to match docker repo**

### Tag and push to docker repo
```bash
docker tag assignment12:latest dbal7/is601_assignment12:latest

docker push dbal7/is601_assignment12:latest
```