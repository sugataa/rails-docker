# Dockerizing Ruby on Rails
Making Ruby on Rails and Docker play nice.

## What is Docker?

Package an app or service with its dependencies - code, runtime, libraries, basically everything that you would need to install it on a server.

## What's the difference between Docker & VMs?

Not much, they both do isolation but there are specific tradeoffs:

VMs:
- Require a guest operating system for each isolated application
- Longer startup time to boot VM
- VMs can potentially be GBs in size

Docker:
- Shares host's kernel
- Isolation is done using linux kernel libraries (cgroups)
- Lightweight, milliseconds for bootime, low storage overhead

## Why should I use it?

1. Encapsulates application, such that moving it between environments is simple. Build once, run anywhere mantra.

2. No more pain setting up someone's dev environment, just plug and play a docker image.

3. Docker makes microservices look easy.

4. Scale up fast - images start up very fast, deployments are more predictable and resilient.

Source: https://semaphoreci.com/community/tutorials/dockerizing-a-ruby-on-rails-application

## Common Commands

See running processes:

```docker ps```

Will give an ouput similar to:

```CONTAINER ID        IMAGE                      COMMAND                  CREATED             STATUS              PORTS                    NAMES
55c96a81e2b5        railsdocker_rails-docker   "/bin/sh -c 'bundle e"   6 minutes ago       Up 6 minutes        0.0.0.0:8000->8000/tcp   railsdocker_rails-docker_1
d366bb743191        railsdocker_sidekiq        "bundle exec sidekiq "   6 minutes ago       Up 6 minutes                                 railsdocker_sidekiq_1
8a0941486bdc        redis:3.0.5                "/entrypoint.sh redis"   10 minutes ago      Up 9 minutes        0.0.0.0:6379->6379/tcp   railsdocker_redis_1
c26564a4943e        postgres:9.4.5             "/docker-entrypoint.s"   10 minutes ago      Up 9 minutes        0.0.0.0:5432->5432/tcp   railsdocker_postgres_1```

Connect to the postgres database:

```psql -h localhost -p 5432```


