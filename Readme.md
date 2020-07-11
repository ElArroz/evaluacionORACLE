
## Ejercicio 1
Codigo del modelo DDL solicitado para el ejercicio 1, a ser implementado en D.B. Oracle:
```sql
CREATE TABLE empleado (
    idempleado      INTEGER NOT NULL,
    nombreempleado  VARCHAR2(25) NOT NULL,
    fechaingreso    DATE NOT NULL
);

ALTER TABLE empleado ADD CONSTRAINT empleado_pk PRIMARY KEY ( idempleado );

CREATE TABLE ps (
    idprestacionservicio  INTEGER NOT NULL,
    fecha                 DATE NOT NULL,
    empleado_idempleado   INTEGER NOT NULL,
    servicio_idservicio   INTEGER NOT NULL,
    vehiculo_idvehiculo   INTEGER NOT NULL
);

ALTER TABLE ps ADD CONSTRAINT ps_pk PRIMARY KEY ( idprestacionservicio );

CREATE TABLE servicio (
    idservicio      INTEGER NOT NULL,
    nombreservicio  VARCHAR2(25) NOT NULL,
    valorservicio   INTEGER
);

ALTER TABLE servicio ADD CONSTRAINT servicio_pk PRIMARY KEY ( idservicio );

CREATE TABLE vehiculo (
    idvehiculo      INTEGER NOT NULL,
    marcavehiculo   VARCHAR2(25) NOT NULL,
    modelovehiculo  VARCHAR2(25)
);

ALTER TABLE vehiculo ADD CONSTRAINT vehiculo_pk PRIMARY KEY ( idvehiculo );

ALTER TABLE ps
    ADD CONSTRAINT ps_empleado_fk FOREIGN KEY ( empleado_idempleado )
        REFERENCES empleado ( idempleado );

ALTER TABLE ps
    ADD CONSTRAINT ps_servicio_fk FOREIGN KEY ( servicio_idservicio )
        REFERENCES servicio ( idservicio );

ALTER TABLE ps
    ADD CONSTRAINT ps_vehiculo_fk FOREIGN KEY ( vehiculo_idvehiculo )
        REFERENCES vehiculo ( idvehiculo );


```
### Continuamos agregando datos:
Ingresamos Empleados:
```SQL
INSERT ALL
	INTO empleado (idEmpleado,nombreEmpleado,fechaIngreso) VALUES (1,'Antonio',TO_DATE('01-01-2015', 'DD-MM-YYYY'))
	INTO empleado (idEmpleado,nombreEmpleado,fechaIngreso) VALUES (2,'Cristian',TO_DATE('01-09-2015', 'DD-MM-YYYY'))
	INTO empleado (idEmpleado,nombreEmpleado,fechaIngreso) VALUES (3,'German',TO_DATE('01-11-2016', 'DD-MM-YYYY'))
	INTO empleado (idEmpleado,nombreEmpleado,fechaIngreso) VALUES (4,'Luis',TO_DATE('01-12-2016', 'DD-MM-YYYY'))
SELECT * FROM dual

```
Ingresamos Servicios
```SQL
INSERT ALL
	INTO servicio (idServicio ,nombreServicio,valorServicio) VALUES (1,'Cambio Aceite',55000)
	INTO servicio (idServicio ,nombreServicio,valorServicio) VALUES (2,'Lubricación',25500)
	INTO servicio (idServicio ,nombreServicio,valorServicio) VALUES (3,'Afinamiento',450000)
	INTO servicio (idServicio ,nombreServicio,valorServicio) VALUES (4,'Mantención 5K',100000)
	INTO servicio (idServicio ,nombreServicio,valorServicio) VALUES (5,'Mantención 10K',185000)
	INTO servicio (idServicio ,nombreServicio,valorServicio) VALUES (6,'Mantención 20K',185000)
	INTO servicio (idServicio ,nombreServicio,valorServicio) VALUES (7,'Mantención 30K',255000)
	INTO servicio (idServicio ,nombreServicio,valorServicio) VALUES (8,'Mantención 40K',215000)
	INTO servicio (idServicio ,nombreServicio,valorServicio) VALUES (9,'Mantención +50K',255000)
	INTO servicio (idServicio ,nombreServicio,valorServicio) VALUES (10,'Garantia',0)
	INTO servicio (idServicio ,nombreServicio,valorServicio) VALUES (11,'Vulca_1',10000)
SELECT * FROM dual
```
Ingresamos Vehiculos
```SQL
INSERT ALL
	INTO vehiculo (idvehiculo ,marcaVehiculo, modeloVehiculo) VALUES (1,'Chevrolet','Sail')
	INTO vehiculo (idvehiculo ,marcaVehiculo, modeloVehiculo) VALUES (2,'Chevrolet','Spark')
	INTO vehiculo (idvehiculo ,marcaVehiculo, modeloVehiculo) VALUES (3,'Nissan','Versa')
	INTO vehiculo (idvehiculo ,marcaVehiculo, modeloVehiculo) VALUES (4,'Nissan','Kicks')
	INTO vehiculo (idvehiculo ,marcaVehiculo, modeloVehiculo) VALUES (5,'AUDI','A3')
	INTO vehiculo (idvehiculo ,marcaVehiculo, modeloVehiculo) VALUES (6,'BMV','X5')
	INTO vehiculo (idvehiculo ,marcaVehiculo, modeloVehiculo) VALUES (7,'Mitsubishi','Outlander')
	INTO vehiculo (idvehiculo ,marcaVehiculo, modeloVehiculo) VALUES (8,'Mitsubishi','Katana')
	INTO vehiculo (idvehiculo ,marcaVehiculo, modeloVehiculo) VALUES (9,'Mahindra','Scorpio')
	INTO vehiculo (idvehiculo ,marcaVehiculo, modeloVehiculo) VALUES (10,'Mahindra','Pick up')
SELECT * FROM dual
```
Ingresamos Prestacion de servicios
```SQL
INSERT ALL
	INTO ps (IDPRESTACIONSERVICIO,SERVICIO_IDSERVICIO,EMPLEADO_IDEMPLEADO,VEHICULO_IDVEHICULO,FECHA) VALUES (1,1,2,1,TO_DATE('20-09-2018', 'DD-MM-YYYY'))
	INTO ps (IDPRESTACIONSERVICIO,SERVICIO_IDSERVICIO,EMPLEADO_IDEMPLEADO,VEHICULO_IDVEHICULO,FECHA) VALUES (2,1,2,1,TO_DATE('22-09-2018', 'DD-MM-YYYY'))
	INTO ps (IDPRESTACIONSERVICIO,SERVICIO_IDSERVICIO,EMPLEADO_IDEMPLEADO,VEHICULO_IDVEHICULO,FECHA) VALUES (3,1,4,5,TO_DATE('28-09-2018', 'DD-MM-YYYY'))
	INTO ps (IDPRESTACIONSERVICIO,SERVICIO_IDSERVICIO,EMPLEADO_IDEMPLEADO,VEHICULO_IDVEHICULO,FECHA) VALUES (4,1,3,5,TO_DATE('05-10-2018', 'DD-MM-YYYY'))
	INTO ps (IDPRESTACIONSERVICIO,SERVICIO_IDSERVICIO,EMPLEADO_IDEMPLEADO,VEHICULO_IDVEHICULO,FECHA) VALUES (5,2,3,9,TO_DATE('07-10-2018', 'DD-MM-YYYY'))
	INTO ps (IDPRESTACIONSERVICIO,SERVICIO_IDSERVICIO,EMPLEADO_IDEMPLEADO,VEHICULO_IDVEHICULO,FECHA) VALUES (6,3,4,7,TO_DATE('19-10-2018', 'DD-MM-YYYY'))
	INTO ps (IDPRESTACIONSERVICIO,SERVICIO_IDSERVICIO,EMPLEADO_IDEMPLEADO,VEHICULO_IDVEHICULO,FECHA) VALUES (7,4,1,5,TO_DATE('25-10-2018', 'DD-MM-YYYY'))
	INTO ps (IDPRESTACIONSERVICIO,SERVICIO_IDSERVICIO,EMPLEADO_IDEMPLEADO,VEHICULO_IDVEHICULO,FECHA) VALUES (8,11,4,5,TO_DATE('01-11-2018', 'DD-MM-YYYY'))
	INTO ps (IDPRESTACIONSERVICIO,SERVICIO_IDSERVICIO,EMPLEADO_IDEMPLEADO,VEHICULO_IDVEHICULO,FECHA) VALUES (9,11,2,2,TO_DATE('28-11-2018', 'DD-MM-YYYY'))
	INTO ps (IDPRESTACIONSERVICIO,SERVICIO_IDSERVICIO,EMPLEADO_IDEMPLEADO,VEHICULO_IDVEHICULO,FECHA) VALUES (10,9,3,7,TO_DATE('29-11-2018', 'DD-MM-YYYY'))
SELECT * FROM dual
```
### Aca realizamos las consultas solicitadas:

