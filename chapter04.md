# Capítulo IV: Product Implementation & Validation
## 4. Product Implementation & Validation
### 4.1. Software Configuration Management
#### 4.1.1. Software Development Environment Configuration

Para asegurar una colaboración eficiente y mantener la calidad del 
desarrollo de **Klippr**, se ha definido un entorno de desarrollo común para todos los miembros del equipo. A continuación se detalla la lista de productos/software que se utilizaron para el desarrollo de **Klippr**:

**Product UX/UI Design**

Para el diseño de la experiencia de usuario y la interfaz de la Landing Page de **Klippr**, se utilizaron las siguientes herramientas:

* **Figma**: Se empleó para la creación de wireframes, mockups y prototipos. https://figma.com/es-es/
* **UXPressia**: Utilizada para elaborar los User Personas, User Journey ,User Task Matrix, Emphaty Maps. https://uxpressia.com/es
* **Miro**: Se empleó para la creación de mapas de experiencia de usuario y flujos de usuario. https://miro.com/es-es/

**Software Development**

Para el desarrollo de la Landing Page y la aplicación móvil de **Klippr**, se utilizaron las siguientes herramientas:

* **Android Studio (Instalación local)**: IDE para el desarrollo de aplicaciones móviles nativas y/o híbridas. https://developer.android.com/studio?hl=es-419
* **VS Code**: Editor de código fuente con múltiples extensiones y soporte para desarrollo de múltiples lenguajes de programación. https://code.visualstudio.com/
* **Rider (Instalación local)**: IDE para el desarrollo de aplicaciones con C# y ASP .NET. https://www.jetbrains.com/rider/
* **GitHub**: Plataforma de desarrollo colaborativo para alojar y gestionar repositorios de código fuente. https://github.com/

**Project Managment and Collaboration**

