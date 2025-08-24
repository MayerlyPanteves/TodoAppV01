# TodoAppV01 - Documentación

Repositorio: [https://github.com/MayerlyPanteves/TodoAppV01.git](https://github.com/MayerlyPanteves/TodoAppV01.git)

---

## Introducción

TodoAppV01 es una aplicación Android para la gestión de tareas, desarrollada en Android Studio. Esta documentación proporciona una visión completa del proyecto, incluyendo requerimientos, arquitectura, diseño y proceso de desarrollo.

---

## Requerimientos del Sistema

### Requerimientos Funcionales
- Crear, editar y eliminar tareas.
- Marcar tareas como completadas.
- Organizar tareas por categorías.
- Establecer fechas de vencimiento para tareas.
- Recordatorios para tareas próximas.

### Requerimientos No Funcionales
- Interfaz intuitiva y responsive.
- Almacenamiento local de datos con Room.
- Compatibilidad con Android 8.0+.
- Rendimiento fluido y eficiente.

---

## Android Studio y SDK

El proyecto fue desarrollado utilizando Android Studio y el SDK de Android con las siguientes configuraciones:
- **Android Studio:** Versión 2022.3.1 o superior.
- **SDK:** Android API 33 (Android 13).
- **Gradle:** Versión 8.0.
- **Kotlin:** Versión 1.8.20.

---

## Diagramas del Sistema

### Diagrama de Clases

<img width="512" height="512" alt="image" src="https://github.com/user-attachments/assets/c3506ed0-69b5-43e9-bfdf-91786ab1330e" />

### Diagrama de Paquetes

<img width="512" height="512" alt="image" src="https://github.com/user-attachments/assets/f010478a-a922-4fda-bac2-27f21e624f78" />

### Diagrama de Componentes

<img width="512" height="512" alt="image" src="https://github.com/user-attachments/assets/76097b96-22a4-4f96-95cd-15bee88a89fa" />

---

## Arquitectura y Capas

La aplicación sigue la arquitectura **MVVM (Model-View-ViewModel)** con las siguientes capas:

### Capa de Presentación
- Activities y Fragments
- ViewModels
- Componentes de UI (XML)
- Adaptadores para RecyclerView

### Capa de Dominio
- Repositorios
- Casos de uso
- Modelos de datos

### Capa de Datos
- DAO (Data Access Objects)
- Base de datos (Room)
- Entidades

---

## Metodología de Desarrollo

El proyecto sigue una adaptación de metodologías ágiles con énfasis en:
- Desarrollo iterativo e incremental.
- Entrega continua con Git Flow.
- Code reviews entre compañeros.
- Pruebas unitarias para componentes críticos.
- Documentación constante del proceso.

---

## Mapa de Navegación

El flujo de navegación de la aplicación es el siguiente:

- **Pantalla de Inicio** (Lista de tareas)
- **→** **Detalle de Tarea**
- **→** **Editar Tarea**
- **↲** **Añadir Nueva Tarea**

La navegación se implementa utilizando el componente **Navigation** de Android Jetpack.

---

## Implementación y Código

### Lenguajes y Tecnologías
- **Kotlin:** Lenguaje principal para la lógica de la aplicación.
- **XML:** Para el diseño de interfaces de usuario.
- **Room:** Persistencia de datos local.
- **LiveData:** Observación de cambios en los datos.
- **ViewModel:** Gestiona datos relacionados con la UI.

### Control de Versiones
El proyecto utiliza **Git** para control de versiones con el siguiente flujo:
- Rama `main` para releases estables.
- Rama `develop` para integración de features.
- Ramas feature para desarrollo de nuevas funcionalidades.
- Commits descriptivos y convencionales.

### Librerías y Frameworks
#### Librerías de Presentación
- AndroidX AppCompat
- Material Design Components
- ConstraintLayout
- RecyclerView

#### Frameworks y Arquitectura
- Android Architecture Components
- Room Persistence Library
- LiveData y ViewModel
- Navigation Component

### Buenas Prácticas y Patrones
- Principios **SOLID** aplicados en la estructura del proyecto.
- Patrón **Repository** para el acceso a datos.
- Inyección de dependencias manual (próximamente Hilt/Dagger).
- Nomenclatura clara y consistente en paquetes y clases.
- Código comentado para facilitar el mantenimiento.

### Ejemplo de Código 
```kotlin
// TaskDao.kt - Data Access Object para las tareas
@Dao
interface TaskDao {
    @Query("SELECT * FROM task ORDER BY dueDate ASC")
    fun getAllTasks(): LiveData<List<Task>>
    
    @Insert(onConflict = OnConflictStrategy.REPLACE)
    suspend fun insert(task: Task)
    
    @Update
    suspend fun update(task: Task)
    
    @Delete
    suspend fun delete(task: Task)
    
    @Query("SELECT * FROM task WHERE id = :taskId")
    fun getTaskById(taskId: Long): LiveData<Task>
}

### Pruebas unitarias
Se implementaron pruebas unitarias para los componentes críticos:

Pruebas para ViewModels verificando la lógica de negocio.
Pruebas para repositorios mockeando las fuentes de datos.
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
Configuraciones y acceso a datos
Configuración de Base de Datos
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
Configuración de dependencias
Las dependencias del proyecto se gestionan a través de Gradle:

Gradle

// build.gradle (Module)
dependencies {
    implementation "androidx.room:room-runtime:2.5.2"
    kapt "androidx.room:room-compiler:2.5.2"
    implementation "androidx.lifecycle:lifecycle-viewmodel-ktx:2.6.1"
    implementation "androidx.lifecycle:lifecycle-livedata-ktx:2.6.1"
    implementation "androidx.navigation:navigation-fragment-ktx:2.6.0"
    implementation "com.google.android.material:material:1.9.0"
}
