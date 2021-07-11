# Observaciones

Barbara, felicitaciones por tu trabajo. Es increible el nivel de atención al detalle que demostras con este trabajo: cada espaciado, cada linea, se nota que está pensada y repensada para seguir a la perfección el modelo de Ada. Me gusta además cómo le diste tu estilo con los colores y las imágenes. El resultado es una web que te refleja y a la vez cumple a la perfección lo solicitado.

Tengo, lamentablmemente, pocos comentarios para hacerte, ya que el nivel de este trabajo es realmente muy alto. Pero siempre hay algo que comentar! :) Como dije en clase, este trabajo no se hace para que constates conocimientos, sino para que aprendas: en ese sentido, mi intencion es que estos comentarios te sirvan para aprender, mejorar tu codigo a futuro e ir apreciando mejor qué se espera de nosotras como desarrolladoras front end.

## Estructura correcta de documento HTML

Tu HTML esta realmente excelente. Claro, prolijo, muy bien comentado e identado.

Tenés cierta tendencia a tener divs de más. Algunas estructuras de tu web se podrían resolver con menos divs. Dicho esto, yo prefiero que los divs sobren antes de que falten: un div de más se soluciona muy fácil, un div menos puede ser un gran dolor de cabeza cuando estamos recién arrancando. Este sería un comentario que quizá me reservaría para futuros trabajos, pero veo tan bien tu código que me siento confiada en recomendarte que empieces a ver estas cosas desde ya. 

Si tenés ganas, con tiempo, te diría que valdría la pena recorrer tu html y notar que estructuras como esta se pueden hacer más breves:

```html
<nav class="navegacion">
    <div class="navegacion-barra">
        <div class="navegacion-menu">
            <ul class="navegacio-menu-link">
                <li><a href="#Hola" class="navegacion-link">HOLA</a></li>
                <li><a href="#conocimientos" class="navegacion-link">CONOCIMIENTOS</a></li>
                <li><a href="#proyectos" class="navegacion-link">PROYECTOS</a></li>
                <li><a href="#contactame" class="navegacion-link navegacion-link-contacto">CONTACTO</a></li>
            </ul>
        </div>
    </div>
</nav>
```

Todos los estilos de `navegacion-barra` se podrían llevar a `navegacion` sin problema, y el div `navegacion-menu` no cumple ninguna función así que se podría sacar también. 

Te lo comento aquí como un ejemplo, pero esto es algo que se repite a lo largo de tu código. 

## Respeta la consigna

- El portfolio cuenta con las secciones solicitadas
- Al clickear en los links de navegación, debe llevar a la sección correspondiente
- Al clickear en los links de contacto, debe llevar a la página externa
  correspondiente
- El portfolio debe tener un diseño responsivo y verse correctamente en distintos dispositivos
- El portfolio debe estar deployado y ser accesible desde una URL
- El repositorio en GitHub debe tener un readme adecuado

Todos estos puntos están cumplidos. Menciono especialmente tu responsive: es increíble lo bien que solucionaste las distintas resoluciones, siguiendo casi a la perfección el modelo y preocupandote para que todo se vea hermoso, veamos tu web desde cualquier dispositivo. 

El único comentario que te haría al respecto es que en las resoluciones de 1100 a 1200px(escritorios pequeños) tu codigo "rebalsa". Te das cuenta porque hay un scroll horizontal, y una especie de barra blanca que cubre todo el extremo derecho. Esto ocurre normalmente cuando hay un elemento que rebalsa su contenedor, forzando que el body sea más grande que la pantalla. En tu caso, ese elemento es `proyectos-contenedor`. Prestá atención a este código: 

```css
.proyectos-contenedor {
margin: 0;
width: 1100px;
display: flex;
flex-wrap: wrap;
padding-left: 70px;
padding-right: 70px;
```

El body en este caso mide entre 1100 y 1200px. Pero proyectos-contenedor es más grande que eso: mide 1100px mas 70px a la derecha, por el padding, y 70px a la izquierda. 1240px en total, más grande que la pantalla. Esto podría solucionarse con un `box-sizing: border-box`, pero viendo los esfuerzos que hiciste para que este contenedor y muchos otrosn se vean responsive, quizá quieras repensar la estrategia de darles un width fijo. Tu código es un poco inmantenible así como está: son muchas media queries, en general no deberíamos necesitar una para 800px y otra para 900px. Creo que comenté en clase que lo más habitual es seguir las que sugiere bootstrap:

```css
/* Celulares */
@media (max-width: 576px) { ... }

/* Celulares en modo horizontal y tablets pequeñas */
@media (max-width: 768px) { ... }

/* Tablets  */
@media (max-width: 992px) { ... }

/* Monitores pequeños */
@media (max-width: 1200px) { ... }

/* Monitores grandes */
@media (max-width: 1400px) { ... }
```

