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
* **Flutter SDK**: Framework de código abierto de Google para crear aplicaciones multiplataforma (Android, iOS, Web) desde una sola base de código en Dart. https://flutter.dev/
* **Dart**: Lenguaje de programación optimizado para la creación de aplicaciones en Flutter, con tipado fuerte y soporte para programación asíncrona. https://dart.dev/

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
* Klippr Business: https://github.com/QRustOrg/Klippr-Business

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

**Flutter y Dart**:

Para el desarrollo de **Klippr Business** (aplicación para negocios), se utilizó **Flutter** con **Dart**. Las siguientes pautas aseguran consistencia y legibilidad en el código:

**Nomenclatura General**:

Para los nombres de variables y funciones se empleará **camelCase**. **PascalCase** se utilizará para los nombres de clases y widgets.

```dart
// Variables y funciones (camelCase)
final String userName;
void getUserName() {}

// Clases y widgets (PascalCase)
class User {}
class HomeScreen extends StatelessWidget {}
```

**Widgets**:

Los widgets deben ser funciones puras siempre que sea posible. Se prefiere `StatelessWidget` sobre `StatefulWidget` a menos que se requiera estado local.

```dart
class PromotionCard extends StatelessWidget {
  final Promotion promotion;
  
  const PromotionCard({super.key, required this.promotion});

  @override
  Widget build(BuildContext context) {
    return Card(
      child: Text(promotion.title),
    );
  }
}
```

**Clean Architecture en Flutter**:

El proyecto sigue una arquitectura en capas **Domain**, **Data** y **Presentation**:

* **Domain Layer**: Contiene las entidades del negocio y casos de uso.
* **Data Layer**: Gestiona repositorios y fuentes de datos (API, base de datos local).
* **Presentation Layer**: Maneja la lógica de interfaz mediante **BLoC** o **Provider** y widgets.

```dart
// Domain Layer - Entity
class BusinessUser {
  final String id;
  final String businessName;
  final String email;
  
  BusinessUser({
    required this.id,
    required this.businessName,
    required this.email,
  });
}

// Data Layer - Repository
class BusinessRepository {
  Future<List<Promotion>> getPromotions(String businessId) async {
    // Implementación con llamada a API
  }
}

// Presentation Layer - Widget
class BusinessHomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Klippr Business')),
      body: Center(child: Text('Bienvenido')),
    );
  }
}
```

**Resultado visual de las convenciones aplicadas**:

A continuación se muestran las pantallas de **Klippr Business** desarrolladas siguiendo estas convenciones:

![Klippr Business - Home](assets/chapter04/klippr-bussiness/klippr-business-home.png)

![Klippr Business - Crear Promoción](assets/chapter04/klippr-bussiness/klippr-business-promotion-create-view.png)

![Klippr Business - Crear Promoción - Paso 1](assets/chapter04/klippr-bussiness/klippr-business-promotion-create-view-1.png)

![Klippr Business - Crear Promoción - Paso 2](assets/chapter04/klippr-bussiness/klippr-business-promotion-create-view-2.png)

![Klippr Business - Editor](assets/chapter04/klippr-bussiness/klippr-business-editor-view.png)

![Klippr Business - Promociones Activas](assets/chapter04/klippr-bussiness/klippr-active-promotions.png)

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

![Vercel-Dashboard](assets/chapter04/vercel-deploy/vercel-dashboard.png)

En esta pantalla seleccionamos el repositorio de **Landing Page** ***(Klippr-Landing-Page)*** y posteriormente, seleccionamos el botón **"Import"**.

![Selecting-Repository](assets/chapter04/vercel-deploy/selecting-repo.png)

A continuación, la plataforma nos muestra un resumen de la configuración de despliegue, donde confirmamos que el proyecto está configurado correctamente y seleccionamos el botón **"Deploy"**.

![Pre-Deploy](assets/chapter04/vercel-deploy/pre-deploy.png)

Luego de pulsar en **"Deploy"**, **Vercel** iniciará el proceso de despliegue. Una vez finalizado el proceso, se mostrará un dashboard con algunos datos del proyecto.

![Success-Deploy](assets/chapter04/vercel-deploy/deploy-dashboard.png)

Finalmente, si todo ha ido bien, podremos acceder a la **Landing Page** desplegada en la URL asignada por **Vercel**.

![Deploy-Final](assets/chapter04/vercel-deploy/deploy.png)

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

![Hero Section](assets/chapter04/execution-evidence/landing-page/klippr-hero.png)

**Problem Section**:

En esta sección se expone la problemática principal que nuestros usuarios enfrentan, generando empatía y resaltando la necesidad de nuestra solución.

![Problem Section](assets/chapter04/execution-evidence/landing-page/klippr-problem.png)

**How It Works Section**:

En esta sección se detalla el funcionamiento paso a paso de la aplicación, guiando al visitante de forma sencilla sobre cómo empezar a utilizarla.

![How It Works Section](assets/chapter04/execution-evidence/landing-page/klippr-howitworks.png)

**Benefits Bussiness Section**:

En esta sección se destacan los beneficios que Klippr ofrece a los negocios asociados, incentivándolos a afiliarse y aumentar sus ventas.

![Benefits Bussiness Section](assets/chapter04/execution-evidence/landing-page/klippr-benefits-bussiness.png)

**Benefits Client Section**:

En esta sección se muestran las ventajas principales para los usuarios finales, enfatizando el ahorro y la conveniencia que brinda la plataforma.

![Benefits Client Section](assets/chapter04/execution-evidence/landing-page/klippr-benefits-client.png)

**Testimonials Section**:

En esta sección se presentan opiniones y experiencias reales de usuarios, generando confianza en el producto mediante validación social.

![Testimonials Section](assets/chapter04/execution-evidence/landing-page/klippr-testimonials.png)

**Comparison Section**:

En esta sección se realiza una comparativa frente a otras alternativas, subrayando nuestra propuesta de valor y ventajas competitivas.

![Comparison Section](assets/chapter04/execution-evidence/landing-page/klippr-comparison.png)

**Footer Section**:

En esta sección se ubican los enlaces finales de navegación, información de contacto y políticas de privacidad para facilitar el soporte al usuario.

![Footer Section](assets/chapter04/execution-evidence/landing-page/klippr-footer.png)

**Backend**

A continuación se muestran evidencias del backend desplegado y todos los endpoints desarrollados:

![Backend-1](assets/chapter04/execution-evidence/backend/backend-1.png)

![Backend-2](assets/chapter04/execution-evidence/backend/backend-2.png)

![Backend-3](assets/chapter04/execution-evidence/backend/backend-3.png)

![Backend-4](assets/chapter04/execution-evidence/backend/backend-4.png)

**Mobile App**

![Mobile App](assets/chapter04/execution-evidence/mobile/klippr-mobile-1.png)

![Mobile App-2](assets/chapter04/execution-evidence/mobile/klippr-mobile-2.png)

![Mobile App-3](assets/chapter04/execution-evidence/mobile/klippr-mobile-3.png)

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

![promotion-evidence-1](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-promotion-1.png)

### 1. Gestion de Promociones (Promotion)

El controlador de **Promotion** expone las funcionalidades críticas para el ciclo de vida de las ofertas:

* **Endpoints de Promociones**: Permite a las empresas gestionar sus campañas y a los usuarios visualizarlas.

- **Creación y Gestión de Ofertas** 

![promotion-evidence-2](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-promotion-2.png)

- **Detalles de la Promoción**

![promotion-evidence-3](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-promotion-3.png)

- **Visualización y Búsqueda**

![promotion-evidence-4](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-promotion-4.png)

- **Actualización de Estados**

![promotion-evidence-5](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-promotion-5.png)

- **Eliminación y Limpieza**

![promotion-evidence-6](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-promotion-6.png)

![promotion-evidence-7](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-promotion-7.png)

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

![redemption-evidence-1](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-1.png)

### 1. Gestion de Canjes (Redemption)

El controlador de **Redemption** expone las funcionalidades esenciales para la validación y ejecución del canje:

* **Endpoints de Canjes**: Facilitan la interacción segura entre la solicitud del consumidor y la aprobación del sistema.

- **Proceso de Canje (Redemption Process)** 

![redemption-evidence-2](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-2.png)

- **Validación de Parámetros**

![redemption-evidence-3](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-3.png)

- **Historial de Redenciones**

![redemption-evidence-4](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-4.png)

- **Verificación de Códigos**

![redemption-evidence-5](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-5.png)

- **Confirmación de Éxito**

![redemption-evidence-6](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-6.png)

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

![iam-profile](assets/chapter04/vercel-deploy/evidences-sprint/iam/iambc.png)

### 1. Gestion de Identidad y Acceso (IAM)

El controlador de **Authentication** expone las funcionalidades criticas para el ciclo de vida del usuario:

* **POST `/api/Authentication/sign-in`**: Permite a los usuarios existentes obtener un token de acceso mediante sus credenciales.
* **POST `/api/Authentication/sign-up/consumer`**: Proceso de registro optimizado para el usuario final (Consumer), vinculando la identidad con su perfil correspondiente.
* **POST `/api/Authentication/sign-up/business`**: Registro especializado para entidades de negocio, activando las reglas de validacion propias de este sector.

- **Validacion parametro Post** 

![iam-profile](assets/chapter04/vercel-deploy/evidences-sprint/iam/pro2.png)

- **Registration Process**

![iam-profile](assets/chapter04/vercel-deploy/evidences-sprint/iam/iaproc.png)

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

![sw-bcprofile](assets/chapter04/vercel-deploy/evidences-sprint/profile/bcpro.png)

