# Portafolio Web con Autenticación y CRUD

Aplicación web moderna con autenticación de usuarios y sistema CRUD (Crear, Leer, Actualizar, Eliminar) utilizando **Firebase** como backend. Cada usuario puede gestionar sus propias tareas en tiempo real.

## 🎯 Descripción del Proyecto

Este proyecto es una aplicación web interactiva que permite a los usuarios:
- **Crear una cuenta** y autenticarse de forma segura
- **Iniciar sesión** con sus credenciales
- **Gestionar tareas** personalizadas (agregar, editar, eliminar)
- **Datos en tiempo real** sincronizados automáticamente en la nube

La aplicación cuenta con una interfaz moderna con tema oscuro (dark mode) y está completamente responsiva para dispositivos móviles.

## 🛠 Tecnologías Utilizadas

### Frontend
- **HTML5**: Estructura semántica del documento
- **CSS3**: Estilos con diseño responsivo y animaciones personalizadas
- **JavaScript (Vanilla)**: Lógica de la aplicación sin dependencias externas
- **Google Fonts**: Tipografía Inter para mejor legibilidad

### Backend y Servicios en la Nube
- **Firebase Authentication**: Autenticación segura con email y contraseña
- **Firebase Firestore**: Base de datos NoSQL en tiempo real
- **Firebase Storage**: Almacenamiento de archivos (configurado, listo para usar)

### Características de Seguridad
- Validación de usuarios con Firebase Auth
- Datos aislados por usuario (baseados en UID)
- Conexiones HTTPS automáticas
- Variables de configuración almacenadas (se recomienda usar variables de entorno en producción)

## 📋 Funcionalidades

### Autenticación
- ✅ Registro de nuevos usuarios
- ✅ Inicio de sesión
- ✅ Cierre de sesión
- ✅ Estado de autenticación en tiempo real
- ✅ Mensajes de error y estado

### Gestor de Tareas (CRUD)
- ✅ **Crear**: Agregar nuevas tareas
- ✅ **Leer**: Listar todas las tareas del usuario
- ✅ **Actualizar**: Editar tareas existentes
- ✅ **Eliminar**: Borrar tareas

## 🚀 Instalación y Configuración

### Requisitos Previos
- Navegador web moderno (Chrome, Firefox, Safari, Edge)
- Cuenta en [Firebase Console](https://console.firebase.google.com)
- Git instalado (para clonar el repositorio)

### Pasos de Instalación

1. **Clonar el repositorio**
```bash
git clone https://github.com/ikushira/portafolio-firebase.git
cd portafolio-firebase
```

2. **Configurar Firebase**
El archivo `portafolio.html` ya contiene la configuración de Firebase. Si necesitas usar un proyecto diferente:
   - Ve a [Firebase Console](https://console.firebase.google.com)
   - Crea un nuevo proyecto o selecciona uno existente
   - En la sección "Construcción" activa:
     - **Authentication**: Habilita Email/Contraseña
     - **Firestore Database**: Crea a base de datos en modo desarrollo
   - Copia la configuración de tu proyecto y reemplaza `firebaseConfig` en el HTML

3. **Ejecutar la aplicación**
   - Abre el archivo `portafolio.html` en tu navegador, o
   - Usa un servidor local:
   ```bash
   python -m http.server 8000
   # Luego abre http://localhost:8000
   ```

## 📁 Estructura del Proyecto

```
portafolio-firebase/
├── portafolio.html      # Archivo principal (HTML + CSS + JavaScript)
└── README.md            # Este archivo
```

**Nota**: El proyecto está contenido en un único archivo HTML. Para proyectos más grandes, se recomienda separar HTML, CSS y JavaScript en archivos independientes.

## 🔒 Configuración de Seguridad en Firebase

### Reglas de Firestore (Recomendadas)
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /tasks/{document=**} {
      allow read, write: if request.auth.uid == resource.data.uid;
      allow create: if request.auth.uid != null;
    }
  }
}
```

### Reglas de Authentication
- Acceso público para registro
- Validación de email (activar en Firebase Console)
- Recuperación de contraseña habilitada

## 💾 Base de Datos (Firestore)

### Estructura de Colecciones

**Colección: `tasks`**
```json
{
  "id": "documento_id_auto_generado",
  "text": "Descripción de la tarea",
  "uid": "ID_del_usuario_propietario",
  "timestamp": "2024-01-15T10:30:00Z"
}
```

## 🎨 Diseño y Experiencia de Usuario

- **Tema Oscuro**: Color de fondo #0b0f14 con acentos en verde (#00ff88)
- **Animaciones**: Cargador con puntos parpadeantes
- **Responsividad**: Adaptado para móvil, tablet y desktop
- **Mensajes de Estado**: Feedback visual del usuario en cada acción
- **Botones Intuitivos**: Colores diferenciados por acción
  - Verde: Acciones primarias (registrar, iniciar sesión)
  - Rojo: Acciones destructivas (eliminar)
  - Amarillo: Acciones secundarias (editar)

## 📱 Uso de la Aplicación

### Primer Acceso
1. Haz clic en **"Registrarse"** con un correo y contraseña
2. Una vez creada la cuenta, automáticamente se muestra la sección de tareas

### Gestión de Tareas
1. Escribe una tarea en el campo de entrada
2. Haz clic en **"Agregar"** para crear la tarea
3. Usa **"✏️"** para editar una tarea existente
4. Usa **"❌"** para eliminar una tarea

### Cerrar Sesión
Haz clic en el botón **"Cerrar sesión"** para salir

## 🐛 Troubleshooting

| Problema | Solución |
|----------|----------|
| Firebase no inicializa | Verifica la configuración de Firebase en el HTML |
| No puedo registrarme | Asegúrate de que Auth está habilitado en Firebase |
| Las tareas no guardan | Activa Firestore y verifica las reglas de seguridad |
| Error CORS | Usa un servidor local, no abras el archivo directamente |

## 📞 Contacto y Autor

- **Nombre**: Luis Aldana
- **Perfil**: Desarrollador Web Junior
- **Especialidades**: JavaScript, Firebase
- **GitHub**: [github.com/ikushira](https://github.com/ikushira)

## 📜 Licencia

Este proyecto está bajo la licencia **MIT**. Puedes usar, modificar y distribuir libremente con atribución.

## 🎓 Aprendizajes y Mejoras Futuras

### Tecnologías Aprendidas
- ✅ Módulos ES6 en navegadores
- ✅ Firebase SDK y APIs
- ✅ Manejo de promesas y async/await
- ✅ Manipulación del DOM
- ✅ Autenticación y autorización
- ✅ Bases de datos NoSQL

### Mejoras Futuras
- [ ] Migrar a framework (React, Vue, Svelte)
- [ ] Agregar categorías a las tareas
- [ ] Implementar temas personalizables
- [ ] Agregar paginación para muchas tareas
- [ ] Sistema de notificaciones
- [ ] Exportar tareas a PDF
- [ ] Sincronización offline (Service Workers)
- [ ] Pruebas automáticas (Jest, Cypress)

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Para reportar bugs o sugerir mejoras:
1. Abre un Issue describiendo el problema
2. Crea un Pull Request con tus cambios
3. Asegúrate de que el código siga las convenciones del proyecto

---

**Hecho con ❤️ por Luis Aldana | 2024**
