---
title: "CREATE TABLE empleado (     id_empleado      INTEGER NOT NULL,     nombre_empleado  VARCHAR2(20),     fecha_ingreso    DATE );  ALTER TABLE empleado ADD CONSTRAINT empleado_pk PRIMARY KEY ( id_empleado );  CREATE TABLE prestaciones (     id_prestacion_servicio  INTEGER NOT NULL,     id_servicio             INTEGER NOT NULL,     id_empleado             INTEGER NOT NULL,     id_vehiculo             INTEGER NOT NULL,     fecha                   DATE );  ALTER TABLE prestaciones     ADD CONSTRAINT prestaciones_pk PRIMARY KEY ( id_prestacion_servicio,                                                  id_servicio,                                                  id_empleado,                                                  id_vehiculo );  CREATE TABLE servicio (     id_servicios     INTEGER NOT NULL,     nombre_servicio  VARCHAR2(50),     valor_servicio   VARCHAR2(20) );  ALTER TABLE servicio ADD CONSTRAINT servicio_pk PRIMARY KEY ( id_servicios );  CREATE TABLE vehiculo (     id_vehiculo      INTEGER NOT NULL,     marca_vehiculo   VARCHAR2(20),     modelo_vehiculo  VARCHAR2(20) );  ALTER TABLE vehiculo ADD CONSTRAINT vehiculo_pk PRIMARY KEY ( id_vehiculo );"
tags: ""
---

## EJERCICIO_1

## DLL_1

```sql
CREATE TABLE empleado (
    idempleado      INTEGER NOT NULL,
    nombreempleado  VARCHAR2(20),
    fechaingreso    DATE
);

ALTER TABLE empleado ADD CONSTRAINT empleado_pk PRIMARY KEY ( idempleado );

CREATE TABLE prestaciones (
    idprestacionservicio  INTEGER NOT NULL,
    idservicio            INTEGER NOT NULL,
    idempleado            INTEGER NOT NULL,
    idvehiculo            INTEGER NOT NULL,
    fecha                 DATE
);

ALTER TABLE prestaciones
    ADD CONSTRAINT prestaciones_pk PRIMARY KEY ( idprestacionservicio,
                                                 idservicio,
                                                 idempleado,
                                                 idvehiculo );

CREATE TABLE servicio (
    idservicios     INTEGER NOT NULL,
    nombreservicio  VARCHAR2(20),
    valorservicio   VARCHAR2(20)
);

ALTER TABLE servicio ADD CONSTRAINT servicio_pk PRIMARY KEY ( idservicios );

CREATE TABLE vehiculo (
    idvehiculo      INTEGER NOT NULL,
    marcavehiculo   VARCHAR2(20),
    modelovehiculo  VARCHAR2(20)
);

ALTER TABLE vehiculo ADD CONSTRAINT vehiculo_pk PRIMARY KEY ( idvehiculo );
```

## DML_1

### INGRESAR DATOS

```sql
INSERT ALL
	INTO EMPLEADO (idempleado,nombreempleado,fechaingreso) VALUES (1,'Francisco',TO_DATE('01-03-2005', 'DD-MM-YYYY'))
	INTO EMPLEADO (idempleado,nombreempleado,fechaingreso) VALUES (2,'Jorge',TO_DATE('01-07-2018', 'DD-MM-YYYY'))
	INTO EMPLEADO (idempleado,nombreempleado,fechaingreso) VALUES (3,'Pedro',TO_DATE('01-03-2014', 'DD-MM-YYYY'))
	INTO EMPLEADO (idempleado,nombreempleado,fechaingreso) VALUES (4,'Diego',TO_DATE('01-10-2001', 'DD-MM-YYYY'))
SELECT * FROM dual


INSERT ALL
	INTO SERVICIOS (idservicio,nombreservicio,valorservicio) VALUES (1,'Desabolladora',120000)
	INTO SERVICIOS (idservicio,nombreservicio,valorservicio) VALUES (2,'Pulido',35000)
	INTO SERVICIOS (idservicio,nombreservicio,valorservicio) VALUES (3,'Pintura',180000)
	INTO SERVICIOS (idservicio,nombreservicio,valorservicio) VALUES (4,'Lavado',10000)
SELECT * FROM dual


INSERT ALL
        INTO VEHICULO (idvehiculo,marcavehiculo,modelovehiculo) VALUES (1,'KIA','Sportage')
        INTO VEHICULO (idvehiculo,marcavehiculo,modelovehiculo) VALUES (2,'Renault','Capture')
        INTO VEHICULO (idvehiculo,marcavehiculo,modelovehiculo) VALUES (3,'Citroen','C3')  
        INTO VEHICULO (idvehiculo,marcavehiculo,modelovehiculo) VALUES (4,'Nissan','Kicks')  
SELECT * FROM dual	
```

