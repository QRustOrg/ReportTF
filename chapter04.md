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
import com.frock.klippr.core.ui.theme.PrimaryColor
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
            text = "Welcome to Klippr!",
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

* **Samuel Bonifacio**: Despliegue de **Landing Page & Backend**(Creación de BCS: Promotion & Redemption), además de la documentación de estos procesos.<br>
* **Julio Guillen**: <br> Creación los Bounded Contexts de Community y Setting, además de la documentación de estos procesos.<br>
* **Alberto Ponce**: Creacion de BC: Favorites, ademas de encargarme de todo el apartado de las Validation Interviews <br> 
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

## Community Bounded Context

Como parte del desarrollo del backend en **C#**, se ha consolidado el Bounded Context de **Community**. Este módulo actúa como el espacio de interacción social entre los consumidores y los dueños de negocio, permitiendo fortalecer la comunicación, la participación y la retroalimentación dentro de la plataforma.

### Implementacion Tecnica de Community
Se ha diseñado un flujo robusto y escalable para garantizar una interacción dinámica y segura entre los usuarios y los negocios. Los logros principales incluyen:

* **Sistema de Comentarios:** Implementación de funcionalidades para que los usuarios puedan publicar comentarios y opiniones sobre los negocios y promociones.
* **Calificaciones y Reseñas:** Integración de un sistema de puntuación que permite valorar la experiencia del consumidor con el negocio.
* **Interacción con el Dueño del Negocio:** Desarrollo de mecanismos que facilitan la comunicación entre la comunidad y los propietarios de los establecimientos.

---

## Evidencias de Ejecucion: Módulo Community

A continuacion se presentan los endpoints desarrollados y testeados a traves de la interfaz de Swagger:

![communityn-evidence-1](/assets/chapter04/execution-evidence/backend/community/klippr-community-1.png)

### 1. Gestion de Comunidad (Community)

El controlador de **Community** expone las funcionalidades esenciales para la interacción entre consumidores y negocios:

* **Endpoints de Comunidad**: Facilitan la interacción segura entre usuarios y dueños de negocio dentro de la plataforma.

- **Publicación de Comentarios (Community Process)** 

![communityn-evidence-2](/assets/chapter04/execution-evidence/backend/community/klippr-community-2.png)

- **Validación de Contenido**

![community-evidence-3](/assets/chapter04/execution-evidence/backend/community/klippr-community-3.png)

- **Gestión de Calificaciones y Reseñas**

![community-evidence-4](/assets/chapter04/execution-evidence/backend/community/klippr-community-4.png)

- **Editar Contenido**

![community-evidence-5](/assets/chapter04/execution-evidence/backend/community/klippr-community-5.png)

![community-evidence-6](/assets/chapter04/execution-evidence/backend/community/klippr-community-6.png)

- **Eliminar Calificaciones y Reseñas**

![community-evidence-6](/assets/chapter04/execution-evidence/backend/community/klippr-community-7.png)

## Setting Bounded Context

Como parte del desarrollo del backend en **C#**, se ha consolidado el Bounded Context de **Settings**. Este módulo actúa como el núcleo de configuración de la plataforma, permitiendo la administración y personalización de preferencias tanto para consumidores como para dueños de negocio.

### Implementacion Tecnica de Setting
Se ha diseñado un flujo robusto y flexible para garantizar una gestión segura y centralizada de las configuraciones del sistema. Los logros principales incluyen:

* **Gestión de Preferencias de Usuario:** Implementación de funcionalidades para personalizar configuraciones relacionadas con la cuenta, notificaciones y experiencia de uso.
* **Persistencia Segura de Configuraciones:** Desarrollo de mecanismos que aseguran el almacenamiento confiable y consistente de las preferencias definidas por los usuarios.
* **Actualización Dinámica de Ajustes:** Implementación de procesos que permiten modificar configuraciones en tiempo real sin afectar la estabilidad del sistema.

---

## Evidencias de Ejecucion: Módulo Setting

A continuación se presentan los endpoints desarrollados y testeados a través de la interfaz de Swagger:

![setting-evidence-1](/assets/chapter04/execution-evidence/backend/setting/klippr-setting-1.png)

### 1. Gestion de Comunidad (Settings)

El controlador de **Settings** expone las funcionalidades esenciales para la administración de preferencias y parámetros de la plataforma:

* **Endpoints de Settings**: Facilitan la actualización y consulta segura de ajustes relacionados con usuarios y negocios.

- **Creacion de comentarios (Settings Process)** 

![setting-evidence-2](/assets/chapter04/execution-evidence/backend/setting/klippr-setting-2.png)

- **Validación de Configuraciones**

![setting-evidence-3](/assets/chapter04/execution-evidence/backend/community/klippr-community-3.png)

- **Gestión de Parámetros de Negocio**

![setting-evidence-4](/assets/chapter04/execution-evidence/backend/community/klippr-community-4.png)

- **Actualización de Preferencias**

![setting-evidence-5](/assets/chapter04/execution-evidence/backend/community/klippr-community-5.png)

![setting-evidence-6](/assets/chapter04/execution-evidence/backend/community/klippr-community-6.png)

- **Eliminar Configuracion**

![setting-evidence-6](/assets/chapter04/execution-evidence/backend/community/klippr-community-7.png)

# Favorites Bounded Context

Como parte del desarrollo del backend en **C#**, se ha consolidado el Bounded Context de **Favorites**. Este módulo permite a los usuarios guardar promociones de interés para consultarlas posteriormente, facilitando el seguimiento de ofertas relevantes y mejorando la experiencia de descubrimiento.

### Implementación Técnica de Favorites
Se ha utilizado **ASP.NET Core** junto con **Entity Framework Core** y **SQLite** para garantizar la persistencia y recuperación eficiente de los favoritos. Los logros principales incluyen:

* **Guardado de Promociones:** Implementación de un flujo de guardado que valida duplicados, asegurando que un usuario no pueda guardar la misma promoción más de una vez.
* **Consulta por Usuario:** Un servicio de consulta que recupera todas las promociones guardadas asociadas a un usuario específico.
* **Eliminación Segura:** Aplicación de reglas de dominio que garantizan que solo el propietario del favorito pueda eliminarlo.


## Evidencias de Ejecución: Módulo Favorites

A continuación se presentan los endpoints desarrollados y testeados a través de la interfaz de Swagger:

![favorites-swagger](/assets/chapter04/execution-evidence/backend/favorites/POST1favorites.png)

### 1. Gestión de Favoritos

El controlador de **Favorites** expone las funcionalidades críticas para el ciclo de vida de un favorito:

* **POST `/api/v1/favorites`**: Permite a un usuario guardar una promoción como favorita. Retorna **201 Created** con los datos del favorito creado.
* **GET `/api/v1/favorites/user/{userId}`**: Recupera la lista completa de promociones guardadas por un usuario específico.
* **GET `/api/v1/favorites/{id}`**: Obtiene un favorito específico mediante su identificador interno.
* **DELETE `/api/v1/favorites/{favoriteId}`**: Elimina una promoción de la lista de favoritos del usuario. Solo el propietario puede realizar esta acción.

- **Validación parámetro Post**

![favorites-post](/assets/chapter04/execution-evidence/backend/favorites/POST1favorites.png)

- **Registration Process**

![favorites-process](/assets/chapter04/execution-evidence/backend/favorites/GETID1favorites.png)
![favorites-process](/assets/chapter04/execution-evidence/backend/favorites/GETID2favorites.png)
![favorites-process](/assets/chapter04/execution-evidence/backend/favorites/GETUSERID1favorites.png)
![favorites-process](/assets/chapter04/execution-evidence/backend/favorites/GETUSERID2favorites.png)

### Notas de Integración
El Bounded Context de Favorites es completamente independiente: no depende de los Bounded Contexts de **Profile** ni de **Promotions** directamente. La comunicación con otros contextos se realiza únicamente a través de la **FavoritesContextFacade**, que expone operaciones de solo lectura mediante primitivos, garantizando el aislamiento del dominio.

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

