# reto_02

Este diagrama de clases, hecho con **Mermaid**, representa un sistema de gestión de proyectos y tareas. En él, se muestra cómo están relacionadas las clases de usuarios, proyectos, tareas, recursos y otros elementos importantes del sistema.

- **Usuario**: puede ser un `Administrador` o un `Colaborador`, y participa en proyectos y tareas.
- **Proyecto**: agrupa tareas, tiene un estado y un equipo de trabajo.
- **Tarea**: se asocia con recursos y notificaciones, y tiene un estado y una prioridad.
- **Recurso**: incluye documentos y herramientas que se utilizan en las tareas.
- **Administrador**: gestiona proyectos, usuarios y roles.
- **Colaborador**: se encarga de actualizar las tareas y trabajar en el proyecto.
- **Notificación**: informa a los usuarios sobre los cambios en las tareas.

```mermaid
  classDiagram
    Usuario "1" --> "1..*" Proyecto : participa
    Proyecto "1" --> "1..*" Tarea : contiene
    Tarea "1" --> "0..*" Recurso : utiliza
    Tarea "1" --> "0..*" Notificacion : genera
    Usuario <|-- Administrador
    Usuario <|-- Colaborador
    Recurso <|-- Documento
    Recurso <|-- Herramienta

    class Usuario {
        +nombre: String
        +email: String
        +rol: String
        +verNotificaciones()
    }
 
    class Proyecto {
        +nombre: String
        +descripcion: String
        +estado: String
        +equipo: List<Usuario>
        +agregarTarea(tarea: Tarea)
        +finalizarProyecto()
    }
    
    class Tarea {
        +titulo: String
        +descripcion: String
        +prioridad: String
        +estado: String
        +asignadoA: Usuario
        +completarTarea()
        +agregarRecurso(recurso: Recurso)
    }
    
    class Recurso {
        +nombre: String
        +descripcion: String
        +acceder()
    }
    
    class Documento {
        +tipoArchivo: String
        +subirVersion()
        +descargar()
    }
   
    class Herramienta {
        +tipo: String
        +configurar()
    }
    
    class Notificacion {
        +mensaje: String
        +destinatario: Usuario
        +fechaEnvio: Date
        +enviar()
    }
   
    class Administrador {
        +crearProyecto()
        +eliminarUsuario(usuario: Usuario)
        +actualizarTarea(tarea: Tarea)
        +añadirUsuario(usuario: Usuario)
        +asignarRol(usuario: Usuario, rol: String) 
    }
    
    class Colaborador {
        +actualizarTarea(tarea: Tarea)
    }
    
