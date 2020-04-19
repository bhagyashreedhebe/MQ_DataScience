# COMP257 Major Project

**Group V** -  [Blake Lockley](https://github.com/blakelockley), [Sam Hornsey](https://github.com/SamuelHornsey)

**Currently Live** - https://datascience.samuelhornsey.com/

[![Build Status](https://travis-ci.com/blakelockley/data-science-project.svg?token=H7zFcTcoATQYxDfrSB3d&branch=master)](https://travis-ci.com/blakelockley/data-science-project)

## Overview

Looking at the poster for almost any Hollywood blockbuster you might have noticed that the names of the starring actors never seem to line up with the actor or actress on the poster itself. This is because of a concept called **[‘Top Billing’](https://en.wikipedia.org/wiki/Billing_(filmmaking)#Top_and_above-title_billing)** and it gives us an insight of how important that actor truly is. To find out more checkout [Why Don't Movie Poster Names EVER Line Up?!](https://youtu.be/yQhC1Kfrs3o) by Austin Mcconnell, which served as inspiration for this project. So with this in mind we would like to know...

**Can the actors, directors and crew behind a movie be a predictor to the success of a film?**

## Delivery 

Our analysis will be presented in the form of an ‘interactive visual essay’ web app. As the user scrolls the page, the narrative or our analysis will develop. The webapp will also offer multiple interactive components such as the "Dream Cast" feature where users can select the stars, director budget and other aspects of a movie and receive a prediction on how successful it will be. The underlying analysis and experimentation will also be recorded in a collection of Jupyter notebooks.

## Narrative

### Defining Success

- Introduce reviews dataset
- Creating predictors with existing features to identify "what is success"
- Man vs Machine (interactive feature)
- Conclude what our success metric will be (y / label)

### Actors/Directors as a predictor

- Introduce films (people) dataset
- Expermimentation to encoding dataset
- Viewing an actors carreer (interactive feature)
- Creating an predictor using augmented features from films (people) and reviews dataset 

### Making Predictions

- Showcase the main predictor - the **Dream Cast** interactive feature
- Conclusion on how well people as a feature can help create a predictive model

## Getting Started

After cloning the repo, run commands from the root directory of the project:

1. Create virtualenv

```console
$ virtualenv env
```

2. Enter virtualenv and install dependencies

```console
$ source ./env/bin/activate
$ pip install -r requirements.txt
```

3. Change script permissions (if necessary)

```console
$ chmod  a+x ./bin/*.sh
```

**Steps 4 & 5 are for running the webapp with message queuing enabled only**

4. If docker image for RabbitMQ is not already running launch via the docker-compose script

```console
$ ./bin/docker-compose.sh
```

5. Launch celery task queue

```console
$ ./bin/celery.sh
```

**Launching the webapp**

6. Run services via scripts located in the bin directory (all scripts listed below)

```console
$ ./bin/webapp.sh
```

## Project Structure

### bin/

Contains scripts to run all services in the project.

- **webapp.sh: Launch webapp**
- notebook.sh: Launch Jupyter notebooks
- test.sh: Run unit tests
- coverage.sh: Run code coverage test
- celerary.sh: Run celery (message queuing)
- docker-compose.sh: Instantiate docker images (message queuing)

### notebook/

All analysis and experimentation contained in Jupyter notebooks.

### webapp/

Webapp of the 'interactive visual essay' - contains templates, api services, interactive components, etc.

### test/

All unit tests, allows for automated testing for CI/CD.

### data/

Contains all csv datasets used throughout the project.

## API Endpoints

Allowing for interaction with the backend, all endpoints return JSON responses.

When using **message queuing** endpoints will return an identifier to poll for async result.

### /api/scraper

Interact with the wikipedia web scraper.

| Endpoint      | Service       
| ------------- |-------------|
| **/api/scraper/film/\<film\>** | Returns all details for \<film\>.  |
| **/api/scraper/year/\<year\>** | Returns list of films names released in \<year\>. |

### /api/format

Data formatting into UI elements.

### /api/graph

Data for loading into chart js.

### Automated Builds
