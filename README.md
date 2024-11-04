# Proyecto Final
### Empresa Web

------------


### Integrantes del grupo:
- Abner Edin Esquit Gutiérrez 7691-20-12964
- Ayker Desidery Hernández Montes 7691-22-11360
- Daniel Estuardo Salazar Escobar 7691-22153
- Dylan Fernando Alberto Escobar Aceituno 7691-22-13576

------------


## Lineamientos a seguir:
1)    Grupos máximo de 5 personas 
2)    Aplicar los conceptos de la Programación Orientada a Objetos (POO).
3)    Toda la aplicación deberá de ser en Java Web.
4)    Utilizar el patrón de arquitectura de software MVC (Modelo–vista–controlador)
5)    Deberá de funcionar en red, es decir deberán de publicar la aplicación en un servidor (local), y las maquinas cliente deberán de acceder a ella por medio de un navegador web.
6)    La aplicación deberá de ser amigable e interactiva para el usuario (usar bootstrap como recomendación no como obligación).
7)    Crear un repositorio en GitHub para colaborar como grupo.
8)    Distribuir de forma equitativa la elaboración del programa.
9)    Al finalizar todos los integrantes del grupo deben de tener en sus equipos el código fuente  actualizado  y evidenciar  en el Insights la colaboración de cada integrante del grupo
10)    Deberán de realizar una presentación final del proyecto.

11) Crear el proyecto según indica el documento Adjunto


------------

## Base de datos:
```sql
create database proyecto_db;
use proyecto_db;

create table clientes(
id_cliente int primary key not null auto_increment,
nombres varchar(60),
apellidos varchar(60),
nit varchar(12),
genero bit,
telefono varchar(25),
correo_electronico varchar(45),
fecha_ingreso datetime
);

create table puestos(
id_puesto smallint not null primary key auto_increment,
puesto varchar(50)
);

create table proveedores(
id_proveedor int not null primary key auto_increment,
proveedor varchar(60),
nit varchar(12),
direccion varchar(80),
telefono varchar(25)
);

create table marcas(
id_marca smallint not null auto_increment primary key,
marca varchar(50)
);

create table empleados(
id_empleado int not null primary key auto_increment,
nombres varchar(60),
apellidos varchar(60),
direccion varchar(80),
telefono varchar(25),
dpi varchar(15),
genero bit,
fecha_nacimiento date,
id_puesto smallint not null,
fecha_inicio_labores date,
fecha_ingreso datetime,
constraint fk_empleados_id_puesto foreign key (id_puesto) references puestos(id_puesto)
);

create table productos(
id_producto int not null auto_increment primary key,
producto varchar(50),
id_marca smallint not null,
descripcion varchar(100),
imagen varchar(30),
precio_costo decimal(8,2),
precio_venta decimal(8,2),
existencia int,
fecha_ingreso datetime,
constraint fk_productos_id_marca foreign key (id_marca) references marcas(id_marca)
);

create table compras(
id_compra int not null auto_increment primary key,
no_orden_compra int,
