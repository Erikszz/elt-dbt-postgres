FROM python:3.8-slim

# install dependencies
RUN apt-get update && apt-get install -y wget gnupg2

# add PostgreSQL repository
RUN echo "deb http://apt.postgresql.org/pub/repos/apt bookworm-pgdg main" > /etc/apt/sources.list.d/pgdg.list && \
    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -

# install PostgreSQL client
RUN apt-get update && apt-get install -y postgresql-client

# copy the ELT script
COPY elt_script.py .

# set the default command to run the ELT script
CMD ["python", "elt_script.py"]