#### 4.2.2. Sprint 2
##### 4.2.2.1. Sprint Planning 2

En este segundo sprint, el enfoque principal fue la implementación de historias de usuario en la **Landing Page** y el primer prototipo de **Klippr**, en resumen: implementar las principales vistas funcionales y establecer la navegación entre ellas.

Las tareas se distribuyeron de esta forma:

* **Samuel Bonifacio**: Despliegue de **Landing Page & Backend**(Creación de BCS: Promotion & Redemption), además de la documentación de estos procesos.<br>
* **Julio Guillen**: <br> Creación los Bounded Contexts de Community y Setting, además de la documentación de estos procesos.<br>
* **Alberto Ponce**: Creacion de BC: Favorites, ademas de encargarme de todo el apartado de las Validation Interviews <br> 
* **Alejandro Galindo**: <br>
* **Jefferson Castro**: <br>

También se añadió el **logo oficial** de la aplicación en todas las vistas principales para **unificar la identidad visual**.
----------
En este segundo sprint se consolidó la implementación de las funcionalidades principales del producto, logrando el despliegue de la Landing Page y del backend,así como el desarrollo de los principales Bounded Contexts que soportan la lógica de negocio de la aplicación.

Las responsabilidades del equipo se distribuyeron de la siguiente manera:

- **Samuel Bonifacio:** Responsable del despliegue de la Landing Page y del Backend en entornos públicos. Además, desarrolló los Bounded Contexts de **Settings**, **Dashboard** y **Redemption**, así como la documentación técnica correspondiente.

- **Julio Guillén:** Encargado del desarrollo del Bounded Context **Promotion**, además de la elaboración de la documentación asociada a dichos componentes.

- **Alberto Ponce:** Responsable del desarrollo del Bounded Context de **Favorites**.

- **Alejandro Galindo:** Responsable de las funcionalidades asignadas dentro del Bounded Context de **Community**, colaborando en la integración de componentes y validación de los flujos de usuario.

- **Jefferson Castro:** Responsable de las funcionalidades asignadas dentro del Sprint 2, participando en la implementación.

Adicionalmente, se realizaron pruebas funcionales de las características implementadas para verificar su correcto funcionamiento y preparar el producto para las actividades de validación correspondientes.

##### 4.2.2.2. Sprint Backlog 2

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
    <td>US-04</td>
    <td>Generar código QR</td>
    <td>Como usuario, quiere generar un código QR único para canjear promociones disponibles.</td>
    <td>Alta</td>
    <td>Samuel</td>
    <td>Completado</td>
  </tr>

  <tr>
    <td>US-20</td>
    <td>Guardar promociones</td>
    <td>Como usuario, quiere guardar promociones favoritas para acceder a ellas posteriormente.</td>
    <td>Alta</td>
    <td>Alberto</td>
    <td>Completado</td>
  </tr>

  <tr>
    <td>US-21</td>
    <td>Buscar promociones</td>
    <td>Como usuario, quiere buscar promociones por nombre para encontrarlas fácilmente.</td>
    <td>Alta</td>
    <td>Samuel</td>
    <td>Completado</td>
  </tr>

  <tr>
    <td>US-17</td>
    <td>Registro</td>
    <td>Como usuario, quiere registrarse en la plataforma para acceder a sus funcionalidades.</td>
    <td>Alta</td>
    <td>Jefferson</td>
    <td>Completado</td>
  </tr>

  <tr>
    <td>US-18</td>
    <td>Login</td>
    <td>Como usuario, quiere iniciar sesión de forma segura en la aplicación.</td>
    <td>Alta</td>
    <td>Jefferson</td>
    <td>Completado</td>
  </tr>
</table>

##### 4.2.2.3. Development Evidence for Sprint Review

* **Mobile Application**

En el desarrollo del **Frontend**, la implementación fue realizada de manera colaborativa por todos los integrantes del equipo, trabajando tanto en entorno local como mediante el uso de **GitHub** como repositorio principal de control de versiones.

<table border="1" cellpadding="8" cellspacing="0" style="width:100%; border-collapse: collapse;">
  <tr>
    <th>Repository</th>
    <th>Branch</th>
    <th>Commit ID</th>
    <th>Commit Message</th>
    <th>Author</th>
    <th>Committed on (Date)</th>
  </tr>
  
  <tr>
    <td>Klippr-LandingPage</td>
    <td>main</td>
    <td>db0df97</td>
    <td>feat: add conextion with db</td>
    <td>JeffersonCastroPariona</td>
    <td>Jun 18, 2026</td>
  </tr>
  
  <tr>
    <td>Klippr-LandingPage</td>
    <td>main</td>
    <td>49d3c2c</td>
    <td>feat: add review section</td>
    <td>AlejandroG12970</td>
    <td>Jun 17, 2026</td>
  </tr>
  
  <tr>
    <td>Klippr-LandingPage</td>
    <td>main</td>
    <td>3ee4839</td>
    <td>fix: update Dashboard</td>
    <td>aponceperales</td>
    <td>Jun 17, 2026</td>
  </tr>

  <tr>
    <td>Klippr-LandingPage</td>
    <td>main</td>
    <td>57c2d19</td>
    <td>feat: added Promos, Community and Favorites</td>
    <td>aponceperales</td>
    <td>Jun 15, 2026</td>
  </tr>
</table>

<br>

* **Backend**

En el desarrollo del **Backend**, la implementación también fue realizada de manera colaborativa por todos los integrantes del equipo, utilizando **GitHub** como sistema de control de versiones y trabajo distribuido.

El backend fue desplegado en **Railway**, permitiendo su acceso público para pruebas, validación de endpoints y verificación del funcionamiento de los Bounded Contexts implementados durante el Sprint 2.

<table border="1" cellpadding="8" cellspacing="0" style="width:100%; border-collapse: collapse;">
  <tr>
    <th>Repository</th>
    <th>Branch</th>
    <th>Commit ID</th>
    <th>Commit Message</th>
    <th>Author</th>
    <th>Committed on (Date)</th>
  </tr>

  <tr>
    <td>Klippr-Backend</td>
    <td>main</td>
    <td>ca76253</td>
    <td>feat: merge profile branch updates into main</td>
    <td>samuelbonifacio015</td>
    <td>Jun 19, 2026</td>
  </tr>

  <tr>
    <td>Klippr-Backend</td>
    <td>main</td>
    <td>dea71a2</td>
    <td>fix: add parameterless constructor to SavingsStatistics for EF Core materialization</td>
    <td>samuelbonifacio015</td>
    <td>MJunay 18, 2026</td>
  </tr>

  <tr>
    <td>Klippr-Backend</td>
    <td>main</td>
    <td>eba7f36</td>
    <td>feat: update favorites infrastructure, domain and shared</td>
    <td>aponceperales</td>
    <td>Jun 14, 2026</td>
  </tr>

  <tr>
    <td>Klippr-Backend</td>
    <td>main</td>
    <td>341d71d</td>
    <td>feat: update redemption infrastructure, aggregate</td>
    <td>samuelbonifacio015</td>
    <td>Jun 11, 2026</td>
  </tr>
</table>

##### 4.2.2.4. Testing Suite Evidence for Sprint Review

##### 4.2.2.5. Execution Evidence for Sprint Review

Durante este segundo Sprint logramos realizar la implementación del Mobile App y el Backend. El Backend fue desplegado para su validación, mientras que la Mobile App se ejecutó de forma local.

A continuación, se presentan evidencias de ejecución de los dos productos:

**Mobile App**

A continuación se muestran evidencias de la Mobile App ejecutada localmente y de las funcionalidades desarrolladas durante el Sprint 2:

### Profile

### Dashboard

#### Pantalla del Dashboard — Opción para Dejar Reseña

Desde la sección **Dashboard**, el usuario puede visualizar de manera centralizada la información más relevante de su cuenta. Esta vista presenta indicadores de promociones disponibles y otros promociones de interés. De esta manera, el Dashboard facilita una navegación más eficiente y una mejor experiencia de usuario al concentrar la información esencial en una sola pantalla.

