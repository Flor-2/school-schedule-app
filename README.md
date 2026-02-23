PROYECTO: SISTEMA DE GESTIÓN DE HORARIO SEMANAL
1. Descripción del Proyecto
El presente proyecto consiste en el desarrollo de una aplicación web para la gestión del horario semanal de un centro educativo. El sistema permite registrar asignaturas, profesores, aulas y asignar bloques de tiempo específicos para cada grado académico.
La aplicación facilita la organización eficiente del horario escolar, evitando conflictos en la asignación de docentes y aulas. Además, permite visualizar las clases registradas y administrar los datos de forma dinámica.
2. Arquitectura del Proyecto
El sistema fue desarrollado siguiendo una arquitectura en capas, lo que permite una mejor organización del código y separación de responsabilidades.
Domain / Entities
En esta capa se definió el modelo principal:
ScheduleItem, que contiene:
•	Id
•	SubjectName (Asignatura)
•	TeacherName (Profesor)
•	DayOfWeek (Día de la semana)
•	StartTime (Hora de inicio)
•	EndTime (Hora de fin)
•	RoomNumber (Aula)
•	GradeLevel (Grado)
Esta entidad representa cada bloque del horario académico.
Persistence / Infrastructure
Se utilizó Entity Framework Core junto con SQL Server para la persistencia de datos.
Se creó un ApplicationDbContext que contiene:
public DbSet<ScheduleItem> ScheduleItems { get; set; }
Se aplicaron migraciones para generar la base de datos automáticamente.


API / Application
Se implementó la lógica de negocio directamente en la capa web mediante el uso del DbContext.
El sistema permite:
•	Agregar clases
•	Eliminar clases
•	Consultar clases registradas
Además, se implementó una validación especial para evitar conflictos de horario.
Frontend
Se desarrolló la interfaz utilizando Blazor, permitiendo:
•	Formulario dinámico con listas desplegables (InputSelect)
•	Visualización en tabla
•	Botones de eliminación
•	Mensajes de error en caso de conflicto
La interfaz evita que el usuario escriba manualmente, reduciendo errores.
3. Funcionalidades Implementadas
El sistema permite:
✔ Registrar nuevas clases
✔ Visualizar el horario completo
✔ Eliminar clases
✔ Persistencia en base de datos
✔ Validación de conflictos
4. Validación de Conflictos (Desafío Extra)
Se implementó una validación que impide:
•	Asignar al mismo profesor en dos aulas diferentes a la misma hora.
•	Asignar dos clases distintas en la misma aula al mismo tiempo.
Antes de guardar un registro, el sistema verifica en la base de datos si existe un conflicto usando una consulta con .Any().
Si se detecta conflicto, se muestra un mensaje de error y la clase no se registra.
Esto garantiza la integridad del horario académico.
5. Tecnologías Utilizadas
•	.NET 8
•	Blazor
•	Entity Framework Core
•	SQL Server
•	C#
•	HTML / Bootstrap
6. Base de Datos
La tabla generada automáticamente contiene los siguientes campos:
•	Id (Primary Key)
•	SubjectName
•	TeacherName
•	DayOfWeek
•	StartTime
•	EndTime
•	RoomNumber
•	GradeLevel
La base de datos fue creada mediante migraciones de Entity Framework.
7. Conclusión
El desarrollo de este sistema permitió aplicar conceptos fundamentales de arquitectura en capas, persistencia de datos con Entity Framework y validación de reglas de negocio.
La implementación del control de conflictos mejora la confiabilidad del sistema y garantiza una correcta gestión del horario escolar.
El proyecto demuestra la correcta integración entre frontend, backend y base de datos en una aplicación web moderna.

