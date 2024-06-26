# README
## Leer la Wiki para más detalles y evidencias: 
https://github.com/LuisAngelRD/Rueda_LibretaDirecciones/wiki

## Descripción
Este proyecto está destinado a crear una libreta de direcciones, en donde se despliega un menú interactivo para poder elegir entre varias opciones disponibles, el usuario deberá indicarle las acciones al programa para poder darle seguimiento a las funciones donde el programa desplegará los registros de manera ordenada separada por los campos proporcionados.
# Diagrama de clases UML
![AddressBook](https://github.com/LuisAngelRD/Rueda_LibretaDirecciones/assets/163966681/15cd9d09-487c-4eb2-8b4f-dca1e9643624)
# Funcionamiento
## Opción a)
El usuario indica que se desea cargar una serie de textos separados por un salto de línea, en donde cada uno contendrá información necesaria para llenar los registros. Es de suma importancia recordar que estos registros llevan un orden específico, siendo como primer dato a ingresar el nombre de la persona, seguido de su apellido, posteriormente debe encontrarse el dato correspondiente a la calle de residencia, seguido de la ciudad, el estado, el número postal, el número telefónico y por último una dirección de correo electrónico.

## Opción b)
El usuario indica que se desea agregar manualmente un nuevo registro en el AddressBook, en donde se realizará una serie de entradas dependiendo de lo solicitado, manteniendo el mismo orden ya antes visto en la opción a) siendo la primera entrada de dato el nombre de la persona, hasta llegar finalmente al correo electrónico. De igual forma, el programa siempre informará en todo momento cuál es el dato que se requiere al usuario.

Al terminar las entradas, el registro se encontrará disponible para su despliegue en las opciones posteriores.

## Opción c)
El usuario indica que se desea borrar una dirección de la libreta. El programa pedirá al usuario ingresar el apellido de la persona que se desea eliminar el registro, esto de modo más accesible para poder encontrar el registro correcto. Posteriormente, el programa despliega todos los resultados concordantes con el apellido ingresado, siendo una numeración en orden alfabético de la A-Z. Cada dirección contará con un número asignado a esta misma iniciando por el número 1-Límite, en donde el usuario deberá digitar el número identificador de la entrada a eliminar. En el momento en el que el usuario realiza la acción, la dirección es eliminada permanentemente del AddressBook.

## Opción d)
El usuario indica que se desea buscar una dirección en concreto. Para realizar esto, el usuario deberá ingresar el apellido de la persona en cuestión, y al igual que en la opción anterior, se desplegará la lista de todos los resultados concordantes con el apellido ingresado anteriormente. En este caso, no se puede mostrar solo un resultado en caso de haber más de una persona con el mismo apellido, ya que al buscarlo por este mismo, el programa arrojará todos los resultados concordantes. El usuario podrá encontrar todas las personas con ese apellido, así como sus datos de dirección en la libreta en orden alfabético.

## Opción e)
El usuario indica que se desea mostrar un listado de todas las direcciones del AddressBook en un orden alfabético. Es importante recordar que se recomienda haber ingresado ya sea por una carga de archivo o manualmente, al menos un registro de dirección, de lo contrario no se mostrarán direcciones y el AddressBook estará vacío.

## Opción f)
El usuario indica que se desea finalizar el proceso de ejecución del programa. Al momento de ser digitada la entrada con la letra f, el programa se detendrá exitosamente. Es importante recordar que al momento de realizar esta acción, el AddressBook no guarda permanentemente ninguna dirección, siendo necesario volver a cargar o ingresar manualmente direcciones en futuras ejecuciones del programa.

## Limitaciones
El programa no guarda los registros de las entradas ingresadas, será necesario volver a ingresar registros de entradas en las futuras ejecuciones para poder usar el AddressBook satisfactoriamente.
El programa puede llegar a tener un error persistente en la opción a) Upload from a file, en caso de que el archivo txt no se encuentre en la ruta correcta para su lectura y obtención de datos.

# Clases

## AddressBookApplication

### Descripción
La clase `AddressBookApplication` es la clase principal de la aplicación de libreta de direcciones, su responsabilidad principal es iniciar la aplicación y mostrar el menú principal.

### Métodos
- `main(String[] args)`: Método estático principal que inicia la aplicación, crea una instancia de `AddressBook` y `Menu`, y luego muestra el menú principal llamando a `displayMenu()` del `Menu`.

