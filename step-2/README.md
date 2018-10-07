# Step 2

Where do I find geo data for my website?

To make the tutorial as relevant as possible, I want to show how it's possible to
download information about my workshop country (in this case, Zimbabwe) and import
it into PostGIS.  This can be difficult to install and troubleshoot, so I might end
up showing most of this on the projector. Even if students cannot import data in the workshop, they can run future steps with the tables in the PostGIS cloud instance or the Jupyter notebooks.

All of these datasets will be imported into a PostGIS database (PostgreSQL + extensions).

Data will be used in the later steps.

### Installing and running locally

Install Python, pip, PostgreSQL, and PostGIS extensions.

Install ogr2ogr by installing GDAL.

IF YOU ARE SETTING UP DATABASE AND READ-ONLY USER FOR THE FIRST TIME:

```
mkdir ~/Documents/pyzimmer # data can be stored in any new directory, just be consistent
initdb pyzimmer/
postgres -D pyzimmer/
createdb pyzim
psql pyzim

# you are now in the PSQL prompt
CREATE USER py;
ALTER USER py WITH PASSWORD 'zim';
GRANT CONNECT ON DATABASE pyzim TO py;
GRANT USAGE ON SCHEMA public TO py;
ALTER DEFAULT PRIVILEGES IN SCHEMA public
  GRANT SELECT ON TABLES TO py;
```

### Interactive Tutorial

TBD: walk-through downloading and importing districts

You can test that the data got imported into PostGIS and is readable by py:zim user:

TBD: replace the trains example with districts:

```
psql pyzim -U py
# you are now in the PostgreSQL prompt

SELECT COUNT(*) FROM trains;

 count
------
    2
```

TBD: walk-through downloading and importing OSM features

TBD: test that OSM features are present

### Learnings

- Do members of PyZim know good sources for local open data?
- What is OpenStreetMap?
- How can I get data to make quality websites?
- (Ideally) how-to for installing ogr2ogr on my computer