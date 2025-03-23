# Base de Datos de División Administrativa del Ecuador  

Este repositorio contiene scripts SQL para la creación y población de una base de datos con información de las provincias, cantones y parroquias del Ecuador.

## Contenido del Repositorio  

Este repositorio incluye los siguientes archivos:  

- **`provincias_schema_data.sql`** → Contiene la estructura de la tabla `PROVINCIAS` y la inserción de sus datos.  
- **`cantones_schema_data.sql`** → Contiene la estructura de la tabla `CANTONES` y la inserción de sus datos.  
- **`parroquias_schema_data.sql`** → Contiene la estructura de la tabla `PARROQUIAS` y la inserción de sus datos.  
- **`2022_CPV_NACIONAL_DENSIDAD_POBLACIONAL.xlsx`** → Archivo original del censo usado como fuente de datos.

## Estructura de la Base de Datos  

La base de datos se compone de tres tablas relacionadas:  

```sql
CREATE TABLE PROVINCIAS (
    PROVINCIA_ID SERIAL PRIMARY KEY,
    PROVINCIA_NOMBRE VARCHAR(35) NOT NULL
);

CREATE TABLE CANTONES (
    CANTON_ID SERIAL PRIMARY KEY,
    CANTON_NOMBRE VARCHAR(50) NOT NULL,
    PROVINCIA_ID INTEGER NOT NULL,
    CONSTRAINT FK_CANTON_PROVINCIA FOREIGN KEY (PROVINCIA_ID) REFERENCES PROVINCIAS(PROVINCIA_ID)
);

CREATE TABLE PARROQUIAS (
    PARROQUIA_ID SERIAL PRIMARY KEY,
    PARROQUIA_NOMBRE VARCHAR(75) NOT NULL,
    CANTON_ID INTEGER NOT NULL,
    CONSTRAINT FK_PARROQUIA_CANTON FOREIGN KEY (CANTON_ID) REFERENCES CANTONES(CANTON_ID)
);
```

## Licencia

Este proyecto está disponible bajo la licencia MIT.

## Contribuciones

Las contribuciones son bienvenidas. Para realizar mejoras o agregar nuevas funcionalidades, por favor abre un issue o un pull request en este repositorio.
