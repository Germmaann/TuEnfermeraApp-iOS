# Tu Enfermera - App iOS

Esta es la aplicación iOS para Tu Enfermera, un WebView wrapper de https://tuenfermera.mx

## 📋 Requisitos previos

1. **Cuenta Apple Developer** ($99/año)
   - Ve a https://developer.apple.com
   - Crea una cuenta y paga la membresía

2. **Cuenta Codemagic** (gratis para empezar)
   - Ve a https://codemagic.io
   - Regístrate con tu email o GitHub

3. **Repositorio Git**
   - Sube esta carpeta a GitHub, GitLab o Bitbucket

## 🚀 Configuración en Codemagic

### Paso 1: Conectar repositorio
1. Abre https://codemagic.io/apps
2. Click en "Add application"
3. Conecta tu repositorio (GitHub/GitLab/Bitbucket)
4. Selecciona el repo con esta carpeta

### Paso 2: Configurar certificados iOS
1. Ve a Apple Developer: https://developer.apple.com/account/resources/certificates/list
2. Crea:
   - **App ID**: `com.tuenfermera.app`
   - **Distribution Certificate** (Production)
   - **Provisioning Profile** (App Store)

3. En Codemagic:
   - Ve a Teams → Code signing identities → iOS
   - Sube el certificado (.p12)
   - Sube el provisioning profile (.mobileprovision)
   - Ingresa el password del certificado

### Paso 3: Configurar App Store Connect API
1. Ve a App Store Connect: https://appstoreconnect.apple.com
2. Users and Access → Keys → App Store Connect API
3. Crea una nueva key (Team Manager role)
4. Descarga el archivo .p8

5. En Codemagic:
   - Ve a Teams → App Store Connect
   - Sube el archivo .p8
   - Ingresa el Key ID y Issuer ID

### Paso 4: Variables de entorno (en Codemagic)
```
APP_STORE_CONNECT_PRIVATE_KEY: (contenido del archivo .p8)
APP_STORE_CONNECT_KEY_IDENTIFIER: (Key ID de App Store Connect)
APP_STORE_CONNECT_ISSUER_ID: (Issuer ID de App Store Connect)
```

### Paso 5: Iniciar build
1. En Codemagic, selecciona tu app
2. Click en "Start new build"
3. Selecciona la branch y workflow "ios-app"
4. Click "Start new build"

## 📱 Después del build exitoso

1. El IPA se subirá automáticamente a TestFlight
2. En App Store Connect, configura:
   - Nombre de la app: "Tu Enfermera"
   - Descripción
   - Screenshots (iPhone 6.7", 6.5", 5.5")
   - Categoría: Medical o Health & Fitness
   - Precio: Gratis
   - Edad mínima: 4+

3. Envía a revisión de Apple (toma 1-3 días)

## 🎨 Íconos de la app (necesarios)

Crea iconos en estos tamaños:
- 1024x1024 (App Store)
- 180x180 (iPhone)
- 167x167 (iPad Pro)
- 152x152 (iPad)
- 120x120 (iPhone)
- 87x87 (iPhone Settings)
- 80x80 (iPad Settings)
- 76x76 (iPad)
- 58x58 (Settings)
- 40x40 (Spotlight)

Herramienta recomendada: https://www.appicon.co

## ⚙️ Configuración del proyecto Xcode

Si necesitas abrir el proyecto en Xcode (en Mac o servicio cloud):

1. Crea un nuevo proyecto en Xcode:
   - File → New → Project
   - iOS → App
   - Product Name: "TuEnfermera"
   - Bundle Identifier: "com.tuenfermera.app"
   - Interface: SwiftUI
   - Language: Swift

2. Reemplaza el archivo `ContentView.swift` con el que te proporcioné

3. Agrega los permisos en Info.plist:
   ```xml
   <key>NSCameraUsageDescription</key>
   <string>Esta app necesita acceso a la cámara para subir fotos</string>
   <key>NSPhotoLibraryUsageDescription</key>
   <string>Esta app necesita acceso a tus fotos para subir imágenes</string>
   ```

## 🔄 Actualizaciones

Cuando actualices tu web (https://tuenfermera.mx):
- Los cambios se reflejan automáticamente en la app
- NO necesitas recompilar ni reenviar a App Store
- Solo recompila si cambias:
  - Ícono de la app
  - Número de versión
  - Permisos (Info.plist)

## 💰 Costos

- **Apple Developer**: $99/año (obligatorio)
- **Codemagic**:
  - Gratis: 500 min/mes (suficiente para 8-10 builds)
  - Pro: $40/mes (builds ilimitados)

## 🆘 Soporte

Si tienes problemas:
1. Revisa los logs en Codemagic
2. Verifica que los certificados estén vigentes
3. Confirma que el Bundle ID coincida en todos lados
4. Contacta soporte de Codemagic: support@codemagic.io

## 📧 Notificaciones

Recibirás emails en: german_guerrero_rm@yahoo.com cuando:
- ✅ Build exitoso
- ❌ Build fallido
- 📱 App lista en TestFlight
- ✓ App aprobada por Apple

---

**¿Necesitas ayuda?** Escríbeme los errores o dudas que tengas durante el proceso.
