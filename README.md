# Entregable Final — Tecnología de Base de Datos I

Migración de tablas, vistas y consultas de verificación de la base `employees` (MariaDB) hacia `pdb_employees` (PostgreSQL 18), como fase final del proyecto de migración de SGBD iniciado en el Bloque 3.

## Contenido del repositorio

| Archivo | Descripción |
|---|---|
| [`informe_final.md`](./informe_final.md) | Informe completo: migración de tablas, migración de vistas y consultas de verificación, con comandos y salidas reales. |
| [`backup/pdb_employees_backup.dump`](./backup/pdb_employees_backup.dump) | Respaldo de la base `pdb_employees` ya migrada (formato `custom` de `pg_dump`, 34 MB). |

## Resumen de resultados

- **6 tablas migradas**, 3 919 015 filas en total, sin diferencias de conteo entre origen y destino.
- **2 vistas** (`dept_emp_latest_date`, `current_dept_emp`) recreadas y verificadas con datos reales.
- **Verificación en tres capas**: conteo de filas, checksum MD5 e integridad referencial (0 huérfanos en las 6 relaciones de llave foránea).

## Cómo restaurar el backup

```bash
createdb pdb_employees_restaurada
pg_restore -h <host> -U <usuario> -d pdb_employees_restaurada backup/pdb_employees_backup.dump
```

## Proyecto relacionado

Este entregable depende de la estructura creada en la actividad anterior del Bloque 3 (diccionario de datos, diseño en pgModeler y migración de estructura DDL), que definió el esquema de `pdb_employees` sobre el que se cargaron estos datos.