<p align="center">
    <img src="assets\chapter04\sprint2-dashboard\dashboard.png">
</p>

### Promotion

#### Pantalla de Promotion — Pantalla con promociones

Desde la sección **Promotion**, el usuario puede visualizar el catálogo de promociones disponibles dentro de la aplicación. Cada promoción muestra información como su imagen, nombre y descripción breve, permitiendo al usuario explorar las diferentes opciones disponibles de manera rápida y organizada.

<p align="center">
    <img src="assets\chapter04\sprint2-promotion\promos-view.png">
</p>

#### Pantalla de Promotion — Pantalla con promocion elegida

Al seleccionar una promoción, el usuario accede a una vista detallada donde puede consultar información completa sobre la oferta. Esta pantalla presenta datos como la descripción de la promoción, el porcentaje de descuento, condiciones de uso, fecha de vigencia y demás detalles relevantes. Asimismo, con la opcion de aceptar las condiciones del uso antes de utilizarla.

<p align="center">
    <img src="assets\chapter04\sprint2-promotion\promos-chosen.png">
</p>

### Redemption

#### Pantalla de Redemption — Pantalla del QR

Una vez aceptados los términos y condiciones, el usuario accede a la pantalla de la promoción, **Redemption**, donde se genera y muestra un código QR único asociado al beneficio seleccionado, para garantizar una experiencia de canje rápida y segura.

<p align="center">
    <img src="assets\chapter04\sprint2-redemption\redemption.png">
</p>

### Favorites

#### Pantalla de Favorites — Pantalla vacia

Desde la sección **Favoritos**, cuando no existen promociones registradas, la pantalla muestra un mensaje informativo indicando que la lista se encuentra vacía.

<p align="center">
    <img src="assets\chapter04\sprint2-favorite\favorite-empty.png">
</p>

#### Pantalla de Favorites — Pantalla con promociones

Desde la sección **Favoritos**, el usuario puede visualizar las promociones que ha marcado previamente como favoritas. En este caso, la pantalla presenta dos promociones registradas, mostrando información relevante como la imagen, el nombre de la promoción y sus principales características. Esta funcionalidad permite al usuario acceder rápidamente a la promo de su interés y gestionarlas de manera sencilla.

<p align="center">
    <img src="assets\chapter04\sprint2-favorite\favorite-promos.png">
</p>

## Community

**Backend (Actualizado)**

A continuación se muestran evidencias del Backend desplegado actualizado, su documentación y los endpoints desarrollados:

![Backend-1](/assets/chapter04/sprint2-backend/backend-1.png)

![Backend-2](/assets/chapter04/sprint2-backend/backend-2.png)

![Backend-3](/assets/chapter04/sprint2-backend/backend-3.png)

![Backend-4](/assets/chapter04/sprint2-backend/backend-4.png)

![Backend-5](/assets/chapter04/sprint2-backend/backend-5.png)

![Backend-6](/assets/chapter04/sprint2-backend/backend-6.png)

![Backend-7](/assets/chapter04/sprint2-backend/backend-7.png)

##### 4.2.2.6. Services Documentation Evidence for Sprint Review

Tras culminar el Sprint 2, se completó el desarrollo de los endpoints del backend, consolidando la lógica de negocio y la arquitectura funcional de **Klippr**. En esta iteración se trabajó principalmente en la implementación de los bounded contexts de **Authentication**, **Favorites**, **Promotion**, **Redemption**, **Users** y **Profile**, los cuales se encuentran desplegados en **Railway** y disponibles para su consumo mediante la API. A continuación, se presentan las evidencias correspondientes a la documentación de los endpoints implementados:

# Profile Bounded Context

## Promotion Bounded Context

Como parte del desarrollo del backend en **C#**, se ha consolidado el Bounded Context de **Promotion**, módulo encargado de la administración de promociones dentro de **Klippr**. Este componente permite a los negocios crear y gestionar ofertas que posteriormente serán visualizadas y utilizadas por los usuarios de la plataforma.

### Implementacion Tecnica de Promotion

Se ha estructurado la lógica para permitir que los negocios definan promociones con diferentes reglas de negocio y restricciones. Los logros principales incluyen:

* **Gestión de Promociones:** Implementación de funcionalidades CRUD para la creación, consulta, actualización y eliminación de promociones.
* **Configuración de Ofertas:** Desarrollo de mecanismos para definir atributos como título, descripción, porcentaje de descuento, fecha de inicio, fecha de expiración y cantidad disponible.
* **Validaciones de Negocio:** Incorporación de reglas que garantizan la validez y disponibilidad de las promociones según las condiciones establecidas por cada negocio.

## Evidencias de Ejecucion: Módulo Promotion

A continuacion se presentan los endpoints desarrollados y testeados a traves de la interfaz de Swagger:

![promotion-evidence-0](/assets/chapter04/sprint2-promotion/promos-0.png)

### Gestion de Promociones (Promotion)

El controlador de **Promotion** expone las funcionalidades críticas para el ciclo de vida de las ofertas:

* **Creación de Promociones**

Permite registrar nuevas promociones dentro de la plataforma, definiendo información como nombre, descripción, porcentaje de descuento, fechas de vigencia y cantidad disponible.

![promotion-evidence-1](/assets/chapter04/sprint2-promotion/promos-1.png)

* **Listado General de Promociones**

Permite consultar todas las promociones registradas en el sistema para su administración y visualización.

![promotion-evidence-2](/assets/chapter04/sprint2-promotion/promos-2.png)

* **Consulta de Promoción por Identificador**

Permite obtener la información detallada de una promoción específica mediante su identificador único.

![promotion-evidence-3](/assets/chapter04/sprint2-promotion/promos-3.png)

* **Actualización de Promociones**

Permite modificar la información de una promoción existente, incluyendo datos descriptivos, fechas de vigencia y condiciones asociadas.

![promotion-evidence-4](/assets/chapter04/sprint2-promotion/promos-4.png)

* **Eliminación de Promociones**

Permite eliminar promociones registradas en el sistema cuando ya no sean necesarias o deban ser retiradas de forma permanente.

![promotion-evidence-5](/assets/chapter04/sprint2-promotion/promos-5.png)

* **Listado de Promociones Activas**

Permite consultar únicamente las promociones que se encuentran vigentes y disponibles para ser utilizadas por los consumidores.

![promotion-evidence-6](/assets/chapter04/sprint2-promotion/promos-6.png)

* **Listado de Promociones por Negocio**

Permite obtener todas las promociones asociadas a un negocio específico, facilitando la gestión individual de sus campañas.

![promotion-evidence-7](/assets/chapter04/sprint2-promotion/promos-7.png)

* **Publicación de Promociones**

Permite cambiar el estado de una promoción para que sea visible y accesible para los consumidores dentro de la aplicación.

![promotion-evidence-8](/assets/chapter04/sprint2-promotion/promos-8.png)

* **Cancelación de Promociones**

Permite desactivar una promoción previamente publicada, evitando que continúe disponible para nuevos canjes.

![promotion-evidence-9](/assets/chapter04/sprint2-promotion/promos-9.png)

## Redemption Bounded Context

Como parte del desarrollo del backend en **C#**, se ha implementado y consolidado el Bounded Context de **Redemption**. Este módulo permite conectar las promociones publicadas por los negocios con los consumidores que desean utilizarlas, garantizando un flujo seguro y controlado durante todo el proceso.

### Implementacion Tecnica de Redemption

Se ha desarrollado una arquitectura orientada a la gestión y validación de canjes, asegurando la correcta ejecución de cada transacción. Los principales avances alcanzados incluyen:

* **Generación de Canjes:** Implementación de mecanismos para registrar solicitudes de canje asociadas a promociones vigentes.
* **Validación de Promociones:** Verificación automática de condiciones como disponibilidad, vigencia, estado de la promoción y restricciones aplicables antes de autorizar el canje.
* **Confirmación de Canjes:** Desarrollo de funcionalidades que permiten validar y confirmar el uso efectivo de una promoción por parte del negocio.
* **Consulta de Historial:** Implementación de servicios para obtener el historial de canjes realizados por consumidores y negocios.

