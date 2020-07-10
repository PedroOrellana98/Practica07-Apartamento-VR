# Practica07-Apartamento-VR
```
CONSEJO ACADÉMICO Aprobación: 2016 / 04 / 06
Formato: Guía de Práctica de Laboratorio / Talleres / Centros de Simulación
```
## PRÁCTICA DE LABORATORIO

# CARRERA: COMPUTACION ASIGNATURA: PROGRAMACIÓN HIPERMEDIAL

## NRO. PRÁCTICA: 7 TÍTULO PRÁCTICA: Desarrollo de una aplicación de realidad virtual usando

## la herramienta Unity y desplegada en un dispositivo móvil Android.

## OBJETIVO ALCANZADO:

## • Experimenta con aplicaciones de realidad virtual.

## • Experimenta con aplicaciones de realidad aumentada.

## • Distingue la diferencia entre tecnologías de realidad virtual y realidad aumentada.

## ACTIVIDADES DESARROLLADAS

## 1. Crear un repositorio en GitHub con el nombre “Practica07 – Apartamento VR”

## 2. Realizar un commit y push por cada requerimiento de los puntos antes descritos.

## a. Ignorar las carpetas Temp y Library

## b. Agregar el archivo apk comprimido en .zip

## 3. Luego, se debe crear el archivo README del repositorio de GitHub.

## 4. Generar informe de los resultados en el formato de prácticas. Debe incluir:

## a) El desarrollo de cada uno de los requerimientos antes descritos.

## b) La evidencia del correcto diseño de la escena

## c) La evidencia del correcto funcionamiento de la aplicación

## d) El informe debe incluir conclusiones apropiadas.

## e) En el informe se debe incluir la información de GitHub (usuario y URL del repositorio de la práctica)

## f) En el informe se debe incluir la firma digital de los estudiantes

## 5. En el archivo README del repositorio debe constar la misma información del informe de resultados de

## la práctica que se indica en el punto anterior

Con base al archivo VR-Scenes-and-Objects_Build-an-Apartment-4.3.1 se pide crear una escena con un apartamento en Unity.
Para lo cual, se debe tener en cuenta los siguientes requerimientos:

1. El Apartamento debe tener al menos 25 modelos prefabs (objetos 3D) que deben ser colocados apropiadamente dentro
    de la escena. Los objetos no pueden estar flotando sin motivos reales.
2. Crear al menos un material para cambiar el color de uno o varios objetos de la escena.
3. Crear un tablero de ajedrez y colocarlo sobre un objeto (por ejemplo: mesa, estante, etc.) usando materiales y texturas.
4. Crear al menos tres cuadros o portarretratos con imágenes del estudiante y su familia.
5. Crear un globo terráqueo usando una textura con base a una imagen del mapa del mundo
6. Crear al menos un shader que cambie el color de un objeto con base al tiempo transcurrido desde la ejecución de la
    aplicación.
7. Animar las manecillas del reloj.


```
CONSEJO ACADÉMICO Aprobación: 2016 / 04 / 06
Formato: Guía de Práctica de Laboratorio / Talleres / Centros de Simulación
```
8. Crear un trigger que permita cambiar el sentido de una de las manecillas del reloj.
9. Animar el globo terráqueo para que gire horizontalmente.
10. Crear un trigger que permita girar y detener la animación del globo terráqueo
11. Añadir una cámara de realidad virtual (GoogleVR) y colocarla para que la aplicación inicie dentro de la escena del
    apartamento.
12. Actualizar las configuraciones del jugador (Nombre de la compañía, nombre del producto, paquete, soporte para VR,
    etc.)
13. Añadir luces a la escena
14. Desplegar la aplicación para dispositivos Android.

Generar el informe de práctica en el formato correspondiente.

Extra. Agregar sonidos de la ciudad. Revisar,

https://docs.unity3d.com/ScriptReference/AudioSource.html

## RESULTADO(S) OBTENIDO(S):

# 1. Repositorio Github

# 2. Archivo README

# 3. Capturas de la aplicación

## Se han utilizado varios modelos prefabs para el apartamento, cabe recalcar que también se obtuvo modelos en 3D

## de la asset store como camra VR, muñecos de acción, portafolio, etc.


```
CONSEJO ACADÉMICO Aprobación: 2016 / 04 / 06
Formato: Guía de Práctica de Laboratorio / Talleres / Centros de Simulación
```
## Se creo un material para que cambie el color según el entorno que es una esfera la cual esta situada a la derecha

## en un estante.