- **Validacion parametro Post** 

![sw-bcprofile](assets/chapter04/vercel-deploy/evidences-sprint/profile/post-parameter.png)

- **Company Profile** 

![sw-bcprofile](assets/chapter04/vercel-deploy/evidences-sprint/profile/emplog.png)

- **User Profile** 

![sw-bcprofile](assets/chapter04/vercel-deploy/evidences-sprint/profile/userlog.png)

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

![communityn-evidence-1](assets/chapter04/execution-evidence/backend/community/klippr-community-1.png)

### 1. Gestion de Comunidad (Community)

El controlador de **Community** expone las funcionalidades esenciales para la interacción entre consumidores y negocios:

* **Endpoints de Comunidad**: Facilitan la interacción segura entre usuarios y dueños de negocio dentro de la plataforma.

- **Publicación de Comentarios (Community Process)** 

![communityn-evidence-2](assets/chapter04/execution-evidence/backend/community/klippr-community-2.png)

- **Validación de Contenido**

![community-evidence-3](assets/chapter04/execution-evidence/backend/community/klippr-community-3.png)

- **Gestión de Calificaciones y Reseñas**

![community-evidence-4](assets/chapter04/execution-evidence/backend/community/klippr-community-4.png)

- **Editar Contenido**

![community-evidence-5](assets/chapter04/execution-evidence/backend/community/klippr-community-5.png)

![community-evidence-6](assets/chapter04/execution-evidence/backend/community/klippr-community-6.png)

- **Eliminar Calificaciones y Reseñas**

![community-evidence-6](assets/chapter04/execution-evidence/backend/community/klippr-community-7.png)

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

![setting-evidence-1](assets/chapter04/execution-evidence/backend/setting/klippr-setting-1.png)

### 1. Gestion de Comunidad (Settings)

El controlador de **Settings** expone las funcionalidades esenciales para la administración de preferencias y parámetros de la plataforma:

* **Endpoints de Settings**: Facilitan la actualización y consulta segura de ajustes relacionados con usuarios y negocios.

- **Creacion de comentarios (Settings Process)** 

![setting-evidence-2](assets/chapter04/execution-evidence/backend/setting/klippr-setting-2.png)

- **Validación de Configuraciones**

![setting-evidence-3](assets/chapter04/execution-evidence/backend/community/klippr-community-3.png)

- **Gestión de Parámetros de Negocio**

![setting-evidence-4](assets/chapter04/execution-evidence/backend/community/klippr-community-4.png)

- **Actualización de Preferencias**

![setting-evidence-5](assets/chapter04/execution-evidence/backend/community/klippr-community-5.png)

![setting-evidence-6](assets/chapter04/execution-evidence/backend/community/klippr-community-6.png)

- **Eliminar Configuracion**

![setting-evidence-6](assets/chapter04/execution-evidence/backend/community/klippr-community-7.png)

# Favorites Bounded Context

Como parte del desarrollo del backend en **C#**, se ha consolidado el Bounded Context de **Favorites**. Este módulo permite a los usuarios guardar promociones de interés para consultarlas posteriormente, facilitando el seguimiento de ofertas relevantes y mejorando la experiencia de descubrimiento.

### Implementación Técnica de Favorites
Se ha utilizado **ASP.NET Core** junto con **Entity Framework Core** y **SQLite** para garantizar la persistencia y recuperación eficiente de los favoritos. Los logros principales incluyen:

* **Guardado de Promociones:** Implementación de un flujo de guardado que valida duplicados, asegurando que un usuario no pueda guardar la misma promoción más de una vez.
* **Consulta por Usuario:** Un servicio de consulta que recupera todas las promociones guardadas asociadas a un usuario específico.
* **Eliminación Segura:** Aplicación de reglas de dominio que garantizan que solo el propietario del favorito pueda eliminarlo.


## Evidencias de Ejecución: Módulo Favorites

A continuación se presentan los endpoints desarrollados y testeados a través de la interfaz de Swagger:

![favorites-swagger](assets/chapter04/execution-evidence/backend/favorites/POST1favorites.png)

### 1. Gestión de Favoritos

El controlador de **Favorites** expone las funcionalidades críticas para el ciclo de vida de un favorito:

* **POST `/api/v1/favorites`**: Permite a un usuario guardar una promoción como favorita. Retorna **201 Created** con los datos del favorito creado.
* **GET `/api/v1/favorites/user/{userId}`**: Recupera la lista completa de promociones guardadas por un usuario específico.
* **GET `/api/v1/favorites/{id}`**: Obtiene un favorito específico mediante su identificador interno.
* **DELETE `/api/v1/favorites/{favoriteId}`**: Elimina una promoción de la lista de favoritos del usuario. Solo el propietario puede realizar esta acción.

- **Validación parámetro Post**

![favorites-post](assets/chapter04/execution-evidence/backend/favorites/POST1favorites.png)

- **Registration Process**

![favorites-process](assets/chapter04/execution-evidence/backend/favorites/GETID1favorites.png)
![favorites-process](assets/chapter04/execution-evidence/backend/favorites/GETID2favorites.png)
![favorites-process](assets/chapter04/execution-evidence/backend/favorites/GETUSERID1favorites.png)
![favorites-process](assets/chapter04/execution-evidence/backend/favorites/GETUSERID2favorites.png)

### Notas de Integración
El Bounded Context de Favorites es completamente independiente: no depende de los Bounded Contexts de **Profile** ni de **Promotions** directamente. La comunicación con otros contextos se realiza únicamente a través de la **FavoritesContextFacade**, que expone operaciones de solo lectura mediante primitivos, garantizando el aislamiento del dominio.

# Notifications Bounded Context

Como parte del desarrollo del backend en **C#**, se ha consolidado el Bounded Context de **Notifications**. Este módulo permite gestionar notificaciones para los usuarios de la plataforma, informándoles sobre eventos relevantes como canjes generados, favoritos añadidos y promociones por vencer, mejorando la comunicación y experiencia dentro de la app.

### Implementación Técnica de Notifications
Se ha utilizado **ASP.NET Core** junto con **Entity Framework Core** y **MySQL** para garantizar la persistencia y recuperación eficiente de las notificaciones. Los logros principales incluyen:

* **Creación de Notificaciones:** Implementación de un flujo de creación que registra eventos del sistema como `RedemptionGenerated`, `RedemptionExpiring` y `FavoriteAdded`, asociándolos a un usuario específico.
* **Consulta por Usuario:** Un servicio de consulta que recupera todas las notificaciones de un usuario, con soporte para filtrar únicamente las no leídas mediante el parámetro `unreadOnly`.
* **Marcado como Leída:** Operación que permite marcar una notificación individual como leída, actualizando su estado en base de datos.
* **Marcado Masivo:** Operación que marca todas las notificaciones de un usuario como leídas en una sola llamada.
* **Eliminación Segura:** Aplicación de reglas de dominio que garantizan que solo el propietario de la notificación pueda eliminarla.


## Evidencias de Ejecución: Módulo Notifications

A continuación se presentan los endpoints desarrollados y testeados a través de la interfaz de Swagger:

![notifications-swagger](assets/chapter04/execution-evidence/backend/notifications/POST1Notifications.png)

### 1. Gestión de Notificaciones

El controlador de **Notifications** expone las funcionalidades críticas para el ciclo de vida de una notificación:

* **POST `/api/v1/Notifications`**: Permite crear una notificación para un usuario. Retorna **201 Created** con los datos de la notificación creada, incluyendo su `notificationId`, tipo, título, mensaje y estado de lectura.
* **GET `/api/v1/Notifications/user/{userId}`**: Recupera la lista completa de notificaciones de un usuario específico, incluyendo el conteo total y el conteo de no leídas. Soporta el parámetro opcional `?unreadOnly=true`.
* **PATCH `/api/v1/Notifications/{notificationId}/read`**: Marca una notificación específica como leída. Retorna **204 No Content** al completarse exitosamente.
* **PATCH `/api/v1/Notifications/user/{userId}/read-all`**: Marca todas las notificaciones de un usuario como leídas en una sola operación. Retorna **204 No Content**.
* **DELETE `/api/v1/Notifications/{notificationId}`**: Elimina una notificación. Solo el propietario puede realizar esta acción. Retorna **204 No Content**.

- **Validación POST - Creación de Notificación**

![notifications-post](assets/chapter04/execution-evidence/backend/notifications/POST1notifications.png)

- **Registro y Consulta**

![notifications-get-user](assets/chapter04/execution-evidence/backend/notifications/GET1notifications.png)
![notifications-get-user](assets/chapter04/execution-evidence/backend/notifications/GET2notifications.png)

- **Marcado de Notificación como Leída**

![notifications-patch-read](assets/chapter04/execution-evidence/backend/notifications/PATCH1notifications.png)
![notifications-patch-read](assets/chapter04/execution-evidence/backend/notifications/PATCH2notifications.png)

- **Eliminación de Notificación**

![notifications-delete](assets/chapter04/execution-evidence/backend/notifications/DELETE1notifications.png)

### Notas de Integración
El Bounded Context de Notifications es completamente independiente: no depende directamente de otros Bounded Contexts. Las notificaciones son generadas por eventos de la aplicación cliente (canjes, favoritos, vigencia de promociones) y se persisten localmente en la tabla `NotificationItem`. La comunicación con otros contextos, de requerirse en el futuro, se realizaría únicamente a través de una fachada dedicada, garantizando el aislamiento del dominio.

##### 4.2.1.7. Software Deployment Evidence for Sprint Review

**Evidencias del despliegue de Landing Page**

