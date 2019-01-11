# Exercise 2.1

docker-compose.yml:

version: '3.5'

services:
   frontti:
      image: frontend
      build: .
      ports:
       - 5000:5000
   backi:
      image: backend
      build: .
      ports:
       - 8000:8000

command:

docker-compose up -d

# Exercise 2.2

docker-compose.yml:

version: '3.5'

services:
   frontti:
      image: frontend
      build: .
      ports:
       - 5000:5000
   backi:
      image: backend
      build: .
      ports:
       - 8000:8000
      environment:
       - REDIS=redis
   redis:
      image: redis

command:

docker-compose up

# Exercise 2.3

docker-compose.yml file:

version: '3.5'

services:
   frontti:
      image: frontend
      build: .
      ports:
       - 5000:5000
   backi:
      image: backend
      build: .
      ports:
       - 8000:8000
      environment:
       - REDIS=redis
       - DB_USERNAME=vseppane
       - DB_PASSWORD=sala1nen
       - DB_HOST=postgres
   redis:
      image: redis
   postgres:
      image: postgres
      environment:
       - POSTGRES_PASSWORD=sala1nen
       - POSTGRES_USER=vseppane

command:

docker-compose up