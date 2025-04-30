```mermaid

---
title: Robot minisumo
---
classDiagram
direction TB
    class RobotEnemigo {
	    float: Tamaño
	    float: Peso
	    str: Nombre
	    +Moverse_atras()
	    +Moverse_adelante()
	    +Girar_en_su_eje()
	    +Girar_derecha()
	   +Girar_izquierda() 
    }
    class Minisumo {
	    float : Tamaño
	    float : Peso
	    str : Nombre
	    Parar()
	    +Moverse_atras()
	    +Moverse_adelante()
	    +Girar_en_su_eje()
	    +Girar_derecha()
	   +Girar_izquierda()
    }
    class Puente_H {
	    str : Tipo_de_puente_H
	    float : Voltage_de_entrada
	    float : Voltaje_de_salida
	    +Encender_motor()
	    +Apagar_motor()
	    +Cambiar_velocidad_motor()
        +Cambiar_giro_motor()
    }
    class Motores {
	    float : Relacion_del_motor
	    int : RPM
	    +Girar_adelante()
	    +Girar_atras()
    }
    class Sensores {
	    str : Tipo_de_lectura
	    str : Ubicacion
	    +Medir_señal()
    }
    class Micro_controlador {
	    str : Tipo_de_microcontrolador
	    float : Voltaje_de_salida
	    +Enviar_codigo()
    }
    class Carcaza {
	    str: Material
	    float: Tamaño
	    float: Peso
    }
    class Sensor_ultrasonido {
	str: Sensor_ultrasonido
    }
    class Sensor_piso {
	str: Sensor_inflarojo
	  
    }
    class Sensor_inflarojo {
	str: Sensor_inflarojo
    }

    Sensores <|-- Sensor_ultrasonido
    Sensores <|-- Sensor_piso
    Sensores <|-- Sensor_inflarojo
    Micro_controlador --> Puente_H : controla
    Puente_H --> Motores : controla
    Micro_controlador --> Sensores : controla
    Minisumo --> RobotEnemigo : detecta
    RobotEnemigo --> Minisumo : detecta
    Minisumo *-- "1" Carcaza
    Minisumo *-- "2" Motores
    Minisumo *-- "1 o 2" Puente_H
    Minisumo *-- "1 o 2" Micro_controlador
    Minisumo *-- "1 o mas" Sensores

