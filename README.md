[![GitHub release](https://img.shields.io/github/release-pre/valasek/timesheet.svg)](https://github.com/valasek/timesheet/releases)
[![GitHub issues](https://img.shields.io/github/issues/valasek/timesheet.svg)](https://github.com/valasek/timesheet/issues)
[![Go Report Card](https://goreportcard.com/badge/github.com/valasek/timesheet)](https://goreportcard.com/report/github.com/valasek/timesheet)


| **Linux & Mac & Windows** |
| :-----------------------: |
| [![Build Status](https://travis-ci.org/valasek/timesheet.svg?branch=master)](https://travis-ci.org/valasek/timesheet) |

# Supporting Simple Timesheet

Simple Timesheet is project with its ongoing development made possible entirely by the support of these awesome backers. If you'd like to join them, please consider:

- [Become a backer or sponsor on Patreon](https://www.patreon.com/valasek)
- [One-time donation via PayPal](https://paypal.me/StanislavValasek)

---

# Simple Timesheet

Self-hosted web application for weekly reporting. Report your consulting hours on projects using selected rates.

# Rationale

Reporting and billing process includes three separated steps with well-defined data which flows in between:
* **Time reporting** - all consultants
  * covered by this app - data are safe, eliminates manual errors, shows important data for consultants, data entry is as easy as possible
* **Billing preparation** (confirming/editing reported hours for billing) - project manager or administrative person
  * covered partially by this app. If you bill 1:1 with your reporting then it has all you need
  * data are available in the DB which can be exported by this app read or exported by any DB tool
* **Exporting reported and billed hours** in the internal accounting system for the invoicing to the clients and consultants - salaries
  * not covered by this app
  * data are available in the DB which can be exported by this app read or exported by any DB tool

# Screenshots

![Home](screenshots/home.png?raw=true "Home")

![Reported Overview](screenshots/reported_overview.png?raw=true "Reported Overview")

![State Holidays](screenshots/holidays.png?raw=true "State Holidays")

![Admnistration](screenshots/administration.png?raw=true "Admnistration")

![Help](screenshots/help.png?raw=true "Help")

# Requirements

- Linux, Windows or MacOS
- PostgreSQL DB
- Initialize the DB via `timesheet db --clean`
- Import data from csv via `timesheet db --load all`
  - mandatory: consultants, projects, rates, holidays
  - optional: reported_records
- start the server `timesheet server`

Simple timesheet can be also deployed using Docker (server image size 24.9 MB, DB image size 312 MB)

# How to start
`docker-compose -f "docker-compose.yml" up -d --build`
- Update Application settings , Vacation settings and Warning limits to meet your needs
- Use Backup & Restore to export demo data. Update csv files and import back your projects, rates, consultants and holidays.
- You are good to go 


# Contributing

I would love your help! Before submitting a PR, please read over the [Contributing](CONTRIBUTING.md) guide.

Here's a couple of areas that could use some love:

* **Import/Export plugins** - do you like functionality but want to integrate with your company billing SW? Create an issue and if you can submit PR.
* **Javascripts** - I'm no JS wizz, I'm sure the Javascript code in ui/src could be improved/simplified/tested.  
* **Documentation** - Typo? Does something not make sense? Could it be worded better? Please help!
* **Test Coverage** - Would love to get coverage over 80%, fontend and backend.


# Pro Version

My plan is to soon start working on a Pro Version of Timesheet for enterprise. Along with support, some of the planned features include:

* User management/login
* Permissions
* HTTPS
* Plugin for import/export 
* Reporting metrics
* Onsite and Online option

If you or your organization would like to help beta test a Pro version of Timesheet, please get in touch with me:

    Twitter: @valasek
    Email: valasek at gmail.com

# Standing on the shoulders of giants

[Go](https://golang.org/), [Gorm](https://gorm.io/), [Vue](https://vuejs.org/), [axios](https://github.com/axios/axios), [Vuetify](https://vuetifyjs.com/en/), [PostgreSQL](https://www.postgresql.org/)

## Backend

- Middleware: [Negroni](https://github.com/urfave/negroni)
- Router: [Gorilla](https://github.com/gorilla/mux)
- Orm: [Gorm](https://github.com/jinzhu/gorm) (with [PostgreSQL](https://www.postgresql.org/) persistence)
- Jwt authentication: [jwt-go](https://github.com/dgrijalva/jwt-go) and [go-jwt-middleware](https://github.com/auth0/go-jwt-middleware)
- User management

## Frontend

- [Vue.js](https://vuejs.org/) spa client with webpack
- [Vuetify](https://vuetifyjs.com/en/) - light theme
