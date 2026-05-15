# Capítulo IV: Product Implementation & Validation

## 4.1 Software Configuration Management

### 4.1.1 Software Development Environment Configuration

**Project Management**
| Plataforma | Descripción | Enlace |
| :--- | :--- | :--- |
| Trello | Seguimiento detallado del progreso de tareas y designación de responsables. | https://trello.com |
| Discord / WhatsApp | Comunicación interna del equipo para reuniones y mensajes rápidos. | https://discord.com |
| GitHub | Organización centralizada del código fuente y control de versiones. | https://github.com |

**Requirement Management**
| Plataforma | Descripción | Enlace |
| :--- | :--- | :--- |
| UXPressia | Diseño de User Personas, User Journey Mapping y Empathy Mapping | https://uxpressia.com |
| Miro | Visualización y desarrollo de escenarios As-Is y To-Be. | https://miro.com |

**Product UX/UI Design**
| Plataforma | Descripción | Enlace |
| :--- | :--- | :--- |
| Figma | Herramienta principal para diseño colaborativo de wireframes, mockups y prototipos. | https://www.figma.com |

**Software Development**
| Tecnología | Descripción | Enlace |
| :--- | :--- | :--- |
| Kotlin | Lenguaje principal para el desarrollo de la aplicación Android nativa. | https://kotlinlang.org |
| Jetpack Compose | Framework declarativo de UI para Android, parte del ecosistema Jetpack de Google. | https://developer.android.com/jetpack/compose |
| Flutter | Framework multiplataforma de Google para construir aplicaciones móviles con Dart. | https://flutter.dev |
| Dart | Lenguaje de programación utilizado junto a Flutter para la lógica y UI multiplataforma. | https://dart.dev |
| Android Studio | IDE oficial para desarrollo Android con soporte nativo para Kotlin y Jetpack Compose. | https://developer.android.com/studio |
| JetBrains ToolBox | Gestión de IDEs: IntelliJ IDEA, Android Studio. | https://www.jetbrains.com/toolbox-app |

**Software Documentation**
| Plataforma | Descripción |
| :--- | :--- |
| GitHub | Gestión de la documentación en repositorios y organizaciones. |
| Markdown | Formato base para la presentación y documentación del proyecto. |

### 4.1.2 Source Code Management

Se utiliza la estrategia **GitHub Flow** con las siguientes ramas principales:

- **`main`:** Código de producción estable y listo para despliegue o release.
- **`develop`:** Rama de integración continua donde se consolidan las features antes de pasar a `main`.

**Convenciones de nomenclatura:**
| Tipo | Prefijo | Formato | Ejemplo |
| :--- | :--- | :--- | :--- |
| Característica | `feature/` | `feature/nombre-descriptivo` | `feature/login-screen` |
| Lanzamiento | `release/` | `release/x.y.z` | `release/1.0.0` |
| Corrección urgente | `hotfix/` | `hotfix/x.y.z-descripcion` | `hotfix/1.0.1-fix-auth` |

**Repositorios:**
- Organización: https://github.com/QRustOrg
- Backend: https://github.com/QRustOrg/Klippr-Backend
- Landing Page: https://github.com/QRustOrg/Klippr-LandingPage
- Informe: https://github.com/QRustOrg/ReportTB1

### 4.1.3 Source Code Style Guide & Conventions

**Kotlin / Jetpack Compose:**
- Clases y Composables: `PascalCase` (ej. `LoginScreen`, `UserCard`)
- Variables y funciones: `camelCase` (ej. `userName`, `fetchUserData()`)
- Constantes: `SCREAMING_SNAKE_CASE` (ej. `MAX_RETRY_COUNT`)
- Composables: siempre con mayúscula inicial, anotados con `@Composable`
- Archivos Kotlin: `PascalCase` coincidiendo con la clase principal (ej. `LoginScreen.kt`)

**Flutter / Dart:**
- Clases y Widgets: `PascalCase` (ej. `HomeScreen`, `CustomButton`)
- Variables y funciones: `camelCase` (ej. `isLoading`, `getUserProfile()`)
- Constantes: `camelCase` con prefijo `k` (ej. `kPrimaryColor`, `kDefaultPadding`)
- Archivos Dart: `snake_case` (ej. `home_screen.dart`, `user_repository.dart`)
- Estructura de carpetas sugerida: `lib/screens/`, `lib/widgets/`, `lib/models/`, `lib/services/`

### 4.1.4 Software Deployment Configuration

**Android:**
1. Configurar `build.gradle` con `versionCode` y `versionName` correspondientes al release.
2. Generar el APK/AAB firmado desde **Build → Generate Signed Bundle/APK** en Android Studio.
3. Subir el `.aab` a **Google Play Console** en el track correspondiente (Internal, Alpha, Beta o Production).
4. Completar la ficha de la aplicación y enviar para revisión.

**Flutter:**
1. Ejecutar `flutter build apk --release` o `flutter build appbundle --release` para Android.
2. Ejecutar `flutter build ios --release` para iOS (requiere Xcode y cuenta de Apple Developer).
3. Subir los artefactos generados a las respectivas tiendas (Google Play / App Store Connect).
4. Gestionar versiones con el campo `version` en `pubspec.yaml` (ej. `1.0.0+1`).

### 4.2. Landing Page & Mobile Application Implementation
#### 4.2.1. Sprint n
##### 4.2.1.1. Sprint Planning n
##### 4.2.1.2. Sprint Backlog n
##### 4.2.1.3. Development Evidence for Sprint Review
##### 4.2.1.4. Testing Suite Evidence for Sprint Review
##### 4.2.1.5. Execution Evidence for Sprint Review

**POST - METRICS**

<p align="center">
    <img src="assets/chapter04/sprint1-analytics/post-metrics.png">
</p>

<p align="center">
    <img src="assets/chapter04/sprint1-analytics/post-metrics2.png">
</p>

**GET - BusinessDashboardId**

<p align="center">
    <img src="assets/chapter04/sprint1-analytics/get-dashboard.png">
</p>

**GET - CampaignId**

<p align="center">
    <img src="assets/chapter04/sprint1-analytics/get-campaign.png">
</p>

**POST - AbuseReports**

<p align="center">
    <img src="assets/chapter04/sprint1-analytics/post-abuse.png">
</p>

<p align="center">
    <img src="assets/chapter04/sprint1-analytics/post-abuse2.png">
</p>

**GET - AbuseReports**

<p align="center">
    <img src="assets/chapter04/sprint1-analytics/get-abuse.png">
</p>

##### 4.2.1.6. Services Documentation Evidence for Sprint Review
##### 4.2.1.7. Software Deployment Evidence for Sprint Review
##### 4.2.1.8. Team Collaboration Insights during Sprint
### 4.3. Validation Interviews
#### 4.3.1. Diseño de Entrevistas
#### 4.3.2. Registro de Entrevistas
#### 4.3.3. Evaluaciones según heurísticas