En la gestión de proyectos y colaboración del equipo se utilizaron:
* **Trello**: Utilizado para la planificación y seguimiento de tareas, distribuidas en listas de "por hacer", "en progreso" y "hecho". https://trello.com/
* **WhatsApp**: Medio de comunicación instantánea para coordinar avances, resolver dudas rápidas y hacer recordatorios. https://web.whatsapp.com/
* **Google Meet**: Herramienta utilizada para realizar reuniones virtuales más formales, presentaciones de avances y coordinación general del equipo. [https://meet.google.com/landing?hs=193&pli=1](https://meet.google.com/landing?hs=193&pli=1)

**Software Documentation**: 

Para la documentación del proyecto se usaron las siguientes herramientas:

* **Lucidchart**: Utilizado para la creación de diagramas de flujo y arquitectura del sistema. https://www.lucidchart.com/pages
* **Visual Paradigm**: Utilizado para la creación de diagramas de flujo y arquitectura del sistema. https://www.paradigm.com/drive/#proj=0&dashboard=

#### 4.1.2. Source Code Management

La gestión del código fuente es una parte fundamental del proceso de desarrollo colaborativo de software, ya que permite un control eficiente de los cambios y versiones del código fuente. En esta sección se describe el sistema de control de versiones implementado por **Klippr**, utilizando GitHub como plataforma de alojamiento de repositorios. Además se detallan las convenciones de trabajo, como el modelo GitFlow y versionado semántico (Conventional Commits).

<br>

**URL de los Repositorios**: 

* Organización: https://github.com/QRustOrg/ReportTB1
* Reporte: https://github.com/QRustOrg/ReportTB1
* Landing Page: https://github.com/QRustOrg/LandingPage
* Aplicación Movil: https://github.com/QRustOrg/Klippr-MobileApp
* Backend: https://github.com/QRustOrg/Klippr-Backend

**Estructura de Ramas**: 

Para mantener un flujo organizado en el desarrollo, se ha implementado el modelo GitFlow a través de las siguientes ramas:

* Main Branch: Rama principal (main) que contiene las versiones estables del proyecto. Todas las demás ramas derivan de esta.
* Develop Branch: Rama de desarrollo (develop) que contiene las características en desarrollo y se fusiona con la Main Branch al final de cada sprint.
* Feature Branches: Ramas de características (feature) que se crean para desarrollar nuevas funcionalidades y se fusionan con la Develop Branch al finalizar.

**Convenciones de commits**: 

Para mantener un flujo de trabajo consistente y claro, se han establecido las siguientes convenciones de commits:

```
<type>[optional scope]: <description>

[optional body]

[optional footer]
```

* Type: 
  * feat: Agregar una nueva funcionalidad.
  * fix: Corregir un bug.
  * docs: Actualizar la documentación.
  * refactor: Refactorizar el código.
  * test: Agregar o corregir pruebas.
  * chore: Tareas de mantenimiento.

* Scope: Brinda información sobre el alcance del commit.
```
feat(update): redemption interface & infrastructure settings
```

**Ejemplos de commits**:

```
feat(update): redemption interface & infrastructure settings
chore(db): delete db seed
fix(endpoint): add swagger docs and fix promotion creation route
```

#### 4.1.3. Source Code Style Guide & Conventions

**Nomenclatura General**:

Para mantener consistencia y claridad en el código, bajo el patrón **Clean Architecture**, se aplicarán convenciones de nomenclatura por **Google Kotlin Style Guide** y **Jetpack Compose Guidelines**.

Para los nombres de los variables y funciones se empleará **camelCase**. **PascalCase** se utilizará para los nombres de las clases y interfaces.

* Ejemplos:

```kotlin

// Variables y funciones (camelCase)
val userName: String
fun getUserName()

// Clases y componentes (PascalCase)
class User {
  @Composable
  fun UserProfile()
}

// Recursos XML (snake_case)
1_user_avatar.png
activity_main.xml
```

**Sangría**:

La sangría debe ser de **4 espacios por bloque** en Kotlin. No se recomienda el uso de tabulaciones, de acuerdo con las convenciones oficiales de Android Developers.

**Kotlin**:

Kotlin es el lenguaje principal utilizado en el proyecto. Las siguientes pautas aseguran consistencia y legibilidad en el código:

```kotlin
fun calculateUserAge(birthDate: LocalDate): Int {
    val currentDate = LocalDate.now()
    return Period.between(birthDate, currentDate).years
}
```

**Uso de `val` y `var`**:

Es recomendable utilizar `val` en lugar de `var` para definir variables inmutables, siguiendo el principio de inmutabilidad recomendado por Google (s.f.).

```kotlin
val userName = "Samuel"
var userAge = 20
```

**Formato de funciones y clases**:

Las llaves de apertura deben ir en la misma línea que la declaración, y la llave de cierre debe ubicarse en su propia línea.

```kotlin
class UserRepository {
    fun getUserById(id: String): User {
        return userDao.getUser(id)
    }
}
```

**Espaciado**:

Se debe incluir un espacio después de los dos puntos en las declaraciones de tipos y entre operadores.

```kotlin
val distance: Float = 23.5f
val sum = x + y
```

**Imports**:

No se deben utilizar imports comodín, ejemplo: `import com.example.*`. Solo se deben importar las clases necesarias.

```kotlin
import com.frock.chapaturuta.core.ui.theme.PrimaryColor
import androidx.compose.material3.Text
```

**Jetpack Compose**:

Compose se usa para la interfaz de usuario. Las convenciones aseguran consistencia visual y estructural en la aplicación móvil.

**Nomenclatura de Composables**:

Los nombres de las funciones composables deben usar **PascalCase** y terminar con la palabra `Screen` o `Component`, dependiendo de su función.

```kotlin
@Composable
fun LoginScreen(navController: NavController)

@Composable
fun RouteCard(routeName: String, onClick: () -> Unit)
```

**Estructura y legibilidad**:

Cada Composable debe tener una estructura clara y con espaciado adecuado para mejorar la legibilidad.

```kotlin
@Composable
fun HomeScreen() {
    Column(
        modifier = Modifier
            .fillMaxSize()
            .padding(16.dp),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Text(
            text = "Welcome to ChapaTuRuta!",
            style = MaterialTheme.typography.titleLarge
        )
        Spacer(modifier = Modifier.height(20.dp))
        Button(onClick = { /* Navigate to routes */ }) {
            Text("Explore Routes")
        }
    }
}
```

**Uso de colores y temas**:

Los colores y estilos deben provenir del archivo de tema ubicado en `core/ui/theme/`, respetando las convenciones de Material Design 3.

```kotlin
Button(
    onClick = { /* TODO */ },
    colors = ButtonDefaults.buttonColors(containerColor = PrimaryColor)
) {
    Text("Register", color = Color.White)
}
```

**Clean Architecture**:

El proyecto sigue la arquitectura en capas **Domain**, **Data** y **Presentation**, donde cada capa tiene una responsabilidad definida.

**Domain Layer**:

Contiene los casos de uso (*use cases*) y las entidades del negocio.

```kotlin
class GetUserUseCase(private val repository: UserRepository) {
    suspend operator fun invoke(id: String): User {
        return repository.getUserById(id)
    }
}
```

**Data Layer**:

Gestiona las fuentes de datos, como API y base de datos local.

```kotlin
class UserRepositoryImpl(private val api: UserApi) : UserRepository {
    override suspend fun getUserById(id: String): User {
        return api.getUser(id)
    }
}
```

**Presentation Layer**:

Maneja la lógica de interfaz mediante **ViewModel** y **Composables**.

```kotlin
@HiltViewModel
class LoginViewModel @Inject constructor(
    private val loginUseCase: LoginUseCase
) : ViewModel() {
    var uiState by mutableStateOf(LoginUiState())
        private set

    fun onLoginClicked() {
        viewModelScope.launch {
            uiState = uiState.copy(isLoading = true)
            loginUseCase(uiState.email, uiState.password)
        }
    }
}
```

**XML (Resources)**:

Aunque Jetpack Compose reemplaza gran parte del XML, se mantendrán recursos para íconos, cadenas y temas.

**Nombres de archivos**:

Los nombres de archivos deben escribirse en **snake_case** y en minúsculas.

```xml
ic_logo_app.xml
background_primary.xml
colors.xml
strings.xml
```

**Cadenas**:

Todas las cadenas visibles al usuario deben almacenarse en `res/values/strings.xml`.

```xml
<string name="app_name">Klippr</string>
<string name="login_button">Iniciar sesión</string>
```
#### 4.1.4. Software Deployment Configuration

Para el despliegue de la **Landing Page**, se utilizó **Vercel**. Una plataforma basada en la nube que permite el despliegue de aplicaciones web de manera gratuita y simple.

**URL**: https://klippr-landing-page.vercel.app/

##### Proceso de Implementación

* **Creación del repositorio**: <br>
Desde la organización de Github, se seleccionó la opción de **"New Repository"**. Donde alojamos el proyecto.

* **Configuración del repositorio**: <br>
Se asignó una visibilidad pública y un nombre al proyecto, requisitos mínimos que **Vercel** requiere para el despliegue. 

##### Configuración de despliegue desde Vercel

Previo al despliegue, se realizó el **"merge"** de las ramas de desarrollo a la rama **"main"**. Posteriormente, accedemos a la plataforma de **Vercel** para realizar el despligue del servicio. 

Luego, seleccionamos el botón **"Add New"** -> **"Project"** para iniciar el proceso de despliegue. 

![Vercel-Dashboard](/assets/chapter04/vercel-deploy/vercel-dashboard.png)

En esta pantalla seleccionamos el repositorio de **Landing Page** ***(Klippr-Landing-Page)*** y posteriormente, seleccionamos el botón **"Import"**.

![Selecting-Repository](/assets/chapter04/vercel-deploy/selecting-repo.png)

A continuación, la plataforma nos muestra un resumen de la configuración de despliegue, donde confirmamos que el proyecto está configurado correctamente y seleccionamos el botón **"Deploy"**.

![Pre-Deploy](/assets/chapter04/vercel-deploy/pre-deploy.png)

Luego de pulsar en **"Deploy"**, **Vercel** iniciará el proceso de despliegue. Una vez finalizado el proceso, se mostrará un dashboard con algunos datos del proyecto.

![Success-Deploy](/assets/chapter04/vercel-deploy/deploy-dashboard.png)

Finalmente, si todo ha ido bien, podremos acceder a la **Landing Page** desplegada en la URL asignada por **Vercel**.

![Deploy-Final](/assets/chapter04/vercel-deploy/deploy.png)

### 4.2. Landing Page & Mobile Application Implementation
#### 4.2.1. Sprint 1
##### 4.2.1.1. Sprint Planning 1

En este primer sprint, el enfoque principal fue la implementación de historias de usuario en la **Landing Page** y el primer prototipo de **Klippr**, en resumen: implementar las principales vistas funcionales y establecer la navegación entre ellas.

Las tareas se distribuyeron de esta forma:

* **Samuel Bonifacio**: <br>
* **Julio Guillen**: <br>
* **Alberto Ponce**: <br>
* **Alejandro Galindo**: <br>
* **Jefferson Castro**: <br>

También se añadió el **logo oficial** de la aplicación en todas las vistas principales para **unificar la identidad visual**.

##### 4.2.1.2. Sprint Backlog 1

<table border="1" cellpadding="8" cellspacing="0" style="width:100%; border-collapse: collapse;">
  <tr>
    <th>ID</th>
    <th>Historia de Usuario</th>
    <th>Descripción</th>
    <th>Prioridad</th>
    <th>Responsable</th>
    <th>Estado</th>
  </tr>
  <tr>
    <td>US-01</td>
    <td>Explorar descuentos</td>
    <td>Como usuario, quiere visualizar descuentos disponibles para encontrar promociones.<br><br><b>Criterios de Aceptación:</b><br><b>Dado que</b> el usuario accede a la aplicación,<br><b>Cuando</b> visualiza la lista de descuentos,<br><b>Entonces</b> observa promociones disponibles.</td>
    <td>Alta</td>
    <td>Samuel</td>
    <td>Completado</td>
  </tr>
  <tr>
    <td>US-02</td>
    <td>Filtrar descuentos</td>
    <td>Como usuario, quiere filtrar descuentos por categoría o ubicación.<br><br><b>Criterios de Aceptación:</b><br><b>Dado que</b> existen filtros disponibles,<br><b>Cuando</b> el usuario selecciona un criterio,<br><b>Entonces</b> se muestran descuentos filtrados.</td>
    <td>Alta</td>
    <td>Samuel</td>
    <td>Completado</td>
  </tr>
  <tr>
    <td>US-03</td>
    <td>Ver detalle de promoción</td>
    <td>Como usuario, quiere ver condiciones de una promoción.<br><br><b>Criterios de Aceptación:</b><br><b>Dado que</b> selecciona una promoción,<br><b>Cuando</b> accede al detalle,<br><b>Entonces</b> visualiza condiciones y vigencia.</td>
    <td>Alta</td>
    <td>Samuel</td>
    <td>Completado</td>
  </tr>
</table>

##### 4.2.1.3. Development Evidence for Sprint Review
##### 4.2.1.4. Testing Suite Evidence for Sprint Review
##### 4.2.1.5. Execution Evidence for Sprint Review
##### 4.2.1.6. Services Documentation Evidence for Sprint Review
##### 4.2.1.7. Software Deployment Evidence for Sprint Review
##### 4.2.1.8. Team Collaboration Insights during Sprint
### 4.3. Validation Interviews
#### 4.3.1. Diseño de Entrevistas
#### 4.3.2. Registro de Entrevistas
#### 4.3.3. Evaluaciones según heurísticas