## Evidencias de Ejecucion: Módulo Redemption

A continuacion se presentan los endpoints desarrollados y testeados a traves de la interfaz de Swagger:

![redemption-evidence-1](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-1.png)

### Gestion de Canjes (Redemption)

El controlador de **Redemption** expone las funcionalidades esenciales para la validación y ejecución del canje:

* **Generación de Canjes**

Permite registrar una solicitud de canje para una promoción determinada, verificando que la oferta se encuentre disponible y cumpla con las condiciones establecidas.

![redemption-evidence-1](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-2.png)

* **Confirmación de Canjes**

Permite validar y confirmar un canje previamente generado, garantizando que la promoción sea utilizada de manera correcta y evitando usos duplicados.

![redemption-evidence-2](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-3.png)

* **Consulta de Canje por Identificador**

Permite obtener la información detallada de un canje específico mediante su identificador único, incluyendo datos asociados a la promoción y al consumidor.

![redemption-evidence-3](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-4.png)

* **Historial de Canjes por Consumidor**

Permite consultar todos los canjes realizados por un consumidor específico, facilitando el seguimiento de promociones utilizadas dentro de la plataforma.

![redemption-evidence-4](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-5.png)

* **Historial de Canjes por Negocio**

Permite obtener el listado de canjes asociados a un negocio determinado, proporcionando visibilidad sobre el uso y desempeño de sus promociones.

![redemption-evidence-5](/assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-6.png)

# Favorites Bounded Context

Como parte del desarrollo del backend en **C#**, se ha implementado y consolidado el Bounded Context de **Favorites**. Este componente permite a los consumidores guardar ofertas de su interés para acceder a ellas posteriormente, mejorando la experiencia de navegación y facilitando el acceso rápido a promociones relevantes.

### Implementación Técnica de Favorites

La solución fue desarrollada utilizando **ASP.NET Core**, **Entity Framework Core** y **SQLite**, garantizando una gestión eficiente de la información y una adecuada persistencia de los datos. Los principales avances alcanzados incluyen:

* **Registro de Favoritos:** Implementación de funcionalidades que permiten a los usuarios agregar promociones a su lista de favoritos de manera rápida y sencilla.
* **Consulta Personalizada:** Desarrollo de servicios que permiten recuperar todas las promociones favoritas asociadas a un usuario específico.
* **Eliminación de Favoritos:** Implementación de mecanismos para remover promociones guardadas cuando el usuario ya no desea mantenerlas en su lista.

## Evidencias de Ejecucion: Módulo Favorites

A continuacion se presentan los endpoints desarrollados y testeados a traves de la interfaz de Swagger:

![favorite-evidence-0](/assets/chapter04/sprint2-favorite/favorites-0.png)

## Evidencias de Ejecución: Módulo Favorites

El controlador de **Favorites** expone las funcionalidades críticas para el ciclo de vida de un favorito:

* **Listado de Favoritos por Usuario**

Permite consultar todas las promociones marcadas como favoritas por un usuario específico, facilitando el acceso rápido a ofertas previamente guardadas.

![favorite-evidence-1](/assets/chapter04/sprint2-favorite/favorites-1.png)

* **Consulta de Favorito por Identificador**

Permite obtener la información detallada de un registro de favorito mediante su identificador único.

![favorite-evidence-2](/assets/chapter04/sprint2-favorite/favorites-2.png)

* **Registro de Favoritos**

Permite asociar una promoción a la lista de favoritos de un usuario, aplicando validaciones para evitar registros duplicados y garantizar la integridad de los datos.

![favorite-evidence-3](/assets/chapter04/sprint2-favorite/favorites-3.png)

* **Eliminación de Favoritos**

Permite remover una promoción previamente guardada en la lista de favoritos de un usuario, manteniendo actualizadas sus preferencias dentro de la plataforma.

![favorite-evidence-4](/assets/chapter04/sprint2-favorite/favorites-4.png)

# Community Bounded Context

##### 4.2.2.7. Software Deployment Evidence for Sprint Review

### Evidencias del Despliegue de Backend

Como parte de los objetivos del Sprint 2, el backend fue desplegado exitosamente en un entorno público utilizando **Railway**, permitiendo el acceso a los servicios REST implementados y a su documentación técnica mediante **Swagger/OpenAPI**.

![Railway](/assets/chapter04/deployment-evidence/railway-1.png)

Para el despliegue se utilizó **Railway**, plataforma cloud que ofrece integración directa con repositorios de **GitHub**, facilitando la automatización del proceso de integración y despliegue continuo. Gracias a esta integración, cada actualización realizada en el repositorio puede ser desplegada de manera rápida y consistente en el entorno de producción.

La plataforma permitió configurar las variables de entorno necesarias para la ejecución de la aplicación, así como gestionar el monitoreo básico del servicio desde una interfaz centralizada.

![Railway](/assets/chapter04/deployment-evidence/railway-2.png)

### Evidencias de la Documentación de la API

Como resultado de la implementación de los diferentes Bounded Contexts desarrollados durante el Sprint 2, se habilitó la documentación interactiva de la API mediante Swagger, permitiendo visualizar y probar los endpoints disponibles para los módulos de **Authentication**, **Favorites**, **Promotion**, **Redemption**, **Analytics** y demás componentes del sistema.

![Backend-1](/assets/chapter04/execution-evidence/backend/backend-v2.png)

##### 4.2.2.8. Team Collaboration Insights during Sprint

Durante el desarrollo del **Sprint 2**, el equipo mantuvo una comunicación constante y colaborativa para asegurar el cumplimiento de los objetivos planteados. Se realizaron reuniones periódicas mediante **Discord**, permitiendo coordinar actividades, resolver impedimentos y dar seguimiento al avance de cada integrante. Asimismo, se utilizaron herramientas como **Trello** para la gestión de tareas y organización del conocimiento del proyecto.

**Resumen del Sprint 2:**

* **Backend y APIs:** Se completó la implementación de los principales Bounded Contexts de la solución, incluyendo **Profile, Favorites, Promotion y Redemption**, exponiendo sus funcionalidades mediante endpoints REST documentados.
* **Despliegue del Backend:** Los servicios fueron desplegados exitosamente en **Railway**, permitiendo el acceso público a la API y a su documentación técnica mediante Swagger/OpenAPI.
* **Validación de Funcionalidades:** Se implementaron y probaron los flujos principales de autenticación, gestión de promociones, favoritos, canjes y métricas de negocio, garantizando la correcta interacción entre los diferentes módulos del sistema.
* **Mejora de Artefactos:** Se revisaron y actualizaron los entregables desarrollados en iteraciones anteriores, incorporando correcciones y mejoras identificadas durante el proceso de validación.
* **Preparación de Evidencias:** Se recopilaron evidencias de las funcionalidades principales de la aplicación, así como material de apoyo para la elaboración de los videos de validación, About-the-Product y About-the-Team.

### 4.3. Validation Interviews

#### 4.3.1. Diseño de Entrevistas

#### Segmento 1

**P1.** ¿Cuándo fue la última vez que buscaste un descuento antes de ir a algún lugar?

**P2.** ¿Alguna vez un cupón no te funcionó en el momento de usarlo?

**P3.** ¿Qué entiendes que hace esta app?

**P4.** ¿El título *"Descuentos reales. Canjes seguros. Comunidad que confía."* fue suficiente para entender la propuesta?

**P5.** ¿Te identificaste con los tres problemas que muestra la página?

**P6.** ¿El flujo de 4 pasos quedó claro?

**P7.** El paso "Activar" dice que Klippr genera un QR único vinculado a tu cuenta que solo tú puedes usar. ¿Eso te pareció una ventaja clara, algo confuso, o algo que ya dabas por sentado?

**P8.** La página tiene una sección con números y un testimonio de una usuaria llamada Lizbeth. ¿Eso te generó confianza o lo sentiste insuficiente?

**P9.** En la sección "Hecho para ti", hay una pestaña con las funciones del usuario. ¿Las leíste? ¿Alguna te sorprendió o te pareció redundante?