---

## Menu

### Descripción
La clase `Menu` maneja la interacción con el usuario a través de un menú de opciones permite al usuario cargar entradas desde un archivo, agregar nuevas entradas, eliminar entradas, buscar entradas y listar todas las entradas.

### Atributos
- `private final AddressBook addressBook`: Una referencia a la instancia singleton de `AddressBook`.

### Métodos
- `public Menu()`: Constructor que inicializa la libreta de direcciones obteniendo la instancia única de `AddressBook`.
- `public void displayMenu()`: Muestra el menú principal y maneja la selección de opciones del usuario en un bucle hasta que el usuario decida salir.
- `private void loadEntries(Scanner scanner)`: Solicita al usuario el nombre de un archivo y carga las entradas desde ese archivo a la libreta de direcciones.
- `public void addEntry(Scanner scanner)`: Solicita al usuario la información necesaria para crear una nueva entrada de dirección y la añade a la libreta de direcciones.
- `public void removeEntry(Scanner scanner)`: Solicita al usuario el inicio del apellido para buscar y eliminar la entrada correspondiente de la libreta de direcciones.
- `public void findEntry(Scanner scanner)`: Solicita al usuario el inicio del apellido para buscar entradas que coincidan y las muestra.
- `public void listEntries()`: Lista todas las entradas de la libreta de direcciones ordenadas alfabéticamente por el primer nombre.

---

## AddressBook

### Descripción
La clase `AddressBook` contiene todas las entradas de la libreta de direcciones y utiliza el patrón Singleton para asegurarse de que solo haya una instancia de `AddressBook`.

### Atributos
- `private List<AddressEntry> addressEntryList`: Una lista que contiene todas las entradas de direcciones.
- `private static AddressBook instance`: La instancia única de `AddressBook`.

### Métodos
- `private AddressBook()`: Constructor privado para evitar la creación directa de instancias.
- `public static AddressBook getInstance()`: Método estático que retorna la instancia única de `AddressBook`.
- `public List<AddressEntry> getAddressEntryList()`: Retorna la lista de entradas de direcciones.
- `public void list()`: Lista todas las entradas de direcciones ordenadas alfabéticamente por el primer nombre.
- `public void remove(AddressEntry addressEntry)`: Elimina una entrada de dirección de la lista.
- `public void add(AddressEntry addressEntry)`: Añade una nueva entrada de dirección a la lista.
- `public List<AddressEntry> find(String startOfLastName)`: Busca y retorna las entradas de dirección que coincidan con el inicio del apellido dado.
- `public void loadFromFile(String fileName) throws IOException`: Carga entradas de dirección desde un archivo.

---

## AddressEntry

### Descripción
La clase `AddressEntry` representa una única entrada de dirección en la libreta de direcciones.

### Atributos
- `private String firstName`: Primer nombre.
- `private String lastName`: Apellido.
- `private String street`: Calle.
- `private String city`: Ciudad.
- `private String state`: Estado.
- `private int zip`: Código postal.
- `private String phone`: Número de teléfono.
- `private String email`: Correo electrónico.

### Métodos
- `public AddressEntry(String firstName, String lastName, String street, String city, String state, int zip, String phone, String email)`: Constructor que inicializa una entrada de dirección con los datos proporcionados.
- `public String getFirstName()`: Retorna el primer nombre.
- `public void setFirstName(String firstName)`: Establece el primer nombre.
- `public String getLastName()`: Retorna el apellido.
- `public void setLastName(String lastName)`: Establece el apellido.
- `public String getStreet()`: Retorna la calle.
- `public void setStreet(String street)`: Establece la calle.
- `public String getCity()`: Retorna la ciudad.
- `public void setCity(String city)`: Establece la ciudad.
- `public String getState()`: Retorna el estado.
- `public void setState(String state)`: Establece el estado.
- `public int getZip()`: Retorna el código postal.
- `public void setZip(int zip)`: Establece el código postal.
- `public String getPhone()`: Retorna el número de teléfono.
- `public void setPhone(String phone)`: Establece el número de teléfono.
- `public String getEmail()`: Retorna el correo electrónico.
- `public void setEmail(String email)`: Establece el correo electrónico.
- `public String toString()`: Retorna una cadena que representa la entrada de dirección con toda la información de contacto.

## Gracias por leer
