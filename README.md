# Xenify Links - GitHub Pages Setup

Este repositorio contiene los archivos necesarios para que funcionen los App Links (Android) y Universal Links (iOS) de la aplicación Xenify.

## 📁 Estructura del Proyecto

```
xenify-links/
├── .well-known/
│   ├── assetlinks.json          # Verificación para Android App Links
│   └── apple-app-site-association # Verificación para iOS Universal Links
├── refer/
│   └── index.html              # Página de referidos
├── index.html                  # Página principal
└── README.md                   # Este archivo
```

## 🔧 Configuración Necesaria

### 1. Android (assetlinks.json)

**Necesitas actualizar el SHA256 fingerprint:**

```bash
# Para debug keystore:
keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android

# Para release keystore:
keytool -list -v -keystore ruta/a/tu/keystore.jks -alias tu-alias
```

Luego reemplaza `SHA256_FINGERPRINT_AQUI` en `.well-known/assetlinks.json`

### 2. iOS (apple-app-site-association)

**Necesitas actualizar el Team ID:**

1. Ve a [Apple Developer Portal](https://developer.apple.com/account/)
2. En "Membership" encontrarás tu Team ID
3. Reemplaza `TU_TEAM_ID` en `.well-known/apple-app-site-association`

### 3. URLs Generadas

Una vez configurado GitHub Pages, tus enlaces serán:

- **Principal:** `https://tu-usuario.github.io/xenify-links/`
- **Referidos:** `https://tu-usuario.github.io/xenify-links/refer?code=CODIGO`

### 4. Verificación de Archivos

Los archivos de verificación estarán disponibles en:

- **Android:** `https://tu-usuario.github.io/xenify-links/.well-known/assetlinks.json`
- **iOS:** `https://tu-usuario.github.io/xenify-links/.well-known/apple-app-site-association`

## 🚀 Activar GitHub Pages

1. Ve a Settings → Pages
2. Source: Deploy from branch
3. Branch: main
4. Folder: / (root)
5. Save

## ✅ Probar la Configuración

1. **Verificar archivos:** Los URLs de `.well-known` deben ser accesibles
2. **Probar enlaces:** `https://tu-usuario.github.io/xenify-links/refer?code=123`
3. **App Links/Universal Links:** Los enlaces deben abrir la app automáticamente

## 📱 Actualizar Código de la App

No olvides actualizar el `referral_service.dart` con tu dominio real:

```dart
static const String appDomain = 'tu-usuario.github.io';
static const String referralPath = '/xenify-links/refer';
```