En esta sección se muestran las evidencias del **despliegue de Landing Page** desarrollada con **Next.js, React y TypeScript**

**Url: https://klippr-landing-page.vercel.app/**

![Vercel Deploy](assets/chapter04/vercel-deploy/deploy-dashboard.png)

![Landing-Page](assets/chapter04/vercel-deploy/deploy.png)

**Evidencias del despliegue de Backend**

El Backend ha sido desarrollado con **C#** y **ASP.NET Core**, utilizando **JWT (JSON Web Tokens)** para la autenticación y autorización. Se encuentra desplegado en **Railway**.

**Url: https://klippr-backend-production.up.railway.app/swagger/index.html**

![Railway](assets/chapter04/deployment-evidence/railway-1.png)

Para el despliegue del Web Service se seleccionó **Railway**, una plataforma en la nube que se integró de forma directa con nuestro repositorio de **GitHub**. Esta conexión garantiza la automatización completa del flujo de despliegue, de modo que cada nueva actualización en el código fuente se refleje de inmediato en el entorno de producción.

**Railway** destaca por ofrecer una configuración intuitiva y escalable, resultando idónea para servicios backend y arquitecturas basadas en APIs. Mediante su panel de control, se logró vincular el repositorio del proyecto, establecer las variables de entorno requeridas y ejecutar el despliegue de forma ágil, eliminando la dependencia de herramientas de terceros o configuraciones complejas desde el IDE.

![Railway](assets/chapter04/deployment-evidence/railway-2.png)

La imagen muestra el entorno de producción en Railway, donde el backend fue desplegado correctamente. Estado: El mensaje “Deployment successful” confirma que el despliegue se realizó sin errores.

![Backend-1](assets/chapter04/execution-evidence/backend/backend-1.png)

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

Segmento Objetivo 1: Usuario consumidor (B2C)

Evidencias de Ejecución: Módulo IAM (Customer Views)

A continuación se presentan las capturas de pantalla de la aplicación móvil que demuestran el funcionamiento del módulo de IAM integrado con el backend:

Pantalla de Login and Sign-up— Opción para sign up and start session 

Desde la pantalla de Login, el usuario puede acceder al módulo de IAM de la aplicación móvil. En esta vista se presentan las opciones principales de autenticación: **Sign up**, que permite registrar una nueva cuenta de usuario, y **Start session**, que habilita el inicio de sesión mediante credenciales previamente registradas. Esta pantalla constituye el punto de entrada al flujo de autenticación integrado con el backend, permitiendo validar la identidad del usuario y acceder a las funcionalidades protegidas de la aplicación.

![sign-up](assets/chapter04/execution-evidence/backend/IAM/sign-up.png)

![login](assets/chapter04/execution-evidence/backend/IAM/login.png)

Pantalla de Reset password

![forgotten](assets/chapter04/execution-evidence/backend/IAM/forgotten.png)

Evidencias de Ejecución: Módulo Profile (Customer Views)

Pantalla Profile-data

Desde la pantalla **Profile-data**, el usuario puede visualizar y completar la información asociada a su perfil dentro de la aplicación móvil. Esta vista permite registrar o actualizar datos personales necesarios para la identificación del usuario, manteniendo la información vinculada a su cuenta autenticada mediante el módulo de IAM. Asimismo, la pantalla se integra con el backend para almacenar y recuperar los datos del perfil, garantizando que la información del usuario se mantenga disponible durante el uso de las funcionalidades de la aplicación.

![profile-info](assets/chapter04/execution-evidence/backend/IAM/profile-info.png)

Pantalla Configuracion-Options para updating user parameters

Desde la pantalla **Configuración - Options**, el usuario puede acceder a las opciones disponibles para actualizar los parámetros asociados a su cuenta dentro de la aplicación móvil. Esta vista permite gestionar preferencias y datos configurables del usuario, facilitando la modificación de información personal o ajustes relacionados con su perfil. Los cambios realizados son procesados mediante la integración con el backend, asegurando que los parámetros actualizados se almacenen correctamente y se mantengan vinculados al módulo de IAM.

![dashb](assets/chapter04/execution-evidence/backend/IAM/dashb.png)

![options](assets/chapter04/execution-evidence/backend/IAM/options.png)

Pantalla Edit profile

Desde la pantalla **Edit profile**, el usuario puede modificar la información registrada previamente en su perfil dentro de la aplicación móvil. Esta vista permite actualizar datos personales asociados a la cuenta, como nombres, apellidos, información de contacto u otros campos requeridos por el sistema. Los cambios realizados son enviados al backend para su validación y almacenamiento, asegurando que la información del usuario se mantenga actualizada y vinculada correctamente al módulo de IAM.

![edit-profile](assets/chapter04/execution-evidence/backend/IAM/edit-profile.png)

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

![Backend-1](assets/chapter04/sprint2-backend/backend-1.png)

![Backend-2](assets/chapter04/sprint2-backend/backend-2.png)

![Backend-3](assets/chapter04/sprint2-backend/backend-3.png)

![Backend-4](assets/chapter04/sprint2-backend/backend-4.png)

![Backend-5](assets/chapter04/sprint2-backend/backend-5.png)

![Backend-6](assets/chapter04/sprint2-backend/backend-6.png)

![Backend-7](assets/chapter04/sprint2-backend/backend-7.png)

### Klippr Business App

A continuación se presentan las evidencias de la aplicación **Klippr Business** desarrollada en **Flutter** para el segmento de negocios, permitiendo a los dueños de negocio gestionar sus promociones y campañas desde su dispositivo móvil.

#### Home

Desde la pantalla principal **Home**, el negocio puede visualizar un resumen de sus promociones activas, métricas clave de rendimiento y acceso rápido a las funcionalidades principales de la plataforma. Esta vista constituye el punto de entrada a la aplicación, concentrando la información más relevante para la gestión del negocio.

![Klippr Business - Home](assets/chapter04/klippr-bussiness/klippr-business-home.png)

#### Creación de Promociones

La vista **Crear Promoción** permite al negocio registrar nuevas ofertas dentro de la plataforma. A través de un formulario estructurado, el usuario puede definir el título, descripción, porcentaje de descuento, fechas de vigencia y cantidad disponible de la promoción.

![Klippr Business - Crear Promoción](assets/chapter04/klippr-bussiness/klippr-business-promotion-create-view.png)

**Paso 1 — Información Básica**: En esta primera etapa, el negocio ingresa los datos generales de la promoción, incluyendo nombre, descripción y categoría.

![Klippr Business - Crear Promoción - Paso 1](assets/chapter04/klippr-bussiness/klippr-business-promotion-create-view-1.png)

**Paso 2 — Condiciones y Restricciones**: En esta segunda etapa, el negocio configura las condiciones de uso, fechas de vigencia y límites de la promoción.

![Klippr Business - Crear Promoción - Paso 2](assets/chapter04/klippr-bussiness/klippr-business-promotion-create-view-2.png)

#### Editor de Promociones

Desde la vista **Editor**, el negocio puede modificar los datos de una promoción existente, permitiendo actualizar información como descripción, fechas de vigencia, descuento y estado de la oferta. Los cambios realizados son enviados al backend para su validación y almacenamiento.

![Klippr Business - Editor](assets/chapter04/klippr-bussiness/klippr-business-editor-view.png)

#### Promociones Activas

La pantalla **Promociones Activas** lista todas las ofertas vigentes del negocio, mostrando información relevante como el nombre, estado, fechas y cantidad de canjes realizados. Esta vista permite al negocio monitorear el desempeño de sus campañas y gestionar su portafolio de promociones de manera eficiente.

![Klippr Business - Promociones Activas](assets/chapter04/klippr-bussiness/klippr-active-promotions.png)

##### 4.2.2.6. Services Documentation Evidence for Sprint Review

Tras culminar el Sprint 2, se completó el desarrollo de los endpoints del backend, consolidando la lógica de negocio y la arquitectura funcional de **Klippr**. En esta iteración se trabajó principalmente en la implementación de los bounded contexts de **Authentication**, **Favorites**, **Promotion**, **Redemption**, **Users** y **Profile**, los cuales se encuentran desplegados en **Railway** y disponibles para su consumo mediante la API. A continuación, se presentan las evidencias correspondientes a la documentación de los endpoints implementados:

## IAM Bounded Context

Como parte del desarrollo del backend, se ha consolidado el Bounded Context de **IAM**. Este módulo es fundamental para la gestión de identidad y acceso dentro de la plataforma, encargado de administrar el registro de usuarios, el inicio de sesión, la autenticación mediante credenciales, la generación de tokens y la protección de los recursos disponibles en la aplicación.

**Implementación Técnica de IAM**

Se ha estructurado la lógica para permitir que los usuarios puedan registrarse, autenticarse y acceder de forma segura a las funcionalidades protegidas del sistema. Asimismo, se garantiza la integración entre la aplicación móvil y el backend mediante mecanismos de validación de identidad y control de acceso. Los logros principales incluyen:

**Registro de Usuarios:** Implementación del flujo de creación de cuentas, permitiendo almacenar la información necesaria del usuario y asociarla a una identidad válida dentro del sistema.

**Inicio de Sesión:** Desarrollo del proceso de autenticación mediante credenciales, validando el correo electrónico y la contraseña del usuario antes de permitir el acceso a la aplicación.

**Generación de Token JWT:** Implementación de la emisión de tokens de autenticación para mantener sesiones seguras y permitir el consumo de endpoints protegidos desde la aplicación móvil.

**Validación de Credenciales:** Control de acceso mediante la verificación de los datos ingresados por el usuario, asegurando que solo usuarios registrados y autenticados puedan ingresar al sistema.

