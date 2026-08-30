struct Numero {
    valor: u64,
} 

impl Numero{
    //constructor
    fn new(valor: u64) -> Numero {
        Numero{ valor }
    }

    fn espar(&self) -> bool{
        self.valor %2 == 0
    }

    fn cantdigitos(&self) -> u64{
        let mut n = self.valor;
        let mut cantidad = 0;
        while n > 0{
            cantidad += 1;
            n = n/10;
        }
        cantidad
    }

    fn esmayor(&self, x:u64) ->bool{
        self.valor > x
    }

    //Metodo que devuelva la suma de todos los numeros naturales del valor, incluido el valor
    //ejemplo: valor = 5 = 1 + 2 + 3 + 4 + 5 = 15
    fn sumanat(&self) -> u64{
        let mut suma = 0;
        for i in 1..=self.valor{
            suma = suma + i;
        }
        suma
    }

    //1.- Metodo que devulve potencia propia: valor elevado a valor.
    fn potencia(&self) -> u64 {
        self.valor.pow(self.valor as u32)
    }

    //2.- Metodo que devuelve si el valor es multiplo de "n".
    fn multiplo(&self) -> u64 {
        let mut cont: u64 = 0;
        for i in 1..=self.valor{
            if self.valor % i == 0{
                cont += 1;
            }
        }
        cont
    }

    //Metodo que devuelve la cantidad de digitos impares.
    //El metodo "impares" devuelve la cantidad de numeros impares que hay en su composicion 
    //por ejemplo 11 esta compuesto por 2 numeros impares (1 y 1)
    fn impares(&self) -> u64 {
        let mut n: u64 = 0;
        let mut valor:u64 = self.valor;

        while valor > 0{
            if (valor % 10) %2 != 0{
                n += 1;
            }
            valor /= 10;
        }
        n
    }

    //1.- invertir los digitos del numero
    fn invertir(&self) -> u64 {
        let mut invertido: u64 = 0;
        let mut n= self.valor;
        while n > 0{
            let digito = n % 10;
            invertido = invertido * 10 + digito;
            n /= 10;
        }
        invertido

    } 


    //2.- es capicua?
    fn capicua(&self) -> bool{
        let mut n = self.valor;
        let mut invertido = 0;

        while n > 0{
            let digito = n % 10;
            invertido = invertido * 10 + digito;
            n /= 10;
        }
        invertido == self.valor
    }

    //3.- Obtener la raiz digital de 2134 es: 2 + 1 + 3 + 4 = 10
    // (como 10 tiene 2 digitos 1 + 0 = 1) raiz digital  2134 es  = 1
    fn raizdig(&self) -> u64 {
        let mut n = self.valor;
        while n >= 10 {
            let mut suma = 0u64;
            while n > 0 {
                suma += n % 10;
                n /= 10;
            }
            n = suma;
        }
        n
    }

}

fn main() {
    //la instancia
    let n = Numero::new(8);
    let m =Numero::new(6);

    println!("El valor actual de n de la instancia n es:{}", n.valor);
    println!("El valor es par?: {}", n.espar());
    println!("La cantidad de digitos del valor de la instancia es: {}", n.cantdigitos());
    println!("El valor es mayor que el numero x?: {}", n.esmayor(77));
    println!("La suma natural del valor es: {}", n.sumanat());
    println!("La potencia de valor es: {}", n.potencia());
    println!("Los multiplos son: {}", n.multiplo());
    println!("El total de numeros impares es: {}", n.impares());
    println!("El total de numeros impares es:{}", m.impares());
    println!("El numero invertido es: {}", n.invertir());
    println!("El numero es capicua?: {}", n.capicua());
    println!("la raiz digital es: {}", n.raizdig());
}
