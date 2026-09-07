# proyecto-3er-semestre
clientes
void main() {

    Scanner teclado = new Scanner(System.in);
    String id;
    String nombre;
    int Edad;
    double peso;
    double altura;
    int op;

    clientes C1= null;

    ArrayList<clientes> lstclientes = new ArrayList<>();

    boolean estado = true;

    while (estado) {

        System.out.println("""
                
                MENU DE CLIENTES
                1. CREAR UN CLIENTE
                2. CALCULAR IMC
                3. CLASIFICAR IMC
                4. INGRESAR NUEVO PESO
                5. MOSTRAR CLIENTES
                6. MOSTRAR CLIENTES POR ID
                7.SALIR
                
                """);

            System.out.println("SELECCIONE UNA OPCION DEL MENU");
            op = teclado.nextInt();

            switch (op) {

            case 1:
            System.out.println("CREAR CLIENTE");

            System.out.println("INGRESE ID");
            id = teclado.next();

            System.out.println("INGRESE SU NOMBRE");
            nombre = teclado.next();

            System.out.println("INGRESE SU EDAD");
            int edad = teclado.nextInt();

            System.out.println("INGRESE SU PESO");
            peso = teclado.nextDouble();

            System.out.println("INGRESE SU ALTURA");
            altura = teclado.nextDouble();

            C1 = new  clientes(
                    id,
                    nombre,
                    edad,
                    peso,
                    altura
            );
            lstclientes.add(C1);
            System.out.println("CLIENTE CREADO CORRECTAMENTE");
            break;

            case 2:

            System.out.println("MOSTRAR IMC POR ID");

            System.out.println("INGRESE EL ID DEL CLIENTE");
            String codigo_1 = teclado.next();

            clientes encontrado_1 = null;

            for (clientes c : lstclientes) {
                if (c.getId().equalsIgnoreCase(codigo_1)) {
                    encontrado_1 = c;
                    break;
                }
            if (encontrado_1!= null){

            System.out.println(("EL IMC DEL USUARIO:" + encontrado_1.getNombre()));
            System.out.println("IMC: " + encontrado_1.calcularIMC());

            }else{

                System.out.println(("NO ENCONTRADO"));
            }
            }
            break;

                case 3:

                if (C1 != null) {
                    System.out.println("CLASIFICACION DEL IMC");
                    System.out.println("CLIENTE: " + C1.getNombre());
                    System.out.println("IMC: " + C1.calcularIMC());

                }else{
                    System.out.println("NO SE HA CREADO UN OBJETO");
                    }
                    break;

                    case 4:

                        System.out.println("ACTUALIZAR PESO");
                        System.out.println("INGRESE EL ID DEL CLIENTE:");
                        String codigoPeso = teclado.next();
                        clientes clientePeso = null;

                        for (clientes c : lstclientes) {
                            if (c.getId().equalsIgnoreCase(codigoPeso)) {
                                clientePeso = c;
                                break;
                            }
                        }
                        if (clientePeso != null) {
                            System.out.println("INGRESE EL NUEVO PESO:");
                            double nuevoPeso = teclado.nextDouble();
                            boolean actualizado = clientePeso.actualizarpeso(nuevoPeso);
                            if (actualizado) {
                                System.out.println("PESO ACTUALIZADO CORRECTAMENTE");
                            } else {
                                System.out.println("EL PESO DEBE SER MAYOR A 0");
                            }
                        } else {
                            System.out.println("CLIENTE NO ENCONTRADO");
                        }
                        break;
                        case 5:

                         System.out.println("MOSTRAR CLIENTE");

                         if (lstclientes.isEmpty()) {
                        System.out.println("NO HAY CLIENTE");

                        }else{

                        for (clientes c :lstclientes){
                            System.out.println(c);
                        }
                    }
                        break;

                        case 6:

                        System.out.println("MOSTRAR CLIENTES POR ID");
                        String codigo;
                        System.out.println("INGRESE EL ID A BUSCAR");
                        codigo = teclado.next();

                        clientes encontrado = null;

                        for (clientes c : lstclientes) {
                            if (c.getId().equalsIgnoreCase(codigo)) {
                                encontrado = c;
                            }
                        }
                        if (encontrado!= null) {
                            System.out.println(encontrado);
                        }else {
                            System.out.println("NO ENCONTRADO");
                        }
                            break;

                        case 7:
                        System.out.println("SALIR");
                        estado = false;
                        break;


            }
                }

            }