**Gestión de Perfil de Usuario:** Integración de funcionalidades para consultar, registrar y actualizar información asociada al perfil del usuario autenticado.

**Protección de Endpoints:** Configuración de mecanismos de autorización para restringir el acceso a recursos sensibles del backend, garantizando que las operaciones protegidas solo puedan ser ejecutadas por usuarios autenticados.

**Integración con la Aplicación Móvil:** Conexión del módulo IAM con las pantallas de Login, Sign up, Profile-data, Edit profile y Configuración, permitiendo que los flujos de autenticación y actualización de datos funcionen correctamente desde el cliente móvil.

---

## Evidencias de Ejecución: Módulo IAM (Reviews)

A continuación se presentan los endpoints desarrollados y testeados a través de la interfaz de Swagger:

![admin-profile](assets/chapter04/execution-evidence/backend/IAM/adminprof.png)

![auth](assets/chapter04/execution-evidence/backend/IAM/auth.png)

Dentro del Bounded Context de IAM también se implementaron endpoints orientados a la gestión y consulta de usuarios. Estos permiten obtener información de un usuario mediante su identificador, realizar búsquedas por correo electrónico, listar usuarios registrados y filtrar usuarios según su rol. Dichos endpoints forman parte del control de identidad y acceso de la plataforma, ya que permiten administrar la información asociada a las cuentas registradas y verificar los roles vinculados a cada usuario autenticado.

![bcusers](assets/chapter04/execution-evidence/backend/IAM/bcus.png)

![getlistusers](assets/chapter04/execution-evidence/backend/IAM/getlistus.png)

Implementation of Reset Password

![reset](assets/chapter04/execution-evidence/backend/IAM/reset.png)

## Evidencias de Ejecución: Módulo Profile (Reviews)

A continuación se presentan las capturas de pantalla de la aplicación móvil que demuestran el funcionamiento del módulo Profile, específicamente en la integración con las reseñas publicadas por el usuario. Este flujo permite visualizar la relación entre el perfil autenticado y las interacciones realizadas dentro de la plataforma, como la consulta de reseñas asociadas, la publicación de opiniones y la gestión de información vinculada a la experiencia del usuario.

Las evidencias muestran cómo el usuario, desde su perfil, puede acceder a información relacionada con sus actividades dentro de la aplicación, incluyendo las reseñas generadas a partir de promociones canjeadas. De esta manera, se valida la correcta integración entre el módulo de perfil, el módulo de comunidad y el backend, garantizando que la información mostrada corresponda al usuario autenticado.

![bcprofile](assets/chapter04/execution-evidence/backend/IAM/bcprof.png)

Validaciones endopints

POST /api/profiles/consumer: Crea el perfil de un cliente consumidor usando el usuario autenticado.

![post-cons](assets/chapter04/execution-evidence/backend/profile/post-cons.png)


GET /api/profiles/consumer/{profileId}: Obtiene el perfil de consumidor asociado a un usuario.

![get-cons](assets/chapter04/execution-evidence/backend/profile/get-consu.png)

PUT /api/profiles/consumer: Actualiza los datos del perfil de consumidor.

![put-cons](assets/chapter04/execution-evidence/backend/profile/put-con.png)


GET /api/admin/profiles/by-user/{userId}: Obtiene el perfil de un usuario, sea consumidor o negocio.

![get-role](assets/chapter04/execution-evidence/backend/profile/get-role.png)

## Promotion Bounded Context

Como parte del desarrollo del backend en **C#**, se ha consolidado el Bounded Context de **Promotion**, módulo encargado de la administración de promociones dentro de **Klippr**. Este componente permite a los negocios crear y gestionar ofertas que posteriormente serán visualizadas y utilizadas por los usuarios de la plataforma.

### Implementacion Tecnica de Promotion

Se ha estructurado la lógica para permitir que los negocios definan promociones con diferentes reglas de negocio y restricciones. Los logros principales incluyen:

* **Gestión de Promociones:** Implementación de funcionalidades CRUD para la creación, consulta, actualización y eliminación de promociones.
* **Configuración de Ofertas:** Desarrollo de mecanismos para definir atributos como título, descripción, porcentaje de descuento, fecha de inicio, fecha de expiración y cantidad disponible.
* **Validaciones de Negocio:** Incorporación de reglas que garantizan la validez y disponibilidad de las promociones según las condiciones establecidas por cada negocio.

## Evidencias de Ejecucion: Módulo Promotion

A continuacion se presentan los endpoints desarrollados y testeados a traves de la interfaz de Swagger:

![promotion-evidence-0](assets/chapter04/sprint2-promotion/promos-0.png)

### Gestion de Promociones (Promotion)

El controlador de **Promotion** expone las funcionalidades críticas para el ciclo de vida de las ofertas:

* **Creación de Promociones**

Permite registrar nuevas promociones dentro de la plataforma, definiendo información como nombre, descripción, porcentaje de descuento, fechas de vigencia y cantidad disponible.

![promotion-evidence-1](assets/chapter04/sprint2-promotion/promos-1.png)

* **Listado General de Promociones**

Permite consultar todas las promociones registradas en el sistema para su administración y visualización.

![promotion-evidence-2](assets/chapter04/sprint2-promotion/promos-2.png)

* **Consulta de Promoción por Identificador**

Permite obtener la información detallada de una promoción específica mediante su identificador único.

![promotion-evidence-3](assets/chapter04/sprint2-promotion/promos-3.png)

* **Actualización de Promociones**

Permite modificar la información de una promoción existente, incluyendo datos descriptivos, fechas de vigencia y condiciones asociadas.

![promotion-evidence-4](assets/chapter04/sprint2-promotion/promos-4.png)

* **Eliminación de Promociones**

Permite eliminar promociones registradas en el sistema cuando ya no sean necesarias o deban ser retiradas de forma permanente.

![promotion-evidence-5](assets/chapter04/sprint2-promotion/promos-5.png)

* **Listado de Promociones Activas**

Permite consultar únicamente las promociones que se encuentran vigentes y disponibles para ser utilizadas por los consumidores.

![promotion-evidence-6](assets/chapter04/sprint2-promotion/promos-6.png)

* **Listado de Promociones por Negocio**

Permite obtener todas las promociones asociadas a un negocio específico, facilitando la gestión individual de sus campañas.

![promotion-evidence-7](assets/chapter04/sprint2-promotion/promos-7.png)

* **Publicación de Promociones**

Permite cambiar el estado de una promoción para que sea visible y accesible para los consumidores dentro de la aplicación.

![promotion-evidence-8](assets/chapter04/sprint2-promotion/promos-8.png)

* **Cancelación de Promociones**

Permite desactivar una promoción previamente publicada, evitando que continúe disponible para nuevos canjes.

![promotion-evidence-9](assets/chapter04/sprint2-promotion/promos-9.png)

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

![redemption-evidence-1](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-1.png)

### Gestion de Canjes (Redemption)

El controlador de **Redemption** expone las funcionalidades esenciales para la validación y ejecución del canje:

* **Generación de Canjes**

Permite registrar una solicitud de canje para una promoción determinada, verificando que la oferta se encuentre disponible y cumpla con las condiciones establecidas.

![redemption-evidence-1](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-2.png)

* **Confirmación de Canjes**

Permite validar y confirmar un canje previamente generado, garantizando que la promoción sea utilizada de manera correcta y evitando usos duplicados.

![redemption-evidence-2](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-3.png)

* **Consulta de Canje por Identificador**

Permite obtener la información detallada de un canje específico mediante su identificador único, incluyendo datos asociados a la promoción y al consumidor.

![redemption-evidence-3](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-4.png)

* **Historial de Canjes por Consumidor**

Permite consultar todos los canjes realizados por un consumidor específico, facilitando el seguimiento de promociones utilizadas dentro de la plataforma.

![redemption-evidence-4](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-5.png)

* **Historial de Canjes por Negocio**

Permite obtener el listado de canjes asociados a un negocio determinado, proporcionando visibilidad sobre el uso y desempeño de sus promociones.

![redemption-evidence-5](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-6.png)

# Favorites Bounded Context

Como parte del desarrollo del backend en **C#**, se ha implementado y consolidado el Bounded Context de **Favorites**. Este componente permite a los consumidores guardar ofertas de su interés para acceder a ellas posteriormente, mejorando la experiencia de navegación y facilitando el acceso rápido a promociones relevantes.

### Implementación Técnica de Favorites

La solución fue desarrollada utilizando **ASP.NET Core**, **Entity Framework Core** y **SQLite**, garantizando una gestión eficiente de la información y una adecuada persistencia de los datos. Los principales avances alcanzados incluyen:

* **Registro de Favoritos:** Implementación de funcionalidades que permiten a los usuarios agregar promociones a su lista de favoritos de manera rápida y sencilla.
* **Consulta Personalizada:** Desarrollo de servicios que permiten recuperar todas las promociones favoritas asociadas a un usuario específico.
* **Eliminación de Favoritos:** Implementación de mecanismos para remover promociones guardadas cuando el usuario ya no desea mantenerlas en su lista.

## Evidencias de Ejecucion: Módulo Favorites

A continuacion se presentan los endpoints desarrollados y testeados a traves de la interfaz de Swagger:

![favorite-evidence-0](assets/chapter04/sprint2-favorite/favorites-0.png)

## Evidencias de Ejecución: Módulo Favorites

El controlador de **Favorites** expone las funcionalidades críticas para el ciclo de vida de un favorito:

* **Listado de Favoritos por Usuario**

Permite consultar todas las promociones marcadas como favoritas por un usuario específico, facilitando el acceso rápido a ofertas previamente guardadas.

