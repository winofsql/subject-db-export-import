# subject-db-export-inport

## MySQL CMD Export
```
mysqldump --host=localhost --user=root --password= lightbox > lightbox-backup.sql 
```

## MySQL CMD Import
```
mysql -h localhost -u root -D lightbox --password= < lightbox-backup.sql 
```

### MySQL csv Export
```
SELECT
    *
 FROM
    社員マスタ
 INTO OUTFILE
     'C:/app/workspace/subject-1101/subject-1008-mysql/data03.932'
    CHARACTER SET cp932
    FIELDS TERMINATED BY ','
    OPTIONALLY ENCLOSED BY '"'
    LINES TERMINATED BY '\r\n';
```

## MySQL csv Import
```
LOAD DATA INFILE
    'C:/app/workspace/subject-1101/subject-1008-mysql/data01.932'
 INTO TABLE 社員マスタ
    CHARACTER SET cp932
    FIELDS TERMINATED BY ','
    OPTIONALLY ENCLOSED BY '"'
    LINES TERMINATED BY '\r\n';
```

## PostgreSQL CMD Export
```
pg_dump -d -U postgres lightbox > lightbox.sql
```

## PostgreSQL csv Export
```
COPY 社員マスタ
    TO '/app/workspace/csv/postgres-export-syain.csv'
WITH
    CSV HEADER
    ENCODING 'sjis'
```

## PostgreSQL csv Import
```
COPY 社員マスタ
    FROM '/app/workspace/csv/postgres-export-syain.csv'
WITH
    CSV HEADER
    ENCODING 'sjis'
```

