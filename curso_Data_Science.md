# Curso Data Science
## Modulo 1: operaciones con String

Es importante saber los inidices de los str, comienzan en 0




| M | A | R | I | A |   | I | G | N | A | C | I | A |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10| 11| 12|

    name="maria ignacia"

    name[::2]   #toma los index pares
        result= 'mrainca'
    
    name[0:5:2] #toma los pares hasta el index 5
        result= 'mra'

la suma de str es:

    a='1'
    b='2'
    c=a+b
        c=12

mayusculas y minusculas:

    b= name.upper()
    print(b)

    result= MARIA IGNACIA

    c=b.lower()
    print(c)
    
    result= maria ignacia

funcion "find" encuentra el index del primer elemento que se menciona en ()
 y "split" lo separa el str y lo convierte en *lista*

    name.find('ig')
        result=6

    name.split()
        result= ['maria', 
        'ignacia']    #lista


RegEx incluye search, split, findall, y sub.

    import re

    s1 = "Michael Jackson is the best"

    pattern = r"Jackson"

    result = re.search(pattern, s1)

    if result:
        print("Match found!")
    else:
        print("Match not found.")

tambien puede buscar cantidad de digitos o cantidad de letras: \
\d: digitos \
\w: letras \
\W: cualquier caracter que no sea letra
\s: espacio 

    pattern = r"\d\d\d\d\d\d\d\d\d\d"  # Matches any ten consecutive digits
    text = "My Phone number is 1234567890"
    match = re.search(pattern, text)

    if match:
        print("Phone number found:", match.group())
    else:
        print("No match")

*findall()*

    pattern = r"\W"         # Matches any non-word character
    text = "Hello, world!"
    matches = re.findall(pattern, text)

    print("Matches:", matches)


*split()*

    s1='La ignacia es bacan'

    res=re.split("\s", s1)          #\s: espacios
    print(res)

        result= ['la','ignacia', 'es', 'bacan']

*sub()*

    re.sub('Vilna','ignacia',s1)

        result= 'la vilna es bacan'

## Modulo 2: estructuras de datos
# Listas y tuples
\
# tuples:
 elementos (str,int,float) separados por comas dentro de parentesis. Su *type()* es tuple

\
*Se pueden sumar tuple:

    tuple1=("hola", 1, 2.7)
    tuple2=("chao",2)
    tuple_total=tuple1+tuple2
        result= ("hola", 1, 2.7, "chao",2)



* Dentro de un tuple pueden haber más tuples "nesting"

    ejemplo=(1,("hola", 66),2.333,("que",3, "hago"))
    ejemplo[1]  ->  ("hola", 66)
    #Para acceder al tuple dentro del tuple:
    ("hola", 66)[0]   ->   "hola"
    #ó
    ejemplo[1][0]


los index se verían como a continuación:
|tuple:  |1| ("hola", 66)|2.333 |("que",3, "hago") |
|--------|-|-------------|------|------------------|
|ejemplo |0| 1           | 2    | 3                | 
|ejemplo | |   [0]   [1] |      | [0]  [1]   [2]   | 

Se puede acceder a cada elemento del string de un tuple:

ejemplo[1][0][0]  -> h
ejemplo[1][0][1]  -> o
ejemplo[1][0][2]  -> l
ejemplo[1][0][3]  -> a

# Listas

elementos separados por comas dentro de corchetes 
Se pueden incluir tuples dentro de listas:

    List1=["Tony", 11, ("Moca", "cata"), ["coco", 1]]


Tienen las mismas caracteristicas que un tuple
* Puedes acceder a listas o tuples dentro de una lista a través del index

    List1[2]  ->  ("Moca", "cata")

* Puedes aplicar slicing:

    List1[2:4]= [("Moca", "cata"),["coco", 1]]

* Puedes combinar listas sumandolas o usando *.extend*

    Lista_total=List1+ [202,"yoyo"]
        Lista_total  --> ["Tony", 11, ("Moca", "cata"), ["coco", 1],202,"yoyo"]

    ó

    List1.extend([202,"yoyo"])