![favorite-evidence-1](assets/chapter04/sprint2-favorite/favorites-1.png)

* **Consulta de Favorito por Identificador**

Permite obtener la información detallada de un registro de favorito mediante su identificador único.

![favorite-evidence-2](assets/chapter04/sprint2-favorite/favorites-2.png)

* **Registro de Favoritos**

Permite asociar una promoción a la lista de favoritos de un usuario, aplicando validaciones para evitar registros duplicados y garantizar la integridad de los datos.

![favorite-evidence-3](assets/chapter04/sprint2-favorite/favorites-3.png)

* **Eliminación de Favoritos**

Permite remover una promoción previamente guardada en la lista de favoritos de un usuario, manteniendo actualizadas sus preferencias dentro de la plataforma.

![favorite-evidence-4](assets/chapter04/sprint2-favorite/favorites-4.png)

# Notifications Bounded Context

Como parte del desarrollo del backend en **C#**, se ha implementado y consolidado el Bounded Context de **Notifications**. Este componente permite gestionar las notificaciones de los usuarios dentro de la plataforma, informándoles sobre eventos relevantes como canjes generados, favoritos añadidos y promociones por vencer, mejorando la comunicación y la experiencia general de uso.

### Implementación Técnica de Notifications

La solución fue desarrollada utilizando **ASP.NET Core**, **Entity Framework Core** y **MySQL**, garantizando una gestión eficiente de la información y una adecuada persistencia de los datos. Los principales avances alcanzados incluyen:

* **Creación de Notificaciones:** Implementación de funcionalidades que permiten registrar notificaciones asociadas a eventos del sistema, como canjes generados, favoritos añadidos y promociones próximas a vencer.
* **Consulta Personalizada:** Desarrollo de servicios que permiten recuperar todas las notificaciones de un usuario específico, con soporte para filtrar únicamente las no leídas.
* **Marcado como Leída:** Implementación de mecanismos para actualizar el estado de una notificación individual, permitiendo al usuario indicar que ha tomado conocimiento de ella.
* **Marcado Masivo como Leídas:** Funcionalidad que permite marcar todas las notificaciones pendientes de un usuario como leídas en una sola operación.
* **Eliminación de Notificaciones:** Implementación de mecanismos para remover notificaciones cuando el usuario ya no desea mantenerlas, aplicando validaciones que garantizan que solo el propietario pueda realizarla.

## Evidencias de Ejecución: Módulo Notifications

A continuación se presentan los endpoints desarrollados y testeados a través de la interfaz de Swagger:

![notifications-evidence-0](assets/chapter04/execution-evidence/backend/notifications/POST1Notifications.png)

## Gestión de Notificaciones

El controlador de **Notifications** expone las funcionalidades críticas para el ciclo de vida de una notificación:

* **Creación de Notificación**

Permite registrar una nueva notificación para un usuario específico, asociándola a un tipo de evento del sistema. Aplica validaciones sobre los campos requeridos y retorna los datos completos del registro creado.

![notifications-evidence-1](assets/chapter04/execution-evidence/backend/notifications/POST1Notifications.png)
![notifications-evidence-1](assets/chapter04/execution-evidence/backend/notifications/POST2Notifications.png)

* **Consulta de Notificaciones por Usuario**

Permite recuperar todas las notificaciones asociadas a un usuario específico, incluyendo el conteo total y el conteo de notificaciones no leídas. Soporta el filtro opcional de solo no leídas.

![notifications-evidence-2](assets/chapter04/execution-evidence/backend/notifications/GET1Notifications.png)
![notifications-evidence-2](assets/chapter04/execution-evidence/backend/notifications/GET2Notifications.png)

* **Marcado de Notificación como Leída**

Permite actualizar el estado de una notificación específica a leída, indicando que el usuario ha tomado conocimiento del evento asociado.

![notifications-evidence-3](assets/chapter04/execution-evidence/backend/notifications/PATCH1Notifications.png)

* **Marcado Masivo como Leídas**

Permite marcar todas las notificaciones pendientes de un usuario como leídas en una sola operación, optimizando la gestión del centro de notificaciones.

![notifications-evidence-4](assets/chapter04/execution-evidence/backend/notifications/PATCH2Notifications.png)

* **Eliminación de Notificación**

Permite remover una notificación previamente registrada, aplicando validaciones que garantizan que solo el propietario pueda realizar esta acción dentro de la plataforma.

![notifications-evidence-5](assets/chapter04/execution-evidence/backend/notifications/DELETE1Notifications.png)

# Community Bounded Context (Reviews)

Como parte del desarrollo del módulo **Community**, se ha implementado y consolidado el Bounded Context de **Reviews**. Este componente permite a los usuarios publicar reseñas sobre los servicios contratados, interactuar mediante reacciones y comentarios, y fomentar la retroalimentación entre la comunidad de usuarios de la plataforma.

### Implementación Técnica de Reviews

La solución fue desarrollada utilizando **Flutter** en el frontend con **Jetpack Compose**, consumiendo una API REST que gestiona la persistencia y validación de las reseñas. Los principales avances alcanzados incluyen:

* **Publicación de Reseñas:** Implementación de funcionalidades que permiten a los usuarios registrar una reseña asociada a un servicio previamente contratado.
* **Validación de Elegibilidad:** Desarrollo de un mecanismo que verifica si el usuario cumple con las condiciones necesarias para poder reseñar, evitando publicaciones no autorizadas o duplicadas.
* **Interacción Social:** Implementación de reacciones (likes) sobre las reseñas publicadas, permitiendo a otros usuarios expresar su valoración sobre el contenido compartido.
* **Comentarios sobre Reseñas:** Desarrollo de servicios que permiten listar y publicar comentarios dentro de una reseña específica, enriqueciendo la conversación alrededor de cada opinión.

## Evidencias de Ejecución: Módulo Community

El controlador de **Reviews** expone las funcionalidades críticas para el ciclo de vida de una reseña:

* **Listado de Reseñas**

Permite consultar todas las reseñas registradas en la plataforma, facilitando la visualización de la retroalimentación compartida por los usuarios.

![community-evidence-1](assets/chapter04/sprint2-community/reviews1.png)

* **Publicación de Reseña**

Permite a un usuario registrar una nueva reseña, aplicando las validaciones necesarias para garantizar la integridad de la información publicada.

![community-evidence-2](assets/chapter04/sprint2-community/reviews2.png)

* **Verificación de Elegibilidad**

Permite comprobar si un usuario cuenta con los permisos y condiciones necesarias para poder reseñar un servicio determinado.

![community-evidence-3](assets/chapter04/sprint2-community/reviews3.png)

* **Reacción a una Reseña**

Permite a los usuarios reaccionar (like) sobre una reseña existente, promoviendo la interacción dentro de la comunidad.

![community-evidence-4](assets/chapter04/sprint2-community/reviews4.png)

* **Listado de Comentarios**

Permite consultar todos los comentarios asociados a una reseña específica.

![community-evidence-5](assets/chapter04/sprint2-community/reviews5.png)

* **Publicación de Comentario**

Permite a un usuario añadir un comentario dentro de una reseña, fomentando la discusión y el intercambio de opiniones.

![community-evidence-6](assets/chapter04/sprint2-community/reviews6.png)

##### 4.2.2.7. Software Deployment Evidence for Sprint Review

### Evidencias del Despliegue de Backend

Como parte de los objetivos del Sprint 2, el backend fue desplegado exitosamente en un entorno público utilizando **Railway**, permitiendo el acceso a los servicios REST implementados y a su documentación técnica mediante **Swagger/OpenAPI**.

![Railway](assets/chapter04/deployment-evidence/railway-1.png)

Para el despliegue se utilizó **Railway**, plataforma cloud que ofrece integración directa con repositorios de **GitHub**, facilitando la automatización del proceso de integración y despliegue continuo. Gracias a esta integración, cada actualización realizada en el repositorio puede ser desplegada de manera rápida y consistente en el entorno de producción.

La plataforma permitió configurar las variables de entorno necesarias para la ejecución de la aplicación, así como gestionar el monitoreo básico del servicio desde una interfaz centralizada.

![Railway](assets/chapter04/deployment-evidence/railway-2.png)

### Evidencias de la Documentación de la API

Como resultado de la implementación de los diferentes Bounded Contexts desarrollados durante el Sprint 2, se habilitó la documentación interactiva de la API mediante Swagger, permitiendo visualizar y probar los endpoints disponibles para los módulos de **Authentication**, **Favorites**, **Promotion**, **Redemption**, **Analytics** y demás componentes del sistema.

![Backend-1](assets/chapter04/execution-evidence/backend/backend-v2.png)

##### 4.2.2.8. Team Collaboration Insights during Sprint

Durante el desarrollo del **Sprint 2**, el equipo mantuvo una comunicación constante y colaborativa para asegurar el cumplimiento de los objetivos planteados. Se realizaron reuniones periódicas mediante **Discord**, permitiendo coordinar actividades, resolver impedimentos y dar seguimiento al avance de cada integrante. Asimismo, se utilizaron herramientas como **Trello** para la gestión de tareas y organización del conocimiento del proyecto.

**Resumen del Sprint 2:**

