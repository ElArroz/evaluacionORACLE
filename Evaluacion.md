---


---

<h2 id="ejercicio-1">Ejercicio 1</h2>
<p>Codigo del modelo DDL solicitado para el ejercicio 1, a ser implementado en D.B. Oracle:</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> empleado <span class="token punctuation">(</span>
    idEmpleado      <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    nombreEmpleado  VARCHAR2<span class="token punctuation">(</span><span class="token number">25</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    fechaIngreso    <span class="token keyword">DATE</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> empleado <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> empleado_pk <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> idEmpleado <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> servicio <span class="token punctuation">(</span>
    idServicio      <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    nombreServicio  VARCHAR2<span class="token punctuation">(</span><span class="token number">25</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    valorServicio   <span class="token keyword">INTEGER</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> servicio <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> servicio_pk <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> idServicio <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> vehiculo <span class="token punctuation">(</span>
    idVehiculo      <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    marcaVehiculo   VARCHAR2<span class="token punctuation">(</span><span class="token number">25</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    modeloVehiculo  VARCHAR2<span class="token punctuation">(</span><span class="token number">25</span><span class="token punctuation">)</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> vehiculo <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> vehiculo_pk <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> idVehiculo <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> prestacion_servicio <span class="token punctuation">(</span>
    idprestacionServicio  <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    idServicio            <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    idEmpleado            <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    idVehiculo            <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    fecha                 <span class="token keyword">DATE</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> prestacion_servicio
    <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> prestacion_servicio_fk <span class="token keyword">FOREIGN</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> idServicio<span class="token punctuation">,</span>
                                                        idprestacionServicio<span class="token punctuation">,</span>
                                                        idEmpleado<span class="token punctuation">,</span>
                                                        idVehiculo <span class="token punctuation">)</span><span class="token punctuation">;</span>


</code></pre>
<h3 id="continuamos-agregando-datos">Continuamos agregando datos:</h3>
<p>Ingresamos Empleados:</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">INSERT</span> <span class="token keyword">ALL</span>
	<span class="token keyword">INTO</span> empleado <span class="token punctuation">(</span>idEmpleado<span class="token punctuation">,</span>nombreEmpleado<span class="token punctuation">,</span>fechaIngreso<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token string">'Antonio'</span><span class="token punctuation">,</span>TO_DATE<span class="token punctuation">(</span><span class="token string">'01-01-2015'</span><span class="token punctuation">,</span> <span class="token string">'DD-MM-YYYY'</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> empleado <span class="token punctuation">(</span>idEmpleado<span class="token punctuation">,</span>nombreEmpleado<span class="token punctuation">,</span>fechaIngreso<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token string">'Cristian'</span><span class="token punctuation">,</span>TO_DATE<span class="token punctuation">(</span><span class="token string">'01-09-2015'</span><span class="token punctuation">,</span> <span class="token string">'DD-MM-YYYY'</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> empleado <span class="token punctuation">(</span>idEmpleado<span class="token punctuation">,</span>nombreEmpleado<span class="token punctuation">,</span>fechaIngreso<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token string">'German'</span><span class="token punctuation">,</span>TO_DATE<span class="token punctuation">(</span><span class="token string">'01-11-2016'</span><span class="token punctuation">,</span> <span class="token string">'DD-MM-YYYY'</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> empleado <span class="token punctuation">(</span>idEmpleado<span class="token punctuation">,</span>nombreEmpleado<span class="token punctuation">,</span>fechaIngreso<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">4</span><span class="token punctuation">,</span><span class="token string">'Luis'</span><span class="token punctuation">,</span>TO_DATE<span class="token punctuation">(</span><span class="token string">'01-12-2016'</span><span class="token punctuation">,</span> <span class="token string">'DD-MM-YYYY'</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> dual

</code></pre>
<p>Ingresamos Servicios</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">INSERT</span> <span class="token keyword">ALL</span>
	<span class="token keyword">INTO</span> servicio <span class="token punctuation">(</span>idServicio <span class="token punctuation">,</span>nombreServicio<span class="token punctuation">,</span>valorServicio<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token string">'Cambio Aceite'</span><span class="token punctuation">,</span><span class="token number">55000</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> servicio <span class="token punctuation">(</span>idServicio <span class="token punctuation">,</span>nombreServicio<span class="token punctuation">,</span>valorServicio<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token string">'Lubricación'</span><span class="token punctuation">,</span><span class="token number">25500</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> servicio <span class="token punctuation">(</span>idServicio <span class="token punctuation">,</span>nombreServicio<span class="token punctuation">,</span>valorServicio<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token string">'Afinamiento'</span><span class="token punctuation">,</span><span class="token number">450000</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> servicio <span class="token punctuation">(</span>idServicio <span class="token punctuation">,</span>nombreServicio<span class="token punctuation">,</span>valorServicio<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">4</span><span class="token punctuation">,</span><span class="token string">'Mantención 5K'</span><span class="token punctuation">,</span><span class="token number">100000</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> servicio <span class="token punctuation">(</span>idServicio <span class="token punctuation">,</span>nombreServicio<span class="token punctuation">,</span>valorServicio<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">5</span><span class="token punctuation">,</span><span class="token string">'Mantención 10K'</span><span class="token punctuation">,</span><span class="token number">185000</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> servicio <span class="token punctuation">(</span>idServicio <span class="token punctuation">,</span>nombreServicio<span class="token punctuation">,</span>valorServicio<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">6</span><span class="token punctuation">,</span><span class="token string">'Mantención 20K'</span><span class="token punctuation">,</span><span class="token number">185000</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> servicio <span class="token punctuation">(</span>idServicio <span class="token punctuation">,</span>nombreServicio<span class="token punctuation">,</span>valorServicio<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">7</span><span class="token punctuation">,</span><span class="token string">'Mantención 30K'</span><span class="token punctuation">,</span><span class="token number">255000</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> servicio <span class="token punctuation">(</span>idServicio <span class="token punctuation">,</span>nombreServicio<span class="token punctuation">,</span>valorServicio<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">8</span><span class="token punctuation">,</span><span class="token string">'Mantención 40K'</span><span class="token punctuation">,</span><span class="token number">215000</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> servicio <span class="token punctuation">(</span>idServicio <span class="token punctuation">,</span>nombreServicio<span class="token punctuation">,</span>valorServicio<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">9</span><span class="token punctuation">,</span><span class="token string">'Mantención +50K'</span><span class="token punctuation">,</span><span class="token number">255000</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> servicio <span class="token punctuation">(</span>idServicio <span class="token punctuation">,</span>nombreServicio<span class="token punctuation">,</span>valorServicio<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">,</span><span class="token string">'Garantia'</span><span class="token punctuation">,</span><span class="token number">0</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> servicio <span class="token punctuation">(</span>idServicio <span class="token punctuation">,</span>nombreServicio<span class="token punctuation">,</span>valorServicio<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">,</span><span class="token string">'Vulca_1'</span><span class="token punctuation">,</span><span class="token number">10000</span><span class="token punctuation">)</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> dual
</code></pre>
<p>Ingresamos Vehiculos</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">INSERT</span> <span class="token keyword">ALL</span>
	<span class="token keyword">INTO</span> vehiculo <span class="token punctuation">(</span>idvehiculo <span class="token punctuation">,</span>marcaVehiculo<span class="token punctuation">,</span> modeloVehiculo<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token string">'Chevrolet'</span><span class="token punctuation">,</span><span class="token string">'Sail'</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> vehiculo <span class="token punctuation">(</span>idvehiculo <span class="token punctuation">,</span>marcaVehiculo<span class="token punctuation">,</span> modeloVehiculo<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token string">'Chevrolet'</span><span class="token punctuation">,</span><span class="token string">'Spark'</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> vehiculo <span class="token punctuation">(</span>idvehiculo <span class="token punctuation">,</span>marcaVehiculo<span class="token punctuation">,</span> modeloVehiculo<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token string">'Nissan'</span><span class="token punctuation">,</span><span class="token string">'Versa'</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> vehiculo <span class="token punctuation">(</span>idvehiculo <span class="token punctuation">,</span>marcaVehiculo<span class="token punctuation">,</span> modeloVehiculo<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">4</span><span class="token punctuation">,</span><span class="token string">'Nissan'</span><span class="token punctuation">,</span><span class="token string">'Kicks'</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> vehiculo <span class="token punctuation">(</span>idvehiculo <span class="token punctuation">,</span>marcaVehiculo<span class="token punctuation">,</span> modeloVehiculo<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">5</span><span class="token punctuation">,</span><span class="token string">'AUDI'</span><span class="token punctuation">,</span><span class="token string">'A3'</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> vehiculo <span class="token punctuation">(</span>idvehiculo <span class="token punctuation">,</span>marcaVehiculo<span class="token punctuation">,</span> modeloVehiculo<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">6</span><span class="token punctuation">,</span><span class="token string">'BMV'</span><span class="token punctuation">,</span><span class="token string">'X5'</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> vehiculo <span class="token punctuation">(</span>idvehiculo <span class="token punctuation">,</span>marcaVehiculo<span class="token punctuation">,</span> modeloVehiculo<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">7</span><span class="token punctuation">,</span><span class="token string">'Mitsubishi'</span><span class="token punctuation">,</span><span class="token string">'Outlander'</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> vehiculo <span class="token punctuation">(</span>idvehiculo <span class="token punctuation">,</span>marcaVehiculo<span class="token punctuation">,</span> modeloVehiculo<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">8</span><span class="token punctuation">,</span><span class="token string">'Mitsubishi'</span><span class="token punctuation">,</span><span class="token string">'Katana'</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> vehiculo <span class="token punctuation">(</span>idvehiculo <span class="token punctuation">,</span>marcaVehiculo<span class="token punctuation">,</span> modeloVehiculo<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">9</span><span class="token punctuation">,</span><span class="token string">'Mahindra'</span><span class="token punctuation">,</span><span class="token string">'Scorpio'</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> vehiculo <span class="token punctuation">(</span>idvehiculo <span class="token punctuation">,</span>marcaVehiculo<span class="token punctuation">,</span> modeloVehiculo<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">,</span><span class="token string">'Mahindra'</span><span class="token punctuation">,</span><span class="token string">'Pick up'</span><span class="token punctuation">)</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> dual
</code></pre>
<p>Ingresamos Prestacion de servicios</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">INSERT</span> <span class="token keyword">ALL</span>
	<span class="token keyword">INTO</span> PRESTACION_SERVICIO <span class="token punctuation">(</span>IDPRESTACIONSERVICIO<span class="token punctuation">,</span>IDSERVICIO<span class="token punctuation">,</span>IDEMPLEADO<span class="token punctuation">,</span>IDVEHICULO<span class="token punctuation">,</span>FECHA<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">1</span><span class="token punctuation">,</span>TO_DATE<span class="token punctuation">(</span><span class="token string">'20-09-2018'</span><span class="token punctuation">,</span> <span class="token string">'DD-MM-YYYY'</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> PRESTACION_SERVICIO <span class="token punctuation">(</span>IDPRESTACIONSERVICIO<span class="token punctuation">,</span>IDSERVICIO<span class="token punctuation">,</span>IDEMPLEADO<span class="token punctuation">,</span>IDVEHICULO<span class="token punctuation">,</span>FECHA<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">1</span><span class="token punctuation">,</span>TO_DATE<span class="token punctuation">(</span><span class="token string">'22-09-2018'</span><span class="token punctuation">,</span> <span class="token string">'DD-MM-YYYY'</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> PRESTACION_SERVICIO <span class="token punctuation">(</span>IDPRESTACIONSERVICIO<span class="token punctuation">,</span>IDSERVICIO<span class="token punctuation">,</span>IDEMPLEADO<span class="token punctuation">,</span>IDVEHICULO<span class="token punctuation">,</span>FECHA<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">4</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">,</span>TO_DATE<span class="token punctuation">(</span><span class="token string">'28-09-2018'</span><span class="token punctuation">,</span> <span class="token string">'DD-MM-YYYY'</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> PRESTACION_SERVICIO <span class="token punctuation">(</span>IDPRESTACIONSERVICIO<span class="token punctuation">,</span>IDSERVICIO<span class="token punctuation">,</span>IDEMPLEADO<span class="token punctuation">,</span>IDVEHICULO<span class="token punctuation">,</span>FECHA<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">4</span><span class="token punctuation">,</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">,</span>TO_DATE<span class="token punctuation">(</span><span class="token string">'05-10-2018'</span><span class="token punctuation">,</span> <span class="token string">'DD-MM-YYYY'</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> PRESTACION_SERVICIO <span class="token punctuation">(</span>IDPRESTACIONSERVICIO<span class="token punctuation">,</span>IDSERVICIO<span class="token punctuation">,</span>IDEMPLEADO<span class="token punctuation">,</span>IDVEHICULO<span class="token punctuation">,</span>FECHA<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">5</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token number">9</span><span class="token punctuation">,</span>TO_DATE<span class="token punctuation">(</span><span class="token string">'07-10-2018'</span><span class="token punctuation">,</span> <span class="token string">'DD-MM-YYYY'</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> PRESTACION_SERVICIO <span class="token punctuation">(</span>IDPRESTACIONSERVICIO<span class="token punctuation">,</span>IDSERVICIO<span class="token punctuation">,</span>IDEMPLEADO<span class="token punctuation">,</span>IDVEHICULO<span class="token punctuation">,</span>FECHA<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">6</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token number">4</span><span class="token punctuation">,</span><span class="token number">7</span><span class="token punctuation">,</span>TO_DATE<span class="token punctuation">(</span><span class="token string">'19-10-2018'</span><span class="token punctuation">,</span> <span class="token string">'DD-MM-YYYY'</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> PRESTACION_SERVICIO <span class="token punctuation">(</span>IDPRESTACIONSERVICIO<span class="token punctuation">,</span>IDSERVICIO<span class="token punctuation">,</span>IDEMPLEADO<span class="token punctuation">,</span>IDVEHICULO<span class="token punctuation">,</span>FECHA<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">7</span><span class="token punctuation">,</span><span class="token number">4</span><span class="token punctuation">,</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">,</span>TO_DATE<span class="token punctuation">(</span><span class="token string">'25-10-2018'</span><span class="token punctuation">,</span> <span class="token string">'DD-MM-YYYY'</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> PRESTACION_SERVICIO <span class="token punctuation">(</span>IDPRESTACIONSERVICIO<span class="token punctuation">,</span>IDSERVICIO<span class="token punctuation">,</span>IDEMPLEADO<span class="token punctuation">,</span>IDVEHICULO<span class="token punctuation">,</span>FECHA<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">8</span><span class="token punctuation">,</span><span class="token number">11</span><span class="token punctuation">,</span><span class="token number">4</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">,</span>TO_DATE<span class="token punctuation">(</span><span class="token string">'01-11-2018'</span><span class="token punctuation">,</span> <span class="token string">'DD-MM-YYYY'</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> PRESTACION_SERVICIO <span class="token punctuation">(</span>IDPRESTACIONSERVICIO<span class="token punctuation">,</span>IDSERVICIO<span class="token punctuation">,</span>IDEMPLEADO<span class="token punctuation">,</span>IDVEHICULO<span class="token punctuation">,</span>FECHA<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">9</span><span class="token punctuation">,</span><span class="token number">11</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">,</span>TO_DATE<span class="token punctuation">(</span><span class="token string">'28-11-2018'</span><span class="token punctuation">,</span> <span class="token string">'DD-MM-YYYY'</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
	<span class="token keyword">INTO</span> PRESTACION_SERVICIO <span class="token punctuation">(</span>IDPRESTACIONSERVICIO<span class="token punctuation">,</span>IDSERVICIO<span class="token punctuation">,</span>IDEMPLEADO<span class="token punctuation">,</span>IDVEHICULO<span class="token punctuation">,</span>FECHA<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">,</span><span class="token number">9</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token number">7</span><span class="token punctuation">,</span>TO_DATE<span class="token punctuation">(</span><span class="token string">'29-11-2018'</span><span class="token punctuation">,</span> <span class="token string">'DD-MM-YYYY'</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> dual
</code></pre>
<h3 id="aca-realizamos-las-consultas-solicitadas">Aca realizamos las consultas solicitadas:</h3>
<p><strong>1.-</strong> <em>Mostrar la cantidad de prestaciones de servicios ejecutados entre el 01 de octubre y el 26 de<br>
noviembre del 2018:</em></p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">SELECT</span> <span class="token function">COUNT</span><span class="token punctuation">(</span>idprestacionservicio<span class="token punctuation">)</span>
<span class="token keyword">FROM</span> prestacion_servicio
<span class="token keyword">WHERE</span> fecha <span class="token operator">BETWEEN</span> <span class="token string">'01/10/2018'</span> <span class="token operator">AND</span> <span class="token string">'26/11/2018'</span><span class="token punctuation">;</span>
</code></pre>
<p><strong>2.-</strong> <em>Mostrar la cantidad total de prestaciones realizadas agrupadas por idVehiculo:</em></p>
<blockquote>
<p><em>Le colocamos un para de alias con “AS” para facilitar su lectura:</em></p>
</blockquote>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">SELECT</span> idvehiculo <span class="token keyword">AS</span> Vehiculo<span class="token punctuation">,</span><span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token operator">*</span><span class="token punctuation">)</span> <span class="token keyword">as</span> Prestaciones
<span class="token keyword">FROM</span> prestacion_servicio
<span class="token keyword">GROUP</span> <span class="token keyword">BY</span> idvehiculo
</code></pre>
<p><strong>3.-</strong> <em>Mostrar los vehículos con la menor cantidad de prestaciones de servicios realizados:</em></p>
<blockquote>
<p><em>Se ordena el listado de prestaciones menores o iguales a 2, por tipo de vehiculos:</em></p>
</blockquote>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">SELECT</span> idvehiculo<span class="token punctuation">,</span><span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token operator">*</span><span class="token punctuation">)</span> <span class="token keyword">as</span> ctdServicios
<span class="token keyword">FROM</span> prestacion_servicio
<span class="token keyword">GROUP</span> <span class="token keyword">BY</span> idvehiculo
<span class="token keyword">HAVING</span> <span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token operator">*</span><span class="token punctuation">)</span><span class="token operator">&lt;=</span><span class="token number">2</span>
<span class="token keyword">ORDER</span> <span class="token keyword">BY</span> ctdServicios <span class="token keyword">ASC</span><span class="token punctuation">;</span>

</code></pre>
<h2 id="ejercicio-2">Ejercicio 2</h2>
<p>Código del Modelo DDL para el ejercicio 2, a ser implementado en D.B. Oracle:</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> empleado <span class="token punctuation">(</span>
    idEmpleado		<span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    nombre  		VARCHAR2<span class="token punctuation">(</span><span class="token number">25</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    apellido  		VARCHAR2<span class="token punctuation">(</span><span class="token number">25</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    direccion		VARCHAR2<span class="token punctuation">(</span><span class="token number">25</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    telefono		VARCHAR2<span class="token punctuation">(</span><span class="token number">25</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    idDepartamento	<span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> empleado <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> empleado_pk <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> idEmpleado<span class="token punctuation">,</span>
							   idDepartamento <span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<h2 id="ejercicio-3">Ejercicio 3</h2>
<p>Código del Modelo DDL del ejercicio 3, para ser implementado en D.B. Oracle:</p>
<blockquote>
<p><em>Tal como lo genera  la herramienta Oracle SQLdeveloper, se adjuntan imagenes del diseño logico y relacional</em></p>
</blockquote>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> actor <span class="token punctuation">(</span>
    id_actor                        <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    nombreactor                     VARCHAR2<span class="token punctuation">(</span><span class="token number">30</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    nacionalidad                    VARCHAR2<span class="token punctuation">(</span><span class="token number">30</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    apariciones                     <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    lista_actores_id_lista_actores  <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> actor <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> actor_pk <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> id_actor <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> cine <span class="token punctuation">(</span>
    id_cine    <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    nombre     VARCHAR2<span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    direccion  VARCHAR2<span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    fono       VARCHAR2<span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">)</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> cine <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> cine_pk <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> id_cine <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> director <span class="token punctuation">(</span>
    id_director                   <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    nombreactor                   VARCHAR2<span class="token punctuation">(</span><span class="token number">30</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    nacionalidad                  VARCHAR2<span class="token punctuation">(</span><span class="token number">30</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    apariciones                   <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    lista_directores_id_listadir  <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> director <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> director_pk <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> id_director <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> funcion <span class="token punctuation">(</span>
    id_cine               <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    id_funcion            <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    nombre                VARCHAR2<span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    dias                  VARCHAR2<span class="token punctuation">(</span><span class="token number">15</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    horainicio            <span class="token keyword">INTEGER</span><span class="token punctuation">,</span>
    sala_id_sala          <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    promociones_id_promo  <span class="token keyword">INTEGER</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> funcion <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> funcion_pk <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> id_cine <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> funcion <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> funcion_id_funcion_un <span class="token keyword">UNIQUE</span> <span class="token punctuation">(</span> id_funcion <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> lista_actores <span class="token punctuation">(</span>
    id_lista_actores       <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    listaactores           VARCHAR2<span class="token punctuation">(</span><span class="token number">30</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    peliculas_id_pelicula  <span class="token keyword">INTEGER</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">UNIQUE</span> <span class="token keyword">INDEX</span> lista_actores__idx <span class="token keyword">ON</span>
    lista_actores <span class="token punctuation">(</span>
        peliculas_id_pelicula
    <span class="token keyword">ASC</span> <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> lista_actores <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> lista_actores_pk <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> id_lista_actores <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> lista_directores <span class="token punctuation">(</span>
    id_listadir            <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    listadirec             VARCHAR2<span class="token punctuation">(</span><span class="token number">30</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    peliculas_id_pelicula  <span class="token keyword">INTEGER</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">UNIQUE</span> <span class="token keyword">INDEX</span> lista_directores__idx <span class="token keyword">ON</span>
    lista_directores <span class="token punctuation">(</span>
        peliculas_id_pelicula
    <span class="token keyword">ASC</span> <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> lista_directores <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> lista_directores_pk <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> id_listadir <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> opinion <span class="token punctuation">(</span>
    id_opinion             <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    nombre                 VARCHAR2<span class="token punctuation">(</span><span class="token number">30</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    <span class="token number">edad</span>                   <span class="token keyword">INTEGER</span><span class="token punctuation">,</span>
    fecha                  <span class="token keyword">DATE</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    calificacion           VARCHAR2<span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    comentario             VARCHAR2<span class="token punctuation">(</span><span class="token number">100</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    peliculas_id_pelicula  <span class="token keyword">INTEGER</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> opinion <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> opinion_pk <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> id_opinion <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> peliculas <span class="token punctuation">(</span>
    id_pelicula                     <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    nombredistribucion              VARCHAR2<span class="token punctuation">(</span><span class="token number">30</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    titulooriginal                  VARCHAR2<span class="token punctuation">(</span><span class="token number">30</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    genero                          VARCHAR2<span class="token punctuation">(</span><span class="token number">30</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    idiomaoriginal                  VARCHAR2<span class="token punctuation">(</span><span class="token number">30</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    subtituloesp                    CHAR<span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    anioproduccion                  <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    website                         VARCHAR2<span class="token punctuation">(</span><span class="token number">30</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    calificacion                    VARCHAR2<span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    fechaestreno                    <span class="token keyword">DATE</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    id_lista_directores             <span class="token keyword">INTEGER</span><span class="token punctuation">,</span>
    lista_directores_id_listadir    <span class="token keyword">INTEGER</span><span class="token punctuation">,</span>
    lista_actores_id_lista_actores  <span class="token keyword">INTEGER</span><span class="token punctuation">,</span>
    funcion_id_cine                 <span class="token keyword">INTEGER</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">UNIQUE</span> <span class="token keyword">INDEX</span> peliculas__idx <span class="token keyword">ON</span>
    peliculas <span class="token punctuation">(</span>
        lista_actores_id_lista_actores
    <span class="token keyword">ASC</span> <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">UNIQUE</span> <span class="token keyword">INDEX</span> peliculas__idxv1v1 <span class="token keyword">ON</span>
    peliculas <span class="token punctuation">(</span>
        lista_directores_id_listadir
    <span class="token keyword">ASC</span> <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> peliculas <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> peliculas_pk <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> id_pelicula <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> promociones <span class="token punctuation">(</span>
    id_promo   <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    nombre     VARCHAR2<span class="token punctuation">(</span><span class="token number">30</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    descuento  <span class="token keyword">INTEGER</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> promociones <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> promociones_pk <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> id_promo <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> sala <span class="token punctuation">(</span>
    cine_id_cine  <span class="token keyword">INTEGER</span>
        <span class="token keyword">CONSTRAINT</span> nnc_sala_id_cine <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    id_sala       <span class="token keyword">INTEGER</span>
        <span class="token keyword">CONSTRAINT</span> nnc_sala_id_sala <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    nombre        VARCHAR2<span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    butacas       <span class="token keyword">INTEGER</span>
        <span class="token keyword">CONSTRAINT</span> nnc_sala_butacas <span class="token operator">NOT</span> <span class="token boolean">NULL</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> sala <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> sala_pk <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> cine_id_cine <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> sala <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> sala_id_sala_un <span class="token keyword">UNIQUE</span> <span class="token punctuation">(</span> id_sala <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> actor
    <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> actor_lista_actores_fk <span class="token keyword">FOREIGN</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> lista_actores_id_lista_actores <span class="token punctuation">)</span>
        <span class="token keyword">REFERENCES</span> lista_actores <span class="token punctuation">(</span> id_lista_actores <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> director
    <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> director_lista_directores_fk <span class="token keyword">FOREIGN</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> lista_directores_id_listadir <span class="token punctuation">)</span>
        <span class="token keyword">REFERENCES</span> lista_directores <span class="token punctuation">(</span> id_listadir <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> funcion
    <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> funcion_cine_fk <span class="token keyword">FOREIGN</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> id_cine <span class="token punctuation">)</span>
        <span class="token keyword">REFERENCES</span> cine <span class="token punctuation">(</span> id_cine <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> funcion
    <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> funcion_promociones_fk <span class="token keyword">FOREIGN</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> promociones_id_promo <span class="token punctuation">)</span>
        <span class="token keyword">REFERENCES</span> promociones <span class="token punctuation">(</span> id_promo <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> funcion
    <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> funcion_sala_fk <span class="token keyword">FOREIGN</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> sala_id_sala <span class="token punctuation">)</span>
        <span class="token keyword">REFERENCES</span> sala <span class="token punctuation">(</span> id_sala <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> opinion
    <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> opinion_peliculas_fk <span class="token keyword">FOREIGN</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> peliculas_id_pelicula <span class="token punctuation">)</span>
        <span class="token keyword">REFERENCES</span> peliculas <span class="token punctuation">(</span> id_pelicula <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> peliculas
    <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> peliculas_funcion_fk <span class="token keyword">FOREIGN</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> funcion_id_cine <span class="token punctuation">)</span>
        <span class="token keyword">REFERENCES</span> funcion <span class="token punctuation">(</span> id_cine <span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> sala
    <span class="token keyword">ADD</span> <span class="token keyword">CONSTRAINT</span> sala_cine_fk <span class="token keyword">FOREIGN</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span> cine_id_cine <span class="token punctuation">)</span>
        <span class="token keyword">REFERENCES</span> cine <span class="token punctuation">(</span> id_cine <span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<pre><code>   .,::,.
  -\^__^/-
 codeElArroz
</code></pre>

