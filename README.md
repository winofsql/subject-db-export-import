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

### MySQL csv Import
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
pg_dump -d lightbox -U postgres -Fp --inserts -f /app/workspace/postgres-backup.data
```
-d データーベース -U ユーザ -Fp テキストフォーマット --insert insert文でデータを出力 -f 出力ファイル

## PostgreSQL CMD Import
```
pg_restore -Fp -c -d lightbox /app/workspace/postgres-backup.data
```
-c 直前に削除 

### PostgreSQL csv Export
```
COPY 社員マスタ
    TO '/app/workspace/csv/postgres-export-syain.csv'
WITH
    CSV HEADER
    ENCODING 'sjis'
```

### PostgreSQL csv Import
```
COPY 社員マスタ
    FROM '/app/workspace/csv/postgres-export-syain.csv'
WITH
    CSV HEADER
    ENCODING 'sjis'
```

## SQLite3 CMD

### csv Export (1)
```
sqlite3 -csv -header lightbox.sqlite3 "select * from 社員マスタ" > syain.csv
```

### csv Export (2)
#### csvget.txt
```
.headers on
.mode csv
.output syain.csv
SELECT * FROM 社員マスタ;
.quit
```
```
sqlite3 lightbox.sqlite3 < csvget.txt
```
#### csv インポートコマンド
```
.import csv_file_path table_name
```
