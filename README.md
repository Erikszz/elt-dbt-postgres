# **A Simple ELT Pipeline with Docker, PostgreSQL, and dbt**

This project creates a custom dataset, stores it in the source database, and then loads it into the destination database following the ELT approach. Once the data is in the database, it is transformed using dbt to ensure it is clean, structured, and ready for further analysis.

#### **Project Structure**
* `.dbt` - This folder contains the result of running `dbt init`.
* `custom_postgres` - The dbt folder containing transformations and any related subfolders.
* `elt_script/` - Contains the Dockerfile and ELT script related to the Docker Compose file.
* `source_db_init/init.sql` - This SQL script initializes the source database with sample data, creating tables and inserting sample data into them.
* `docker-compose.yaml` - Contains the containers for the source and destination databases, the ELT script container, and the dbt container.

#### **ELT Flow and Process**
* The `init.sql` file will automatically run when the PostgreSQL container starts, initializing the database.
* After PostgreSQL is ready (retrying up to 5 times).
* Extract data from the source PostgreSQL database.
* Load data into the destination PostgreSQL database.
* Transform the data using dbt.

#### **How To Start**

##### **Make virtual enviroment**
```
python -m venv dbt-venv
```

##### **Activate virtual enviroment**
Windows:
```
dbt-venv\Scripts\activate
```

Linux:
```
source dbt-venv/bin/activate
```

##### **Installing dbt-postgres**
```
python -m pip install dbt-core dbt-postgres
```

##### **Initialize dbt project**
```
dbt init <project name>
```

##### **Running Docker and Docker-Compose in Detached Mode**
```
docker-compose up -d --build
```

##### **Stop All Containers**
```
docker-compose down
```


#### **Resources**
* Get to Know More About [Docker](https://www.docker.com/) and [Docker-Compose](https://docs.docker.com/compose/)
* Learn More About [PostgreSQL Image in Docker](https://hub.docker.com/_/postgres/)
* Learn More About [Dbt Image in Docker](https://docs.getdbt.com/docs/core/docker-install)
* What is [dbt](https://docs.getdbt.com/docs/introduction)?
* Get Started with [dbt](https://docs.getdbt.com/docs/get-started-dbt)