**P10.** La página incluye una tabla comparando Klippr con "cuponeras tradicionales" y "super-apps". ¿La revisaste? ¿Te fue útil?

**P11.** Después de ver esa comparativa, ¿sientes que Klippr tiene algo que las apps que ya usas no tienen?

**P12.** Al final de la página hay un botón que dice *"Visita la App en GitHub"*. ¿Eso es lo que esperabas encontrar? ¿Qué pensaste cuando lo viste?

**P13.** Si la app estuviera disponible para descargar ahora mismo, ¿la descargarías después de ver esta página?

**P14.** ¿Hay algo en la página que te pareció confuso, que no encajó o que sentiste fuera de lugar?

**P15.** Si pudieras cambiar solo una cosa de esta landing para que convenza mejor a alguien de tu edad, ¿qué sería? ¿Y qué no tocarías?

#### Segmento 2

**P1.** ¿Actualmente haces campañas de descuentos para tu negocio? ¿Cómo las gestionas y cómo mides si funcionaron?

**P2.** ¿Has tenido problemas con fraude en cupones o con clientes que intentaron usar un descuento de formas no previstas?

**P3.** ¿Qué entiendes que hace esta plataforma para un negocio como el tuyo?

**P4.** Hay un enlace en la parte superior que dice *"¿Tienes un negocio? Conoce cómo Klippr te ayuda →"*. ¿Lo viste? ¿Lo usaste?

**P5.** ¿Qué sección de la página te pareció más útil para decidir si afilias tu negocio, y cuál sentiste que no te aportaba?

**P6.** En la sección "Hecho para ti — y para tu negocio" hay una pestaña "Para tu negocio". ¿La encontraste y la revisaste? ¿Las funciones que describe son las que esperarías?

**P7.** La página menciona que uno de los problemas que resuelve es el de "campaña a ciegas". ¿Eso resuena con algo que vives en tu negocio?

**P8.** ¿Esta landing te genera suficiente confianza para registrar tu negocio y publicar una campaña?

**P9.** La página tiene un testimonio de una usuaria consumidora. Desde la perspectiva de tu negocio, ¿eso es suficiente prueba social?

**P10.** La tabla comparativa incluye filas como "Dashboard para el negocio" y "Autogestión de campañas". ¿Esas filas ayudaron a entender qué diferencia a Klippr?

**P11.** La tabla dice que con Klippr puedes crear una campaña *"desde la app, en minutos"*. ¿Eso te parece creíble basándote en lo que viste?

**P12.** Al final de la página el botón dice *"Visita la App en GitHub"*. ¿Eso es lo que esperabas encontrar como negocio interesado en afiliarse?

**P13.** Después de ver la landing, ¿qué tan probable es que consideres afiliar tu negocio a Klippr?

**P14.** ¿Hubo algún momento en la página donde sentiste que la información no era suficiente para seguir evaluando la plataforma como negocio?

**P15.** Si le mostraras esta landing a otro dueño de negocio, ¿qué le dirías que tiene de bueno y qué debería ignorar? ¿Cuál sería el cambio más urgente?

#### 4.3.2. Registro de Entrevistas

#### Segmento 1

<table border="1" cellpadding="8" cellspacing="0" style="width:100%; border-collapse: collapse;">
  <tr>
    <th colspan="2">Entrevista 1</th>
  </tr>
  <tr>
    <td><strong>Nombre:</strong></td>
    <td>Fabrizio Osorio</td>
  </tr>
  <tr>
    <td><strong>Edad:</strong></td>
    <td>22 años</td>
  </tr>
  <tr>
    <td><strong>Distrito:</strong></td>
    <td>Surco, Lima</td>
  </tr>
  <tr>
    <td><strong>URL del video:</strong></td>
    <td>
      https://upcedupe-my.sharepoint.com/:v:/g/personal/u202320684_upc_edu_pe/IQBta8ur2O0qQ7dQjoBIQ9ScAcbSpkAnsw-AnSoW1CY9zOU?e=Te6hgO&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D <br>
      Timing: 10:28 <br>
      Duración: 10:28 minutos
    </td>
  </tr>
  <tr>
    <td><strong>Screenshot del video:</strong></td>
    <td><img src="assets/chapter04/entrevistas/Entrevista1S1.png"></td>
  </tr>
  <tr>
    <td colspan="2"><strong>Resumen de la entrevista:</strong></td>
  </tr>
  <tr>
    <td colspan="2">
      El entrevistado es un usuario habitual del celular que ha tenido malas experiencias previas con cupones compartidos por WhatsApp y redes sociales. Al ver el prototipo, comprendió la propuesta de forma inmediata y se identificó con los tres problemas planteados, especialmente con el del cupón reutilizado, que le había ocurrido personalmente. Valoró el flujo de 4 pasos como claro y sencillo, destacando el QR único como el diferencial principal frente a los cupones tradicionales. El paso "Activar" le resultó una ventaja clarísima: el hecho de que el descuento sea intransferible le generó mayor confianza que cualquier código genérico.La sección de estadísticas y el testimonio de Lizbeth le generaron confianza, aunque hubiera preferido más de un testimonio. La tabla comparativa le pareció honesta y útil. El único punto de fricción fue el botón final "Visita la App en GitHub", que le resultó completamente fuera de contexto al esperar un botón de descarga. Indicó que descargaría la app sin dudarlo, con una puntuación de 5/5, y recomendó reemplazar el CTA final y agregar más testimonios con fotos reales.
    </td>
  </tr>
</table>

<br>

<table border="1" cellpadding="8" cellspacing="0" style="width:100%; border-collapse: collapse;">
  <tr>
    <th colspan="2">Entrevista 2</th>
  </tr>
  <tr>
    <td><strong>Nombre:</strong></td>
    <td>Jeiner Gutierrez</td>
  </tr>
  <tr>
    <td><strong>Edad:</strong></td>
    <td>22 años</td>
  </tr>
  <tr>
    <td><strong>Distrito:</strong></td>
    <td>San Miguel, Lima</td>
  </tr>
  <tr>
    <td><strong>URL del video:</strong></td>
    <td>
      https://upcedupe-my.sharepoint.com/:v:/g/personal/u202320684_upc_edu_pe/IQDEv1eI_r-xRJyvWQAN297JASKBtzpyzOzNY5bDoFF41Ug?e=QL6zJY&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D <br>
      Timing: 02:00 <br>
      Duración: 12:44 minutos
    </td>
  </tr>
  <tr>
    <td><strong>Screenshot del video:</strong></td>
    <td><img src="assets/chapter04/entrevistas/Entrevista2S1.png"></td>
  </tr>
  <tr>
    <td colspan="2"><strong>Resumen de la entrevista:</strong></td>
  </tr>
  <tr>
    <td colspan="2">
      El entrevistado trabaja en una empresa, sale a comer fuera con regularidad y usa Rappi de forma ocasional sin una rutina definida de búsqueda de descuentos. Ha experimentado cupones vencidos en Rappi, lo que le genera una desconfianza moderada hacia ese tipo de promociones.Comprendió correctamente la propuesta del prototipo, aunque el término "comunidad que confía" le resultó vago en un primer momento y requirió continuar leyendo para entenderlo como una referencia a las reseñas verificadas. Se identificó con los dos primeros problemas planteados. El flujo de 4 pasos le pareció claro en general, pero el paso "Activar" no fue autoexplicativo por sí solo y consideró que podría tener un nombre más descriptivo. El testimonio de Lizbeth le pareció auténtico pero insuficiente al ser el único. Los números de la sección de estadísticas no captaron su atención. Destacó el historial de canjes y las reseñas verificadas como las funciones más útiles. Al igual que el perfil anterior, el CTA final de GitHub le generó confusión al asociarlo con herramientas para desarrolladores. Indicó que le daría una oportunidad a la app con una puntuación de 4/5, condicionada a la disponibilidad de negocios en su zona.

  </tr>
</table>

<br>

#### Segmento 2

