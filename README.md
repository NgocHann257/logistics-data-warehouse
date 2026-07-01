# Data Warehouse Pipeline

Pipeline này tích hợp:
- Ingestion từ file CSV vào DuckDB local
- Validation bằng Great Expectations
- Transform bằng dbt vào các schema silver/gold
- Đồng bộ dữ liệu lên MotherDuck qua biến môi trường secrets

## Cấu hình cần thiết trên GitHub

Thêm hai secrets trong repository:
- MOTHERDUCK_TOKEN
- MOTHERDUCK_DB

## Chạy local

```bash
python -m pip install -r requirements.txt
python elt/ingest.py
dbt deps --project-dir elt/dbt_dataco --profiles-dir elt/dbt_dataco
dbt build --project-dir elt/dbt_dataco --profiles-dir elt/dbt_dataco
```
