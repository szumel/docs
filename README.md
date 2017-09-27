# Project name

E-commerce shop

## Getting Started

These instructions will get you project specific informations and
the whole idea from development to deployment process.

See versioning for notes on how to manage git branches.

See deployment for notes on how to deploy the project on a live system.

See environments for notes what environments exist and how to use them.

## 1. Built With
* [Magento2](https://developer.magento.com/) - platform
* [Composer](https://getcomposer.org/) - dependency management
* [PSR rules](http://www.php-fig.org/psr/)

### 1.1 Installing
All dependencies related to M2 can be found:
```
http://devdocs.magento.com/guides/v2.1/install-gde/system-requirements-tech.html
```

Installing dependencies is related to OS 
e.g. on Debian and Ubuntu - apt tool could be used.

Configure local DNS and  web server.

Database and database user must be created.

## 2. Running the tests

This project is not test driven.

## 3. Versioning

GIT is used for version management.

1. master - main production branch
2. develop - main stable branch with newest features
3. feature - feature development branch
4. release - representing features bundle in stable state

#### 3.1 Development

Workflow: 
1. Feature

* Feature branch must be created from develop branch
* Stable feature must be merged back into develop branch

```bash
---DEVELOPMENT---
git checkout develop
git pull origin develop
git checkout -b feature-1 develop

git checkout develop
git merge --no-ff feature-1
git push origin develop
---END DEVELOPMENT---
```
#### 3.2 Deployment

1. Release 

* Release branch must be created from master branch
* Stable develop branch must be merged into release branch
* Stable release branch (merged with develop) 
should be merged into master branch
* Master branch should be tagged and pushed to origin with tags

```bash
---DEPLOYMENT---
git checkout develop
git pull origin develop
git checkout -b release-1 master
git merge develop
git checkout master
git merge --no-ff release-1
git tag 0.1
git push origin master --tags
---END DEPLOYMENT---
```
## 4. Environments
### 4.1 Test
Url - http://test.subdomain.com

##### Autorelease
On every push to develop branch.

[branches](.gitlab-ci.yml)

[config](release.xml)
##### M2
Compilation is enabled.

[config](m2release.xml)

### 4.2 Staging

Staging exists but it is unstable.

### 4.3 Production

Not yet specified.
