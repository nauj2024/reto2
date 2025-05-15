# reto2
```mermaid
classDiagram
    class Usuario {
        - String nombre
        - String ID
        - String direccion
        - List~Prestamo~ historialPrestamos
        + consultarHistorial()
        + realizarPrestamo()
    }

    class Bibliotecario {
        - String nombre
        - String ID
        - String cargo
        + registrarPrestamo()
        + registrarDevolucion()
    }

    class Libro {
        - String titulo
        - String autor
        - String ISBN
        - String estado
        - int añoPublicacion
        + marcarComoPrestado()
        + marcarComoDisponible()
    }

    class Prestamo {
        - Date fechaInicio
        - Date fechaFin
        - Libro libro
        - Usuario usuario
        - Bibliotecario bibliotecario
        + esValido()
        + calcularMulta()
    }

    class Catalogo {
        - List~Libro~ listaLibros
        + buscarLibro()
        + agregarLibro()
        + eliminarLibro()
    }

    Usuario "1" --> "0..*" Prestamo : realiza
    Bibliotecario "1" --> "0..*" Prestamo : gestiona
    Prestamo "1" --> "1" Libro : incluye
    Prestamo "1" --> "1" Usuario : pertenece a
    Prestamo "1" --> "1" Bibliotecario : registrado por
    Catalogo "1" *-- "0..*" Libro : contiene
