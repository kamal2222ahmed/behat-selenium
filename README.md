# Behat Zalenium TEST
ref: 
1. https://github.com/kamal2222ahmed/behat-selenium
2. https://opensource.zalando.com/zalenium/
3. https://runnable.com/docker/getting-started/
4. https://github.com/edmondscommerce/behat-zalenium-context
5. https://www.edmondscommerce.co.uk/handbook/Development-Tools/Testing/Zalenium/
6. http://localhost:4444/wd/hub
7. http://localhost:4444/grid/admin/live


:warning: You must have docker installed if you want execute test on your local environment.

## 1. Installation

```bash
$ composer install
```

## 2. Start docker environment

We have setup 3 containers in order to run our test.
 - Webserver with Nginx to serve our html files
 - Selenium to perform browser operation
 - Php cli for execute behat tests

```bash
# up the nginx & selenium container and wait until selenium is ready
$ make start 
```

## 3. Run behat tests

In order to run the tests only when your features files have change, we use Makefile
for run the suite of tests, the execution if perfomed into a dedicated container for 
avoid any configuration issue related to php version or communication with seleniumm services.

> You can execute `make clean` to drop the log file and be able to re run the test again.

```bash
$ make behat
```

## 4. Purge the local environment

If you want cleanup the containers created by this project,
run the next command.

```bash
$ make purge
```

=============== For Demo with Selenium using Python:

1. cd to repo git@github.com:kamal2222ahmed/behat-selenium.git

2. docker-compose up -d

3. cd to repo https://github.com/testdrivenio/selenium-grid-docker-swarm.git

4. $ for i in {1..8}; do {
          python project/script.py ${i} &
        };
        done

Observe the parallel selenium tests running at http://localhost:4444/grid/console