<table border="1" cellpadding="8" cellspacing="0" style="width:100%; border-collapse: collapse;">
  <tr>
    <th colspan="2">Entrevista 3</th>
  </tr>
  <tr>
    <td><strong>Nombre:</strong></td>
    <td>Jesus Ponce</td>
  </tr>
  <tr>
    <td><strong>Edad:</strong></td>
    <td>30 años</td>
  </tr>
  <tr>
    <td><strong>Distrito:</strong></td>
    <td>Tarapot, San Martin</td>
  </tr>
  <tr>
    <td><strong>URL del video:</strong></td>
    <td>
      https://upcedupe-my.sharepoint.com/:v:/g/personal/u202320684_upc_edu_pe/IQA4Qkn4PLG2R6xp0VJXXFzFAS8Z1xc0gufsaGwU1fj3SnQ?e=ovZv4b&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D <br>
      Timing: 02:00 <br>
      Duración: 17:23 minutos
    </td>
  </tr>
  <tr>
    <td><strong>Screenshot del video:</strong></td>
    <td><img src="assets/chapter04/entrevistas/Entrevista1S2.png"></td>
  </tr>
  <tr>
    <td colspan="2"><strong>Resumen de la entrevista:</strong></td>
  </tr>
  <tr>
    <td colspan="2">
      El entrevistado gestiona un negocio de gastronomía con más de un local. Realiza promociones en Instagram y WhatsApp pero reconoce que no tiene ninguna forma de medir sus resultados. Ha sufrido pérdidas económicas reales por un código de descuento que se viralizó en Instagram y fue usado por más personas de las planificadas. Al ver el prototipo, identificó de forma inmediata la propuesta y su utilidad para su negocio. El enlace "¿Tienes un negocio?" lo encontró rápidamente y lo llevó directo a la sección correspondiente. La sección "Para tu negocio" y la tabla comparativa fueron los elementos que más lo convencieron, especialmente el dashboard con métricas y la posibilidad de pausar o editar campañas desde la app. El problema de "campaña a ciegas" resonó como una descripción exacta de su situación actual. Consideró que el prototipo genera suficiente confianza, valorando el proceso de aprobación por administrador como una señal de seriedad. Sin embargo, señaló que la ausencia de precios y de un testimonio de otro negocio afiliado son los dos elementos que frenan una decisión más rápida. El CTA final de GitHub le resultó confuso al esperar un botón de registro o contacto. Evaluó la probabilidad de afiliarse con un 4/5 y recomendó como cambio urgente agregar precios referenciales y testimonio de negocio.
    </td>
  </tr>
</table>

<br>

<table border="1" cellpadding="8" cellspacing="0" style="width:100%; border-collapse: collapse;">
  <tr>
    <th colspan="2">Entrevista 4</th>
  </tr>
  <tr>
    <td><strong>Nombre:</strong></td>
    <td>Harleen Palomino</td>
  </tr>
  <tr>
    <td><strong>Edad:</strong></td>
    <td>24 años</td>
  </tr>
  <tr>
    <td><strong>Distrito:</strong></td>
    <td>Puerto Maldonado, Madre de Dios</td>
  </tr>
  <tr>
    <td><strong>URL del video:</strong></td>
    <td>
      https://upcedupe-my.sharepoint.com/:v:/g/personal/u202320684_upc_edu_pe/IQCn8HytdOeKQLgLhrdeIJebAYXP7Hpce6f_Ipv8GiQPYa4?e=7jP0Uo&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D <br>
      Timing: 02:00 <br>
      Duración: 15:26 minutos
    </td>
  </tr>
  <tr>
    <td><strong>Screenshot del video:</strong></td>
    <td><img src="assets/chapter04/entrevistas/Entrevista2S2.png"></td>
  </tr>
  <tr>
    <td colspan="2"><strong>Resumen de la entrevista:</strong></td>
  </tr>
  <tr>
    <td colspan="2">
      El entrevistado gestiona un negocio de retail y realiza promociones esporádicas en redes sociales sin una estrategia estructurada. No ha tenido problemas graves de fraude, pero reconoce que su mayor dificultad es no saber si sus campañas generan resultados concretos. Comprendió la propuesta del prototipo con claridad, identificando el dashboard de métricas como el elemento de mayor valor para su negocio. El enlace hacia la sección de negocios lo encontró tarde, después de haber recorrido primero el contenido del consumidor, lo que le hizo preguntarse si habría una forma de llegar más rápido desde el perfil de negocio. El problema de "campaña a ciegas" resonó con su experiencia, aunque consideró que el prototipo explica bien el problema pero queda vago en cómo lo resuelve en la práctica. La confianza generada fue moderada, condicionada a no conocer la plataforma previamente y a la ausencia de ejemplos de negocios ya afiliados. El testimonio de Lizbeth le resultó insuficiente desde la perspectiva empresarial, ya que necesitaría ver resultados concretos de otro negocio similar. El CTA final de GitHub le generó confusión al no saber qué era y esperar un botón de contacto o registro. Evaluó la probabilidad de afiliarse con un 3/5 y recomendó reemplazar el CTA final y agregar precios o un formulario de contacto como cambios prioritarios.
    </td>
  </tr>
</table>

<br>

#### 4.3.3. Evaluaciones según heurísticas

## UX Heuristics & Principles Evaluation
### Usability - Inclusive Design - Information Architecture

---

| Campo | Detalle |
|---|---|
| **CARRERA** | Ingeniería de Software |
| **CURSO** | 1acc0238 Aplicaciones para dispositivos móviles |
| **SECCIÓN** | Código de la sección |
| **PROFESORES** | Todos |
| **AUDITOR** | Grupo 3 |
| **CLIENTE(S)** | Participantes Segmento 1 (S1-A, S1-B) · Participantes Segmento 2 (S2-A, S2-B) |

---

> **NOTA:** Esta evaluación toma como base las respuestas obtenidas en las entrevistas
> realizadas a 4 perfiles distribuidos en 2 segmentos: Jóvenes/Adultos (18–45 años)
> y Empresas Afiliadas. El objeto de evaluación es el **prototipo de la aplicación Klippr**,
> una plataforma de descuentos con canjes seguros mediante QR único por usuario.

---

**PROTOTIPO A EVALUAR:** Klippr — Aplicación móvil de descuentos y canjes seguros

---

## 1. TAREAS A EVALUAR

### 1.1 Tareas incluidas en esta evaluación

| # | Tarea | Segmento |
|---|---|---|
| 1 | Registro de un nuevo usuario (Consumer o Business) | Ambos |
| 2 | Búsqueda y exploración de promociones disponibles | S1 |
| 3 | Activación de un QR único para canjear una promoción | S1 |
| 4 | Guardado de una promoción en favoritos | S1 |
| 5 | Consulta de la lista de favoritos del usuario | S1 |
| 6 | Eliminación de un favorito guardado | S1 |
| 7 | Publicación de una campaña de descuento desde el perfil Business | S2 |
| 8 | Consulta del dashboard de métricas de una campaña activa | S2 |
| 9 | Uso del enlace de navegación hacia la sección de negocios | S2 |
| 10 | Comparación del prototipo frente a otras plataformas mediante la tabla comparativa | Ambos |

### 1.2 Tareas NO incluidas en esta evaluación

| # | Tarea excluida | Justificación |
|---|---|---|
| 1 | Compartir una promoción con otro usuario | Fuera del alcance del sprint actual |
| 2 | Responder reseñas públicas desde el perfil de negocio | No evaluado en las sesiones |
| 3 | Administrar múltiples campañas simultáneas | Funcionalidad no mostrada en el prototipo |
| 4 | Exportar métricas del dashboard | No contemplado en el prototipo evaluado |
| 5 | Gestión de perfil y configuración de cuenta | Fuera del flujo evaluado |

---

## 2. ESCALA DE SEVERIDAD