```sql
*Mostrar cantidad de prestaciones de servicios ejecutados entre el 01 de octubre y el 26 de noviembre del 2018*

SELECT count(idservicio) FROM prestaciones
WHERE fecha
BETWEEN '2018-10-01' AND '2018-11-26';


*Mostrar cantidad total de prestaciones realizadas agrupadas por idVehículo*

SELECT count(idservicio) FROM prestaciones
WHERE idvehiculo IS NOT NULL;


*Mostrar los vehiculos con la menor cantidad de prestaciones de servicios realizados*

SELECT idvehiculo FROM prestaciones
ORDER BY idservicio ASC; 
```

## EJERCICIO_2

## DLL_2

```sql
CREATE TABLE empleado (
    idempleado     INTEGER NOT NULL,
    nombre         VARCHAR2(20) NOT NULL,
    apellido       VARCHAR2(20) NOT NULL,
    direccion      VARCHAR2(20) NOT NULL,
    telefono       VARCHAR2(15) NOT NULL,
    iddepatamento  INTEGER NOT NULL
);

ALTER TABLE empleado ADD CONSTRAINT empleado_pk PRIMARY KEY ( idempleado );
```

## DML_2

```sql
INSERT ALL
	INTO EMPLEADO (idempleado,nombreempleado,fechaingreso) VALUES (1,'Francisco','Perez','Zapadores 345 dpto 302', 97453921,001)
	INTO EMPLEADO (idempleado,nombreempleado,fechaingreso) VALUES (2,'Jorge','Fernandez','General Jofre 335', 98220924,002)
    INTO EMPLEADO (idempleado,nombreempleado,fechaingreso) VALUES (3,'Pedro','Garcia','Zapadores 345 dpto 302', 97226538,003)
    INTO EMPLEADO (idempleado,nombreempleado,fechaingreso) VALUES (4,'Diego','Solis','Lo Vial 122 dpto 708', 98107425,004)
SELECT * FROM dual
```

## EJERCICIO_3

## DLL_3

```sql
CREATE TABLE actor (
    idactor      INTEGER NOT NULL,
    nombreactor  VARCHAR2(30 CHAR) NOT NULL,
    pelicula     VARCHAR2(30 CHAR),
    personaje    VARCHAR2(30)
);

ALTER TABLE actor ADD CONSTRAINT actor_pk PRIMARY KEY ( idactor );

CREATE TABLE director (
    iddirector      INTEGER NOT NULL,
    nombredirector  VARCHAR2(30 CHAR) NOT NULL,
    nacionalidad    VARCHAR2(30 CHAR),
    peliculas       VARCHAR2(4000)
);

ALTER TABLE director ADD CONSTRAINT director_pk PRIMARY KEY ( iddirector );

CREATE TABLE pelicula (
    idpelicula      INTEGER NOT NULL,
    nombreoriginal  VARCHAR2(30 CHAR),
    nombre          VARCHAR2(30 CHAR),
    genero          VARCHAR2(30 CHAR),
    idioma          VARCHAR2(30 CHAR),
    subesp          CHAR(1),
    origen          VARCHAR2(30 CHAR),
    anio            INTEGER,
    web             VARCHAR2(40 CHAR),
    duracion        DATE,
    calificacion    VARCHAR2(30 CHAR),
    estreno         DATE,
    sinopsis        VARCHAR2(100 CHAR),
    director        VARCHAR2(30 CHAR),
    reparto         VARCHAR2(4000)
);

ALTER TABLE pelicula ADD CONSTRAINT pelicula_pk PRIMARY KEY ( idpelicula );

CREATE TABLE calificacion (
    obra_maestra  VARCHAR2(10),
    muy_buena     VARCHAR2(10),
    buena         VARCHAR2(10),
    regular       VARCHAR2(10),
    mala          VARCHAR2(10)
);

CREATE TABLE opinion (
    opinion           INTEGER NOT NULL,
    nombreopinador    VARCHAR2(30),
    edad              INTEGER NOT NULL,
    fecharealizacion  DATE,
    calificacion      INTEGER NOT NULL
);

ALTER TABLE opinion ADD CONSTRAINT opinion_pk PRIMARY KEY ( opinion,
                                                            calificacion );

CREATE TABLE promocion (
    descuentos   INTEGER NOT NULL,
    descripcion  VARCHAR2(50)
);

ALTER TABLE promocion ADD CONSTRAINT promocion_pk PRIMARY KEY ( descuentos );

CREATE TABLE cine (
    idsala       INTEGER NOT NULL,
    cartelera    VARCHAR2(30),
    descripcion  VARCHAR2(50),
    direccion    VARCHAR2(30),
    telefono     VARCHAR2(15)
);

ALTER TABLE cine ADD CONSTRAINT cine_pk PRIMARY KEY ( idsala );
```
