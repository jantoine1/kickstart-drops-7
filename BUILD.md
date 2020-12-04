# Build the project

This script assumes a web root and working directory of /var/www and a drupal
root of /var/www/repo.

## Navigate into the drupal root folder

```bash
cd drupal
```

## Download the latest Commerce Kickstart release

```bash
drush dl commerce_kickstart
```

## Navigate into the Commerce Kickstart profile folder

```bash
cd profiles/commerce_kickstart
```

## Update the drupal-org-core.make file

### Replace the line beginning with

```
projects[drupal][version]
```

### With

```
projects[drupal][type] = "core"
projects[drupal][download][type] = "git"
projects[drupal][download][url] = "https://github.com/pantheon-systems/drops-7.git"
```

## Run the build script

```bash
./scripts/build.sh -y /var/www/repo-new
```

## Navigate into the web root folder

```bash
cd ../../../
```

## Copy custom files/folders

```bash
mv repo/BUILD.md repo-new/
mv repo/.git repo-new/
```

## Replace the drupal folder

```bash
rm -fr repo
mv repo-new repo
```
