# conceptos-java-
// ABSTRACTA
abstract class Restaurante {
    // ENCAPSULAMIENTO
    private String nombre;
    private int nuEmpleados;

    public Restaurante(String nombre, int nuEmpleados) {
        this.nombre = nombre;
        this.nuEmpleados = nuEmpleados;
    }

    public String getNombre() { return nombre; }

    // MÉTODO ABSTRACTO
    public abstract String recomendacion();

    // SOBRECARGA
    public double propina(double cuenta) {
        return cuenta * 0.10;
    }
    public double propina(double cuenta, double porcentaje) {
        return cuenta * porcentaje;
    }
}

// HERENCIA
class RestauranteItaliano extends Restaurante {
    public RestauranteItaliano(String nombre, int nuEmpleados) {
        super(nombre, nuEmpleados);
    }

    // SOBREESCRITURA
    @Override
    public String recomendacion() {
        return "Restaurante excelente calidad " + getNombre();
    }
}

class RestauranteSushi extends Restaurante {
    public RestauranteSushi(String nombre, int nuEmpleados) {
        super(nombre, nuEmpleados);
    }

    @Override
    public String recomendacion() {
        return "Pida sushi en " + getNombre();
    }
}

public class Main {
    public static void main(String[] args) {
        // POLIMORFISMO
        Restaurante r1 = new RestauranteItaliano("Roma", 5);
        Restaurante r2 = new RestauranteSushi("Tokio", 8);

        System.out.println(r1.recomendacion());
        System.out.println(r2.recomendacion());
        System.out.println(r1.propina(100));
        System.out.println(r1.propina(100, 0.15));
    }
}