* **Backend y APIs:** Se completó la implementación de los principales Bounded Contexts de la solución, incluyendo **Profile, Favorites, Promotion y Redemption**, exponiendo sus funcionalidades mediante endpoints REST documentados.
* **Despliegue del Backend:** Los servicios fueron desplegados exitosamente en **Railway**, permitiendo el acceso público a la API y a su documentación técnica mediante Swagger/OpenAPI.
* **Validación de Funcionalidades:** Se implementaron y probaron los flujos principales de autenticación, gestión de promociones, favoritos, canjes y métricas de negocio, garantizando la correcta interacción entre los diferentes módulos del sistema.
* **Mejora de Artefactos:** Se revisaron y actualizaron los entregables desarrollados en iteraciones anteriores, incorporando correcciones y mejoras identificadas durante el proceso de validación.
* **Preparación de Evidencias:** Se recopilaron evidencias de las funcionalidades principales de la aplicación, así como material de apoyo para la elaboración de los videos de validación, About-the-Product y About-the-Team.

## 4.2.3. Sprint 3

##### 4.2.3.1. Sprint Planning 3

En este tercer sprint, el enfoque principal fue el deploy de la app **Kotlin** para Consumidores y el desarrollo completo de la app **Flutter** para Negocios. Se priorizó la finalización de las funcionalidades restantes, la integración de los módulos desarrollados y la preparación de evidencias para la revisión del sprint.

Las tareas se distribuyeron de la siguiente manera:

* **Samuel Bonifacio**: Despliegue de **App Kotlin** Añadir Sprint 3,Añadir icono a la app, verificar librerías y endpoints del backend.<br>
* **Julio Guillen**: <br> Documentación de Sprint 3.<br>
* **Alberto Ponce**: Migración de arquitectura de aplicaciones **Business** y **Consumer** a DDD <br> 
* **Alejandro Galindo**: Debug de App Kotlin + Integración de Analytics en Business <br>
* **Jefferson Castro**: <br>

##### 4.2.3.2. Sprint Backlog 3

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
    <td>US-10</td>
    <td>Crear promoción</td>
    <td>Como empresa, quiere crear promociones dentro de la plataforma.</td>
    <td>Alta</td>
    <td>Alberto</td>
    <td>Completado</td>
  </tr>

  <tr>
    <td>US-11</td>
    <td>Definir condiciones</td>
    <td>Como empresa, quiere establecer condiciones para sus promociones.</td>
    <td>Media</td>
    <td>Alberto</td>
    <td>Completado</td>
  </tr>

  <tr>
    <td>US-12</td>
    <td>Limitar canjes</td>
    <td>Como empresa, quiere limitar la cantidad de canjes de una promoción.</td>
    <td>Media</td>
    <td>Alberto</td>
    <td>Completado</td>
  </tr>

  <tr>
    <td>US-13</td>
    <td>Publicar reseña</td>
    <td>Como usuario, quiere compartir su experiencia después de usar una promoción.</td>
    <td>Media</td>
    <td>Julio</td>
    <td>Completado</td>
  </tr>

  <tr>
    <td>US-14</td>
    <td>Calificar promoción</td>
    <td>Como usuario, quiere calificar una promoción para expresar su nivel de satisfacción.</td>
    <td>Media</td>
    <td>Julio</td>
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
    <td>US-22</td>
    <td>Editar promoción</td>
    <td>Como empresa, quiere modificar promociones existentes.</td>
    <td>Alta</td>
    <td>Samuel</td>
    <td>Completado</td>
  </tr>

  <tr>
    <td>US-23</td>
    <td>Desactivar promoción</td>
    <td>Como empresa, quiere desactivar promociones que ya no desea mostrar.</td>
    <td>Media</td>
    <td>Samuel</td>
    <td>Completado</td>
  </tr>

  <tr>
    <td>US-24</td>
    <td>Compartir promoción</td>
    <td>Como usuario, quiere compartir promociones con otros usuarios.</td>
    <td>Media</td>
    <td>Julio</td>
    <td>Completado</td>
  </tr>
</table>

##### 4.2.3.3. Development Evidence for Sprint Review

* **Mobile Application**

En el desarrollo del **Frontend** para **Consumer** con **Kotlin**, la implementación fue realizada de manera colaborativa por todos los integrantes del equipo, trabajando tanto en entorno local como mediante el uso de **GitHub** como repositorio principal de control de versiones.

<table border="1" cellpadding="8" cellspacing="0" style="width:100%; border-collapse: collapse;"> <tr> <th>Fecha</th> <th>Commit ID</th> <th>Commit Message</th> <th>Autor</th> </tr> <tr> <td>17 de junio de 2026</td> <td>f2b7aec</td> <td>feat(notification): implement local notification bou ded context</td> <td>Alberto Ponce</td> </tr> <tr> <td>29 de junio de 2026</td> <td>2519c37</td> <td>feat: reestructuracion DDD</td> <td>aponceperales</td> </tr> <tr> <td>17 de junio de 2026</td> <td>5ed8851</td> <td>fix(navigation): wire Comunidad tab to CommunityScreen</td> <td>samuelbonifacio015</td> </tr> <tr> <td>15 de junio de 2026</td> <td>7bb7b41</td> <td>feat: community bc v1</td> <td>AlejandroG12970</td> </tr> <tr> <td>15 de junio de 2026</td> <td>b47fdca</td> <td>feat(redemption): implement QR codes and promo history flow</td> <td>samuelbonifacio015</td> </tr> <tr> <td>15 de junio de 2026</td> <td>9e83b4f</td> <td>feat: add RedemptionQRCode + Promo location filter enhanced</td> <td>samuelbonifacio015</td> </tr> <tr> <td>10 de junio de 2026</td> <td>2f1c395</td> <td>feat(ui): add Profile Repository &amp; UI State for fetching User endpoint</td> <td>samuelbonifacio015</td> </tr> <tr> <td>10 de junio de 2026</td> <td>024a7cb</td> <td>feat(api): add AuthApiService to fetch api/Authentication endpoints</td> <td>samuelbonifacio015</td> </tr> </table>

##### 4.2.3.4. Testing Suite Evidence for Sprint Review

Durante el **Sprint 3**, el equipo realizó pruebas funcionales y de integración orientadas a validar los flujos críticos de la aplicación móvil **Consumer (Kotlin / Jetpack Compose)** y de la aplicación **Business (Flutter)**, así como la correcta comunicación con el backend desplegado en **Railway**.

Las pruebas se ejecutaron de forma **manual** sobre emuladores y dispositivos físicos, complementadas con la verificación de endpoints mediante **Swagger/OpenAPI**. El objetivo principal fue asegurar que las historias de usuario del backlog del Sprint 3 se comportaran de manera estable antes del despliegue de la app Kotlin en **Firebase App Distribution**.

### Alcance de las pruebas

