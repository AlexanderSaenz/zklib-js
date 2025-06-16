# zklib-js-zkteko

> 📦 Mejorada librería Node.js para conectarse a dispositivos biométricos ZKTeco (Asistencia y Huellas) vía UDP.

Esta es una versión mejorada del proyecto original [`zklib-js`](https://github.com/merouanezouaid/zklib-js), con mejoras en compatibilidad, manejo de errores y nuevas funciones para dispositivos de control de asistencia.

---

## ✨ Características

- Conexión vía UDP a dispositivos ZKTeco (modelos compatibles con ZKLib)
- Obtención de registros de asistencia
- Listado de usuarios
- Manejo de fechas desde/hasta
- Compatibilidad con múltiples modelos
- Mejor manejo de desconexiones y errores

---

## 📦 Instalación

npm install zklib-js-zkteko

## 🚀 Uso Básico

const ZKLib = require('zklib-js-zkteko');

const zk = new ZKLib('192.168.1.201', 4370); // IP y puerto del dispositivo

(async () => {
  try {
    // 1. Conexión al dispositivo
    await zk.createSocket();

    // 2. Obtener registros de asistencia
    const attendance = await zk.getAttendances();
    console.log(attendance.data);

    // 3. Cerrar conexión
    await zk.disconnect();
  } catch (e) {
    console.error('Error:', e);
  }
})();

## 🛠️ Funciones disponibles
Método	                    Descripción
createSocket()	            Establece la conexión con el dispositivo
getAttendances()	        Recupera todos los registros de asistencia
getUsers()	                Obtiene la lista de usuarios registrados
getInfo()	                Devuelve información del dispositivo
disconnect()	            Finaliza la conexión de forma segura


## ✅ Compatibilidad probada
Tested en los siguientes modelos de ZKTeco:

. K14

. MB160

. iClock680

. VF380

. (y más modelos compatibles con protocolo ZKLib UDP)

## ⚠️ Errores comunes
Error / Excepción	                   Causa probable	                                Solución sugerida
-Timeout: device not responding	       -IP/puerto incorrecto o fuera de red	            -Verifica IP, conexión y     que        el                                                                                    puerto sea 4370
-UDP socket closed	                   -El dispositivo cerró la conexión	            -Asegúrate de no exceder solicitudes
Error code 5	                       Comando inválido o no soportado por el modelo	-Cambia de función o actualiza    firmware

## ⏱️ Ejemplo avanzado: Obtener registros desde una fecha
const fromDate = new Date("2024-01-01T00:00:00");

const logs = await zk.getAttendances({
  from: fromDate
});

🛠️ API disponible
Método	            Parámetros	             Descripción
createSocket()	    —	                     Conecta al dispositivo
disconnect()	    —	                     Cierra la conexión de forma segura
getUsers()	        —	                     Devuelve los usuarios registrados
getAttendances()	{ from, to } (op.)	     Registros de asistencia (puedes filtrar)

## 🧪 Script de prueba 
Puedes ejecutar pruebas rápidamente con:

node test

## 📚 Créditos y origen
Basado en: zklib-js
Autor original: Merouane Zouaid
Mejoras y mantenimiento: Alexander Saenz

## 📄 Licencia
MIT License
