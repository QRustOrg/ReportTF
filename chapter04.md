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

* **Mobile Application**

<br>

* **Landing Page**

En el desarrollo de la **Landing Page**, la implementación se llevó a cabo por todos los integrantes del grupo. Tanto en entorno local como en nube **(Github)**.

Posteriormente el proyecto fue desplegado en **Vercel** para su publicación, permitiendo que el resto de su equipo y los evaluadores puedan acceder a la página para la revisión del sprint.


<table border="1" cellpadding="8" cellspacing="0" style="width:100%; border-collapse: collapse;">
  <tr>
    <th>Repository</th>
    <th>Branch</th>
    <th>Commit ID</th>
    <th>Commit Message</th>
    <th>Author</th>
    <th>Commited on (Date)</th>
  </tr>
  <tr>
    <td>Klippr-LandingPage</td>
    <td>main</td>
    <td>db0df97</td>
    <td>feat:add components Benefits&amp;HowItWorksSections</td>
    <td>JeffersonCastroPariona</td>
    <td>May 10, 2026</td>
  </tr>
  <tr>
    <td>Klippr-LandingPage</td>
    <td>main</td>
    <td>49d3c2c</td>
    <td>feat: add social-proof and comparison section</td>
    <td>AlejandroG12970</td>
    <td>May 10, 2026</td>
  </tr>
  <tr>
    <td>Klippr-LandingPage</td>
    <td>main</td>
    <td>3ee4839</td>
    <td>fix: update LanguageToogle and PainPointsSection</td>
    <td>aponceperales</td>
    <td>May 9, 2026</td>
  </tr>
  <tr>
    <td>Klippr-LandingPage</td>
    <td>main</td>
    <td>57c2d19</td>
    <td>Feature: added PainPointsSection, LanguageToogle and Footer</td>
    <td>aponceperales</td>
    <td>May 9, 2026</td>
  </tr>
  <tr>
    <td>Klippr-LandingPage</td>
    <td>main</td>
    <td>c45396f</td>
    <td>initial commit</td>
    <td>samuelbonifacio015</td>
    <td>May 9, 2026</td>
  </tr>
</table>

<br>

* **Backend**:

En el desarrollo del **Backend**, la implementación se llevó a cabo por todos los integrantes del grupo. Tanto en entorno local como en nube **(Github)**.

Posteriormente el proyecto fue desplegado en **Railway** para su publicación, permitiendo que el resto de su equipo y los evaluadores puedan acceder al servicio y prueben los endpoints.

<table border="1" cellpadding="8" cellspacing="0" style="width:100%; border-collapse: collapse;">
  <tr>
    <th>Repository</th>
    <th>Branch</th>
    <th>Commit ID</th>
    <th>Commit Message</th>
    <th>Author</th>
    <th>Commited on (Date)</th>
  </tr>
  <tr>
    <td>Klippr-Backend</td>
    <td>main</td>
    <td>ca76253</td>
    <td>feat(profile): merge profile branch updates into main</td>
    <td>samuelbonifacio015</td>
    <td>May 14, 2026</td>
  </tr>
  <tr>
    <td>Klippr-Backend</td>
    <td>main</td>
    <td>0d5d8a7</td>
    <td>feat: profile module updates</td>
    <td>JeffersonCastroPariona</td>
    <td>May 14, 2026</td>
  </tr>
  <tr>
    <td>Klippr-Backend</td>
    <td>main</td>
    <td>dea71a2</td>
    <td>fix:add parameterless constructor to SavingsStatistics for EF Core materialization</td>
    <td>samuelbonifacio015</td>
    <td>May 13, 2026</td>
  </tr>
  <tr>
    <td>Klippr-Backend</td>
    <td>main</td>
    <td>88c5fad</td>
    <td>feat: add redepmtion infrastructure</td>
    <td>samuelbonifacio015</td>
    <td>May 12, 2026</td>
  </tr>
  <tr>
    <td>Klippr-Backend</td>
    <td>main</td>
    <td>eba7f36</td>
    <td>feat: update favorites infrastructure, domain and shared</td>
    <td>aponceperales</td>
    <td>May 12, 2026</td>
  </tr>
  <tr>
    <td>Klippr-Backend</td>
    <td>main</td>
    <td>341d71d</td>
    <td>feat: add Redemption aggregate</td>
    <td>samuelbonifacio015</td>
    <td>May 6, 2026</td>
  </tr>
  <tr>
    <td>Klippr-Backend</td>
    <td>main</td>
    <td>add analytics bounded context</td>
    <td>feat: add analytics bounded context</td>
    <td>AlejandroG12970</td>
    <td>May 5, 2026</td>
  </tr>