| Escala | Nivel | Descripción | Acción recomendada |
|---|---|---|---|
| **0** | Sin problema | No representa un problema de usabilidad | Ninguna |
| **1** | Cosmético | Problema menor de presentación | Corregir solo si hay tiempo disponible |
| **2** | Menor | Afecta la experiencia pero no bloquea al usuario | Baja prioridad de corrección |
| **3** | Mayor | Dificulta significativamente el uso del prototipo | Alta prioridad, corregir antes del lanzamiento |
| **4** | Catástrofe | Impide al usuario completar una tarea crítica | Imperativo corregir de inmediato |

---

## 3. TABLA DE RESUMEN DE PROBLEMAS ENCONTRADOS

| # | Problema detectado | Heurística violada | Segmento afectado | Severidad |
|---|---|---|---|---|
| 1 | El CTA final "Visita la App en GitHub" genera confusión en usuarios no técnicos que esperan un botón de descarga o registro | H4 — Consistencia y estándares | Ambos | **3** |
| 2 | Ausencia de información sobre precios y proceso de afiliación para negocios, bloqueando la evaluación del prototipo como negocio potencial | H10 — Ayuda y documentación | S2 | **3** |
| 3 | El paso "Activar" en el flujo de 4 pasos no es autoexplicativo sin leer su descripción completa | H6 — Reconocimiento antes que recuerdo | S1 | **2** |
| 4 | La sección de estadísticas muestra valores sin contexto o aparentemente en cero | H1 — Visibilidad del estado del sistema | Ambos | **2** |
| 5 | El término "comunidad que confía" en el título principal resultó abstracto para varios entrevistados | H2 — Coincidencia con el mundo real | S1 | **2** |
| 6 | La fila "UUID por cuenta+oferta" en la tabla comparativa no es comprensible para usuarios no técnicos | H2 — Coincidencia con el mundo real | Ambos | **2** |
| 7 | Solo existe un testimonio de usuario consumidor; el segmento de negocios necesita prueba social desde su propia perspectiva | H8 — Diseño estético y minimalista | S2 | **2** |
| 8 | El flujo de navegación hacia la sección de negocios no es visible de inmediato para perfiles empresariales | H7 — Flexibilidad y eficiencia de uso | S2 | **2** |
| 9 | No se muestran mensajes de error ni estados de fallo ante acciones incorrectas (QR ya usado, credenciales inválidas) | H9 — Recuperación ante errores | Ambos | **2** |
| 10 | No se detallan mecanismos para deshacer acciones como cancelar activación de QR o revertir una campaña publicada | H3 — Control y libertad del usuario | Ambos | **1** |
| 11 | Las filas de la tabla comparativa relacionadas a aspectos técnicos resultan poco relevantes para usuarios sin formación tecnológica | H2 — Coincidencia con el mundo real | S1 | **1** |
| 12 | El enlace "¿Tienes un negocio?" no compite visualmente con el contenido principal del consumidor | H4 — Consistencia y estándares | S2 | **1** |

---

## 4. EVALUACIÓN DETALLADA POR HEURÍSTICA

---

### H1 — Visibilidad del Estado del Sistema

> *El sistema debe mantener a los usuarios informados sobre lo que está ocurriendo, mediante retroalimentación apropiada y en tiempo razonable.*

#### Problemas detectados

| Problema | Evidencia de entrevista | Severidad |
|---|---|---|
| La sección de estadísticas del prototipo muestra valores que los entrevistados percibieron como vacíos o sin contexto, impidiendo comprender qué información está disponible | S1-B: *"Los números no los llegué a leer bien, pasé rápido por esa sección"* · S2-B: *"La landing lo explica bien como problema, pero quedó vago cómo lo resuelve en la práctica"* | **2** |
| No se comunica visualmente el estado del QR después de ser activado (si está disponible, usado o expirado) | Ningún entrevistado mencionó haber visto retroalimentación visual sobre el estado del QR | **2** |

#### Recomendaciones

| # | Recomendación |
|---|---|
| 1 | Mostrar valores reales o ejemplos representativos en la sección de estadísticas con etiquetas claras |
| 2 | Incluir estados visuales del QR: disponible, activo, canjeado y expirado |
| 3 | Agregar indicadores de progreso en los flujos de registro y activación |

---

### H2 — Coincidencia entre el Sistema y el Mundo Real

> *El sistema debe hablar el lenguaje del usuario, usando palabras, frases y conceptos familiares, en lugar de términos orientados al sistema.*

#### Problemas detectados

| Problema | Evidencia de entrevista | Severidad |
|---|---|---|
| El término "comunidad que confía" en el título principal resultó vago para varios entrevistados hasta que continuaron leyendo el prototipo | S1-B: *"El 'comunidad que confía' me quedó vago al inicio. Tuve que seguir leyendo para entender que se refería a las reseñas"* | **2** |
| La fila "UUID por cuenta+oferta" en la tabla comparativa es un tecnicismo incomprensible para el usuario promedio | S2-B: *"La de UUID por cuenta+oferta no quedó clara"* | **2** |
| Algunos términos de la tabla comparativa son técnicos y poco relevantes para usuarios sin formación tecnológica | S1-B: *"Algunas filas son un poco técnicas para un usuario normal"* | **1** |

#### Recomendaciones

| # | Recomendación |
|---|---|
| 1 | Reemplazar "comunidad que confía" por una frase más concreta como "reseñas de quienes sí canjearon" |
| 2 | Sustituir "UUID por cuenta+oferta" por "código único e intransferible por usuario" en la tabla comparativa |
| 3 | Revisar todas las filas técnicas de la tabla comparativa y reescribirlas en lenguaje cotidiano |

---

### H3 — Control y Libertad del Usuario

> *Los usuarios a menudo eligen funciones del sistema por error y necesitan una salida de emergencia claramente marcada para dejar el estado no deseado.*

#### Problemas detectados

| Problema | Evidencia de entrevista | Severidad |
|---|---|---|
| El prototipo no muestra claramente si el usuario puede cancelar la activación de un QR antes de presentarlo en el local | No fue mencionado por ningún entrevistado como funcionalidad visible | **1** |
| No se visualiza si un negocio puede revertir o pausar una campaña ya aprobada de forma intuitiva | S2-A: *"Lo de poder pausar o editar una campaña desde la app también"* — mencionado como expectativa, no como funcionalidad confirmada | **1** |

#### Recomendaciones

| # | Recomendación |
|---|---|
| 1 | Mostrar en el prototipo un botón de "cancelar activación" antes de confirmar el uso del QR |
| 2 | Visualizar claramente las opciones de pausar, editar y eliminar campañas desde el dashboard del negocio |

---

### H4 — Consistencia y Estándares

> *Los usuarios no deberían tener que preguntarse si diferentes palabras, situaciones o acciones significan lo mismo. Se deben seguir las convenciones de la plataforma.*

#### Problemas detectados

| Problema | Evidencia de entrevista | Severidad |
|---|---|---|
| El CTA final "Visita la App en GitHub" rompe la expectativa estándar de descarga o registro que los usuarios de ambos segmentos anticipaban al final de un prototipo de producto | S1-A: *"GitHub no es algo que use. Pensé que iba a haber un botón de descarga en la App Store"* · S1-B: *"Cuando vi GitHub pensé que era algo para desarrolladores"* · S2-A: *"GitHub suena a algo técnico, no a algo para quien gestiona un local"* · S2-B: *"No sabía qué era GitHub"* | **3** |
| El enlace "¿Tienes un negocio?" no tiene la misma jerarquía visual que el contenido dirigido al consumidor, afectando la consistencia de acceso para ambos perfiles | S2-B: *"Lo vi pero tarde, no fue lo primero que noté. Primero fui por el contenido del usuario"* | **1** |

#### Recomendaciones

| # | Recomendación |
|---|---|
| 1 | Reemplazar el CTA final por un botón de lista de espera, descarga o formulario de contacto según el estado de la app |
| 2 | Diferenciar visualmente el CTA para usuarios consumidores y para negocios al final del prototipo |
| 3 | Aumentar la visibilidad del enlace para negocios mediante un banner o sección separada en la parte superior |

---

### H5 — Prevención de Errores

> *Mejor que un buen mensaje de error es un diseño cuidadoso que prevenga que el problema ocurra en primer lugar.*

