# TodoAppV01 - Documentación

Repositorio: [https://github.com/MayerlyPanteves/TodoAppV01.git](https://github.com/MayerlyPanteves/TodoAppV01.git)

---

## Introducción

TodoAppV01 es una aplicación Android para la gestión de tareas, desarrollada en Android Studio. Esta documentación proporciona una visión completa del proyecto, incluyendo requerimientos, arquitectura, diseño y proceso de desarrollo.

---

## Requerimientos del sistema

### Requerimientos funcionales
- Crear, editar y eliminar tareas.
- Marcar tareas como completadas.
- Organizar tareas por categorías.
- Establecer fechas de vencimiento para tareas.
- Recordatorios para tareas próximas.

### Requerimientos no funcionales
- Interfaz intuitiva y responsive.
- Almacenamiento local de datos con Room.
- Compatibilidad con Android 8.0+.
- Rendimiento fluido y eficiente.

---

## Android studio y SDK

El proyecto fue desarrollado utilizando Android Studio y el SDK de Android con las siguientes configuraciones:
- **Android Studio:** Versión 2022.3.1 o superior.
- **SDK:** Android API 33 (Android 13).
- **Gradle:** Versión 8.0.
- **Kotlin:** Versión 1.8.20.

---

## Diagramas del sistema

### Diagrama de clases

<img width="512" height="512" alt="image" src="https://github.com/user-attachments/assets/c3506ed0-69b5-43e9-bfdf-91786ab1330e" />

### Diagrama de paquetes

<img width="512" height="512" alt="image" src="https://github.com/user-attachments/assets/f010478a-a922-4fda-bac2-27f21e624f78" />

### Diagrama de componentes

<img width="512" height="512" alt="image" src="https://github.com/user-attachments/assets/76097b96-22a4-4f96-95cd-15bee88a89fa" />

---

## Arquitectura y capas

La aplicación sigue la arquitectura **MVVM (Model-View-ViewModel)** con las siguientes capas:

### Capa de presentación
- Activities y Fragments
- ViewModels
- Componentes de UI (XML)
- Adaptadores para RecyclerView

### Capa de dominio
- Repositorios
- Casos de uso
- Modelos de datos

### Capa de datos
- DAO (Data Access Objects)
- Base de datos (Room)
- Entidades

---

## Metodología de desarrollo

El proyecto sigue una adaptación de metodologías ágiles con énfasis en:
- Desarrollo iterativo e incremental.
- Entrega continua con Git Flow.
- Code reviews entre compañeros.
- Pruebas unitarias para componentes críticos.
- Documentación constante del proceso.

---

## Mapa de navegación

El flujo de navegación de la aplicación es el siguiente:

- **Pantalla de Inicio** (Lista de tareas)
- **→** **Detalle de Tarea**
- **→** **Editar Tarea**
- **↲** **Añadir Nueva Tarea**

La navegación se implementa utilizando el componente **Navigation** de Android Jetpack.

---

## Implementación y código

### Lenguajes y tecnologías
- **Kotlin:** Lenguaje principal para la lógica de la aplicación.
- **XML:** Para el diseño de interfaces de usuario.
- **Room:** Persistencia de datos local.
- **LiveData:** Observación de cambios en los datos.
- **ViewModel:** Gestiona datos relacionados con la UI.

### Control de versiones
El proyecto utiliza **Git** para control de versiones con el siguiente flujo:
- Rama `main` para releases estables.
- Rama `develop` para integración de features.
- Ramas feature para desarrollo de nuevas funcionalidades.
- Commits descriptivos y convencionales.

### Librerías y frameworks
#### Librerías de presentación
- AndroidX AppCompat
- Material Design Components
- ConstraintLayout
- RecyclerView

#### Frameworks y arquitectura
- Android Architecture Components
- Room Persistence Library
- LiveData y ViewModel
- Navigation Component

### Buenas prácticas y patrones
- Principios **SOLID** aplicados en la estructura del proyecto.
- Patrón **Repository** para el acceso a datos.
- Inyección de dependencias manual (próximamente Hilt/Dagger).
- Nomenclatura clara y consistente en paquetes y clases.
- Código comentado para facilitar el mantenimiento.

### Pruebas unitarias
Se implementaron pruebas unitarias para los componentes críticos:

Pruebas para ViewModels verificando la lógica de negocio.
Pruebas para Repositorios mockeando las fuentes de datos.
Pruebas para DAOs usando una base de datos en memoria.
Pruebas para utilitarios y helpers.

Kotlin
// Ejemplo de prueba unitaria para el ViewModel
@Test
fun addNewTask_setsNewTaskEvent() {
    // Given
    val viewModel = TaskViewModel(repository)
    
    // When
    viewModel.addNewTask()
    
    // Then
    val event = viewModel.navigateToAddTask.getOrAwaitValue()
    assertThat(event.getContentIfNotHandled(), not(nullValue()))
}

### Configuraciones y acceso a datos
#### Configuración de base de Datos

// AppDatabase.kt - Configuración de la base de datos Room
@Database(entities = [Task::class], version = 1)
abstract class AppDatabase : RoomDatabase() {
    abstract fun taskDao(): TaskDao
    
    companion object {
        @Volatile
        private var INSTANCE: AppDatabase? = null
        
        fun getDatabase(context: Context): AppDatabase {
            return INSTANCE ?: synchronized(this) {
                val instance = Room.databaseBuilder(
                    context.applicationContext,
                    AppDatabase::class.java,
                    "task_database"
                ).build()
                INSTANCE = instance
                instance
            }
        }
    }
}

## Configuración de dependencias
Las dependencias del proyecto se gestionan a través de Gradle:

Kotlin
// AppDatabase.kt - Configuración de la base de datos Room
@Database(entities = [Task::class], version = 1)
abstract class AppDatabase : RoomDatabase() {
    abstract fun taskDao(): TaskDao
    
    companion object {
        @Volatile
        private var INSTANCE: AppDatabase? = null
        
        fun getDatabase(context: Context): AppDatabase {
            return INSTANCE ?: synchronized(this) {
                val instance = Room.databaseBuilder(
                    context.applicationContext,
                    AppDatabase::class.java,
                    "task_database"
                ).build()
                INSTANCE = instance
                instance
            }
        }
    }
}

## Contacto
Mayerly Panteves