Que vos necesites hacer cosas como esta habla de que quiza tu estrategia no valga la pena a largo plazo, ya que el codigo es complejo y dificil de cambiar si en algun momento queremos repensar las medidas:

```css
  @media screen and (max-width: 800px) {
    .contacto-contenedor {
      width: 600px;
    }
    .contacto-formulario {
      width: 600px;
    }
    .contacto-texto {
      width: 600px;
    }
  }

  @media screen and (max-width: 700px) {
    .contacto-contenedor {
      width: 500px;
    }
    .contacto-formulario {
      width: 500px;
    }
    .contacto-texto {
      width: 500px;
    }
  }
```

Quizá un width con porcentajes aquí sea mejor, por ejemplo de 90%. Eso ayudaría a que tu código sea un poco menos repetitivo y más fácil de seguir, y también te evitaría problemas como el que te comenté recién. 

Nuevamente, este es un punto bastante complejo y que normalmente no señalaría en esta etapa, pero viendo la alta calidad de tu trabajo me siento confiada sugiriendotelo. 

### Respeta el diseño dado

Cumplido a la perfección. 

### Buena estructura de proyecto

No entiendo por qué tenés dos carpetas de imágenes, especialmente cuando una tiene una mayúscula en el título, algo que podría traerte problemas en el linkeado. Deberías tener todas en una sola carpeta. La excepción a esta regla es el favicon, que siempre debería ir en la carpeta principal. Atención también a su nombre: debería estar en minúscula. 

### Código bien indentado

Tabulas muy bien, lo cual parece un detalle extra cuando una recien comienza pero ayuda un monton a su legibilidad, y que lo hayas logrado en esta etapa es un gran mérito. 

### Comentarios que permiten mejorar la legibilidad del código

Impecables. 

### Uso correcto de etiquetas semánticas

En general usas bien las etiquetas semánticas. Me llama la atención que hayas usado `div` para las tarjetas de Mis Conocimientos y Mis Proyectos: yo diría que deberían ser `article`. Pero es el único detalle a comentar aquí (y hay quien podría discutirme que deberían ser divs)

### Buenos nombres de clases

En general está cumplido, aunque noto algunas clases que tienen identidades confusas y problemas con la capitalización. El id "Hola" debería ser "hola": no usamos mayúsculas en HTML o CSS. El nombre también es poco claro: esta sección es la de presentación, por lo que "hola" no es un nombre descriptivo en un sentido funcional. 

Veo una clase "sección" que se repite a lo largo de tu código que es totalmente innecesaria, ya que sólo agrega flex que es algo que estás agregando en tus otros estilos. Si la intención era ahorrar codigo con esa clase, no está cumplido, ya que sólo agrega código de más. Sospecho que quizá sea por haber seguido de cerca el modelo de Ada, pero el código de la web modelo y el tuyo son muy distintos, por lo que no recomendaría seguir esa estructura aquí. 

Tenes una clase "navegacio-menu-link" donde te falta la n final. Lo escribiste igual en css, así que no trae problemas, pero tratá de evitar esas confusiones ya que pueden ocasionar problemas si por ejemplo otra persona usa tu código y no nota el caracter faltante. 

### Código CSS bien estructurado

Cumplido a nivel formal. Noto algunos estilos innecesarios o confusos, que te voy indicando en tu archivo de css.

### Reutilización de estilos

Cumplido en general, ya que noto muchas veces que usas dos nombres de clase, uno general y otro más específico, para evitar repeticiones innecesarias, como en los íconos de mis proyectos. Podrías mejorarlo, por ejemplo en el código de las secciones que te indiqué más arriba: si todas van a tener el mismo width en distintos media queries, por qué no subsumirlos en una clase contenedora? 

### Cumple con criterios básicos de accesibilidad

- Los colores tienen un contraste adecuado

Cumplido en general, aunque en varios casos se te escapa: en el hover de los iconos de la barra de navegación por ejemplo. 

- Las imágenes tiene el atributo `alt` que corresponde

Deberían ser textos fácilmente legibles por un lector de pantalla, pero en tu caso los ponés todos en una sola palabra: "ProyectoGastos" lo que hace que el lector lo lea de manera extraña y confusa. Pensá en algo que se pueda leer y entender fácilmente: "Proyecto de controlador de gastos". 

- Los íconos y elementos que no presentan texto agregan la información correspondiente por otros medios (etiquetas aria, texto oculto)

No cumplido, por ejemplo en los links a redes sociales de tu footer. Necesitan un aria.

- Los íconos y elementos que no necesitan ser anunciados por un lector de pantalla tienen la etiqueta aria
  correspondiente

No cumplido. 

- Commits con mensajes adecuados

Cumplido, noto muchos y buenos commits en tu proyecto, lo que siempre se agradece.

- Cuenta con un favicon

Cumplido, aunque debería estar en la carpeta principal y con la capitalización indicada. 

### Nota: 9
