# 📱 Local Viewer - App Android Nativo

![Build Status](https://github.com/Andre-Buzeli/android-local-viewer/workflows/Build%20Android%20APK/badge.svg)

App Android nativo que **detecta automaticamente o IP local do WiFi** e acessa a **porta 3000**.

## 🎯 Funcionalidade

- **Detecção automática**: Identifica o IP local da rede WiFi
- **WebView nativo**: Interface completa com JavaScript habilitado  
- **Acesso direto**: Conecta automaticamente em `http://[IP_LOCAL]:3000`
- **Fallback inteligente**: IP padrão se detecção falhar
- **Navegação completa**: Botões voltar/avançar funcionam

## 🚀 Como Usar

### 1. Baixar APK
- Acesse [**Releases**](https://github.com/Andre-Buzeli/android-local-viewer/releases)
- Baixe o arquivo `app-debug.apk`

### 2. Instalar no Dispositivo
```bash
# Via ADB (se tiver configurado)
adb install app-debug.apk

# Ou instale manualmente:
# - Transfira APK para o dispositivo
# - Habilite "Fontes desconhecidas" nas configurações
# - Toque no APK para instalar
```

### 3. Usar o App
1. **Certifique-se** que o dispositivo está na mesma rede WiFi que o servidor
2. **Execute o app** - ele conectará automaticamente
3. **Resultado**: Abre automaticamente `http://[IP_LOCAL]:3000`

## 🔧 Detalhes Técnicos

### Detecção de IP
```java
WifiManager wifiManager = (WifiManager) getSystemService(Context.WIFI_SERVICE);
int ipAddress = wifiManager.getConnectionInfo().getIpAddress();
String localIp = Formatter.formatIpAddress(ipAddress);
```

### Permissões Necessárias
- `INTERNET` - Para acessar URLs
- `ACCESS_NETWORK_STATE` - Para verificar conectividade  
- `ACCESS_WIFI_STATE` - Para detectar IP do WiFi

### Configuração WebView
- ✅ JavaScript habilitado
- ✅ DOM Storage habilitado
- ✅ Zoom controls (sem UI)
- ✅ Wide viewport
- ✅ Cleartext traffic permitido

## 🛠️ Build Automático

Este projeto usa **GitHub Actions** para build automático:

- ✅ **Build**: Compilação automática a cada push
- ✅ **Release**: APK disponibilizado automaticamente
- ✅ **Cache**: Gradle cache otimizado
- ✅ **Java 17**: Build environment configurado

## 📁 Estrutura do Projeto

```
android-local-viewer/
├── app/
│   ├── src/main/
│   │   ├── java/com/example/localviewer/
│   │   │   └── MainActivity.java          # Lógica principal
│   │   ├── res/
│   │   │   ├── layout/activity_main.xml   # Layout WebView
│   │   │   ├── values/strings.xml         # Recursos de texto
│   │   │   ├── values/colors.xml          # Cores do tema
│   │   │   └── values/themes.xml          # Tema Material
│   │   └── AndroidManifest.xml            # Configurações & permissões
│   └── build.gradle                       # Config do módulo app
├── .github/workflows/build.yml            # GitHub Actions
├── build.gradle                           # Config root
├── settings.gradle                        # Settings do projeto
└── gradle.properties                      # Propriedades Gradle
```

## 🎯 Casos de Uso

- **Desenvolvimento local**: Testar apps web em desenvolvimento
- **Acesso rápido**: Interface dedicada para servidor local
- **Demonstrações**: Mostrar projetos rodando localmente
- **Desenvolvimento mobile**: Testar APIs locais

## 🔄 Customização

Para alterar a porta padrão, edite `MainActivity.java`:

```java
private static final int PORT = 3000; // Altere aqui
```

Para alterar IP de fallback:

```java
webView.loadUrl("http://192.168.1.100:" + PORT); // Altere aqui
```

## 📋 Requisitos

- **Android**: API 21+ (Android 5.0+)
- **Rede**: WiFi na mesma rede que o servidor
- **Servidor**: Rodando na porta 3000

---

**🚀 App pronto para uso! Baixe o APK nas [Releases](https://github.com/Andre-Buzeli/android-local-viewer/releases)**