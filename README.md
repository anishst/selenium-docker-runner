# Selenium Docker Runner

To Run Docker Tests created by Docker image from [JavaSeleniumDocker project](https://github.com/anishst/JavaSeleniumDocker)

## How to Run

1. create Jenkins pipeline job using this project
2. run job

## Stopping all Selenium related containers if there is an error

```docker container stop $(docker container ls -q --filter name=selenium*)```