*.append* agrega cosas extra pero como solo 1 elemento nuevo:

    List1.append([202,"yoyo"])  -->  ["Tony", 11, ("Moca", "cata"), ["coco", 1],202,"yoyo",[202,"yoyo"]]

* se cambia un elemento de una lista definiendolo de nuevo:

    List1[2]= 10
    List1 -->  ["Tony", 11, 10, ["coco", 1],202,"yoyo",[202,"yoyo"]]

* para elmiminar se usa *del()*

    del(List1[6])  --> ["Tony", 11, 10, ["coco", 1],202,"yoyo"]

* Se puede usar split para convertir un str a una lista utilizando un caracter especifico que los separa:

    "a,b,c,d".split(",")        #los separará por coma
    result --> ["a","b","c","d"]

* Se puede clonar una lista usando ":", lo que evitará que cambie la nueva lista al modificar la lista original (List1)

    List2= List1[:]

* Para buscar el index de algo especifico se usa *.index('palabra_que_queremos_Encontrar')*
    List1.index("Tony") --> 0

# sets

No guardan la pòsicion de los elementos \
solo hay un unico elemento de cada uno en los sets (no hay duplicados)

Se especifican por los corchetes {}

    set1={"pop", "rock","soul","rock","disco"}
        result --> {'rock','pop','soul','disco'}

* convertis lista en set usar *set(lista aca)*

    set(List1)

* se agregar datos al set con *.add()*

    set1.add('regge')
        result --> {"pop", "rock","soul","rock","disco", "regge"}

* eliminar un dato del set con *.remove*

    set1.remove("pop")
        result --> { "rock","soul","rock","disco", "regge"}

* se puede revisar si un elemento esta en el set usando *in*

    "rock" in set1
        result --> True

* operaciones

Si se tienen dos set se puede encontrar la interseccion de ambos set (los elementos en comun de ambos) usando **&**

    set1={"pop","metal","soul","rock","disco"}
    set2={"pop","rock", "classic"}
    set3=set1 & set2
    set3 --> {"pop","rock"}

* Se pueden unir dos set con *.union()*

    set1.union(set2) --> {"pop","metal","soul","rock","disco", "classic"}    

* Para encontrar los elementos diferentes usar *.difference()*
OJO: si es setA.difference(set_B) mostrara los elementos que solo estan en setA, excluyendo los elementos de la interseccion de ambos y tambien los elementos que solo estan en setB

    set1={"pop","metal","soul","rock","disco"}
    set2={"pop","rock", "classic"}
    set1.difference(set2) --> {"disco","soul", "metal"}
    set2.difference(set1) --> {"classic"}

* se puede revisar si un set es subconjunto de otro set usando *.issubset()*

    set4={"rock","pop","disco"}
    set4.issubset(set1) --> True

# Dictionaries

No tienen elementos e index como las listas o tuples. \
Tienen Keys ( son direcciones y que no necesariamente tienen que ser enteros ) y valores (parecido a los elementos) \
Se denotan por {}
Las keys deben ser inmutables y unicas
ejemplo:

    {'key1': 1, 'key2':"hol",'key3':[1,2,3],'key4':(4,4,4),('key5'):5 }

ejemplo 2:
    {"Thriller":1982, "Back in black": 1980, "the dark side of the moon": 1980}

key= nombre del album
valor= año de estreno

* Para acceder a los valores se utiliza *DICT[key]*

    DICT["Back in black"] --> 1980

tambien agrega mas filas a un diccionario 

    DICT["graduation"] = "2007"
        result --> 
        {"Thriller":1982, "Back in black": 1980, "the dark side of the moon": 1980, "graduation": 2007}

* se elimina una key con *del()*
 
    del(DICT['Thriller'])

* para verificar si hay un key en el diccionario se usa *in*

    "Starboy" in DICT --> false

* para ver todas las keys en el diccionario se usa *.keys()* , el resultado es una lista

DICT.keys() --> ["Thriller":1982, "Back in black": 1980, "the dark side of the moon": 1980, "graduation": 2007]

* para ver los valores se usa *.values()*
DICT.values() -> ['1982','1980','1980','2007']

## Modulo 3: Python programming fundamentals

bla bla bla
hola 