</table>

##### 4.2.1.4. Testing Suite Evidence for Sprint Review

Por el momento no sea han realizado pruebas manuales de navegación entre pantallas. El producto en **Android Studio** aún está en versión estática. **(Solo pantallas visibles en Kotlin).**

##### 4.2.1.5. Execution Evidence for Sprint Review

Durante este primer Sprint logramos realizar la implementación del Landing page, Backend y Mobile App, sin embargo este último por el momento se realizó de forma local.

A continuación se presentan evidencias de ejecución de los 3 productos:

**Landing Page**

**Hero Section**: 

En esta sección se colocó un mensaje que atraiga la atención del visitante, junto con un botón call to action para posteriormente enviarlo a la aplicación móvil desplegada.

![Hero Section](/assets/chapter04/execution-evidence/landing-page/klippr-hero.png)

**Problem Section**:

En esta sección se expone la problemática principal que nuestros usuarios enfrentan, generando empatía y resaltando la necesidad de nuestra solución.

![Problem Section](/assets/chapter04/execution-evidence/landing-page/klippr-problem.png)

**How It Works Section**:

En esta sección se detalla el funcionamiento paso a paso de la aplicación, guiando al visitante de forma sencilla sobre cómo empezar a utilizarla.

![How It Works Section](/assets/chapter04/execution-evidence/landing-page/klippr-howitworks.png)

**Benefits Bussiness Section**:

En esta sección se destacan los beneficios que Klippr ofrece a los negocios asociados, incentivándolos a afiliarse y aumentar sus ventas.

![Benefits Bussiness Section](/assets/chapter04/execution-evidence/landing-page/klippr-benefits-bussiness.png)

**Benefits Client Section**:

En esta sección se muestran las ventajas principales para los usuarios finales, enfatizando el ahorro y la conveniencia que brinda la plataforma.

![Benefits Client Section](/assets/chapter04/execution-evidence/landing-page/klippr-benefits-client.png)

**Testimonials Section**:

En esta sección se presentan opiniones y experiencias reales de usuarios, generando confianza en el producto mediante validación social.

![Testimonials Section](/assets/chapter04/execution-evidence/landing-page/klippr-testimonials.png)

**Comparison Section**:

En esta sección se realiza una comparativa frente a otras alternativas, subrayando nuestra propuesta de valor y ventajas competitivas.

![Comparison Section](/assets/chapter04/execution-evidence/landing-page/klippr-comparison.png)

**Footer Section**:

En esta sección se ubican los enlaces finales de navegación, información de contacto y políticas de privacidad para facilitar el soporte al usuario.

![Footer Section](/assets/chapter04/execution-evidence/landing-page/klippr-footer.png)

**Backend**

A continuación se muestran evidencias del backend desplegado y todos los endpoints desarrollados:

![Backend-1](/assets/chapter04/execution-evidence/backend/backend-1.png)

![Backend-2](/assets/chapter04/execution-evidence/backend/backend-2.png)

![Backend-3](/assets/chapter04/execution-evidence/backend/backend-3.png)

![Backend-4](/assets/chapter04/execution-evidence/backend/backend-4.png)

**Mobile App**