#### Problemas detectados

| Problema | Evidencia de entrevista | Severidad |
|---|---|---|
| El prototipo describe que el QR es único e intransferible, lo que previene el uso duplicado, pero no muestra validaciones visibles durante el registro o la activación | S1-A valoró positivamente el QR único como medida preventiva, pero no mencionó haber visto mensajes de validación en el flujo | **1** |

#### Recomendaciones

| # | Recomendación |
|---|---|
| 1 | Mostrar mensajes de validación en tiempo real durante el registro (campos obligatorios, formato de correo) |
| 2 | Visualizar un mensaje claro cuando un QR ya fue utilizado o ha expirado |

---

### H6 — Reconocimiento antes que Recuerdo

> *Se debe minimizar la carga de memoria del usuario haciendo visibles los objetos, acciones y opciones. El usuario no debería tener que recordar información de una parte del diálogo a otra.*

#### Problemas detectados

| Problema | Evidencia de entrevista | Severidad |
|---|---|---|
| El paso "Activar" en el flujo de 4 pasos requiere leer la descripción completa para comprender qué acción implica; el nombre por sí solo no es autoexplicativo | S1-B: *"El que menos entendí al primer vistazo fue 'Activar', no sabía exactamente qué implicaba hasta que leí la descripción. Quizás el nombre podría ser más descriptivo"* | **2** |

#### Recomendaciones

| # | Recomendación |
|---|---|
| 1 | Renombrar el paso "Activar" por algo más descriptivo como "Genera tu QR" o "Obtén tu código" |
| 2 | Incluir un ícono representativo junto a cada paso del flujo para reforzar el reconocimiento visual |

---

### H7 — Flexibilidad y Eficiencia de Uso

> *Los aceleradores — no vistos por el usuario novato — pueden agilizar la interacción para el usuario experto, permitiendo que el sistema satisfaga tanto a usuarios con experiencia como sin ella.*

#### Problemas detectados

| Problema | Evidencia de entrevista | Severidad |
|---|---|---|
| Un dueño de negocio debe recorrer todo el contenido del consumidor antes de encontrar la sección que le corresponde, reduciendo la eficiencia de navegación para ese perfil | S2-B: *"Me pregunto si habría una forma de llegar más rápido cuando eres un negocio"* | **2** |
| No existe un acceso directo desde el inicio del prototipo para perfiles empresariales que ya conocen la propuesta y quieren ir directo al registro | S2-A llegó al enlace rápido porque lo buscó activamente; S2-B lo encontró tarde de forma pasiva | **2** |

#### Recomendaciones

| # | Recomendación |
|---|---|
| 1 | Agregar una bifurcación de entrada al inicio del prototipo: "Soy consumidor" / "Tengo un negocio" |
| 2 | Implementar un menú de navegación con anclas a las secciones principales del prototipo |

---

### H8 — Diseño Estético y Minimalista

> *Los diálogos no deben contener información irrelevante o raramente necesaria. Cada unidad extra de información compite con la información relevante y disminuye su visibilidad relativa.*

#### Problemas detectados

| Problema | Evidencia de entrevista | Severidad |
|---|---|---|
| La presencia de un único testimonio de usuario consumidor no aporta prueba social suficiente, especialmente para el segmento de negocios que necesita ver resultados desde su propia perspectiva | S2-A: *"Faltó ver el testimonio de un negocio afiliado. Hay que saber qué resultados obtuvo alguien en la misma posición"* · S2-B: *"Como negocio hay que saber qué le pasó a otro local similar"* | **2** |

#### Recomendaciones

| # | Recomendación |
|---|---|
| 1 | Agregar al menos un testimonio de un negocio afiliado con métricas concretas (canjes logrados, aumento de visitas) |
| 2 | Complementar el testimonio existente con foto o avatar que refuerce la autenticidad |

---

### H9 — Ayudar a los Usuarios a Reconocer, Diagnosticar y Recuperarse de Errores

> *Los mensajes de error deben expresarse en lenguaje llano (sin códigos), indicar con precisión el problema y sugerir constructivamente una solución.*

#### Problemas detectados

| Problema | Evidencia de entrevista | Severidad |
|---|---|---|
| El prototipo no muestra mensajes de error ante escenarios de fallo como QR ya utilizado, credenciales incorrectas o campaña rechazada por el administrador | Ningún entrevistado mencionó haber visto estados de error en el prototipo | **2** |
| No se comunica qué ocurre si un negocio envía una campaña que no cumple los requisitos de aprobación | S2-A: *"El hecho de que mencionen un proceso de aprobación por administrador da tranquilidad, pero no quedó claro qué pasa si rechazan tu campaña"* | **2** |

#### Recomendaciones

| # | Recomendación |
|---|---|
| 1 | Diseñar y mostrar pantallas de error para los escenarios más frecuentes: QR expirado, cupón ya canjeado, credenciales inválidas |
| 2 | Incluir notificaciones claras cuando una campaña es rechazada, con indicación de la razón y pasos para corregirla |

---

### H10 — Ayuda y Documentación

> *Aunque es mejor que el sistema pueda usarse sin documentación, puede ser necesario proporcionar ayuda. Dicha información debe ser fácil de buscar, centrada en la tarea del usuario y concisa.*

#### Problemas detectados

| Problema | Evidencia de entrevista | Severidad |
|---|---|---|
| El prototipo no incluye información sobre precios ni costos de afiliación para negocios, siendo este dato crítico para la toma de decisión del segmento empresarial | S2-A: *"Lo que frena es no saber el costo; no vi nada de precios en la landing"* · S2-B: *"Lo que frena es no saber el precio ni si hay negocios similares ya en la plataforma"* | **3** |
| No existe un flujo visible de onboarding para negocios que quieran afiliarse; el siguiente paso después de leer el prototipo no es claro para ese segmento | S2-A: *"Al final cuando se quería saber cómo dar el siguiente paso para afiliarse, no había nada claro"* · S2-B misma observación | **3** |

#### Recomendaciones

| # | Recomendación                                                                                                        |
| - | -------------------------------------------------------------------------------------------------------------------- |
| 1 | Agregar una sección de precios o al menos un rango referencial para el segmento de negocios                          |
| 2 | Incluir un formulario de contacto o botón de "Quiero afiliar mi negocio" como CTA específico para S2                 |
| 3 | Crear una sección de preguntas frecuentes orientada a negocios con dudas sobre el proceso de aprobación y comisiones |

---

## 5. CONSOLIDADO FINAL POR SEVERIDAD

| Severidad            | Cantidad de problemas | Heurísticas afectadas                |
| -------------------- | --------------------- | ------------------------------------ |
| **3 — Mayor**        | 3                     | H4, H10                              |
| **2 — Menor**        | 8                     | H1, H2, H3, H6, H7, H8, H9           |
| **1 — Cosmético**    | 3                     | H3, H4, H5                           |
| **0 — Sin problema** | —                     | H5 (QR único como medida preventiva) |

---

## 6. CONCLUSIONES

| Dimensión | Hallazgo |
|---|---|
| **Fortalezas identificadas** | La sección de identificación de problemas, el flujo de 4 pasos y la tabla comparativa fueron los elementos más valorados por ambos segmentos. El concepto del QR único fue comprendido y valorado de forma unánime como el diferencial principal del producto. |
| **Problemas críticos** | El CTA final (H4) y la ausencia de información de precios y proceso de afiliación para negocios (H10) son los bloqueadores de mayor impacto y deben corregirse con prioridad antes del siguiente ciclo de validación. |
| **Problemas moderados** | La terminología técnica (H2), la visibilidad del estado del sistema (H1), la eficiencia de navegación para negocios (H7) y la insuficiencia de prueba social (H8) afectan la experiencia pero no bloquean completamente al usuario. |
| **Próximos pasos recomendados** | Corregir H4 y H10, incorporar testimonio de negocio afiliado, reescribir términos técnicos en lenguaje cotidiano y añadir estados de error visuales antes del siguiente ciclo de pruebas con usuarios. |