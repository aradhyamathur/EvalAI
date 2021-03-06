# EvalAI

[![Join the chat at https://gitter.im/Cloud-CV/EvalAI](https://badges.gitter.im/Cloud-CV/EvalAI.svg)](https://gitter.im/Cloud-CV/EvalAI?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Build Status](https://travis-ci.org/Cloud-CV/EvalAI.svg?branch=master)](https://travis-ci.org/Cloud-CV/EvalAI)
[![Coverage Status](https://coveralls.io/repos/github/Cloud-CV/EvalAI/badge.svg)](https://coveralls.io/github/Cloud-CV/EvalAI)
[![Requirements Status](https://requires.io/github/Cloud-CV/EvalAI/requirements.svg?branch=master)](https://requires.io/github/Cloud-CV/EvalAI/requirements/?branch=master)
[![Code Health](https://landscape.io/github/Cloud-CV/EvalAI/master/landscape.svg?style=flat)](https://landscape.io/github/Cloud-CV/EvalAI/master)
[![Code Climate](https://codeclimate.com/github/Cloud-CV/EvalAI/badges/gpa.svg)](https://codeclimate.com/github/Cloud-CV/EvalAI)


EvalAI is an open source web application that helps researchers, students and data-scientists to create, collaborate and participate in various AI challenges organized round the globe.

## How to setup

Setting up EvalAI on your local machine is really easy.
Follow this guide to setup your development machine.

1. Install [git], [postgresql] version >= 9.4, [RabbitMQ] and [virtualenv], in your computer, if you don't have it already.
*If you are having trouble with postgresql on Windows check this link [postgresqlhelp].*

2. Get the source code on your machine via git.

    ```shell
    git clone https://github.com/Cloud-CV/EvalAI.git evalai
    ```

3. Create a python virtual environment and install python dependencies.

    ```shell
    cd evalai
    virtualenv venv
    source venv/bin/activate  # run this command everytime before working on project
    pip install -r requirements/dev.txt
    ```

4. Rename `settings/dev.sample.py` as `dev.py` and change credential in `settings/dev.py`

    ```
    cp settings/dev.sample.py settings/dev.py
    ```
    Use your linux system username and password for fields `USER` and `PASSWORD` in `dev.py` file.

5. Create an empty postgres database and run database migration.

    ```
    createdb evalai
    python manage.py migrate --settings=settings.dev
    ```

6. That's it. Now you can run development server at http://127.0.0.1:8000 (for serving backend)

    ```
    python manage.py runserver --settings=settings.dev
    ```


7. Open a new terminal window with node(6.9.2) and ruby(gem) install on your machine and type

    ```
    npm install
    bower install
    ```

8. Now to connect to dev server at http://127.0.0.1:8888 (for serving frontend)

    ```
    gulp dev:runserver
    ```

9. That's it, Open web browser and hit the url `http://127.0.0.1:8888`.

10. (Optional) If you want to see the whole game into play, then start the RabbitMQ worker in a new terminal window using the following command that consumes the submissions done for every challenge:

    ```
    python scripts/workers/submission_worker.py
    ```

## Contribution guidelines

If you are interested in contributing to EvalAI, follow your [contribution guidelines](https://github.com/Cloud-CV/EvalAI/blob/master/CONTRIBUTING.md).

[git]: https://git-scm.com/downloads
[virtualenv]: https://virtualenv.pypa.io/
[postgresql]: http://www.postgresql.org/download/
[postgresqlhelp]: http://bobbyong.com/blog/installing-postgresql-on-windoes/
[rabbitmq]: https://www.rabbitmq.com/