![Mobile App](/assets/chapter04/execution-evidence/mobile/klippr-mobile-1.png)

![Mobile App-2](/assets/chapter04/execution-evidence/mobile/klippr-mobile-2.png)

![Mobile App-3](/assets/chapter04/execution-evidence/mobile/klippr-mobile-3.png)

##### 4.2.1.6. Services Documentation Evidence for Sprint Review

Tras finalizar el Sprint 1, hemos logrado implementar los endpoints de nuestro Backend, estableciendo un modelo de negocio y lógica sólida para **Klippr**. Durante este Sprint nos centramos en la implementación de los bounded contexts de **AdminProfile**, **Analytics**, **Authentication**, **Favorites**, **Promotion**, **Redemption**, **Users**, **Profile**, **Verification** los cuales se encuentran desplegados en **Railway** y se puede acceder a ellos a traves de la API. A continuación se presentan evidencias de la documentación de los endpoints:

## Promotion Bounded Context

Como parte del desarrollo del backend en **C#**, se ha consolidado el Bounded Context de **Promotion**. Este módulo es fundamental para la estrategia de marketing y ventas de la aplicación, encargado de gestionar la creación, configuración y publicación de promociones, ofertas y descuentos por parte de los negocios (Business).

### Implementacion Tecnica de Promotion
Se ha estructurado la lógica para permitir que los negocios definan promociones con diferentes reglas de negocio y restricciones. Los logros principales incluyen:

* **Gestión de Promociones:** Implementación de flujos para la creación, lectura, actualización y eliminación (CRUD) de campañas promocionales.
* **Segmentación y Reglas:** Capacidad para definir fechas de inicio y fin, cantidades limitadas y condiciones específicas para cada oferta.
* **Integración Visual:** Endpoints diseñados para servir la información de manera estructurada a la aplicación móvil, facilitando su visualización para los consumidores.

---

## Evidencias de Ejecucion: Módulo Promotion

A continuacion se presentan los endpoints desarrollados y testeados a traves de la interfaz de Swagger:

![promotion-evidence-1](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-promotion-1.png)

### 1. Gestion de Promociones (Promotion)

El controlador de **Promotion** expone las funcionalidades críticas para el ciclo de vida de las ofertas:

* **Endpoints de Promociones**: Permite a las empresas gestionar sus campañas y a los usuarios visualizarlas.

- **Creación y Gestión de Ofertas** 

![promotion-evidence-2](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-promotion-2.png)

- **Detalles de la Promoción**

![promotion-evidence-3](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-promotion-3.png)

- **Visualización y Búsqueda**

![promotion-evidence-4](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-promotion-4.png)

- **Actualización de Estados**

![promotion-evidence-5](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-promotion-5.png)

- **Eliminación y Limpieza**

![promotion-evidence-6](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-promotion-6.png)

![promotion-evidence-7](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-promotion-7.png)


## Redemption Bounded Context

Como parte del desarrollo del backend en **C#**, se ha consolidado el Bounded Context de **Redemption**. Este módulo actúa como el motor transaccional para la adquisición y canje de promociones, vinculando directamente a los consumidores con las ofertas de los negocios.

### Implementacion Tecnica de Redemption
Se ha diseñado un flujo robusto y transaccional para garantizar la integridad de cada canje. Los logros principales incluyen:

* **Generación de Códigos Unicos:** Creación de identificadores (como códigos QR o alfanuméricos) seguros y únicos para cada redención.
* **Validación en Tiempo Real:** Verificación inmediata de la validez de una promoción (fechas, stock, estado) antes de permitir el canje.
* **Historial de Transacciones:** Registro inmutable de todos los canjes realizados, permitiendo tanto al usuario como al negocio mantener un seguimiento claro de la actividad.

---

## Evidencias de Ejecucion: Módulo Redemption

A continuacion se presentan los endpoints desarrollados y testeados a traves de la interfaz de Swagger:

![redemption-evidence-1](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-1.png)

