
## Ejercicio 1
Código del Modelo DDL del ejercicio parte 1, para ser implementado en D.B. Oracle:
```sql
CREATE TABLE empleado (
    idEmpleado      INTEGER NOT NULL,
    nombreEmpleado  VARCHAR2(25) NOT NULL,
    fechaIngreso    DATE NOT NULL
);
ALTER TABLE empleado ADD CONSTRAINT empleado_pk PRIMARY KEY ( idEmpleado );


CREATE TABLE servicio (
    idServicio      INTEGER NOT NULL,
    nombreServicio  VARCHAR2(25) NOT NULL,
    valorServicio   INTEGER
);
ALTER TABLE servicio ADD CONSTRAINT servicio_pk PRIMARY KEY ( idServicio );


CREATE TABLE vehiculo (
    idVehiculo      INTEGER NOT NULL,
    marcaVehiculo   VARCHAR2(25) NOT NULL,
    modeloVehiculo  VARCHAR2(25)
);
ALTER TABLE vehiculo ADD CONSTRAINT vehiculo_pk PRIMARY KEY ( idVehiculo );


CREATE TABLE prestacion_servicio (
    idprestacionServicio  INTEGER NOT NULL,
    idServicio            INTEGER NOT NULL,
    idEmpleado            INTEGER NOT NULL,
    idVehiculo            INTEGER NOT NULL,
    fecha                 DATE NOT NULL
);


ALTER TABLE prestacion_servicio
    ADD CONSTRAINT prestacion_servicio_pk PRIMARY KEY ( idServicio,
                                                        idprestacionServicio,
                                                        idEmpleado,
                                                        idVehiculo );

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
	INTO PRESTACION_SERVICIO (IDPRESTACIONSERVICIO,IDSERVICIO,IDEMPLEADO,IDVEHICULO,FECHA) VALUES (1,1,2,1,TO_DATE('20-09-2018', 'DD-MM-YYYY'))
	INTO PRESTACION_SERVICIO (IDPRESTACIONSERVICIO,IDSERVICIO,IDEMPLEADO,IDVEHICULO,FECHA) VALUES (2,1,2,1,TO_DATE('22-09-2018', 'DD-MM-YYYY'))
	INTO PRESTACION_SERVICIO (IDPRESTACIONSERVICIO,IDSERVICIO,IDEMPLEADO,IDVEHICULO,FECHA) VALUES (3,1,4,5,TO_DATE('28-09-2018', 'DD-MM-YYYY'))
	INTO PRESTACION_SERVICIO (IDPRESTACIONSERVICIO,IDSERVICIO,IDEMPLEADO,IDVEHICULO,FECHA) VALUES (4,1,3,5,TO_DATE('05-10-2018', 'DD-MM-YYYY'))
	INTO PRESTACION_SERVICIO (IDPRESTACIONSERVICIO,IDSERVICIO,IDEMPLEADO,IDVEHICULO,FECHA) VALUES (5,2,3,9,TO_DATE('07-10-2018', 'DD-MM-YYYY'))
	INTO PRESTACION_SERVICIO (IDPRESTACIONSERVICIO,IDSERVICIO,IDEMPLEADO,IDVEHICULO,FECHA) VALUES (6,3,4,7,TO_DATE('19-10-2018', 'DD-MM-YYYY'))
	INTO PRESTACION_SERVICIO (IDPRESTACIONSERVICIO,IDSERVICIO,IDEMPLEADO,IDVEHICULO,FECHA) VALUES (7,4,1,5,TO_DATE('25-10-2018', 'DD-MM-YYYY'))
	INTO PRESTACION_SERVICIO (IDPRESTACIONSERVICIO,IDSERVICIO,IDEMPLEADO,IDVEHICULO,FECHA) VALUES (8,11,4,5,TO_DATE('01-11-2018', 'DD-MM-YYYY'))
	INTO PRESTACION_SERVICIO (IDPRESTACIONSERVICIO,IDSERVICIO,IDEMPLEADO,IDVEHICULO,FECHA) VALUES (9,11,2,2,TO_DATE('28-11-2018', 'DD-MM-YYYY'))
	INTO PRESTACION_SERVICIO (IDPRESTACIONSERVICIO,IDSERVICIO,IDEMPLEADO,IDVEHICULO,FECHA) VALUES (10,9,3,7,TO_DATE('29-11-2018', 'DD-MM-YYYY'))
SELECT * FROM dual
```
### Aca realizamos las consultas:

**1.-** *Mostrar la cantidad de prestaciones de servicios ejecutados entre el 01 de octubre y el 26 de
noviembre del 2018:*
```sql
SELECT COUNT(idprestacionservicio)
FROM prestacion_servicio
WHERE fecha BETWEEN '01/10/2018' AND '26/11/2018';
```

**2.-** *Mostrar la cantidad total de prestaciones realizadas agrupadas por idVehiculo:*

>*Le colocamos un para de alias con "AS" para facilitar su lectura:*
```sql
SELECT idvehiculo AS Vehiculo,COUNT(*) as Prestaciones
FROM prestacion_servicio
GROUP BY idvehiculo
```
**3.-** *Mostrar los vehículos con la menor cantidad de prestaciones de servicios realizados:*
>*Se ordena el listado de prestaciones de menos a mayor por tipo de vehiculos:*
```sql
SELECT idvehiculo,COUNT(*) as ctdServicios
FROM prestacion_servicio
GROUP BY idvehiculo
ORDER BY ctdServicios ASC;
```

## Ejercicio 2
Código del Modelo DDL del ejercicio parte 2, para ser implementado en D.B. Oracle:
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
Código del Modelo DDL del ejercicio parte 2, para ser implementado en D.B. Oracle:
```sql
