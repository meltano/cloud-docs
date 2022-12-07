# Why would I migrate?
DuckDB offers a number of advantages in some contexts. Some reasons include
1. Better performance: In a small job DuckDB is just a file which in the context
1. Lower dependencies: Unlike Postgres, which requires a dedicated server or virtual machine to run, DuckDB is just a single file that you can run directly on your device. This makes it easier to set up and deploy, and it reduces the need for additional infrastructure and maintenance.
1. Pushing data to S3/Parquet, if your end goal is to pull data from a tap, and push it to s3/parquet you probably don't need to use a datawarehouse and instead can just run locally 

# How to migrate your Meltano project from Postgres to DuckDB
1. Install target-duckdb, follow the install steps [here](https://hub.meltano.com/loaders/target-duckdb)
2. If you're using dbt already in Meltano I'd recommend just updating the pip_url for dbt to `dbt-core~=1.2.0 dbt-duckdb~=1.2.0 duckdb==0.6.1`, this is easier than using the `dbt-duckdb` as you won't have to merge the files that come along with `dbt-duckdb` note these versions will be out of date. Pull the latest versions from the hub 
    1. You will need to update your dbt `profiles.yml` to the type of `duckdb`, as well as add a `path` in an `output` pointing to your duckdb database.
Example profiles.yml
```yaml
config:
  send_anonymous_usage_stats: False
  use_colors: True
meltano:
  target: "{{ env_var('MELTANO_ENVIRONMENT', 'dev') }}"
  outputs:
    dev:
      type: duckdb
      path: "{{ env_var('DBT_PATH') }}"
      threads: 4
      schema: autoidm
    staging:
      type: duckdb
      path: "{{ env_var('DBT_PATH') }}"
      threads: 4
      schema: autoidm
    prod:
      type: duckdb
      path: "{{ env_var('DBT_PATH') }}"
      threads: 4
      schema: autoidm
```
3. Note that the duckdb version will need to be the same for each plugin that you use in meltano. To accomplish that in the pipurl add a space and `duckdb==0.6.1` or whatever version you'd like to use. This will force the correct version of duckdb to be installed with the related plugin
4. You're ready to install everything (I'd recommend doing a clean install especially if you messed with the pip urls) `meltano install --clean`
5. Run the job using target-duckdb instead of postgres ie `meltano run tap-toggl target-duckdb dbt:run`
6. Debug any SQL incompatabilities you may have between Postgres dialect SQL and DuckDB sql. DuckDBs documentation may come in handy [here](https://duckdb.org/docs/sql/introduction) 
