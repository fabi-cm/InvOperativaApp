# 📚 Aplicación Móvil de Evaluación – Investigación Operativa

Esta aplicación móvil está diseñada para gestionar evaluaciones de la materia de Investigación Operativa, permitiendo al docente administrar estudiantes, cargar ejercicios, aplicar exámenes y generar estadísticas automáticas.

---

## 🧑‍💼 Funcionalidades Principales

- Gestión de estudiantes y notas
- Carga y edición de ejercicios por tema
- Configuración de exámenes aleatorios o manuales
- Seguridad durante la prueba (modo sin distracciones)
- Corrección automática o manual
- Envío de calificaciones por correo
- Estadísticas: percentiles, promedios, comparaciones

---

## 🧩 Diagramas

### ὓ8 Casos de Uso

```plaintext
+---------------------+
|     Administrador   |
+---------------------+
     |        |       \
     v        v        v
(Registrar)(Cargar) (Configurar)
(Estud.)   (Ejercic.) (Examen)
    |
    v
(Ver Estadísticas)
    |
    v
(Revisar Respuestas)
    |
    v
(Enviar Calificaciones)

+---------------------+
|      Estudiante     |
+---------------------+
    |        |
    v        v
(Iniciar) (Rendir)
(Sesión)  (Examen)
             |
             v
(Seleccionar modelos / fórmulas)
             |
             v
(Ver Resultado / Historial)
```

---

### ὓ8 Diagrama de Clases (Simplificado)

```plaintext
+----------------------+
|      Usuario         |
+----------------------+
| - nombre             |
| - correo             |
| - celular            |
+----------------------+
          ▲
          |
+----------------------+        +--------------------------+
|   Estudiante         |        |      Administrador       |
+----------------------+        +--------------------------+
| - notas: List<Float> |        | - puedeEditarEjercicios  |
| - historialExamenes  |        | - puedeVerEstadísticas   |
+----------------------+        +--------------------------+

+--------------------------+
|       Ejercicio          |
+--------------------------+
| - id                     |
| - tema                   |
| - enunciado              |
| - formulaEsperada        |
| - respuestaCorrecta      |
+--------------------------+

+--------------------------+
|         Examen           |
+--------------------------+
| - id                     |
| - estudianteId           |
| - preguntas: List<Ejercicio> |
| - fecha                  |
| - calificacion           |
+--------------------------+

+--------------------------+
|       Estadística        |
+--------------------------+
| - paralelo               |
| - promedio               |
| - percentil25            |
| - percentil75            |
+--------------------------+
```

---

## 🔁 Diagrama de Flujo del Examen

```plaintext
  +------------------+
  | Inicia sesión    |
  +------------------+
           |
           v
  +----------------------+
  | Elige "Rendir examen"|
  +----------------------+
           |
           v
  +------------------------------+
  | Cargar preguntas aleatorias |
  +------------------------------+
           |
           v
  +-------------------------------+
  | Mostrar pregunta con opciones|
  | - Seleccionar modelo         |
  | - Ingresar fórmula           |
  | - Dar respuesta numérica     |
  +-------------------------------+
           |
           v
  +-------------------------+
  | Repetir para cada item |
  +-------------------------+
           |
           v
  +-------------------------------+
  | Enviar respuestas / Finalizar|
  +-------------------------------+
           |
           v
  +-----------------------------+
  | ¿Corrección automática?    |
  +-----------------------------+
     /            \
   sí              no
  /                 \
 v                   v
+------------------+ +-------------------------+
| Calificación     | | Esperar revisión manual|
+------------------+ +-------------------------+
        |
        v
+---------------------------+
| Mostrar nota / Enviar por|
| correo electrónico        |
+---------------------------+
```

---

## 📱 Mockups ASCII de las pantallas (Resumen)

```plaintext
1. Login              -> Ingreso como Admin o Estudiante
2. Menú Admin         -> Gestión, carga, configuración
3. Menú Estudiante    -> Rendir examen, ver historial
4. Rendir Examen      -> Modelo, fórmula, respuesta
5. Resultados         -> Nota, envío por correo
6. Estadísticas       -> Promedios, percentiles
7. Cargar ejercicios  -> Enunciado, fórmula, respuesta
8. Ver estudiantes    -> Lista editable de alumnos
```

---

## 🔐 Seguridad Propuesta

- Bloqueo de otras apps durante el examen *(modo kiosko si se usa en tablet Android controlada)*.
- Encriptación de preguntas y respuestas en base local.
- Control de acceso por roles.
- No se guarda la respuesta hasta que finaliza el examen.
- Preguntas aleatorias diferentes por usuario.

---

> Este documento puede ser usado como base de informe, README en un repositorio o punto de partida para desarrolladores.