### 1. Gestion de Canjes (Redemption)

El controlador de **Redemption** expone las funcionalidades esenciales para la validación y ejecución del canje:

* **Endpoints de Canjes**: Facilitan la interacción segura entre la solicitud del consumidor y la aprobación del sistema.

- **Proceso de Canje (Redemption Process)** 

![redemption-evidence-2](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-2.png)

- **Validación de Parámetros**

![redemption-evidence-3](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-3.png)

- **Historial de Redenciones**

![redemption-evidence-4](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-4.png)

- **Verificación de Códigos**

![redemption-evidence-5](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-5.png)

- **Confirmación de Éxito**

![redemption-evidence-6](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-6.png)


## IAM Bounded Context

Como parte del desarrollo del backend en **C#**, se ha consolidado el Bounded Context de **IAM (Identity and Access Management)**. Este modulo es el pilar de seguridad de la aplicacion, encargado de gestionar la identidad de los usuarios, la autenticacion y la autorizacion basada en roles para los perfiles de Consumer y Business.

### Implementacion Tecnica de IAM
Se ha utilizado **ASP.NET Core Identity** junto con **JWT (JSON Web Tokens)** para garantizar comunicaciones seguras entre la aplicacion movil y el servidor. Los logros principales incluyen:

* **Registro Segregado:** Implementacion de flujos de inscripcion diferenciados para asegurar que cada tipo de usuario sea categorizado correctamente desde su creacion.
* **Autenticacion Centralizada:** Un servicio de inicio de sesion unico que valida credenciales y emite tokens de acceso de corta duracion.
* **Seguridad de Datos:** Aplicacion de algoritmos de hashing para la proteccion de contraseñas en la base de datos.

---

## Evidencias de Ejecucion: Módulo Authentication

A continuacion se presentan los endpoints desarrollados y testeados a traves de la interfaz de Swagger:

![iam-profile](/assets/chapter04/vercel-deploy/evidences-sprint/iam/iambc.png)

### 1. Gestion de Identidad y Acceso (IAM)

El controlador de **Authentication** expone las funcionalidades criticas para el ciclo de vida del usuario:

* **POST `/api/Authentication/sign-in`**: Permite a los usuarios existentes obtener un token de acceso mediante sus credenciales.
* **POST `/api/Authentication/sign-up/consumer`**: Proceso de registro optimizado para el usuario final (Consumer), vinculando la identidad con su perfil correspondiente.
* **POST `/api/Authentication/sign-up/business`**: Registro especializado para entidades de negocio, activando las reglas de validacion propias de este sector.


- **Validacion parametro Post** 

![iam-profile](/assets/chapter04/vercel-deploy/evidences-sprint/iam/pro2.png)

- **Registration Process**

![iam-profile](/assets/chapter04/vercel-deploy/evidences-sprint/iam/iaproc.png)

### Notas de Integracion
Los tokens generados por este modulo son requeridos como cabecera `Authorization: Bearer {token}` para interactuar con los Bounded Contexts de **Profile** y **Verification**, asegurando que solo usuarios autenticados puedan gestionar su informacion personal o empresarial.

### 2. Profile

Se han expuesto los endpoints necesarios para la creación (**POST**), actualización (**PUT**) y consulta (**GET**) de perfiles tanto para consumidores finales como para cuentas de negocio.

- **Endpoint `/api/profiles/consumer`**  
  Gestiona la información personal y preferencias del usuario final.

- **Endpoint `/api/profiles/business`**  
  Maneja los datos operativos y comerciales de las empresas registradas.

- **Módulo de Verificación y Administración**

  Se implementó la lógica de negocio para el filtrado de perfiles pendientes de validación, permitiendo a los administradores del sistema aprobar o rechazar solicitudes de acceso.

  - **AdminProfile**  
  Consultas especializadas para la búsqueda de usuarios y perfiles que requieren atención.

  - **Verification**  
  Flujo de trabajo para el envío (**submit**) y aprobación (**approve**) de documentos o datos de identidad.

