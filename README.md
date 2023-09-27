# Code_Weaver's Hangman game
En este repositorio se explica el desarrollo y la ejecución del proyecto final para el curso de Programación de Computadores
### Integrante: Yazney Alejandra Arenas Garrido
### Logo
![logo](https://github.com/alejayz/Proyecto-final-Code_Weaver/assets/124609988/3e251612-f218-4771-a9b1-5fc80c994236)
## Objetivo del proyecto
Este proyecto tiene el fin de implementar distintas herramientas o conceptos vistos durante el curso de Programación de Computadores para solucionar un problema/situación desarrollando un programa en Python.
## Problema/situación
El problema a solucionar es desarrollar un programa en python que simule un juego, en este caso, un ahorcado el cual se llamará Code_Weaver's Hangman game, mediante la aplicación de las herramientas o conceptos vista en el curso de Programación de Computadores.
### ¿Cómo se abordó el problema?
### 1) Diagrama de flujo:
Para entender cómo desarrollar el programa se planteó una serie de pasos, utilizando la herramienta Mermaid para realizar un diagrama con los pasos a seguir. 
```flowchart TD
    A(Bienvenida al juego) --> B[Elegir el idioma]
    B --> C[1.Español]
    B --> D[2.Inglés]
    C & D --> E[Elegir el modo de juego]
    E --> F[1.Individual]
    E --> G[2.Vs]
    F & G --> H[Escoger la categoría 1/9]
    H--> K[El programa elige una palabra al azar]
    K --> L[Escoger el nivel del juego]
    L --> M[Facil = 10 vidas]
    L --> N[Medio = 6 vidas]
    L--> O[Dificil = 4 vidas]
    M & N & O --> P[Se muestra la lista de guiones de acuerdo a la palabra escogida]
    P--> Q[Se pide a el/los jugador/es que ingresen una letra]
    Q --> R{Verificar: ¿la letra está en la palabra oculta?}
    R --> |sí| S[Se muestra la ubicación de la letra]
    R --> |no| T{¿la letra ya se había ingresado?}
    T --> |sí| U[Mostrar mensaje que indica repetición de letra]
    T --> |no| V[Vidas - 1]
    U & V & S--> W[se pide ingresar una nueva letra] --> R
    S --> X{¿letras ingresadas = palabra oculta?}
    X --> |sí| AB[Juego ganado] --> IJ[Mensaje de felicitaciones y se muestra la palabra oculta]
    X --> |no| W
    V --> EF{¿Vidas = 0?}
   EF --> |sí| GH[Juego perdido] --> KL[Mensaje de consolación y se muestra la palabra oculta]
   EF --> |no| W
   IJ & KL --> MN[Fin del juego]
```
![image](https://github.com/alejayz/Proyecto-final-Code_Weaver/assets/124609988/c657329c-43f2-4cbc-a01c-67416a256d37)
![image](https://github.com/alejayz/Proyecto-final-Code_Weaver/assets/124609988/a69f3192-3224-42e5-8ee3-72d2d7e60a23)


### 2) import
Se utiliza el sistema de importación (import) para traer las bibliotecas time y random, los cuales permiten aplicar diferentes funciones de tiempo y aleatoriedad, respectivamente en el codigo del programa.
```python
import random
import time
```
**random.choice():** esta función permite elegir un elemento de forma aleatoria de un conjunto de elementos, ya sea lista, tupla, diccionario,etc.
En este caso se eutilza esta función para escoger una palabra al azar de las listas de palabras para el juego.
```python
aleatoria=list(random.choice(profesiones).upper())
```
**time.sleep():** esta función permite realizar ratrdos de tiempo en cualquier parte del codigo del programa el cual se sguirá ejecuntando luego del tiempo indicado.
Dentro de este programa se utiliza esta fundción para establecer tiempos de espera entre distintos mensajes que arroja el programa.
```python
nombre = input("nombre jugador: ")
        time.sleep(2)
        print("¡Bienvenido " + nombre + ", empieza a divertirte!")
```
## Desarrollo
### Bienvenida
Al iniciar el juego se muestra un mensaje de bienvenida al usuario.
Se crea la variable `idioma` para que el/los jugador/es decida si quiere que el juego se presente en Español o en Inglés, y se presentan las categorías de palabras.
La variable `modo` permite elegir si el/los jugador/es quiere jugar de manera indivual o en Vs uno contra uno. Se ingresa el nombre del jugador.
`categoria` es la variable que permite elegir en qué categoría de las 9 que se presentan, se desea jugar.

```python
print ("-------¡¡¡Bienvenido a CODE_WEAVER'S HANGMAN GAME!!!-------")
time.sleep(3)


idioma=int(input("¿En qué idioma quieres jugar?\n 1)Español\n 2)Inglés\n Elige: ")) #Idioma en el que se llevará a cabo el juego
if idioma == 1: #Español
    profesiones=["abogado","actor","actris","agenteinmobiliario","agrigultor","antropologo","arquitecto","asesorempresarial","asesordeimagen","astronauta","bailarin","arrendero","biologo","bombero","cajero","camarero","camionero","cantante","carnicero","carpintero","cartero","cazador","cocinero","conductor","consejero","conserje","contador","decorador","dentista","deportista","detective","nutricionista","director","diseñador","economista","editor","escultor","estilista","farmaceutico","fisico","florista","fotografo","ganadero","gestor","guardiadeseguridad","herrero","historiador","informatico","ingeniero","jardinero","joyero","juez","leñador","maestro","marinero","mecanico","medico","militar","minero","modista","musico","niñera","obrero","oficinista","operariodeconstruccion","optometra","panadero","pastelero","periodista","pescador","piloto","pintor","policia","politico","portero","profesor","programador","publicista","psicologo","quimico","recepcionista","relojero","repartidor","mensajero","sastre","soldado","secretario","taxista","trabajadorsocial","traductor","vendedor","veterinario","zapatero","mayordomo","psiquiatra","investigador","modelo","fiscal","zoologo"]
    transporte=["bus","automovil","bicicleta","monopatin","tren","camion","metro","motocicleta","cuatriciclo","tractor","lancha","barco","buquedecarga","buquedeguerra","velero","canoa","kayak","submarino","motoacuatica","balsa","avion","avioneta","planeador","helicoptero","globoaeroestatico","zepelin","parapente","teleferico","cohete","transbordador","yate","autobus","propulsor","furgoneta","tanquedeguerra","velocipedo","vehiculotodoterreno","remolque","carrodegolf","quad","trolebus","motoelectrica","girobus","autocar","segway","monociclo","triciclo","silladeruedas","skate","dron","aladelta","avioncohete","ultraligero","jetpack","paracaidas","dirigible","ferrocarril","lancha","ferry","aerodeslizador","tabladesurf","trainera","barcaza","tranvia","limusina","taxi","carrodepolicia","ambulancia","scooter","camiondebomberos","camiondereciclaje","grua","montacargas","mezcladoradecemento","botederemo","carruaje","gondola","monorrail","microbus","convertible","trineodeperros","kart","vehiculohibrido","patrulladepolicia","motodenieve","busescolar","autobusdedospisos","naveespacial","transbordadorespacial","crucero","barcopirata","carro","vehiculo","cochefamiliar","lanchademotor","transatlantico","buquedepasajeros","barcopetrolero","botesalvavidas","bombardero","aviondecombate","avionjumbo"]
    verbos=["intercambiar","graduarse","adivinar","fabricar","memorizar","recomendar","susurrar","discutir","extinguirse","entrenar","buscar","sanar","entregar","preguntar","ensamblar","patrocinar","plantear","exprimir","trotar","asaltar","sembrar","calibrar","impresionar","saborear","incrementar","competir","esperar","cambiar","solucionar","entristecer","alegrar","existir","olvidar","perdonar","asegurar","conjugar","abrazar","explotar","daraluz","transmitir","vulnerar","respetar","investigar","vagar","cepillar","escribir","reestructurar","publicar","manejar","conducir","explorar","encantar","palidecer","mencionar","blindar","cacrecer","embrutecer","pensar","sobresalir","escupir","celebrar","mantener","soportar","herir","lanzar","trasnochar","cavar","arrestar","dirigirse","anunciar","asistir","entretener","acercarse","molestar","aparecer","abandonar","prohibir","avanzar","anunciar","disculparse","absorber","acentuar","pertenecer","completar","chequear","mandar","coronar","cometer","destruir","comprometer","ejecutar","pronunciar","castigar","requerir","recordar","fumar","silbar","herir","despertarse","difundir","golpear","columpiarse","pronosticar","prever","retirar","arrodillarse","tejer","contemplar","privar","implorar","superar","contenerse","contradecir","engañar","comparar","comprar","devolver","decepcionar","recoger","resaltar","implementar","recompensar","esparcir","comprender","presenciar","llevaracabo","admitir","emboscar","tenerimportancia","evaluar","reincidir","convertir","otorgar","indicar","rebotar","estropear","observar","vestir","posarse","residir","sobregirar","emprender","equivocarse","aguantar","confesarse","darzancadas","prosperar","abordar","reir","elegir","extender","convertirse","congelar","moler","sacudir","encoger","preparar","estudiar","descolorar","cortarpapel","maquillarse","desvestirse","imaginar"]
    nacionalidades=["afgana","alemana","arabe","argentina","australiana","belga","boliviana","brasileña","camboyana","canadiense","chilena","china","colombiana","coreana","costarricense","cubana","danesa","ecuatoriana","egipcia","salvadoreña","escocesa","española","estadounidense","estonia","etiope","filipina","finlandesa","francesa","galesa","griega","guatemalteca","haitiana","holandesa","hondureña","indonesa","inglesa","iraqui","irlandesa","irani","italiana","japonesa","jordana","laosiana","letonia","lituania","malaya","marroqui","mexicana","nicaraguense","noruega","neozelandesa","panameña","paraguaya","peruana","polaca","portuguesa","puertorriqueña","dominicana","rumana","rusa","sueca","suiza","tailandesa","taiwanesa","turca","ucraniana","uruguaya","venezolana","vietnamita","britanica","neerlandesa","checa","argelina","marfileña","nigeriana","sudanesa","congoleña","keniata","tanzana","angoleña","mozambiqueña","sudafricana","saudi","uzbeka","pakistani","india","bangladesi","birmana","surcoreana","austriaca","bielorusa","eslovaca","hungara","beliceña","groelandes","jamaiquina","albana","bulgara","croata","macedonia","maltes","moldava","eslovena","camerunes","caboverdiana","catari","yemeni","monaques","serbia","lesotense","armenia","guyanesa","surinamesa","arubeña","curazoleña","bahameña","trinitense","israeli","siria","namibia"]
    animales=["yeti","calamar","foca","delfin","pezleon","leonmarino","cachalote","ballenafranca","ballenaazul","anguilaelectrica","medusa","ballenagris","tiburonballena","sardina","manati","trucha","pulpo","tetradealetasangrante","sepia","pepinodemar","gamba","calderoncomun","cicliconacarado","pulpodeanillosazules","pezarquero","pezcoladeespada","caracoldemar","pezluna","tiburonblanco","arenque","ciclidocebra","dragondemar","carpa","pezespada","tortugamarina","tetracavernicola","pezglobo","pezmariposa","langosta","carpadorada","pezloro","atun","cerdomarino","salmon","almeja","coral","rodaballo","tortuga","mojarra","pezoscar","piraña","marsopas","pezvolador","bocadefuego","pinguino","bacalao","necora","acaraazul","caballitodemar","orca","peztelescopio","pezoso","erizodemar","surubi","estrellademar","tiburonperegrino","camello","lobo","topo","liebre","pantera","gallina","gato","perro","tarantula","oveja","cerdo","iguana","bufalo","gusano","mapache","alce","escorpion","elefante","dromedario","venado","osopolar","osopanda","osohormiguero","araña","osoperezoso","rinoceronte","mula","orangutan","raton","chita","avestruz","leopardo","gorila","cocodrilo","tigre","anaconda","serpiente","gallo","ñandu","caballo","cabra","jaguar","vaca","castor","rana","canguro","hamster","conejo","jirafa","lagartija","becerro","alacran","wmandril","armadillo","caiman","oso","camaleon","tortuga","arañaviuda","koala","ardilla","hormiga","burro","leon","mono","toro","chimpance","zorro","dinosaurio","unicornio","tucan","garzablanca","cebra","hipopotamo","abeja","aguila","antilope","avispa","bisonte","camaleon","cangrejo","canguro","cigueña","cisne","colibri","cucaracha","cuervo","golondrina","gorrion","grillo","hiena","jabali","pavoreal","renacuajo","ruiseñor","buitre","gacela","zarigueya","capibara","guacamayo","osodeanteojos","vibora","halcon"]
    alimentos=["espinaca","alcachofa","guisantes","tomate","pepinillo","zapotenegro","carneroja","pescado","pescadofrito","huevofrito","pavo","cereal","lentejas","mantequilla","queso","yogurtgriego","aceitedecoco","aceitedeaguacate","almendras","chirimoya","percaoceanica","semillasdechia","semillasdecalabaza","calabaza","remolacha","perejil","agua","mandarina","cebolla","repollorojo","pomelorosa","albahaca","almejas","cilantro","albaricoque","nueces","cerezasrojas","lechuga","platanverde","platanomauro","pimenton","salmonrojo","zanahoria","uvaspasas","brocoli","aguacate","arandano","arrozintegral","avenaintegral","berenjena","esparragos","espinacas","frambuesa","garbanzos","jaleareal","piña","coco","naranja","espagueti","pepino","dientesdeleon","emparedado","perrocaliente","hamburguesa","papasfritas","aceitedegirasol","almendratostada","avellana","chocolateblanco","colesdebruselas","ensalada","ensaladadefrutas","fresasconcrema","helado","judiaverde","lechecondensada","lechecuajada","margarina","mortadela","pancasero","panblanco","quesocrema","quesoparmesano","sandia","tortillaespañola","hamburguesadequeso","mayonesa","huevosrevueltos","salsadetomate","pollofrito","albondigas","carneasada","jugodemanzana","vinoblanco","filetedeatun","salchicas","galletas","vegetales","arosdecebolla","aguamineral","aguacongas","granada","pomelo","algodondeazucar","pasteldemanzana","tartadequeso","puredepapas","costilladecerdo","pasteldecarne","macarronesconqueso","pechugadepollo","aceitedeoliva","filetesdepescado","crispetas","gaseosas","panqueques","miel","cerveza","papas"]
    deportes=["Futbol","voleibol","baloncesto","rugby","ciclismo","patinaje","tenis","tenis de mesa","pingpong","esgrima","golf","aikido","karate","judo","beisbol","clavados","triatlon","levantamientodepesas","bolos","canotaje","futbolacuatico","raquetbol","softbol","caza","futbolamericano","acuatlon","natacion","badminton","polo","atletismo","biatlon","boxeo","tiroalblanco","breaking","gimnasiaritmica","gimnasiaartistica","luchalibre","trineo","patinajeartistico","remo","saltos","vela","tiro","taekwondo","salto de esqui","patinajedevelocidad","pesas","balonmano","patinajesobrehielo","hockeysobrehielo","parkour","paracaidas","ciclismodemontaña","natacion","escalada","esacladaenhielo","kayak","alpinismo","buceo","futbolsala","gimnasiaacrobatica","saltotriple","gimnasiadetrampolin","hockeysobrecesped","patinajedevelocidad","voleibolplaya","waterpolo","motocross","equitacion","nadosincronizado","ajedrez","bailedeportivo","motociclismo","yoga","Taichi","jiujitsu","Kungfu","senderismo","motociclismo","patinajeenlínea","pescadeportiva"]
    ropa=["pantalonazul","Pantalones","falda","vestido","camisa","camiseta","calcetines","zapaterozapatos","sueter","chaqueta","sombrero","pantalonescortos","pantalonesdemezclilla","chanclas","uniforme","traje","abrigo","camisetadetiras","camisetasinmangas","camisetaalcuerpo","camisetagrande","pantalonesdealgodon","pantalonesdelino","zapatosdeportivos","zapatosdetela","calcetinescortos","trajedebaño","gomadepelo","sueterligero","cahquetadepiel","chaquetagruesa","abrigodepiel","bufanda","guantes","gorrodeesqui","orejeras","miton","camisainteriortermica","chalecodeplumas","abrigodeplumas","mediasdeinvierno","boina","sueterdecuello","sueterdecuellodetortuga","calcetinesdeinvierno","sudadera","pants","tenis","bandaparalacabeza","sueterconcapucha","patinesdehielo","patinesenlinea","trajedebuceo","chalecosalvavidas","visoresacuaticos","blusa","esmoquin","faldalarga","faldacorta","minifalda","camisola","brasier","pantuflas","amison","bolso","monedero","aretes","billetera","pulseradeoro","tacones","botas","botasdetacon","botasdelluvia","batadebaño","impermeable","ropainterior"]
    casa=["sala","habitacion","cocina","piscina","freidoradeaire","horno","microondas","platos","escoba","computador","escritorio","edificioresidencial","cabaña","ventana","balcon","techo","cornisa","corredor","fachada","fuente","galeria","pasillo","entrada","escaleras","ascensor","azotea","pared","columna","patiotrasero","calefaccion","aireacondicionado","sotano","desvan","mansion","hacienda","jardin","baño","dormitorio","comedor","garage","portico","entrada","buzon","sillon","alfombra","chimenea","biblioteca","mesadecentro","mesaauxiliar","cortinas","ventiladordetecho","marcosdefoto","pinturas","lampara","armario","mesitadenoche","relojdespertador","tenedor","lavadora","estufa","lavanderia","oficina","gabinete","cafetera","batidora","servilleta","despensa","refrigerador","cucharas","tostadora","sabanas","almohada","papelhigienico","cepillodedientes","pastadedientes","lavamanos","estanteria","relojdepared","detergente","aspiradora","cuartodeservicio","utensiliosdecocina","abrelatas","sacacorchos","tabladeplanchar","secadora","botiquin","patiofrontal","plantabaja","tragaluz"]


    modo=int(input("¿En qué modo quieres jugar?\n 1)individual\n 2)Vs\n Elige: ")) #tipo de juego
    if modo==1: #individual
        nombre = input("nombre jugador: ")
        time.sleep(2)
        print("¡Bienvenido " + nombre + ", empieza a divertirte!")
    else: #uno contra uno
     nombreA=input("nombre jugador 1: ")
     nombreB=input("nombre jugador 2: ")
     time.sleep(2)
     print("Bienvenidos " + nombreA + " y " + nombreB + ", empiecen a divertirse!")
    
    categoria=int(input("¿En qué categoría quieres adivinar?\n 1)Profesiones\n 2)Transporte\n 3)Verbos\n 4)Nacionalidades\n 5)Animales\n 6)Alimentos\n 7)Deportes\n 8)Ropa\n 9)Casa\n Elige: " ))
    
```
```python
if idioma == 2: #Inglés
    profesiones=["lawyer","actor","actress","realestateagent","farmer","anthropologist","architect","businessadvisor","imageconsultant","astronaut","dancer","landlord","biologist","firefighter","cashier","waiter","truckdriver","singer","butcher","carpenter","postman","hunter","cook","driver","counselor","janitor","accountant","decorator","dentist","athlete","detective","nutritionist","director","designer","economist","publisher","sculptor" ,"stylist","pharmacist","physicist","florist","photographer","livestockfarmer","manager","securityguard","blacksmith","historian","computerscientist","engineer","gardener","jeweler","judge","woodcutter","teacher","sailor","mechanic","doctor","military","miner","dressmaker","musician" ,"nanny","worker","office worker","construction worker","optometrist","baker","pastry chef","journalist","fisherman","pilot","painter","police"," politician","janitor","teacher","programmer","publicist","psychologist","chemist","receptionist","watchmaker","deliveryboy","messenger","tailor","soldier" ,"secretary","taxi driver","social worker","translator","salesperson","veterinarian","shoemaker","butler","psychiatrist","researcher","model","prosecutor","zoologist"]
    transporte=["bus","car","bicycle","skateboard","train","truck","subway","motorcycle","quadcycle","tractor","boat","ship" ,"cargo ship","warship","sailboat","canoe","kayak","submarine","watercraft","raft","plane","airplane","glider","helicopter"," hotairballoon","zeppelin","paraglider","cable car","rocket","ferry","yacht","bus","propeller","van","wartank","speedo","allterrainvehicle","trailer","golf cart","quad","trolleybus","electric motorcycle","gyrobus","coach","segway","unicycle","tricycle","wheelchair","skate","drone","hang glider","planerocket","ultralight","jetpack","parachute","airship","railway","boat","ferry","hovercraft","surfboard","trainer" ,"barge","tram","limousine","taxi","police car","ambulance","scooter","fire truck","recycling truck","crane","forklift","cement mixer","boat","carriage","gondola","monorail","minibus","convertible","dogsled","kart","hybrid vehicle","police patrol","snowmobile","school bus","double-decker bus" ,"spaceship","space shuttle","cruise","pirate ship","car","vehicle","family car","motorboat","oceanliner","passenger ship","oil ship","lifeboat"," bomber","fighterplane","jumboplane"]
    verbos=["exchange","graduate","guess","manufacture","memorize","recommend","whisper","discuss","extinct","train","seek","heal" ,"deliver","ask","assemble","sponsor","pose","express","jog","assault","sow","calibrate","impress","savor"," increase","compete","wait","change","solve","sadden","rejoice","exist","forget","forgive","insure","conjugate","embrace" ,"explode","give birth","transmit","violate","respect","investigate","wander","brush","write","restructure","publish","handle"," drive","explore","charm","fade","mention","shield","grow","dullen","think","stand out","spit","celebrate","maintain","bear","hurt","throw","sleepup","dig","arrest","address","announce","attend","entertain","approach","annoy"," appear","abandon","forbid","advance","announce","apologize","absorb","accentuate","belong","complete","check","send","crown","commit","destroy","compromise","execute","pronounce","punish","require","remember","smoke","whistle","hurt","wakeup"," spread","hit","swing","predict","foresee","withdraw","kneel","weave","contemplate","deprive","implore","overcome","contain" ,"contradict","deceive","compare","buy","return","disappoint","collect","highlight","implement","reward","spread","understand"," witness","carryout","admit","ambush","haveimportance","evaluate","relapse","convert","grant","indicate","rebound","spoil","observe" ,"dress","perch","reside","overturn","undertake","makeamistake","endure","confess","stride","prosper","address","laugh","choose","extend","become","freeze","grind","shake","shrink","prepare","study","discolor","cutpaper","makeup","undress","imagine"]
    nacionalidades=["afghan","german","arabian","argentinian","australian","belgian","bolivian","brazilian","cambodian","canadian","chilean","chinese" ,"colombian","korean","costarican","cuban","danish","ecuadorian","egyptian","salvadoran","scottish","spanish","american","sstonian"," ethiopian","philippine","finnish","french","welsh","greek","guatemalan","haitian","dutch","honduran","indonesian","english","iraqi" ,"irish","iranian","italian","japanese","jordanian","laotian","latvian","lithuanian","malaysian","moroccan","mexican","nicaraguan","norwegian","newzealand","panamanian","paraguayan","peruvian","polish","portuguese","puertorican","dominican","romanian","russian","swedish","swiss" ,"thai","taiwanese","turkish","ukrainian","uruguayan","venezuelan","vietnamese","british","dutch","czech","algerian","ivorian"," nigerian","sudanese","congolese","kenyan","tanzanian","angolan","mozambican","southafrican","saudi","uzbek","pakistani","indian","bangladesi","burmese","southkorean","austrian","belarusian","slovak","hungarian","belizean","greenlandic","jamaican","albanian","bulgarian","croatian","macedonia","maltese","cameroonian","capeverdean","catari","yemeni","moldova","serbia","lesotense","armenian","guyanese","surinamese","aruban","curazoan","bahamian","trinidadian","israeli","syrian","namibian"]
    animales=["yeti","squid","seal","dolphin","lionfish","sealion","spermwhale","rightwhale","bluewhale","electriceel","jellyfish","graywhale","whaleshark","sardine","manatee","trout","octopus","bleedingfintetra","cuttlefish","seacucumber","shrimp","shortfinpilotwhale","pearlycyclic","blueringoctopus","archerfish","swordfish","seashell","moonfish","whiteshark","herring","zebrafish","seadragon","carp","swordfish","seaturtle","tetracavern","pufferfish","butterflyfish","lobster","carp","fishfish","tuna","seapig","salmon","clam","coral","turtle","turtle","mojarra","fish","piranha","porpoise","flying fish","firemouth","penguin","cod","necora","blueacara","seahorse","killerwhale","telescopefish","fishy","seaurchin","surubi","seastar","baskingshark","camel","wolf","mole","hare","panther","hen","cat","dog","tarantula","sheep","pig","iguana","buffalo","worm","raccoon","moose","scorpion","elephant","dromedary","deer","polar bear","bear","anteater","spider","slothbear","rhinoceros","mule","orangutan","mouse","cheetah","ostrich","leopard","gorilla","crocodile","tiger","anaconda","snake","rooster","nandu","horse","goat","jaguar","cow","beaver","frog","kangaroo","hamster","rabbit","giraffe","lizard","calf","scorpion","wmandrill","armadillo","caiman","bear","chameleon","turtle","spiderwidow","koala","ant","donkey","lion","monkey","chimpanzee","fox","dinosaur","unicorn","toucan","white heron","zebra","hippopotamus","bee","eagle","antelope","wasp","bison","chameleon","crab","kangaroo","stork","swan","hummingbird","cockroach","crow","swallow","sparrow","cricket","hyena","boar","peacock","tadpole","nightingale","vulture","gazelle","possum","capybara","macaw","spectacledbear","adder","hawk"]
    alimentos=["spinach","artichoke","peas","tomato","gherkin","black sapote","red","fish","friedfish","friedegg","turkey","cereal" ,"lentils","butter","cheese","greekyogurt","coconut oil","avocadooil","almonds","cherimoya","percaoceana","chiaseeds","pumpkinseeds","pumpkin"," beet","parsley","water","tangerine","onion","red cabbage","pink grapefruit","basil","clams","cilantro","apricot","walnuts","red cherries" ,"lettuce","green banana","banana","paprika","red salmon","carrot","raisins","broccoli","avocado","blueberry","brownrice","brownoatmeal"," eggplant","asparagus","spinach","raspberry","chickpeas","jelly","pineapple","coconut","orange","spaghetti","cucumber","teethoflion","sandwich","hot dog","burger","fries","sunfloweroil","roastedalmond","hazelnut","whitechocolate","brusselssprouts","salad","fruitsalad","strawberriesandcream","icecream","greenbean","condensedmilk","curdledmilk","margarine","mortadella","homemadebread","white bread","creamcheese","parmesancheese","watermelon","panishomelette","cheeseburger","mayonnaise","scrambledeggs","tomatosauce","friedchicken","meatballs","roastmeat","applejuice","whitewine","tunasteak","sausages","biscuits","vegetables","onionrings","mineral water","aguacongas","pomegranate","grapefruit","somethingsugar","applecake","cheesecake","mashedpotatoes","pork rib","meatloaf","macaroniandcheese","chickenbreast","oliveoil","fishfillets","crispets","sodas","pancakes","honey","beer","potatoes"]
    deportes=["football","volleyball","basketball","rugby","cycling","skating","tennis","tabletennis","pingpong","fencing","golf"," aikido","karate","judo","baseball","diving","triathlon","weightlifting","bowling","boating","watersoccer","racquetball","softball","hunting" ,"football","aquathlon","swimming","badminton","polo","athletics","biathlon","boxing","target shooting","breaking","rhythmicgymnastics","artisticgymnastics"," wrestling","sled","figureskating","rowing","jumping","sailing","shooting","taekwondo","skijumping","speedskating","weights","handball"," iceskating","icehockey","parkour","parachute","mountainbiking","swimming","climbing","icediving","kayak","climbing","diving","football","acrobaticgymnastics" ,"triplejump","trampolinegymnastics","fieldhockey","speedskating","beachvolleyball","waterpolo","motocross","horseriding","synchronizedswimming","chess","sportdance","motorcycling","yoga","Taichi","jiujitsu","Kungfu","hiking","motorcycling","inlineskating","sportfishing"]
    ropa=["bluepants","pants","skirt","dress","shirt","tshirt","socks","shoeshoes","sweater","jacket","hat","shorts","denimpants","flipflops","uniform","suit","coat","striptshirt","sleevelesstshirt","bodytshirt","bigtshirt","cottonpants","linenpants","sportsshoes","clothshoes","shortsocks" ,"swimsuit","hairband","lightsweater","furjacket","thickjacket","furcoat","scarf","gloves","skihat","earmuffs","mitten","thermalundershirt","downvest","downcoat","wintertights","beret","necksweater","turtlenecksweater","wintersocks","sweatshirt","pants","tennis","headband","hoodedsweater","iceskates","inlineskates","divingsuit","lifejacket","watervisors","blouse","tuxedo","longskirt","shortskirt","miniskirt","camisole","bra","slippers","amison","bag","purse","earrings","wallet","goldbracelet","heels","boots","highheeledboots","rainboots","bathrobe","raincoat","underwear"]
    casa=["livingroom","room","kitchen","swimmingpool","airfryer","oven","microwave","dishes","broom","computer","desk","residentialbuilding","cabin","window","balcony","roof","cornice","corridor","facade","fountain","gallery","hallway","entrance","stairs","elevator","roof","wall","column","backyard","heating","airconditioning","basement","attic","mansion","farmhouse","garden","bathroom","bedroom","diningroom","garage","porch","entrance","mailbox","armchair","carpet","fireplace","library","coffeetable","sidetable","curtains","ceilingfan","photoframes","paintings","lamp","wardrobe","nightstand","alarmclock","fork","washingmachine","stove","laundry","office","cabinet","coffeemaker","blender","napkin","pantry","refrigerator","spoons","toaster","sheets","pillow","toiletpaper","toothbrush","toothpaste","sink","shelf","wallclock","detergent","vacuumcleaner","utilityroom","kitchenutensils","canopener","corkscrew","ironingboard","dryer","firstaidkit" ,"frontpatio","groundfloor","skylight"]

    modo=int(input("What mode do you want to play?\n 1)individual\n 2)Vs\n choose: ")) #tipo de juego
    if modo==1: #individual
        nombre = input("player name: ")
        time.sleep(2)
        print("Welcome " + nombre + ", start having fun!")
    else: Vs uno contra uno
     nombreA=input("player name 1: ")
     nombreB=input("player name 2: ")
     time.sleep(2)
     print("Welcome " + nombreA + " and " + nombreB + ", start having fun!")

    categoria=int(input("What category do you want to guess in?\n 1)Professions\n 2)Transport\n 3)Verbs\n 4)Nationalities\n 5)Animals\n 6)Food\n 7)Sports\n 8)Clothes\n 9)House\n Choose: " ))
```
### Desarrollo del juego
En esta parte del programa se presentan las funciones:
**palabraAleatoria():** esta función permite elegir una palabra al azar de la categoria seleccionada dependiendo del idioma escogido.
**ahorcado():** esta funcion mustra la cantidad de vidas del/los jugador/es y muestra la interfaz gráfica del juego.
**letraIngresada():** esta funcion permite que el jugador ingrese letras para adivinar la palabra.
**palabraSecreta():** esta función muestra la palabra que se intentaba adivinar.
**espaciosPalSecreta():** sta función muestra la lista de guiones o espacios que tiene la palabra oculta.
```python
def palabraAleatoria():
        """
        Esta función permite elegir una palabra al azar de la categoria seleccionada.
        entradas: palabras de la lista de la categoría
        salidas: palabra aleatoria, lista de guiones bajos de acuerdo a al palabra
        """
        if categoria==1:
            aleatoria=list(random.choice(profesiones).upper())
            muestra=['_'] * len(aleatoria)
        elif categoria==2:
            aleatoria=list(random.choice(transporte).upper())
            muestra=['_'] * len(aleatoria)
        elif categoria==3:
            aleatoria=list(random.choice(verbos).upper())
            muestra=['_'] * len(aleatoria)
        elif categoria==4:
            aleatoria=list(random.choice(nacionalidades).upper())
            muestra=['_'] * len(aleatoria)
        elif categoria==5:
            aleatoria=list(random.choice(animales).upper())
            muestra=['_'] * len(aleatoria)
        elif categoria==6:
            aleatoria=list(random.choice(alimentos).upper())
            muestra=['_'] * len(aleatoria)
        elif categoria==7:
            aleatoria=list(random.choice(deportes).upper())
            muestra=['_'] * len(aleatoria)
        elif categoria==8:
            aleatoria=list(random.choice(ropa).upper())
            muestra=['_'] * len(aleatoria)
        else:
            aleatoria=list(random.choice(casa).upper())
            muestra=['_'] * len(aleatoria)
            
            return aleatoria,muestra,[]
```
```python
def ahorcado(nivel, intentos):
    
    """
    Esta funcion mustra la cantidad de vidas del/los jugador/es
    Entradas: número que representa el nivel
    salidas: cantidad de vidas
    """
    nivel=int(input("nivel: 1)fácil\n 2)meidio\n 3)difícil\n Elige: "))
    if nivel==1:
        vida=10
        if idioma ==1:
            print("tienes 10 vidas para adivinar =)")
            time.sleep(1) 
            print("¡son muchos intentos, aprovéchalos!")
        if idioma ==2:
            print("You have 10 lives to guess =)")
            time.sleep(1) 
            print("There are many attempts, take advantage of them!")
        
        if intentos==10:
            inten=["                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        elif intentos==9:
            inten=["         ---------|",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        elif intentos==8:
            inten=["        I---------|",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        elif intentos==7:
            inten=["        I---------|",
                   "        I         |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        elif intentos==6:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        elif intentos==5:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "        |         |",
                   "        |         |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        elif intentos==4:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "       /|\        |",
                   "      / | \       |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        elif intentos==3:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "       /|\        |",
                   "      / | \       |",
                   "       / \        |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        elif intentos==2:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "       /|\        |",
                   "      / | \       |",
                   "       / \        |",
                   "      /   \       |",
                   "                  |",
                   "__________________|"]
            return inten
        
        elif intentos==1:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "       /|\        |",
                   "      / | \       |",
                   "       / \        |",
                   "      /   \       |",
                   "      \   /       |",
                   "__________________|"]
            return inten
        
        elif intentos==0:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "       /|\        |",
                   "      / | \       |",
                   "       / \        |",
                   "      /   \       |",
                   "     _\   /_      |",
                   "__________________|"]
            return inten
            
            
    elif nivel==2:
        vida=6
        if idioma ==1:
            print("tienes 6 vidas para adivinar :)")
            time.sleep(1) 
            print("¡son suficientes intentos para lograrlo!")
        if idioma ==2:
            print("You have 6 lives to guess =)")
            time.sleep(1) 
            print("There are enough attempts to achieve it!")
        if intentos==6:
            inten=["                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        if intentos==5:
            inten=["        I---------|",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        if intentos==4:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        if intentos==3:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "        |         |",
                   "        |         |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        if intentos==2:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "       /|\        |",
                   "      / | \       |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        if intentos==1:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "       /|\        |",
                   "      / | \       |",
                   "       / \        |",
                   "      /   \       |",
                   "                  |",
                   "__________________|"]
            return inten
        
        if intentos==0:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "       /|\        |",
                   "      / | \       |",
                   "       / \        |",
                   "      /   \       |",
                   "     _\   /_      |",
                   "__________________|"]
            return inten
    
    
            
    else:
        vida=4
        if idioma == 1:
            print("tienes solo 4 vidas para intentarlo :-/")
            time.sleep(1)
            print("¡mucha suerte!")
        if idioma == 2:
            print("You only have 4 lives to try")
            time.sleep(1)
            print("Good luck")
        if vida==4:
            inten=["                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        if vida==3:
            inten=["        I---------|",
                   "        I         |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        if vida==2:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "       /|\        |",
                   "      / | \       |",
                   "                  |",
                   "                  |",
                   "                  |",
                   "__________________|"]
            return inten
        
        if vida==1:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "       /|\        |",
                   "      / | \       |",
                   "       / \        |",
                   "      /   \       |",
                   "                  |",
                   "__________________|"]
            return inten
        
        if vida==0:
            inten=["        I---------|",
                   "        I         |",
                   "        O         |",
                   "       /|\        |",
                   "      / | \       |",
                   "       / \        |",
                   "      /   \       |",
                   "     _\   /_      |",
                   "__________________|"]
            return inten  
            
    return vida
                       

def letraIngresada(letras)->str:
    """
    Esta funcion permite que el jugador ingrese letras para adivinar la palabra.
    Entradas: el jugador ingresa una letra por la consola
    Salidas: letra ingresada
    """
    letras=input(("ingrese una letra o consonante: "))
    return letras

def palabraSecreta(pal):
    """
    Esta función muestra la palabra que se intentaba adivinar
    Entradas: palabra para adivinar
    Salidas: palabra secreta
    """
    
    print("La palabra secreta era:", " ".join(pal))
    
def espaciosPalSecreta(muestra, letrasMal):
    """
    Esta función muestra la lista de guiones o espacios que tiene la palabra oculta.
    Entradas: las letras de la palabra oculta
    salidas: lista de guiones de la palabra oculta
    """
    for guion in muestra:
        print(guion, end=' ')
    print()
    print()
    if len(letrasMal) > 0:
        print("Letras erróneas:", *letrasMal)
        
        
        
        
def iniciarAhorcado():
    """
    Esta es la funcion principal que da inicio al juego. Llama a las otras funciones para poder empezar a adivinar.
    Entradas: los parametros de las otras funciones
    Salidas: la lista de guiones, letras ingresadas, palabra oculta.
    """
    palabraIn=letraIngresada(i)
    palabraSecreta = palabraAleatoria(categoria)
    muestra = palabraAleatoria(muestra)
    correcto = True
    while correcto:
     for i in palabraSecreta:
         if i.upper() in muestra:
             print(i, end = ' ')
         else:
            print('_', end = " ")
            
    print("\n")
    intent = ahorcado(intento) 
    intento = input(f' errores {intent}. Ingrese nueva letra: ')
    muestra.append(intento.upper())
    
    if palabraIn not in palabraSecreta:
        letraMal = []
        letraMal.append(palabraIn.upper())
```
## Requisitos para ejecutar el programa
Para ejecutar este programa se debe tener instalada la versión más reciente de Python.

# ¡Gracias por la atención!


