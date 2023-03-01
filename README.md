# Codigos
son los códigos que he realizado en clases
#dia 16-feb-2023 sosa vera jesus eduardo 
#personaje y conbate RPG 
class personaje :
    def __init__(self,nombre,inteligencia,defensa,ataque,vida) -> None:   #aki se declaran las variables que se van a utilisar :v
      self.nombre =nombre
      self.inteligencia=inteligencia
      self.defensa=defensa
      self.ataque=ataque
      self.vida=vida 
        
    def atributos(self): #esta es una funcion para poder ver los atributos de los personajes 
       print(self.nombre,":",sep="")
       print(".inteligecia: ",self.inteligencia)
       print(".defensa: ",self.defensa)
       print(".ataque: ",self.ataque)
       print(".vida:",self.vida)

    def esta_vivo(self):
        return self.vida>0  #se verifica que el personaje esta vivo si es verrdadero devolvera un true sino False

    def morir(self): #use esta funcion para poder ver si un personaje estaba vivo o no  
        self.vida = 0
        print(self.nombre, "ha muerto")
    
    def daño(self, enemigo): #aki se realisa el daño 
        return self.ataque- enemigo.defensa
    
    def atacar(self, enemigo): #funcion para atacar puse una condicion y es que si el ataque es menor que uno un 0 o
        daño = self.daño(enemigo) # numeros negativos poner el daño a uno pues la defensa del enemigo es mayor
        if daño<1:
            daño=1
        enemigo.vida = enemigo.vida - daño
        print(self.nombre, "ha realizado", daño, "puntos de daño a", enemigo.nombre)
        if enemigo.esta_vivo():
            print("Vida de", enemigo.nombre, "es", enemigo.vida)
        else:
            enemigo.morir()

class guerrero(personaje): #esta hereda la clase de personaje para crear una nueva 
    def __init__(self, nombre, inteligencia, defensa, ataque, vida,espada) -> None:
        super().__init__(nombre, inteligencia, defensa, ataque, vida)
        self.espada=espada  
    def atributos(self):
        super().atributos()
        print(".espada: ",self.espada) 
    
    def daño(self, enemigo):
        super().daño(enemigo)
        return self.ataque*self.espada-enemigo.defensa
          

def combate(jugador_1, jugador_2): #la funcion que realisa la magia es la encargada de aser que los dos personajes conbatan
    turno = 0                       #combatan
    while jugador_1.esta_vivo() and jugador_2.esta_vivo():
        print("\nTurno", turno)
        print(">>> Acción de ", jugador_1.nombre,":", sep="")
        jugador_1.atacar(jugador_2)
        if jugador_2.esta_vivo():
             print(">>> Acción de ", jugador_2.nombre,":", sep="")
             jugador_2.atacar(jugador_1)
             turno = turno + 1
    if jugador_1.esta_vivo():
        print("\nHa ganado", jugador_1.nombre)
    elif jugador_2.esta_vivo():
        print("\nHa ganado", jugador_2.nombre)
    else:
        print("\nEmpate")   

#esto de aki llama alas clases personaje y guerrero para crear un objeto
personaje_1=personaje("eduardo",15,12,30,100)
personaje_2=guerrero("enemigo",10,12,20,100,5)
personaje_1.atributos()
personaje_2.atributos()      

combate(personaje_1, personaje_2)#finalmente conbaten (el guerrero esta roto :v)










#autor=sosa vera jesus eduardo