| Tipo de prueba | Producto | Objetivo | Resultado |
| --- | --- | --- | --- |
| Pruebas funcionales de UI | Consumer (Kotlin) | Validar navegación, autenticación, promociones, favoritos, canje QR, comunidad y notificaciones | Aprobado |
| Pruebas funcionales de UI | Business (Flutter) | Validar home del negocio, creación/edición/desactivación de promociones y visualización de campañas activas | Aprobado |
| Pruebas de integración API | Backend (C# / Railway) | Verificar respuestas de IAM, Promotion, Redemption, Favorites, Community, Notifications y Analytics | Aprobado |
| Pruebas de flujo extremo a extremo | Consumer + Backend | Registro/login → explorar promociones → guardar favorito → generar QR → publicar reseña | Aprobado |
| Pruebas de despliegue | Firebase App Distribution | Confirmar empaquetado APK/AAB, carga del build y disponibilidad para testers | Aprobado |

### Flujos validados en Consumer (Kotlin)

1. **Registro e inicio de sesión (US-17, US-18):** creación de cuenta, autenticación con credenciales y persistencia de sesión mediante token JWT.
2. **Exploración y búsqueda de promociones (US-21):** listado de ofertas, detalle de promoción y búsqueda por nombre.
3. **Favoritos (US-20):** agregar, listar y eliminar promociones favoritas.
4. **Canje con código QR (US-04):** generación de QR único, aceptación de términos y visualización del historial de canjes.
5. **Comunidad y calificaciones (US-13, US-14):** publicación de reseñas, calificación de promociones y visualización de interacciones.
6. **Compartir promoción (US-24):** acción de compartir oferta con otros usuarios desde la vista de detalle.
7. **Notificaciones locales:** recepción y gestión de avisos asociados a eventos de la aplicación.

### Flujos validados en Business (Flutter)

1. **Creación de promociones (US-10):** registro de nuevas ofertas con título, descripción y descuento.
2. **Definición de condiciones y límites (US-11, US-12):** configuración de vigencia, restricciones y cantidad máxima de canjes.
3. **Edición y desactivación de promociones (US-22, US-23):** actualización de datos y retiro de campañas del catálogo activo.
4. **Home y promociones activas:** monitoreo del portafolio de campañas del negocio.

### Criterios de aceptación verificados

* Los endpoints protegidos del backend solo responden con un token JWT válido.
* La app Consumer consume correctamente la API de producción en Railway.
* El flujo de canje genera un QR asociado al usuario autenticado y a la promoción seleccionada.
* Las operaciones de CRUD de promociones en Business se reflejan en el backend.
* La navegación entre módulos (Dashboard, Promotions, Favorites, Community, Profile) no presenta bloqueos ni pantallas huérfanas.
* El build de la app Kotlin se genera, se sube y queda disponible en Firebase App Distribution con el package name `com.example.klippr`.

### Observaciones del ciclo de pruebas

* Se corrigieron problemas de cableado de navegación (por ejemplo, pestaña **Comunidad** hacia `CommunityScreen`).
* Se validó la reestructuración **DDD** en las apps Consumer y Business, confirmando que los repositorios y estados de UI consumen los endpoints correctos.
* Se verificó la integración de librerías y la disponibilidad de los servicios del backend antes del despliegue final.

##### 4.2.3.5. Execution Evidence for Sprint Review

Durante el **Sprint 3** se consolidó la ejecución integral de la **Mobile App Consumer (Kotlin)**, la **Mobile App Business (Flutter)** y el **Backend** desplegado. A diferencia de sprints anteriores, la app Consumer dejó de ejecutarse únicamente de forma local y se preparó para distribución a testers mediante **Firebase App Distribution**.

A continuación se presentan las evidencias de ejecución de los productos:

## Mobile App Consumer — Kotlin & Jetpack Compose

### IAM / Profile

#### Pantalla de Login y Sign-up

Desde la pantalla de **Login**, el usuario puede registrarse o iniciar sesión. Esta vista constituye el punto de entrada al flujo de autenticación integrado con el backend, validando la identidad del consumidor y habilitando el acceso a las funcionalidades protegidas.

![sign-up](assets/chapter04/execution-evidence/backend/IAM/sign-up.png)

![login](assets/chapter04/execution-evidence/backend/IAM/login.png)

#### Pantalla de recuperación de contraseña

![forgotten](assets/chapter04/execution-evidence/backend/IAM/forgotten.png)

#### Pantalla de perfil y edición

Desde **Profile** y **Edit profile**, el usuario consulta y actualiza sus datos personales. La información se mantiene sincronizada con el backend a través del módulo de Profile.

![profile-info](assets/chapter04/execution-evidence/backend/IAM/profile-info.png)

![edit-profile](assets/chapter04/execution-evidence/backend/IAM/edit-profile.png)

#### Configuración de cuenta

Desde **Options**, el usuario gestiona parámetros y preferencias asociadas a su cuenta.

![dashb](assets/chapter04/execution-evidence/backend/IAM/dashb.png)

![options](assets/chapter04/execution-evidence/backend/IAM/options.png)

### Dashboard

Desde la sección **Dashboard**, el usuario visualiza de forma centralizada la información más relevante de su cuenta, incluyendo promociones destacadas y accesos rápidos a los módulos principales.

<p align="center">
    <img src="assets/chapter04/sprint2-dashboard/dashboard.png">
</p>

### Promotion

#### Catálogo de promociones

Desde **Promotion**, el consumidor explora el catálogo de ofertas disponibles, con información visual y descriptiva de cada promoción.

<p align="center">
    <img src="assets/chapter04/sprint2-promotion/promos-view.png">
</p>

#### Detalle de promoción seleccionada

Al elegir una oferta, el usuario accede al detalle completo: descripción, descuento, condiciones, vigencia y opción de aceptar términos antes de canjear.

<p align="center">
    <img src="assets/chapter04/sprint2-promotion/promos-chosen.png">
</p>

### Redemption — Generación de código QR

Una vez aceptados los términos, la app genera un **código QR único** vinculado al usuario y a la promoción seleccionada, permitiendo un canje seguro y trazable.

<p align="center">
    <img src="assets/chapter04/sprint2-redemption/redemption.png">
</p>

### Favorites

#### Lista vacía

Cuando el usuario aún no ha guardado promociones, la pantalla de favoritos muestra un estado vacío informativo.

<p align="center">
    <img src="assets/chapter04/sprint2-favorite/favorite-empty.png">
</p>

#### Lista con promociones guardadas

Al marcar ofertas como favoritas, el usuario puede consultarlas rápidamente desde esta sección.

<p align="center">
    <img src="assets/chapter04/sprint2-favorite/favorite-promos.png">
</p>

### Community — Reseñas y calificaciones

El módulo de **Community** permite publicar reseñas, calificar promociones e interactuar con la comunidad de consumidores, reforzando la confianza en las ofertas de la plataforma.

![community-mobile-1](assets/chapter04/execution-evidence/backend/community/klippr-community-1.png)

![community-mobile-2](assets/chapter04/execution-evidence/backend/community/klippr-community-2.png)

![community-mobile-3](assets/chapter04/execution-evidence/backend/community/klippr-community-3.png)

### Notificaciones

El bounded context de **Notifications** se integró en la app Consumer, permitiendo registrar, consultar y gestionar avisos locales asociados a eventos de la aplicación (canjes, favoritos y vigencia de promociones).

![notifications-get](assets/chapter04/execution-evidence/backend/notifications/GET1Notifications.png)

![notifications-post](assets/chapter04/execution-evidence/backend/notifications/POST1Notifications.png)

## Klippr Business App — Flutter

A continuación se presentan las evidencias de la aplicación **Klippr Business** para el segmento de negocios, completada y validada durante el Sprint 3.

### Home del negocio

Desde la pantalla principal, el negocio visualiza un resumen de sus promociones activas, métricas clave y acceso a las funcionalidades de gestión.

![Klippr Business - Home](assets/chapter04/klippr-bussiness/klippr-business-home.png)

### Creación de promociones

La vista **Crear Promoción** permite registrar nuevas ofertas con un formulario estructurado.

![Klippr Business - Crear Promoción](assets/chapter04/klippr-bussiness/klippr-business-promotion-create-view.png)

**Paso 1 — Información básica:** nombre, descripción y categoría de la promoción.

![Klippr Business - Crear Promoción - Paso 1](assets/chapter04/klippr-bussiness/klippr-business-promotion-create-view-1.png)

**Paso 2 — Condiciones y restricciones:** vigencia, límites de canje y reglas de uso.

![Klippr Business - Crear Promoción - Paso 2](assets/chapter04/klippr-bussiness/klippr-business-promotion-create-view-2.png)

### Editor de promociones

Desde el **Editor**, el negocio modifica datos de una promoción existente (descripción, fechas, descuento y estado).

![Klippr Business - Editor](assets/chapter04/klippr-bussiness/klippr-business-editor-view.png)

### Promociones activas

La pantalla **Promociones Activas** lista las campañas vigentes del negocio, facilitando el monitoreo y la gestión del portafolio de ofertas.

![Klippr Business - Promociones Activas](assets/chapter04/klippr-bussiness/klippr-active-promotions.png)

## Backend actualizado

El backend en **C# / ASP.NET Core** se mantuvo desplegado en **Railway** y disponible para consumo por ambas aplicaciones móviles. A continuación se muestran evidencias de la API y su documentación interactiva:

![Backend-1](assets/chapter04/sprint2-backend/backend-1.png)

![Backend-2](assets/chapter04/sprint2-backend/backend-2.png)

![Backend-3](assets/chapter04/sprint2-backend/backend-3.png)

![Backend-4](assets/chapter04/sprint2-backend/backend-4.png)

![Backend-5](assets/chapter04/sprint2-backend/backend-5.png)

![Backend-v2](assets/chapter04/execution-evidence/backend/backend-v2.png)

##### 4.2.3.6. Services Documentation Evidence for Sprint Review

Tras culminar el **Sprint 3**, se consolidó la documentación y el consumo de los servicios del backend de **Klippr** desde las aplicaciones móviles **Consumer** y **Business**. En esta iteración se priorizó la integración end-to-end de los bounded contexts de **Authentication / IAM**, **Profile**, **Promotion**, **Redemption**, **Favorites**, **Community (Reviews)**, **Notifications**, **Settings** y **Analytics**, todos desplegados en **Railway** y documentados mediante **Swagger/OpenAPI**.

**URL de documentación de la API:** https://klippr-backend-production.up.railway.app/swagger/index.html

A continuación se presentan las evidencias de documentación de los servicios utilizados durante el Sprint 3:

## IAM / Authentication Bounded Context

Módulo responsable del registro, autenticación, emisión de tokens JWT y control de acceso a recursos protegidos. Fue validado de forma integral con las pantallas de Login, Sign-up y recuperación de contraseña de la app Consumer.

![auth](assets/chapter04/execution-evidence/backend/IAM/auth.png)

![admin-profile](assets/chapter04/execution-evidence/backend/IAM/adminprof.png)

![bcusers](assets/chapter04/execution-evidence/backend/IAM/bcus.png)

![reset](assets/chapter04/execution-evidence/backend/IAM/reset.png)

**Operaciones principales documentadas:**

* Registro de usuarios e inicio de sesión.
* Generación y validación de tokens JWT.
* Consulta y listado de usuarios por identificador, correo o rol.
* Flujo de restablecimiento de contraseña.

## Profile Bounded Context

Módulo encargado de la gestión del perfil del consumidor y la consulta de perfiles administrativos.

![bcprofile](assets/chapter04/execution-evidence/backend/IAM/bcprof.png)

* **POST /api/profiles/consumer** — Crea el perfil del consumidor autenticado.

![post-cons](assets/chapter04/execution-evidence/backend/profile/post-cons.png)

* **GET /api/profiles/consumer/{profileId}** — Obtiene el perfil de consumidor.

![get-cons](assets/chapter04/execution-evidence/backend/profile/get-consu.png)

* **PUT /api/profiles/consumer** — Actualiza los datos del perfil.

![put-cons](assets/chapter04/execution-evidence/backend/profile/put-con.png)

* **GET /api/admin/profiles/by-user/{userId}** — Obtiene el perfil asociado a un usuario (consumidor o negocio).

![get-role](assets/chapter04/execution-evidence/backend/profile/get-role.png)

## Promotion Bounded Context

Servicio central para la creación, publicación, edición y desactivación de promociones. Es consumido tanto por la app Business (gestión de campañas) como por la app Consumer (catálogo y búsqueda).

![promotion-evidence-0](assets/chapter04/sprint2-promotion/promos-0.png)

* **Creación de promociones**

![promotion-evidence-1](assets/chapter04/sprint2-promotion/promos-1.png)

* **Listado general y consulta por identificador**

![promotion-evidence-2](assets/chapter04/sprint2-promotion/promos-2.png)

![promotion-evidence-3](assets/chapter04/sprint2-promotion/promos-3.png)

* **Actualización y eliminación**

![promotion-evidence-4](assets/chapter04/sprint2-promotion/promos-4.png)

![promotion-evidence-5](assets/chapter04/sprint2-promotion/promos-5.png)

* **Promociones activas y por negocio**

![promotion-evidence-6](assets/chapter04/sprint2-promotion/promos-6.png)

![promotion-evidence-7](assets/chapter04/sprint2-promotion/promos-7.png)

* **Publicación y cancelación/desactivación**

![promotion-evidence-8](assets/chapter04/sprint2-promotion/promos-8.png)

![promotion-evidence-9](assets/chapter04/sprint2-promotion/promos-9.png)

## Redemption Bounded Context

Módulo que soporta el flujo de canje seguro con generación de código QR, validación de condiciones y consulta de historial.

![redemption-evidence-1](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-1.png)

* **Generación de canjes**

![redemption-evidence-2](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-2.png)

* **Confirmación de canjes**

![redemption-evidence-3](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-3.png)

* **Consulta por identificador e historial por consumidor/negocio**

![redemption-evidence-4](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-4.png)

![redemption-evidence-5](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-5.png)

![redemption-evidence-6](assets/chapter04/execution-evidence/backend/promotion-redemption/klippr-redemption-6.png)

## Favorites Bounded Context

Servicio que permite a los consumidores guardar, consultar y eliminar promociones de interés.

![favorite-evidence-0](assets/chapter04/sprint2-favorite/favorites-0.png)

* **Listado por usuario y consulta por identificador**

![favorite-evidence-1](assets/chapter04/sprint2-favorite/favorites-1.png)

![favorite-evidence-2](assets/chapter04/sprint2-favorite/favorites-2.png)

* **Registro y eliminación de favoritos**

![favorite-evidence-3](assets/chapter04/sprint2-favorite/favorites-3.png)

![favorite-evidence-4](assets/chapter04/sprint2-favorite/favorites-4.png)

## Community (Reviews) Bounded Context

Módulo de reseñas y calificaciones que habilita la publicación de experiencias, verificación de elegibilidad, reacciones y comentarios.

* **Listado de reseñas**

![community-evidence-1](assets/chapter04/sprint2-community/reviews1.png)

* **Publicación de reseña**

![community-evidence-2](assets/chapter04/sprint2-community/reviews2.png)

* **Verificación de elegibilidad**

![community-evidence-3](assets/chapter04/sprint2-community/reviews3.png)

* **Reacción a una reseña**

![community-evidence-4](assets/chapter04/sprint2-community/reviews4.png)

* **Listado y publicación de comentarios**

![community-evidence-5](assets/chapter04/sprint2-community/reviews5.png)

![community-evidence-6](assets/chapter04/sprint2-community/reviews6.png)

## Notifications Bounded Context

Servicio de notificaciones para informar eventos relevantes al usuario (canjes, favoritos y promociones por vencer).

* **Creación de notificación**

![notifications-evidence-1](assets/chapter04/execution-evidence/backend/notifications/POST1Notifications.png)

![notifications-evidence-2](assets/chapter04/execution-evidence/backend/notifications/POST2Notifications.png)

* **Consulta por usuario**

![notifications-evidence-3](assets/chapter04/execution-evidence/backend/notifications/GET1Notifications.png)

![notifications-evidence-4](assets/chapter04/execution-evidence/backend/notifications/GET2Notifications.png)

* **Marcado como leída (individual y masivo)**

![notifications-evidence-5](assets/chapter04/execution-evidence/backend/notifications/PATCH1Notifications.png)

![notifications-evidence-6](assets/chapter04/execution-evidence/backend/notifications/PATCH2Notifications.png)

* **Eliminación de notificación**

![notifications-evidence-7](assets/chapter04/execution-evidence/backend/notifications/DELETE1Notifications.png)

## Settings Bounded Context

Módulo de configuración de parámetros de la aplicación y preferencias del usuario, integrado con las pantallas de opciones de la app Consumer.

![settings-1](assets/chapter04/execution-evidence/backend/setting/klippr-setting-1.png)

![settings-2](assets/chapter04/execution-evidence/backend/setting/klippr-setting-2.png)

![settings-3](assets/chapter04/execution-evidence/backend/setting/klippr-setting-3.png)

![settings-4](assets/chapter04/execution-evidence/backend/setting/klippr-setting-4.png)

## Analytics Bounded Context

Servicio de métricas e indicadores de negocio, integrado durante el Sprint 3 en la app Business para apoyar la visualización de desempeño de campañas.

![analytics-endpoints](assets/chapter04/sprint1-analytics/endpoints-swagger.png)

![analytics-dashboard](assets/chapter04/sprint1-analytics/get-dashboard.png)

![analytics-campaign](assets/chapter04/sprint1-analytics/get-campaign.png)

![analytics-metrics](assets/chapter04/sprint1-analytics/post-metrics.png)

### Notas de integración del Sprint 3

* La app **Consumer (Kotlin)** consume los endpoints de IAM, Profile, Promotion, Redemption, Favorites, Community y Notifications a través de servicios Retrofit/`AuthApiService` y repositorios alineados a DDD.
* La app **Business (Flutter)** consume los endpoints de Promotion y Analytics para crear, editar, desactivar y monitorear campañas.
* El backend permanece como fuente única de verdad desplegada en Railway; ambas apps se conectan al entorno de producción para las pruebas de Sprint Review.
* La documentación Swagger se utilizó como contrato de integración entre frontend y backend durante todo el sprint.

##### 4.2.3.7. Software Deployment Evidence for Sprint Review

Durante el **Sprint 3**, el hito principal de despliegue fue la distribución de la aplicación móvil **Consumer (Kotlin & Jetpack Compose)** mediante **Firebase App Distribution**, permitiendo que testers y stakeholders instalen y validen el build fuera del entorno local de desarrollo. Asimismo, se mantuvo operativo el backend en **Railway** y la landing page en **Vercel**.

### Evidencias del despliegue de la Mobile App Consumer — Firebase App Distribution

Para realizar el despliegue de la app móvil (Kotlin), se utilizó **Firebase Console**, opción **App Distribution**. A continuación se detalla el proceso seguido:

#### 1. Acceso a Firebase Console

Se ingresó al panel de la consola de Firebase del proyecto Klippr.

![Initial Firebase Console](assets/chapter04/sprint3-app-deploy/initial-firebase.png)

![Firebase Console Panel](assets/chapter04/sprint3-app-deploy/firebase-panel.png)

#### 2. Configuración de App Distribution (Android)

Desde el centro de distribución de aplicaciones (**App Distribution**) se seleccionó la plataforma **Android**.

![App Distribution](assets/chapter04/sprint3-app-deploy/app-distribution.png)

#### 3. Registro del package name y carga del build

Al registrar la aplicación Android se configuró el nombre del paquete del proyecto: **`com.example.klippr`**. Posteriormente se cargó el artefacto de distribución (APK/AAB) generado desde el proyecto Kotlin.

![App Upload](assets/chapter04/sprint3-app-deploy/app-upload.png)

![App Uploaded](assets/chapter04/sprint3-app-deploy/app-uploaded.png)

Como resultado, el build de la aplicación Consumer quedó disponible en Firebase App Distribution para su instalación y validación por parte del equipo y testers invitados.

### Evidencias del despliegue de Backend — Railway

El backend en **C# / ASP.NET Core**, con autenticación **JWT**, se mantuvo desplegado en **Render** y accesible de forma pública para las apps móviles y la documentación Swagger.

**URL:** https://klippr-backend-8o4x.onrender.com/swagger/index.html

![Railway](assets/chapter04/deployment-evidence/railway-1.png)

El despliegue se realiza mediante integración con el repositorio de **GitHub**, de modo que las actualizaciones del código fuente se reflejan en el entorno de producción. Railway permitió gestionar variables de entorno, monitorear el servicio y confirmar el estado de despliegue.

![Railway](assets/chapter04/deployment-evidence/railway-2.png)

La imagen del entorno de producción confirma el estado exitoso del despliegue (*Deployment successful*).

![Backend-1](assets/chapter04/execution-evidence/backend/backend-v2.png)

### Evidencias del despliegue de Landing Page — Vercel

La landing page de **Klippr**, desarrollada con **Next.js, React y TypeScript**, permanece publicada en **Vercel** como canal de adquisición y presentación del producto.

**URL:** https://klippr-landing-page.vercel.app/

![Vercel Deploy](assets/chapter04/vercel-deploy/deploy-dashboard.png)

![Landing-Page](assets/chapter04/vercel-deploy/deploy.png)

### Resumen de entornos desplegados en el Sprint 3

| Producto | Tecnología | Plataforma de despliegue | Estado |
| --- | --- | --- | --- |
| Mobile App Consumer | Kotlin + Jetpack Compose | Firebase App Distribution | Desplegado |
| Backend / API | C# + ASP.NET Core | Railway | Desplegado |
| Landing Page | Next.js + React + TypeScript | Vercel | Desplegado |
| Mobile App Business | Flutter | Ejecución y validación local / emulador | Validado |

##### 4.2.3.8. Team Collaboration Insights during Sprint

A continuación se presentan los insights de colaboración del equipo durante el Sprint 3, destacando la comunicación, coordinación y gestión de tareas que permitieron alcanzar los objetivos planteados:

![Consumer Insights](assets/chapter04/sprint3-insights/consumer-insights.png)

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
