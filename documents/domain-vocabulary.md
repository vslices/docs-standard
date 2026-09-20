# Domain Vocabulary — preguntas abiertas de modelado

Este documento registra preguntas propias de domain-vocabulary que surgieron al promover su grafo semántico a Docs Standard, pero que todavía no tienen una representación normativa suficientemente entendida en el YAML.

No reemplaza domain-vocabulary.yml. El YAML sigue siendo la definición consumible por Tooling; este archivo conserva presión de diseño pendiente.

## Cardinalidad de preguntas por término

El árbol actual expresa:

~~~text
¿Qué términos usamos?
└─ ¿Qué significa este término?
~~~

Sin embargo, un Domain Vocabulary normalmente contiene varios términos, y las preguntas subordinadas se responden una vez por cada término.

Ejemplo:

~~~text
¿Qué términos usamos?
├─ Workflow
│  ├─ ¿Qué significa este término?
│  ├─ ¿Dónde aplica este término?
│  └─ ¿Cómo se relaciona con otros?
└─ Flow
   ├─ ¿Qué significa este término?
   ├─ ¿Dónde aplica este término?
   └─ ¿Cómo se relaciona con otros?
~~~

Esto sugiere que el modelo semántico real puede no ser únicamente:

~~~text
question -> answer
~~~

sino algo cercano a:

~~~text
question
    -> N semantic subjects
        -> answers to the same subordinate questions
~~~

La naturaleza exacta de ese sujeto repetido todavía está abierta.

No se asume todavía que deba llamarse collection, record, entity, item o de otra forma.

### Preguntas abiertas

- ¿Cómo declara Docs Standard que una pregunta puede introducir N sujetos semánticos?
- ¿Cómo obtiene identidad estable cada término dentro del Document?
- ¿Las preguntas hijas se materializan por cada término o existe otra forma de asociarlas?
- ¿Cómo descubre Tooling cuál término está siendo actualizado?
- ¿Cómo se selecciona una pregunta cuando la misma identidad de pregunta existe para múltiples términos?
- ¿El selector operativo necesita combinar identidad de sujeto + identidad de pregunta?
- ¿Cómo se preserva el modelo progresivo de authoring cuando pueden aparecer nuevos términos en cualquier momento?
- ¿Qué ocurre con preguntas relacionales que pueden tener N respuestas dentro de un mismo término, como «¿Con qué otros términos puede confundirse?»?
- ¿Necesitamos distinguir cardinalidad de sujetos de cardinalidad de respuestas?

## El término como sujeto semántico

La repetición anterior sugiere que un término podría tener identidad documental propia sin convertirse necesariamente en un artifact independiente.

Esto importa porque:

- varias preguntas describen al mismo término;
- el significado de un término evoluciona sin perder necesariamente su identidad;
- relaciones entre términos necesitan referenciar sujetos concretos;
- aliases, traducciones y formas históricas no deberían crear accidentalmente términos independientes.

Pregunta de investigación:

> ¿Necesita Docs Standard modelar sujetos semánticos internos a un Document, además de preguntas y respuestas?

## Scope del vocabulario y aplicabilidad del término

El Document tiene un artifact.scope que expresa a qué clase de target puede aplicarse un Domain Vocabulary.

Dentro del Document aparece además:

~~~text
¿Dónde aplica este vocabulario?
~~~

y, por cada término:

~~~text
¿Dónde aplica este término?
~~~

Estas tres dimensiones no deberían confundirse:

~~~text
artifact.scope
    = a qué tipo de target puede aplicarse este tipo de Document

vocabulary applicability
    = qué dominio o contexto cubre esta instancia del Vocabulary

term applicability
    = en qué contextos un término particular conserva su significado
~~~

La separación parece semánticamente útil, pero debe validarse con documentos reales.

## Relaciones entre términos

Las relaciones entre términos pueden formar un grafo semántico compartido.

Ejemplos:

~~~text
más general
más específico
forma parte de
contiene
alternativo
complementario
depende de una distinción
~~~

El YAML actual puede preguntar por estas relaciones, pero todavía no define cómo sus respuestas referencian identidades de otros términos.

Pregunta de investigación:

> ¿Cómo referencia una respuesta a otro sujeto semántico del mismo Document sin reducir la relación a texto libre?

Esta pregunta puede converger con el problema de cardinalidad e identidad interna.

## Gobernanza histórica

La investigación histórica incluía preguntas como:

~~~text
¿Quién mantiene este vocabulario?
¿Quién decide cambios?
¿Cuándo debe actualizarse?
¿De dónde puede venir una actualización?
~~~

No fueron promovidas al grafo actual porque describen principalmente gobernanza y lifecycle del artifact, no el significado del vocabulario.

Se conserva este punto como evidencia histórica por si otros Documents muestran que existe una responsabilidad documental separada para ownership, mantenimiento o evolución de artifacts.
