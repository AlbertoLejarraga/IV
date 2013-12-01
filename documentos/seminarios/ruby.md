---
layout: index

---

Una introducci�n ligera al lenguaje Ruby
===


Objetivos espec�ficos
--

* Conocer la historia y origenes de este lenguaje
* Entender los conceptos principales detr�s del mismo
* Conocer y saber usar la sintaxis 
* Aprender las estructuras de datos y control principales
* Instalar y usar bibliotecas
* Hacer un peque�o programa


�Ruby? Pero si es muy f�cil
--

Si alguna vez hab�is o�do hablar de �l, posiblemente conozc�is [Ruby](http://ruby-lang.org) por [Ruby on Rails](http://rubyonrails.org), un marco
  web que sigue el paradigma MVC (Model, View, Controller) creado alrededor de 2005 que usa Ruby como lenguaje
  subyacente; mucha gente llega a Ruby desde la derecha (el On Rails)
  y se piensan que es como un lenguaje de macros que imita a Python o
    a Perl o a ambos... Pero no es as�.

El lenguaje Ruby lo
  cre� [`Matz`, Yukihiro Matsumoto](http://www.ruby-lang.org/en/about/), con la intenci�n de que fuera f�cil de aprender y se
  pareciera lo m�s posible a la forma en la que hablan las personas,
  no a c�mo las m�quinas quieren que hablemos. Y tiene m�rito que no
  le haya salido mal del todo, porque las �ltimas dos veces que
  dijeron eso sali� el COBOL y el SQL. Por otro lado, el nombre Ruby
  puede ser un juego de palabras con las perlas de Perl, o quiz�s
  no. El propio autor dice que es una mezcla de Python (que es
  anterior, pero no mucho) y Perl con un poco de Lisp y Smalltalk
  espolvoreado para que no falte de nada. 

�Y qu� es lo que sale? Pues un lenguaje interpretado, din�mico,
  orientado a objeto, reflexivo, que hasta no hace mucho no era
  demasiado r�pido pero que �ltimamente est� experimentando un
  incremento de rendimiento considerable. Ahora mismo va por la
  versi�n 1.9 (aunque es normal encontrarse instaladas versiones anteriores), pero la 2.0 no est� lejos (menos que la 6.0 de Perl,
  seguro). Por supuesto que por lo que m�s se le sigue conociendo es
  por Ruby on Rails, pero aplicaciones muy populares como Amarok, Vagrant o Sketchup usan
  este lenguaje. Y t� puedes tambien usarlo, si prestas atenci�n y
  haces los ejemplos y actividades de este tutorial, �por qu� no?

<div class='ejercicios' markdown="1">

Instalar Ruby y usar

    ruby --version

para comprobar la versi�n instalada. A la vez, conviene instalar tambi�n `irb`, `rubygems` y `rdoc`.

</div>

Primer programa
--


Para programar en Ruby necesitas el editor y el int�rprete de Ruby propiamente
  dicho. Desc�rgatelo e inst�lalo (o haz las dos cosas a la vez), aunque te vendr� bien tambi�n
  bajarte `irb`, un int�rprete interactivo que te permitir�
  probar cosas sobre la marcha. Servidor usa Emacs como editor, pero
  cualquier otra cosa tambi�n servir�, incluso Notepad. Ahora, si
  quieres ir un poco m�s all�, te puedes
  descargar [un plugin para Eclipse](http://www.ibm.com/developerworks/opensource/library/os-rubyeclipse/) o
  el [RDE, s�lo
    para Windows](http://homepage2.nifty.com/sakazuki/rde_en/). 

Ruby es un int�rprete, as� que no se "ejecuta" desde el men�. El
  ciclo es el habitual en programas para lenguajes interpretados: se
  escribe y se guarda el programa, nos vamos al directorio donde lo
  hemos guardado, si estamos en Linux/Unix lo hacemos ejecutable
  con `chmod +x`, y lo ejecutamos. Pero todav�a no podemos
  ejecutar nada, porque no hemos visto ning�n programa, as� que vamos
  con el primero.

En cuanto al int�rprete de Ruby que se puede instalar, hay muchas
  opciones; hay varias implementaciones de Ruby, aunque la m�s
  popular es la *oficial*, la de Matz (llamada a veces
  MRI). Hay, sin embargo, otras como JRuby (dentro de la m�quina
  virtual Java) o
  incluso [YARV o KRI](http://en.wikipedia.org/wiki/YARV),
  que se ha convertido a partir de la versi�n 1.9 en la "oficial". En
  tu ordenador puede que tengas una u otra, aunque tambi�n te puedes
  instalar [cualquier
    otra](http://en.wikipedia.org/wiki/Ruby_(programming_language)#Implementations).

    #!/usr/bin/ruby
    puts "Esto es jauja"

La primera l�nea es la habitual en lenguajes interpretados: le dice
  al int�rprete de �rdenes de Linux (y al servidor Apache en Windows,
  tambi�n) d�nde tiene que buscar el int�rprete; as� que habr� que
  comprobar que efectivamente se encuentra all�
  escribiendo `which ruby` (s�, en Linux, as� que ya no lo
  voy a decir m�s y asumid directamente que cualquier cosa que diga es
  para Linux a no ser que se diga lo contrario).

  Y la otra no es tan habitual (aunque es como en C, `put
  string`), pero tampoco es que extra�e demasiado. La cadena va
  entre comillas, se usa el cambio de l�nea para acabar la sentencia,
    y ya est�.

Para ejecutarlo se guarda y se hace lo que se ha dicho antes, no
  voy a repetirlo. Y el resultado ser� el esperado. Tambi�n pasar� lo
  mismo si lo hacemos desde `irb`:

    [jmerelo@leonard ruby-para-impacientes]$ irb
    pirb(main):001:0> puts "esto es jauja"
    esto es jauja
    => nil

Pero Ruby es un lenguaje orientado a objetos, o m�s bien empotrado
  de objetos: todo es un objeto en Ruby. As� que lo anterior (y algo m�s) podr�amos
  escribirlo de la forma siguiente.

    puts "--" << "Esto es jauja".center(20) << "--"

 Lo que consigue este program es escribir una cadena centrada en
 una l�nea de 20 caracteres y rodeada por dos guiones
  (`--`). `&lt;&lt;` es el operador de 
 concatenaci�n, que pega una cadena a la siguiente. Pero la 
 parte orientada a objetos est� alrededor del 
    `.` .`center` es un m�todo de la 
 clase [String](http://ruby-doc.org/core/classes/String.html), 
 pero como todo es un objeto en Ruby, no hace falta que lo 
 declaremos expl�citamente, ya es un objeto de por s�, por lo que
 podemos aplicarle los m�todos correspondientes, tales como
 ese. Pas�ndole el argumento 20, centra la cadena en un espacio de 20
 caracteres:

    usuario@usuario-desktop:~/code$ ./jauja-center.rb
    --   Esto es jauja    --  

Tambi�n pod�amos haber creado el objeto expl�citamente, pero
  hubiera sido mucho m�s cl�sico:

    jauja = String::new( "Esto es jauja" )
    puts "--" << jauja.center(20) << "--"

En la primera l�nea vemos un par de cosas: como en otros lenguajes,
las variables en Ruby no tienen ning�n tipo de car�cter
adicional (en realidad se ver�n m�s adelante algunos caracteres, que
    se usan principalmente para resoluci�n de �mbito). S�lo la variable, lo que tiene sentido, porque hace que uno
tenga que escribir menos. Por otro lado, `String` es una
clase, y adem�s una clase est�ndar, por lo que no hay que decirle al
programa que la incluya ni nada. El m�todo `new` es un
m�todo de clase, con lo que la sintaxis para llamarlo, a diferencia del m�todo de un
objeto, es de cuatro puntos (dos puntos dobles). El contenido de la
variable sigue siendo un objeto, as� que se usa de la misma forma que
antes. 

<div class='ejercicios' markdown="1">

Crear un programa en Ruby que imprima los n�meros desde el 1 hasta
otro contenido en una variable. 

</div>

El resto de los tipos de datos se define tambi�n de la forma m�s
l�gica; Ruby trabaja bajo el principio de la m�nima sorpresa (lo que
muchas veces provoca sorpresa si uno proviene de otros lenguajes, que nos tienen mal acostumbrados), o m�s bien
de la m�xima coherencia: una vez aprendida parte del lenguaje, el
resto es m�s o menos igual. Por ejemplo, las matrices:

    matriz = ['esto','es',1,'matriz']
    puts matriz.join << " " << matriz.join("-")

Como ocurre en otros lenguajes din�micos como el Ruby, no hay
distinci�n de tipos: una matriz puede contener n�meros enteros,
cadenas e incluso otras matrices, y desde su creaci�n son objetos de
pleno derecho, pudi�ndosele aplicar m�todos como `join` que
une todos los elementos de la matriz, con o sin alg�n car�cter de por
medio. Este peque�o programa imprimir�:

    usuario@usuario-desktop:~/ruby-para-impacientes$ code/matriz.rb
    estoes1matriz esto-es-1-matriz

como, imagino, era de esperar. 

No son los �nicos tipos de matrices: las matrices asociativas son
  aquellas que usan una clave para acceder a cada uno de los elementos
  (en vez de hacerlo en secuencia), sumamente �tiles para evitar la
  distribuci�n de la informaci�n de una estructura de datos por
  m�ltiples matrices y su acceso f�cil usando una clave

    sonido_de = { :vaca => 'muuu',
	  :buho => 'uuu',
	  :caballo => 'iiiii' }
    puts sonido_de.inspect


Que, aparte de introducir las llaves (para claves... �lo ves como se
	  trata de no sorprender?) pone unos dos puntitos delante de
	  las mismas que la verdad que s� sorprenden. Y es porque se
	  trata de cadens un poco especiales, denominadas
	  *s�mbolos*. Los s�mbolos en Ruby son como cadenas con las que
	  no se va hacer nada de lo que se suele hacer con las mismas:
	  ni partirlas, ni a�adirles nada, ni quitarles nada. Unas
	  cadenas constantes, m�s o menos, que no es otra cosa lo que
necesitamos en una variable asociativa,
	  denominada [Hash](http://ruby-doc.org/core/classes/Hash.html)
	  en Ruby. Por supuesto, se puede usar una cadena normal y
	  corriente como clave:

	  precio_de = { "pipas" => 'bajo',
	  "coche" => 'depende',
	  "plan E" => 'exagerado' }
	  puts precio_de.to_s

que al ejecutarse, por usar `to_s` para convertir a una
	  cadena la matriz asociativa en vez del inspect anterior no
se ve nada, pero es otra forma de hacer las cosas. `to_s` es tambi�n
	  un ejemplo de *casting*: convierte cualquier tipo (que use
	  ese m�todo, claro) en una cadena. Ruby es un lenguaje con
	  tipificaci�n fuerte, aunque din�mica: se le asigna tipo
	  din�micamente a las variables, pero una vez asignado s�lo se
	  pueden llevar a cabo las operaciones de ese tipo o bien se
	  les aplica las operaciones de una forma determinada: `+`
	  act�a como concatenaci�n para cadenas y como suma para tipos
	  num�ricos. 

<div class='ejercicios' markdown="1">

�Se pueden crear estructuras de datos mixtas en Ruby? Crear un array
de hashes de arrays e imprimirlo.

</div>

Como los arrays y hashes son objetos, tambi�n se usa normalmente un
m�todo para recorrerlos, como en el ejemplo siguiente:

    zipi = { :foo => 'bar', 
      :baz => 'quux'}

    zipi.keys().each do |zape|
      puts zipi[zape]
    end

`keys()` recorre las claves del hash y la funci�n `each` ejecuta un
					       bloque. C�mo funciona
					       esto exactamente se
					       ver� m�s adelante, pero
					       por lo pronto se puede ver la sintaxis en
					       la que se declara `zape` como variable de
					       bucle. Esa variable *recibe* cada valor,
					       equivalente a la variable de bucle
					       cl�sica. Si hacemos `each` sobre la
					       variable directamente recorrer� las claves
					       y los valores, escribi�ndolas como las
					       cadenas que son.
						   
<div class='ejerccios' maridown='1'>

Recorrer una estructura compleja exhaustivamente, imprimiendo todos los datos.

</div>


Leyendo y escribiendo
--

Trat�ndose de un lenguaje orientado a objetos, habr� que buscar la
  clase para abrir y cerrar ficheros, que se llama en un alarde de
  originalidad `File`.


	fh = File::new( ARGV[0] )
	while (line = fh.gets ) 
		nombre, apellidos  = line.split(',')
		puts "* Nombre #{nombre}\n\tapellidos #{apellidos}"
	end

En este caso, tampoco es sorprendente la matriz que se usa para
acceder a la l�nea de comandos: `ARGV`, igual que en C (pero en
may�sculas) o en Perl (pero sin d�lares). Ya puestos, introducimos
tambi�n una esctructura de control: el bucle `while` que
va leyendo l�nea a l�nea con `gets` (lo contrario
que `puts`, que es para escribir). El cuerpo del bucle no
usa llaves, s�lo la indentaci�n y la palabra `end` para indicar el
final. 

Fijaros tambi�n en una cosa curiosa: el `=` de la primera l�nea
  tiene a la izquiera y a la derecha una matriz: dos variables a las
  que se le asigna lo que queda al partir (`split`) la l�nea del
  tipo `nombre, apellidos` por la coma que lo
  divide. Simplemente se ponen a la izquierda las variables a las que
  van a ir a parar los diferentes elementos de la matriz. Y en la
  l�nea siguiente se imprime la salida, interpolando las cadenas
  usando algo para distinguirlas: `#{}`. Como las variables
  no tienen ning�n s�mbolo delante, hace falta eso al menos para saber
  que se trata de variables, y no de parte de la cadena. El
  resultado es el esperado:

    $ ruby code/fichero.rb code/nombres.txt
    * Nombre Gin�s
	apellidos  Ibn Hassan Rodr�guez
    * Nombre Sergei
	apellidos  Ben Ayoun
    * Nombre Malika
	apellidos  Maliki
    * Nombre Juan
	apellidos  G�mez G�mez

al menos sobre el fichero

    Gin�s, Ibn Hassan Rodr�guez
    Sergei, Ben Ayoun
    Malika, Maliki
    Juan, G�mez G�mez</pre>

Para leer de una web se tienen que usar m�dulos externos, que, como es
natural, est�n tambi�n organizadas en clases, y clases est�n
organizadas jer�rquicamente en espacios de 
  nombres. `Net`, por ejemplo, agrupa diferentes funciones
  relacionadas con la red: web , FTP, y todas esas cosas; dentro de
  esa jerarqu�a, los descendientes se separan con `::`,
  igual que en
  Perl. [Net::HTTP](http://augustl.heroku.com/blog/ruby-net-http-cheat-sheet)
  servir�a para leer cosas de la web. Pero no forma parte del n�cleo o
  *core*, as� que tendremos que importarla expl�citamente con
  `require`:

    require 'net/http'
    Net::HTTP.get_print  'osl.ugr.es', '/'

En `require` cambia un poco la sintaxis: se separan las partes de la
librer�a con `/` y se pone todo en min�sculas. `require`
importa el c�digo, pero no los identificadores; por eso para usar
alguna funci�n del m�dulo hay que decir todo el nombre de la misma:
nombre de la clase `nombre_del_m�todo`. `get_print` es un m�todo
  de clase, y recibe como argumentos el nombre del servidor (el HTTP
  va de soi) y la direcci�n dentro de ese servidor, en este caso el
  directorio ra�z. Al ejecutarlo nos dar� de resultado un mogoll�n de
  texto, todo lo que haya en la p�gina. De camino, conviene fijarse
  que aqu� nos hemos ahorrado unos cuantos par�ntesis, lo que,
sinceramente, me ha sorprendido.

Juntando todo lo anterior, y a�adiendo alguna cosilla m�s de
  nuestra cosecha, podemos bajarnos una p�gina web y
  meterla en un fichero

	require 'net/http'

	url = ARGV[0]
	puts "La url es " << url
	respuesta = Net::HTTP.get  url, '/'
	fname =  "#{url}.html"
	if ( File.writable?(fname) ) 
		salida = File.new fname, "w"	    
		salida.puts( respuesta )
	else
		puts("No puedo escribir en #{fname}")
	end

Nuestra cosecha incluye una interrogaci�n y un `if`, que no
  hab�amos visto antes. La interrogaci�n se usa en los m�todos que
  devuelven un valor l�gico, verdadero o falso (valores que tienen un
  tratamiento diferente en Ruby y en otros lenguajes: un valor l�gico
  es un valor l�gico, no un 0 o una cadena nula). En este caso, si se
  trata o no de un fichero sobre el que tengamos derechos de escritura
  (en lo que, al parecer, es un poco peculiar este Ruby). El bloque
  `if` termina en `end`, como antes el bucle. Adem�s, hemos usado "w"
  como segundo argumento de $File.new$ para abrirlo para
  escritura. Como se ve, no hace falta cerrarlo. Pa qu�, si ya sabe
  hacerlo el ordenador. 
  
<div class='ejerccios' maridown='1'>

1. Almacenar un array en formato JSON en un fichero cuyo nombre se pase por l�nea de �rdenes. 

</div>

Bloques
----

Despu�s de las variables uno de los conceptos importantes en Ruby
  son los bloques. Un bloque es una secuencia de c�digo con sus
  propias variables, y en Ruby se denota por
  llaves `{}` o por `do` - `done`. Se usa, por ejemplo, para bucles tales como los siguientes.

	host = ARGV[0]
	partes = host.split(".")
	partes.each do |p|
		puts "* #{p}"
	end

En este mini-programa le pasamos un nombre de servidor en internet
	(del tipo subdominio.dominio.tld) y nos da cada una de sus partes,
	que se guardan precisamente en una variable que se llama as�. Pero
	el truco est� en la tercera l�nea: `partes.each` es una funci�n
	que recibe un bloque como argumento. Tambi�n lo podr�amos expresar
	de la forma siguiente: 
	
	host = ARGV[0]
	partes = host.split(".")
	partes.each { |p|
		puts "* #{p}"
	}

y ser�a exactamente lo mismo (salvo la precedencia, pero eso no nos importa ahora). 

Los bloques tienen todos la misma estructura: al principio se
  declara una variable, que ser� la variable que ir� tomando los
  valores que reciba de su funci�n uno por uno. En este caso la hemos
  llamado `p`, pero es un nombre arbitrario, porque estamos haciendo
  una declaraci�n. Dentro ya del bloque metemos el c�digo que
  consideremos necesario, y lo finalizamos con llaves o end,
  dependiendo de c�mo lo hayamos comenzado

Lo que ocurre con los bloques en Ruby es que tienen entidad
  propia. Son como funciones an�nimas (es decir, funciones que no
  tienen asignado un nombre), y de hecho se pueden usar como
  tales; adem�s, como todo en Ruby, son objetos, o sea que podemos
  crearlos y pasarlos por ah� como queramos. 

	prefijos = %w( pre post ante super macro mega)
	prefijadores = Hash.new
	prefijos.each { |p|
		prefijadores[p] = lambda { |post| return "#{p}#{post}";}
	}

	puts prefijadores['macro'].call( 'objetivo' )
	puts prefijadores['super'].call( 'chanchi' )
	puts prefijadores['mega'].call( 'chuli' )
   
En este ejemplo hemos empezado definiendo una matriz de forma
abreviada: usando `%w` para ahorrarnos comas y comillas, y
hemos seguido creando un `Hash` (matriz asociativa) donde vamos a
guardar todas las funciones. Recorriendo el array creado y usando
`lambda` creamos una funci�n que tiene una parte fija, `p` que recibe
del bucle, y una parte variable, `post`, que es el argumento que
recibir� cuando se llame, tal como se hace abajo usando `call`
(recordad que es un objeto, y para ejecutar esa funci�n hay que llamar
al m�todo `call` de ese objeto). La
funci�n `prefijadores['macro']` se comportar� de la misma
forma que si la hubi�ramos definido as�

	def prefijador( post ) 
		"macro#{post}";
	end

	puts prefijador('micro');

la �nica diferencia es que en este caso no hace falta usar `call` para
llamar a la funci�n: se puede usar directamente el nombre de la
misma. De camino, vemos como se definen funciones en Ruby: usando
tambi�n `def`. Igual que antes, salvo que ahora damos un nombre al
bloque, lo que le da m�s derechos, al parecer.


<div class='ejercicios' markdown="1">

1. Crear una serie de funciones instanciadas con un URL que devuelvan
alg�n tipo de informaci�n sobre el mismo: fecha de �ltima
modificaci�n, por ejemplo. *Pista*: esa informaci�n est� en la
cabecera HTTP que devuelve

</div>

Instalando nuevos m�dulos


Qu� ser�a de cualquier lenguaje si tuvi�ramos que conformarnos con
  lo que nos da, y no pudi�ramos instalar cosas nuevas... El usar
  repositorios centralizados de m�dulos o bibliotecas lo comenz�
  LaTeX con CTAN, luego sigui� Perl con CPAN, y Ruby tiene su
  colecci�n de gemas para poder baj�rtelas c�modamente. Sin embargo,
  hace falta instalar paquetes para usarlo, no se instala
  autom�ticamente junto con el
  int�rprete. En Ubuntu habr� que instalar el paquete `rubygems`, y
  en otras distros hacer cosas m�s complicadas (o no). La manera m�s
  general es [bajarse
    el paquete de Rubyforge e instalarlo](http://docs.rubygems.org/read/chapter/3), tampoco es demasiado
  complicado. Afortunadamente, a partir de la versi�n 1.9 (que a fecha
  de 2013 ya empieza a aparecer en las distros) vendr� incluida.

Aparte de `gem`, hay que instalarse alguna cosa m�s, porque muchos
  m�dulos en Ruby necesitan herramientas de construcci�n
  adicionales. En concreto, la versi�n `-dev` del paquete
  Ruby que tengamos instalado. Por ejemplo, en alguna versi�n de Ubuntu habr�a que
  escribir 
  
    sudo apt-get install ruby1.8-dev

No siempre es necesario, pero si te da un error alg�n m�dulo t�pico,
  posiblemente sea por eso.

Una vez instalado todo eso, no hay m�s que usarlo. Empezamos por
  buscar algo que queramos instalar:

    jmerelo@sheldon:~/public_html/tutoriales/ruby-para-impacientes$ gem search mysql
    *** LOCAL GEMS ***

Joeves, no devuelve nada. Pero claro, es que busca en la colecci�n
  local de gemas. Habr� que buscar en la remota:

	jmerelo@sheldon:~/public_html/tutoriales/ruby-para-impacientes$ gem search --remote mysql

	*** REMOTE GEMS ***

	activerecord-jdbcmysql-adapter (0.9.6)
	activerecord-mysql-adapter-flags (0.0.3)
	dbd-mysql (0.4.4)
	do_mysql (0.10.1)
	...

Y as� hasta un mogoll�n de cosas. Tendremos un listado de todas las
  disponibles, y todas las versiones. Vamos a instalarnos la tercera;
  si queremos que est� disponible para todos los usuarios tendremos
  que lanzar la orden con privilegios de administrador:

    jmerelo@sheldon:~/ruby-para-impacientes$ sudo gem install ruby-mysql
Successfully installed ruby-mysql-2.9.2
1 gem installed
Installing ri documentation for ruby-mysql-2.9.2...
Installing RDoc documentation for ruby-mysql-2.9.2...
Could not find main page README
Could not find main page README
Could not find main page README
Could not find main page README

En algunos casos puede que d� error, porque falte alguna
  dependencia que haya que instalar desde el sistema operativo; en ese
  caso, es conveniente instalar el paquete correspondiente, en vez de
  hacerlo desde $gem$. Si no es la ultim�sima versi�n luego se puede
  actualizar con gem update. Por ejemplo, un paquete de mysql se puede
  instalar con `sudo apt-get install libdbd-mysql-ruby`;
  posteriormente, al hacer `gem update` se actualizar�
  alguna de las librer�as dependientes que se han instalado con el
  paquete (en mi caso, s�lo una denominada $deprecated$)

<div class='ejercicios' markdown="1">

1. Ver si est� disponible Vagrant como una gema de Ruby e instalarla.

</div>



Referencias adicionales
--


 Como es de esperar, hay libros enteros gratuitos sobre
    Ruby: [Programming Ruby](http://ruby-doc.org/docs/ProgrammingRuby/), por ejemplo, pero el m�s curioso
    es [la gu�a intensa de Ruby por Why](http://mislav.uniqpath.com/poignant-guide), con c�mics, vericuetos inefables,
    pero que finalmente termina ense�ando bastante. 
Como seguramente conoces otro lenguaje de programaci�n, prueba 
	[Ruby
	desde otros lenguajes](http://www.ruby-lang.org/es/documentation/ruby-from-other-languages/), con tutoriales en ingl�s y espa�ol
      que explican c�mo trabajar  con Ruby si se conoce Perl, o Java,
	o Python.

En espa�ol se puede
  mirar [este tutorial de
  Ruby](http://rubytutorial.wikidot.com/), bastante completo,
  o [este resumen](http://rubytutorial.wikidot.com/ruby-15-minutos) para aprender en s�lo 15 minutos. 

Cuando ya est�s harto de
  Ruby,[tambi�n
    puedes aprender un poquico de Ruby on Rails](http://www.maestrosdelweb.com/editorial/rubyonrails/), ya puesto. 


