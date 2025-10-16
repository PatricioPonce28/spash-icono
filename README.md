En primer lugar, crear el proyecto ionic start 
Ir a la documentación: https://capacitorjs.com/docs/guides/splash-screens-and-icons 

Luego Instalar npm install @capacitor/splash-screen
 
Buscar el example en la página y copiar el plugin de para modificar en el archivo capacitor.config.ts en base a lo que necesitemos

"plugins": {

    "SplashScreen": {
      "launchShowDuration": 3000,
      "launchAutoHide": true,
      "launchFadeOutDuration": 3000,
      "backgroundColor": "#ffffffff",
      "androidSplashResourceName": "splash",
      "androidScaleType": "CENTER_CROP",
      "showSpinner": true,
      "androidSpinnerStyle": "large",
      "iosSpinnerStyle": "small",
      "spinnerColor": "#999999",
      "splashFullScreen": true,
      "splashImmersive": true,
      "layoutName": "launch_screen",
      "useDialog": true
    }
    
Después, copiar el llamado a la aplicación y agregarla al app.component.ts 

import { SplashScreen } from '@capacitor/splash-screen'; 

Luego, crear una función showsplash
  
  async showSplash() {
    await SplashScreen.show({
    autoHide: true,
    showDuration: 3000,
    });
  }
  

Y llamarla en el constructor 

export class AppComponent {
  constructor() {
    this.showSplash();
  }
  

Luego se genera la plataforma Android  
 
Luego construir la aplicación con 
ionic build

Luego generar la carpeta de Android 
npx cap add Android

Después, buscar la siguiente página 
https://capacitorjs.com/docs/guides/splash-screens-and-icons 

Ejecutar el comando para generar los assets

npm install @capacitor/assets

En la documentación nos menciona lo de la carpeta assets y hacemos descargamos el símbolo y la imagen para el splash y el ícono con las especificaciones mencionadas. 
<img width="886" height="404" alt="image" src="https://github.com/user-attachments/assets/d3b7b350-f0e6-40c4-8a43-cb8340b08426" />

Generar esa carpeta aparte y copiar en la raíz del proyecto con los mismos nombres y dimensiones que mencionaba la documentación

Ejecutar el comando

npx capacitor-assets generate

Verificar las resoluciones de las imágenes assets en app/src/main/res/drawble donde se ven cargadas nuestras imágenes en diferentes resoluciones para Android

En el AndroidManifest.xml:
Colocar el acceso a Internet
<uses-permission android:name="android.permission.CAMERA" />

O también colocar para Agregar permiso de almacenamiento (lectura/escritura)

<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />

<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />

Finalmente se prueba en Android:

Npx cap open Android
<img width="886" height="404" alt="image" src="https://github.com/user-attachments/assets/2fda448d-1b83-4a8d-8033-0b2bb6af5ad9" />
<img width="361" height="772" alt="image" src="https://github.com/user-attachments/assets/13195ea5-a3ab-4fb2-8236-e9c5aae71e17" />
<img width="720" height="1600" alt="image" src="https://github.com/user-attachments/assets/01befb39-8eb7-40c5-aaf9-b3a33ad0a47c" />




   
 