## El shader que se utilizo y se edito con el visual studio para cambiar de color según el tiempo transcurrido desde que

## se ejecutó la aplicación.

Shader "Custom/MiPrimerShader" {
Properties {
_Color ("Color", Color) = (1,1,1,1)
_MainTex ("Albedo (RGB)", 2D) = "white" {}
_Glossiness ("Smoothness", Range(0,1)) = 0.
_Metallic ("Metallic", Range(0,1)) = 0.
}
SubShader {
Tags { "RenderType"="Opaque" }


```
CONSEJO ACADÉMICO Aprobación: 2016 / 04 / 06
Formato: Guía de Práctica de Laboratorio / Talleres / Centros de Simulación
```
### LOD 200

### CGPROGRAM

// Physically based Standard lighting model, and enable shadows on all light types
#pragma surface surf Standard fullforwardshadows

// Use shader model 3.0 target, to get nicer looking lighting
#pragma target 3.

sampler2D _MainTex;

struct Input {
float2 uv_MainTex;
};

half _Glossiness;
half _Metallic;
fixed4 _Color;

// Add instancing support for this shader. You need to check 'Enable Instancing' on
materials that use the shader.
// See https://docs.unity3d.com/Manual/GPUInstancing.html for more information
about instancing.
// #pragma instancing_options assumeuniformscaling
UNITY_INSTANCING_BUFFER_START(Props)
// put more per-instance properties here
UNITY_INSTANCING_BUFFER_END(Props)

void surf (Input IN, inout SurfaceOutputStandard o) {
// Albedo comes from a texture tinted by color
fixed4 c = tex2D (_MainTex, IN.uv_MainTex) * _Color;
//o.Albedo = c.rgb;
//o.Albedo = float3(0,1,0);
o.Albedo = float3(2, abs(sin(_Time.z)), 0);
// Metallic and smoothness come from slider variables
o.Metallic = _Metallic;
o.Smoothness = _Glossiness;
o.Alpha = c.a;
}
ENDCG
}
FallBack "Diffuse"
}

## Se descargo y se importo la textura de ajedrez al tablero cuyo objeto en 3d era un cubo el cual cmabiando la

## dimensión del objeto se pudo aplicar la textura que se necesitaba.


```
CONSEJO ACADÉMICO Aprobación: 2016 / 04 / 06
Formato: Guía de Práctica de Laboratorio / Talleres / Centros de Simulación
```
## Para el modelo de esfera se ha utilizado una textura para cambiar el modelo del globo terráqueo descargado desde

## internet y puesto en un stand para simular su movimiento y donde está ubicado.

## Para el material que cambie la estructura de la casa se utilizo una textura prefabricada que sirve como material de

## cambio.


```
CONSEJO ACADÉMICO Aprobación: 2016 / 04 / 06
Formato: Guía de Práctica de Laboratorio / Talleres / Centros de Simulación
```
## Para el retrato familiar se utilizo un objeto en 3D que es el cubo el cual se le fue dando forma similar a la cubierta

## de un retrato, y para la imagen se utilizo un plano el cual se inserto la imagen cargada en cada material que simula

## la foto familiar.


```
CONSEJO ACADÉMICO Aprobación: 2016 / 04 / 06
Formato: Guía de Práctica de Laboratorio / Talleres / Centros de Simulación
```
## Para las animaciones del reloj y del globo revisar el punto 4 que tiene un video demostrando como se ejecuta cada

## animación.

## El trigger se utilizó el mismo de la animación de las manecillas del reloj.

## Nombre en GitHub: PedroOrellana

## Url del repositorio: https://github.com/PedroOrellana98/Practica07-Apartamento-VR.git


```
CONSEJO ACADÉMICO Aprobación: 2016 / 04 / 06
Formato: Guía de Práctica de Laboratorio / Talleres / Centros de Simulación
```
# 4. Funcionamiento de la aplicación

## https://estliveupsedu-my.sharepoint.com/:v:/g/personal/porellanaj_est_ups_edu_ec/EQFQ6WkJLBNCpfjkaOS0-

## b0Bde7OLvi3rVyJTVrwcnIxCA?e=ucpyBK

## CONCLUSIONES:

## El entorno virtual es la tecnología del futuro y el desarrollo de modelos en 3D se está volviendo más común para

## los desarrolladores.

## RECOMENDACIONES:

## Se recomendaría el utilizar waypoints para mover al personaje y ver todo el apartamento con los objetos que se

## han insertado.

## Nombre de estudiante: Pedro José Orellana Jaramillo

## Firma de estudiante:


