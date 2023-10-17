# Proyectos
//Programa que al ingresar nombre y edad en años de 4 personas, calcula el promedio de edades en meses y lo muestra en pantalla
    //almacena su nombre, edad y el promedio en archivo y muestra la informacion de las personas que tienen mas de 144 meses de edad
    class Program
    {
        static StreamWriter Escribir;
        static StreamReader Leer;
        public struct registro
        {
            public string nombre;
            public int EdadAños;
            public int EdadMeses;
        }
        static void Main(string[] args)
        {
            //Identificación del programa en pantalla
            Console.WriteLine("MB21020Evaluacion3 Promedio de edades");
            Console.WriteLine("Autor: Fabiola Maria Monge Blanco");
            Console.WriteLine("Grupo de Laboratorio: 33");
            Console.WriteLine("Grupo de teorico: 4\n");
            Console.Title = "Promedio de edades";

            //Declaración de variables
            int prom;

            Console.WriteLine("\n------------Ingreso De Datos--------------");
            registro[] persona = new registro[4];
            LeerDatos(persona);// Llama al método para leer el nombre de la persona
            CalcularEdadMeses(persona);// Llama al método para calcular la edad en meses
            prom = CalcularPromedio(persona);// Llama al método para calcular el promedio de edades en meses

            //Datos de salida
            Console.WriteLine("\n");
            Console.WriteLine("El promedio de edades es:" + prom +  "meses");

            Console.WriteLine("------------Información--------------");
            Escribir = new StreamWriter("Archivo.txt", true);

            for (int i = 0; i < persona.Length; i++)
                if (persona[i].EdadMeses > 144)
                {
                Console.WriteLine("Informacion de la persona {0}:", i + 1);
                Console.WriteLine("Nombre: {0}", persona[i].nombre);
                Console.WriteLine("Edad: {0}", persona[i].EdadAños);
                Console.WriteLine("----------------------------------------------------------------");
                }
                Console.WriteLine("El promedio de edades es:" + prom +  "meses");
            
            Escribir.Close();
            Leer = new StreamReader("Archivo.txt", true);
            string texto = "";
            texto = Leer.ReadToEnd();
            Console.WriteLine(texto);
            Leer.Close();
            Console.ReadKey();
        }
        //Métodos

        //Método para leer los datos de la persona
        public static void LeerDatos(registro[] persona)
        {
            for (int i = 0; i < persona.Length; i++)
            {
                registro dato = new registro();
                Console.WriteLine("Persona {0}", i + 1);
                Console.WriteLine("Introduzca su nombre:");
                dato.nombre = Console.ReadLine();
                if (!dato.nombre.Equals("0") && dato.nombre.Length > 0) {
                    do
                    {
                        Console.WriteLine("Introduzca su edad en años:");
                         dato.EdadAños = int.Parse(Console.ReadLine());
                    } while (dato.EdadAños <= 0);
                }
                    
                Console.WriteLine("----------------------------------------------------------------");
                persona[i] = dato;
            }
                return;
        }
        //Método para calcular la edad en meses
        public static void CalcularEdadMeses(registro[] persona)
        {

            for (int i = 0; i < persona.Length; i++)
            {
                persona[i].EdadMeses = persona[i].EdadAños * 12;
            }
            return;
        }
        //Método para calcular el promedio de edades
        public static int CalcularPromedio(registro[] persona)
        {
            int suma;
            suma = 0;
           
            for (int i = 0; i < persona.Length; i++)
            {
                suma = persona[i].EdadMeses / 4;
            }  
            return suma; 
        }
           
        }
    }
    