![sw-bcprofile](/assets/chapter04/vercel-deploy/evidences-sprint/profile/bcpro.png)

- **Validacion parametro Post** 

![sw-bcprofile](/assets/chapter04/vercel-deploy/evidences-sprint/profile/post-parameter.png)

- **Company Profile** 

![sw-bcprofile](/assets/chapter04/vercel-deploy/evidences-sprint/profile/emplog.png)

- **User Profile** 

![sw-bcprofile](/assets/chapter04/vercel-deploy/evidences-sprint/profile/userlog.png)

##### 4.2.1.7. Software Deployment Evidence for Sprint Review

**Evidencias del despliegue de Landing Page**

En esta sección se muestran las evidencias del **despliegue de Landing Page** desarrollada con **Next.js, React y TypeScript**

**Url: https://klippr-landing-page.vercel.app/**

![Vercel Deploy](/assets/chapter04/vercel-deploy/deploy-dashboard.png)

![Landing-Page](/assets/chapter04/vercel-deploy/deploy.png)

**Evidencias del despliegue de Backend**

El Backend ha sido desarrollado con **C#** y **ASP.NET Core**, utilizando **JWT (JSON Web Tokens)** para la autenticación y autorización. Se encuentra desplegado en **Railway**.

**Url: https://klippr-backend-production.up.railway.app/swagger/index.html**

![Railway](/assets/chapter04/deployment-evidence/railway-1.png)

Para el despliegue del Web Service se seleccionó **Railway**, una plataforma en la nube que se integró de forma directa con nuestro repositorio de **GitHub**. Esta conexión garantiza la automatización completa del flujo de despliegue, de modo que cada nueva actualización en el código fuente se refleje de inmediato en el entorno de producción.

**Railway** destaca por ofrecer una configuración intuitiva y escalable, resultando idónea para servicios backend y arquitecturas basadas en APIs. Mediante su panel de control, se logró vincular el repositorio del proyecto, establecer las variables de entorno requeridas y ejecutar el despliegue de forma ágil, eliminando la dependencia de herramientas de terceros o configuraciones complejas desde el IDE.

![Railway](/assets/chapter04/deployment-evidence/railway-2.png)

La imagen muestra el entorno de producción en Railway, donde el backend fue desplegado correctamente. Estado: El mensaje “Deployment successful” confirma que el despliegue se realizó sin errores.

![Backend-1](/assets/chapter04/execution-evidence/backend/backend-1.png)

##### 4.2.1.8. Team Collaboration Insights during Sprint

Durante el desarrollo del Sprint 1, el equipo de desarrollo mantuvo una comunicación fluida y colaborativa. Se realizaron reuniones por medio de **Discord y Meet** para sincronizar el trabajo, identificar bloqueos y asegurar el avance hacia los objetivos del sprint. Además, se utilizaron herramientas de colaboración como **Trello** y **Obisidan** para gestionar las tareas, compartir información y resolver dudas de manera eficiente. 

**Resumen del Sprint 1:**

* **Landing Page:** Se desarrolló y desplegó exitosamente en Vercel, incluyendo todas las secciones de información y llamadas a la acción.
* **Backend y APIs:** Se implementaron los principales Bounded Contexts (IAM, Profile) en C# y se desplegaron en Railway.
* **Mobile App:** Se construyeron las interfaces estáticas iniciales en Android Studio empleando Jetpack Compose y Kotlin.
* **Despliegue:** Se automatizó el pase a producción vinculando GitHub directamente con Vercel y Railway.
* **Estructura base:** Se consolidó el uso de Clean Architecture y se definieron las convenciones de código y trabajo del equipo.

### 4.3. Validation Interviews
#### 4.3.1. Diseño de Entrevistas
#### 4.3.2. Registro de Entrevistas
#### 4.3.3. Evaluaciones según heurísticas
