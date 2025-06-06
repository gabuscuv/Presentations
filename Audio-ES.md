---
marp: true
transition: fade
description: hi
author: Gaby Bustillo del Cuvillo
paginate: true
---

# Game Audio Design Using Middlewares

Gaby Bustillo del Cuvillo

---

## Que no es esta charla\.\.\.

- Solo quiero lanzar audio:
  1) Usa la solucion integrada (Unreal MetaSounds, Godot/Unity Audio)
  2) Usa Audio Frameworks como: Mozilla CubeB, libsoundio, SDL, OpenAL, FAudio.
  3) Tambien puedes escribir tus propios Audio Backend (programa para WinMM o WASAPI (Windows), Pulse/PipeWire (Linux), Core Audio/AudioUnit (Mac), AAudio (Android)
      1) Ignorar ASIO (Windows), Jack (Linux) (Excepto que realmente necesitas baja latencia, Caso Rocksmith) 
         1) Core Audio (Mac) y Pipewire (Linux) ya tienen modos de baja latencia

---

## Recursos al poder del Sound Designer

1) Forma de abstraer diseño de audio de la programacion
    - Y una forma de que pueda involucrarse directamente en el proyecto sin intermediarios.
2) Independencia de control de filtros y efectos en runtime.
3) Independencia de motor (Pudiendo usar, Unreal, Unity, Godot y/o Custom)

---

## Los Middleware mas populares

Cualquiera de los dos soportan todas las plataformas y tienen API Publica
- ![height:100px](Audio/Wwise.png)
  - No pagas si tu budget es menor que $250K (Caso contrario: minimo $8K)
- ![height:50px](Audio/fmod.png)
  - No pagas si ingresas menos de $200K
    - En caso contrario pagar $2K (si tu budget es mayor a $600K consulta)

---
## Mi Experiencia
![](Audio/GamesWithAudioMiddle.png)

---

## Modos de Operación

 1) Pista Standard con estimulación por parámetros
    1) Infinita
       - [Video (Online)](https://www.youtube.com/watch?v=L6tU6rDpSUA)
       - [Video (Local)](./Audio/FMODExample-DynamicMusicwithSFXSounds.mkv)
    2) Finita
       - Demo
 2) Pistas Trigger/SFX (Llamado Actions en FMOD)
     - Demo
 3) Pistas Multilenguaje/StringTable (Ideal para dialogo)
      - Siguiente Diapositiva

Todas estas acciones, pueden ser posicional (3D) o plano (2D)

---

## Modos de Operación (StringTable)

![height:350px bg vertical right](Audio/FMOD_UnrealIntegration_StringTables.png)
![height:300px bg right](Audio/CallBack.png)
![height:400px](Audio/FMOD_StringTable.png)

---

## Tipica Integracion

<!--  -->
```
/// TankEvent = "event:/Tank"
//  PunchFX = "event:/Punch"
// o usar FMODUnity.EventReference tipo para Seleccion en editor
```
Unity (Oficial):
```
event = FMODUnity.RuntimeManager.CreateInstance(TankEvent)
event.start();
FMODUnity.RuntimeManager.PlayOneShot(DamageEvent, transform.position);
```

Godot (utopia-rise/fmod-gdextension, Probablemente parecido a C API):
```
 event = FmodServer.create_event_instance(TankEvent)
 event.start()
 FmodServer.play_one_shot(PunchFX);
```

---

## Integracion (Unreal Implementacion)


```
    UFUNCTION(...)
    static FFMODEventInstance PlayEventAtLocation(UObject *WorldContextObject, UFMODEvent *Event, const FTransform &Location, bool bAutoPlay);
```

![height:400 right](Audio/FMOD_UnrealTypes.png)

---

## Los filtros/efectos de sonido importan

![bg right](Audio/TypeOfFilters.png)
Ejemplos:

1) Reducir frecuencias dinámicamente según parametros
2) Cambiar el tono de una individual pista/layer

---

## Lo tipico Control de Volumen / VCA


![height:600px ](Audio/FMOD_VolumeControl.png)


---

## Recomendaciones personales de Workflow (1)

1) Usar tablas de excel para concordar nombramiento de Audio, tipo de audio, parametros y demas.
![Music Table](Audio/MusicTable.png)
Source: (GDC 18) Audio Asset Management: Tips and Tricks - Richard Ludlow

---

## Recomendaciones personales de Workflow (2)

2) Usar abstracciones para SFX. (Agnosticos del AudioMiddleware o motor)
   - Especialmente para casos de placeholder, cambio de Middleware rapidos
     - En caso de Unreal + FMOD, por si se pierde referencia a los objectos. (Deberia estar ok, el caso de otras integraciones a ser strings)

---

## Recomendaciones  (3)

3) Experiencia trabajando con Wwise
Conciencia de que solo se puede descargar/instalar el plugin desde su propio launcher Wwise al quedar fijado a una version. (olvidaros de git submodule o Unity Store)
    - Hacer Backup tras generarlo
![](Audio/WwiseLauncher.png)

---

## Recomendaciones de trabajar con Gente (4)

4) Borrar ficheros de símbolos (.sym/.pdb) para transferir entre compañeros. (o bien comprimirlo)
![bg right height:600px](Audio/Wwise_FileSize_Total.jpg) ![bg vertical  ](Audio/Wwise_FileSize_Structure.jpg)

---

Esto es todo.  
Web de Contacto:
![ height:250px ](Common/WebContact.png)
Linkedin:
![height:250px ](Common/Linkedin.png)