**1.-** *Mostrar la cantidad de prestaciones de servicios ejecutados entre el 01 de octubre y el 26 de
noviembre del 2018:*
```sql
SELECT COUNT(idprestacionservicio)
FROM ps
WHERE fecha BETWEEN '01/10/2018' AND '26/11/2018';
```

**2.-** *Mostrar la cantidad total de prestaciones realizadas agrupadas por idVehiculo:*

>*Le colocamos un para de alias con "AS" para facilitar su lectura:*
```sql
SELECT VEHICULO_IDVEHICULO AS Vehiculo,COUNT(*) as Prestaciones
FROM ps
GROUP BY VEHICULO_IDVEHICULO
```
**3.-** *Mostrar los vehículos con la menor cantidad de prestaciones de servicios realizados:*
>*Se ordena el listado de prestaciones menores o iguales a 2, por tipo de vehiculos:*
```sql
SELECT VEHICULO_IDVEHICULO,COUNT(*) as ctdServicios
FROM ps
GROUP BY VEHICULO_IDVEHICULO
HAVING COUNT(*)<=2
ORDER BY ctdServicios ASC;

```

## Ejercicio 2
Código del Modelo DDL para el ejercicio 2, a ser implementado en D.B. Oracle:
```sql
CREATE TABLE empleado (
    idEmpleado		INTEGER NOT NULL,
    nombre  		VARCHAR2(25) NOT NULL,
    apellido  		VARCHAR2(25) NOT NULL,
    direccion		VARCHAR2(25) NOT NULL,
    telefono		VARCHAR2(25) NOT NULL,
    idDepartamento	INTEGER NOT NULL
);
ALTER TABLE empleado ADD CONSTRAINT empleado_pk PRIMARY KEY ( idEmpleado,
							   idDepartamento );
```


