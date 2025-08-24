<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TodoAppV01 - Documentación</title>
    <style>
        :root {
            --primary-color: #3f51b5;
            --secondary-color: #f50057;
            --light-color: #f5f5f5;
            --dark-color: #333;
            --success-color: #4caf50;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background-color: #f9f9f9;
            padding: 0;
            margin: 0;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            background: linear-gradient(135deg, var(--primary-color), #7986cb);
            color: white;
            padding: 2rem 0;
            text-align: center;
            margin-bottom: 2rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        h1, h2, h3, h4 {
            margin-bottom: 1rem;
            color: var(--primary-color);
        }
        
        h1 {
            font-size: 2.5rem;
            color: white;
        }
        
        h2 {
            font-size: 2rem;
            border-bottom: 2px solid var(--primary-color);
            padding-bottom: 0.5rem;
            margin-top: 2rem;
        }
        
        h3 {
            font-size: 1.5rem;
            color: var(--secondary-color);
        }
        
        section {
            background: white;
            border-radius: 8px;
            padding: 1.5rem;
            margin-bottom: 2rem;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
            margin: 1.5rem 0;
        }
        
        .card {
            background: var(--light-color);
            border-left: 4px solid var(--primary-color);
            padding: 1rem;
            border-radius: 4px;
        }
        
        .code-block {
            background: #2d2d2d;
            color: #f8f8f2;
            padding: 1rem;
            border-radius: 4px;
            overflow-x: auto;
            margin: 1rem 0;
            font-family: 'Courier New', monospace;
        }
        
        ul, ol {
            margin-left: 1.5rem;
            margin-bottom: 1rem;
        }
        
        li {
            margin-bottom: 0.5rem;
        }
        
        .badge {
            display: inline-block;
            background: var(--primary-color);
            color: white;
            padding: 0.25rem 0.5rem;
            border-radius: 4px;
            font-size: 0.8rem;
            margin-right: 0.5rem;
        }
        
        .diagram {
            width: 100%;
            max-width: 800px;
            margin: 1rem auto;
            display: block;
            background: white;
            padding: 1rem;
            border-radius: 4px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .nav-map {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 1rem;
            margin: 1.5rem 0;
        }
        
        .nav-item {
            background: var(--light-color);
            padding: 1rem;
            border-radius: 8px;
            text-align: center;
            min-width: 120px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .nav-arrow {
            display: flex;
            align-items: center;
            font-weight: bold;
            color: var(--primary-color);
        }
        
        footer {
            text-align: center;
            padding: 2rem 0;
            margin-top: 2rem;
            background: var(--dark-color);
            color: white;
        }
        
        @media (max-width: 768px) {
            .grid {
                grid-template-columns: 1fr;
            }
            
            .nav-map {
                flex-direction: column;
                align-items: center;
            }
            
            .nav-arrow {
                transform: rotate(90deg);
                margin: 0.5rem 0;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <h1>TodoAppV01 - Documentación</h1>
            <p>Repositorio: <a href="https://github.com/MayerlyPanteves/TodoAppV01.git" style="color: white;">https://github.com/MayerlyPanteves/TodoAppV01.git</a></p>
        </div>
    </header>

    <div class="container">
        <section id="introduction">
            <h2>Introducción</h2>
            <p>TodoAppV01 es una aplicación Android para la gestión de tareas, desarrollada en Android Studio. Esta documentación proporciona una visión completa del proyecto, incluyendo requerimientos, arquitectura, diseño y proceso de desarrollo.</p>
        </section>

        <section id="requirements">
            <h2>Requerimientos del Sistema</h2>
            <div class="grid">
                <div class="card">
                    <h3>Requerimientos Funcionales</h3>
                    <ul>
                        <li>Crear, editar y eliminar tareas</li>
                        <li>Marcar tareas como completadas</li>
                        <li>Organizar tareas por categorías</li>
                        <li>Establecer fechas de vencimiento para tareas</li>
                        <li>Recordatorios para tareas próximas</li>
                    </ul>
                </div>
                <div class="card">
                    <h3>Requerimientos No Funcionales</h3>
                    <ul>
                        <li>Interfaz intuitiva y responsive</li>
                        <li>Almacenamiento local de datos con Room</li>
                        <li>Compatibilidad con Android 8.0+</li>
                        <li>Rendimiento fluido y eficiente</li>
                    </ul>
                </div>
            </div>
        </section>

        <section id="android-studio">
            <h2>Android Studio y SDK</h2>
            <p>El proyecto fue desarrollado utilizando Android Studio y el SDK de Android con las siguientes configuraciones:</p>
            <ul>
                <li><span class="badge">Android Studio</span> Versión 2022.3.1 o superior</li>
                <li><span class="badge">SDK</span> Android API 33 (Android 13)</li>
                <li><span class="badge">Gradle</span> Versión 8.0</li>
                <li><span class="badge">Kotlin</span> Versión 1.8.20</li>
            </ul>
        </section>

        <section id="diagrams">
            <h2>Diagramas del Sistema</h2>
            
            <h3>Diagrama de Clases</h3>
            <div class="code-block">
// Diagrama de clases simplificado
+----------------+       +----------------+       +----------------+
|     Task       |       |   TaskDao      |       | TaskRepository |
+----------------+       +----------------+       +----------------+
| - id: Long     |       | + insert()     |       | - taskDao: TaskDao |
| - title: String|       | + update()     |       | + getAllTasks() |
| - description: |       | + delete()     |       | + getTaskById() |
| - dueDate: Date|       | + getTasks()   |       | + insertTask()  |
| - isCompleted: |       +----------------+       | + updateTask()  |
| - category:    |                                | + deleteTask()  |
+----------------+                                +----------------+
        |                                                   |
        |                                                   |
        V                                                   V
+----------------+                                +----------------+
|   TaskDatabase |                                |  ViewModel     |
+----------------+                                +----------------+
| - static       |                                | - repository:  |
|   instance     |                                |   TaskRepository |
| - getDatabase()|                                | + getTasks()   |
+----------------+                                | + addTask()    |
                                                  | + updateTask() |
                                                  +----------------+
            </div>
            
            <h3>Diagrama de Paquetes</h3>
            <div class="code-block">
todoappv01/
├── data/
│   ├── dao/
│   │   └── TaskDao.kt
│   ├── database/
│   │   └── AppDatabase.kt
│   ├── model/
│   │   └── Task.kt
│   └── repository/
│       └── TaskRepository.kt
├── presentation/
│   ├── view/
│   │   ├── MainActivity.kt
│   │   ├── TaskListFragment.kt
│   │   ├── TaskDetailFragment.kt
│   │   └── AddTaskFragment.kt
│   └── viewmodel/
│       └── TaskViewModel.kt
└── di/
    └── DependencyInjection.kt
            </div>
            
            <h3>Diagrama de Componentes</h3>
            <div class="code-block">
+----------------+    +----------------+    +----------------+
|   UI Components|    |   ViewModel    |    |  Repository    |
|   (Activities, |    |                |    |                |
|   Fragments)   |    |                |    |                |
+----------------+    +----------------+    +----------------+
        |                  |                  |
        | (observa)        | (llama)          | (accede)
        |                  |                  |
        V                  V                  V
+----------------+    +----------------+    +----------------+
|   LiveData     |    |   Use Cases    |    |   Local Data   |
|                |    |                |    |   (Room)       |
+----------------+    +----------------+    +----------------+
            </div>
        </section>

        <section id="architecture">
            <h2>Arquitectura y Capas</h2>
            <p>La aplicación sigue la arquitectura MVVM (Model-View-ViewModel) con las siguientes capas:</p>
            
            <div class="grid">
                <div class="card">
                    <h3>Capa de Presentación</h3>
                    <ul>
                        <li>Activities y Fragments</li>
                        <li>ViewModels</li>
                        <li>Componentes de UI (XML)</li>
                        <li>Adaptadores para RecyclerView</li>
                    </ul>
                </div>
                
                <div class="card">
                    <h3>Capa de Dominio</h3>
                    <ul>
                        <li>Repositorios</li>
                        <li>Casos de uso</li>
                        <li>Modelos de datos</li>
                    </ul>
                </div>
                
                <div class="card">
                    <h3>Capa de Datos</h3>
                    <ul>
                        <li>DAO (Data Access Objects)</li>
                        <li>Base de datos (Room)</li>
                        <li>Entidades</li>
                    </ul>
                </div>
            </div>
        </section>

        <section id="methodology">
            <h2>Metodología de Desarrollo</h2>
            <p>El proyecto sigue una adaptación de metodologías ágiles con énfasis en:</p>
            <ul>
                <li>Desarrollo iterativo e incremental</li>
                <li>Entrega continua con Git Flow</li>
                <li>Code reviews entre compañeros</li>
                <li>Pruebas unitarias para componentes críticos</li>
                <li>Documentación constante del proceso</li>
            </ul>
        </section>

        <section id="navigation">
            <h2>Mapa de Navegación</h2>
            <div class="nav-map">
                <div class="nav-item">Pantalla de Inicio<br>(Lista de tareas)</div>
                <div class="nav-arrow">→</div>
                <div class="nav-item">Detalle de Tarea</div>
                <div class="nav-arrow">→</div>
                <div class="nav-item">Editar Tarea</div>
                <div class="nav-arrow">↲</div>
                <div class="nav-item">Añadir Nueva Tarea</div>
            </div>
            <p>La navegación se implementa utilizando el componente Navigation de Android Jetpack.</p>
        </section>

        <section id="implementation">
            <h2>Implementación y Código</h2>
            
            <h3>Lenguajes y Tecnologías</h3>
            <ul>
                <li><span class="badge">Kotlin</span> Lenguaje principal para la lógica de la aplicación</li>
                <li><span class="badge">XML</span> Para el diseño de interfaces de usuario</li>
                <li><span class="badge">Room</span> Persistencia de datos local</li>
                <li><span class="badge">LiveData</span> Observación de cambios en los datos</li>
                <li><span class="badge">ViewModel</span> Gestiona datos relacionados con la UI</li>
            </ul>
            
            <h3>Control de Versiones</h3>
            <p>El proyecto utiliza Git para control de versiones con el siguiente flujo:</p>
            <ul>
                <li>Rama <code>main</code> para releases estables</li>
                <li>Rama <code>develop</code> para integración de features</li>
                <li>Ramas feature para desarrollo de nuevas funcionalidades</li>
                <li>Commits descriptivos y convencionales</li>
            </ul>
            
            <h3>Librerías y Frameworks</h3>
            <div class="grid">
                <div class="card">
                    <h4>Librerías de Presentación</h4>
                    <ul>
                        <li>AndroidX AppCompat</li>
                        <li>Material Design Components</li>
                        <li>ConstraintLayout</li>
                        <li>RecyclerView</li>
                    </ul>
                </div>
                
                <div class="card">
                    <h4>Frameworks y Arquitectura</h4>
                    <ul>
                        <li>Android Architecture Components</li>
                        <li>Room Persistence Library</li>
                        <li>LiveData y ViewModel</li>
                        <li>Navigation Component</li>
                    </ul>
                </div>
            </div>
            
            <h3>Buenas Prácticas y Patrones</h3>
            <ul>
                <li>Principios SOLID aplicados en la estructura del proyecto</li>
                <li>Patrón Repository para el acceso a datos</li>
                <li>Inyección de dependencias manual (próximamente Hilt/Dagger)</li>
                <li>Nomenclatura clara y consistente en paquetes y clases</li>
                <li>Código comentado para facilitar el mantenimiento</li>
            </ul>
            
            <h3>Ejemplo de Código</h3>
            <div class="code-block">
// TaskDao.kt - Data Access Object para las tareas
@Dao
interface TaskDao {
    @Query("SELECT * FROM task ORDER BY dueDate ASC")
    fun getAllTasks(): LiveData&lt;List&lt;Task&gt;&gt;
    
    @Insert(onConflict = OnConflictStrategy.REPLACE)
    suspend fun insert(task: Task)
    
    @Update
    suspend fun update(task: Task)
    
    @Delete
    suspend fun delete(task: Task)
    
    @Query("SELECT * FROM task WHERE id = :taskId")
    fun getTaskById(taskId: Long): LiveData&lt;Task&gt;
}
            </div>
        </section>

        <section id="testing">
            <h2>Pruebas Unitarias</h2>
            <p>Se implementaron pruebas unitarias para los componentes críticos:</p>
            <ul>
                <li>Pruebas para ViewModels verificando la lógica de negocio</li>
                <li>Pruebas para Repositorios mockeando las fuentes de datos</li>
                <li>Pruebas para DAOs usando una base de datos en memoria</li>
                <li>Pruebas para utilitarios y helpers</li>
            </ul>
            
            <div class="code-block">
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
            </div>
        </section>

        <section id="configuration">
            <h2>Configuraciones y Acceso a Datos</h2>
            
            <h3>Configuración de Base de Datos</h3>
            <div class="code-block">
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
            </div>
            
            <h3>Configuración de dependencias</h3>
            <p>Las dependencias del proyecto se gestionan a través de Gradle:</p>
            <div class="code-block">
// build.gradle (Module)
dependencies {
    implementation "androidx.room:room-runtime:2.5.2"
    kapt "androidx.room:room-compiler:2.5.2"
    implementation "androidx.lifecycle:lifecycle-viewmodel-ktx:2.6.1"
    implementation "androidx.lifecycle:lifecycle-livedata-ktx:2.6.1"
    implementation "androidx.navigation:navigation-fragment-ktx:2.6.0"
    implementation "com.google.android.material:material:1.9.0"
}
            </div>
        </section>
    </div>

    <footer>
        <div class="container">
            <p>Documentación del proyecto TodoAppV01</p>
            <p>Repositorio: <a href="https://github.com/MayerlyPanteves/TodoAppV01.git" style="color: #bb86fc;">https://github.com/MayerlyPanteves/TodoAppV01.git</a></p>
        </div>
    </footer>
</body>
</html>
