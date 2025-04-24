FROM postgres:16

# Copy initialization SQL script
COPY init.sql /docker-entrypoint-initdb.d/
COPY pg_hba.conf /etc/postgresql/16/main/

#docker build -t my-postgres .
#docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d -p 5432:5432 my-postgres