## Ejercicio 3
Código del Modelo DDL del ejercicio 3, para ser implementado en D.B. Oracle:

>*Tal como lo genera  la herramienta Oracle SQLdeveloper, se adjuntan imagenes del diseño logico y relacional*

```sql
CREATE TABLE actor (
    id_actor                        INTEGER NOT NULL,
    nombreactor                     VARCHAR2(30) NOT NULL,
    nacionalidad                    VARCHAR2(30),
    apariciones                     INTEGER NOT NULL,
    lista_actores_id_lista_actores  INTEGER NOT NULL
);

ALTER TABLE actor ADD CONSTRAINT actor_pk PRIMARY KEY ( id_actor );

CREATE TABLE cine (
    id_cine    INTEGER NOT NULL,
    nombre     VARCHAR2(20),
    direccion  VARCHAR2(20),
    fono       VARCHAR2(20)
);

ALTER TABLE cine ADD CONSTRAINT cine_pk PRIMARY KEY ( id_cine );

CREATE TABLE director (
    id_director                   INTEGER NOT NULL,
    nombreactor                   VARCHAR2(30) NOT NULL,
    nacionalidad                  VARCHAR2(30),
    apariciones                   INTEGER NOT NULL,
    lista_directores_id_listadir  INTEGER NOT NULL
);

ALTER TABLE director ADD CONSTRAINT director_pk PRIMARY KEY ( id_director );

CREATE TABLE funcion (
    id_cine               INTEGER NOT NULL,
    id_funcion            INTEGER NOT NULL,
    nombre                VARCHAR2(10) NOT NULL,
    dias                  VARCHAR2(15) NOT NULL,
    horainicio            INTEGER,
    sala_id_sala          INTEGER NOT NULL,
    promociones_id_promo  INTEGER
);

ALTER TABLE funcion ADD CONSTRAINT funcion_pk PRIMARY KEY ( id_cine );

ALTER TABLE funcion ADD CONSTRAINT funcion_id_funcion_un UNIQUE ( id_funcion );

CREATE TABLE lista_actores (
    id_lista_actores       INTEGER NOT NULL,
    listaactores           VARCHAR2(30),
    peliculas_id_pelicula  INTEGER
);

CREATE UNIQUE INDEX lista_actores__idx ON
    lista_actores (
        peliculas_id_pelicula
    ASC );

ALTER TABLE lista_actores ADD CONSTRAINT lista_actores_pk PRIMARY KEY ( id_lista_actores );

CREATE TABLE lista_directores (
    id_listadir            INTEGER NOT NULL,
    listadirec             VARCHAR2(30),
    peliculas_id_pelicula  INTEGER
);

CREATE UNIQUE INDEX lista_directores__idx ON
    lista_directores (
        peliculas_id_pelicula
    ASC );

ALTER TABLE lista_directores ADD CONSTRAINT lista_directores_pk PRIMARY KEY ( id_listadir );

CREATE TABLE opinion (
    id_opinion             INTEGER NOT NULL,
    nombre                 VARCHAR2(30) NOT NULL,
    edad                   INTEGER,
    fecha                  DATE NOT NULL,
    calificacion           VARCHAR2(20) NOT NULL,
    comentario             VARCHAR2(100),
    peliculas_id_pelicula  INTEGER
);

ALTER TABLE opinion ADD CONSTRAINT opinion_pk PRIMARY KEY ( id_opinion );

CREATE TABLE peliculas (
    id_pelicula                     INTEGER NOT NULL,
    nombredistribucion              VARCHAR2(30) NOT NULL,
    titulooriginal                  VARCHAR2(30) NOT NULL,
    genero                          VARCHAR2(30) NOT NULL,
    idiomaoriginal                  VARCHAR2(30) NOT NULL,
    subtituloesp                    CHAR(1) NOT NULL,
    anioproduccion                  INTEGER NOT NULL,
    website                         VARCHAR2(30),
    calificacion                    VARCHAR2(10) NOT NULL,
    fechaestreno                    DATE NOT NULL,
    id_lista_directores             INTEGER,
    lista_directores_id_listadir    INTEGER,
    lista_actores_id_lista_actores  INTEGER,
    funcion_id_cine                 INTEGER
);

CREATE UNIQUE INDEX peliculas__idx ON
    peliculas (
        lista_actores_id_lista_actores
    ASC );

CREATE UNIQUE INDEX peliculas__idxv1v1 ON
    peliculas (
        lista_directores_id_listadir
    ASC );

ALTER TABLE peliculas ADD CONSTRAINT peliculas_pk PRIMARY KEY ( id_pelicula );

CREATE TABLE promociones (
    id_promo   INTEGER NOT NULL,
    nombre     VARCHAR2(30),
    descuento  INTEGER NOT NULL
);

ALTER TABLE promociones ADD CONSTRAINT promociones_pk PRIMARY KEY ( id_promo );

CREATE TABLE sala (
    cine_id_cine  INTEGER
        CONSTRAINT nnc_sala_id_cine NOT NULL,
    id_sala       INTEGER
        CONSTRAINT nnc_sala_id_sala NOT NULL,
    nombre        VARCHAR2(10),
    butacas       INTEGER
        CONSTRAINT nnc_sala_butacas NOT NULL
);

ALTER TABLE sala ADD CONSTRAINT sala_pk PRIMARY KEY ( cine_id_cine );

ALTER TABLE sala ADD CONSTRAINT sala_id_sala_un UNIQUE ( id_sala );

ALTER TABLE actor
    ADD CONSTRAINT actor_lista_actores_fk FOREIGN KEY ( lista_actores_id_lista_actores )
        REFERENCES lista_actores ( id_lista_actores );

ALTER TABLE director
    ADD CONSTRAINT director_lista_directores_fk FOREIGN KEY ( lista_directores_id_listadir )
        REFERENCES lista_directores ( id_listadir );

ALTER TABLE funcion
    ADD CONSTRAINT funcion_cine_fk FOREIGN KEY ( id_cine )
        REFERENCES cine ( id_cine );

ALTER TABLE funcion
    ADD CONSTRAINT funcion_promociones_fk FOREIGN KEY ( promociones_id_promo )
        REFERENCES promociones ( id_promo );

ALTER TABLE funcion
    ADD CONSTRAINT funcion_sala_fk FOREIGN KEY ( sala_id_sala )
        REFERENCES sala ( id_sala );

ALTER TABLE opinion
    ADD CONSTRAINT opinion_peliculas_fk FOREIGN KEY ( peliculas_id_pelicula )
        REFERENCES peliculas ( id_pelicula );

ALTER TABLE peliculas
    ADD CONSTRAINT peliculas_funcion_fk FOREIGN KEY ( funcion_id_cine )
        REFERENCES funcion ( id_cine );

ALTER TABLE sala
    ADD CONSTRAINT sala_cine_fk FOREIGN KEY ( cine_id_cine )
        REFERENCES cine ( id_cine );
```
```
   .,::,.
  -\^__^/-
 codeElArroz
```

