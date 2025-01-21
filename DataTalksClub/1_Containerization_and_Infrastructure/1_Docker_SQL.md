Why docker?  
- Local experiments
- Integration tests (CI/ CD)
- Reproducibility
- Running pipelines on the cloud (AWS, GCP, ...)
- Spark
- Serverless (AWS Lambda, ...)

`docker run -it test:pandas 1989-06-04`

Download dataset: 
```bash
wget https://github.com/DataTalksClub/nyc-tlc-data/releases/download/yellow/yellow_tripdata_2021-01.csv.gz
```

Run Postgres with Docker:
```Bash
docker run -it \
  -e POSTGRES_USER="root" \
  -e POSTGRES_PASSWORD="root" \
  -e POSTGRES_DB="ny_taxi" \
  -v c:/Users/alexe/git/data-engineering-zoomcamp/week_1_basics_n_setup/2_docker_sql/ny_taxi_postgres_data:/var/lib/postgresql/data \
  -p 5432:5432 \
  postgres:13
```
