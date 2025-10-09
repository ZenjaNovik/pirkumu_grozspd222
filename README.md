# pirkumu_grozspd222
# pirkumu_grozspd

class Prece:
    def __init__(self, nosaukums, cena):
        self.nosaukums = nosaukums
        self.cena = cena
    
    def get_info(self):
        return f"{self.nosaukums}: {self.cena} EUR"

class PirkumuGrozs:
    def __init__(self):
        self.preces = []  # Saraksts ar precēm
    
    def pievienot_preci(self, prece):
        self.preces.append(prece)
        print(f"Prece '{prece.nosaukums}' pievienota grozam.")
    
    def aprēķināt_summu(self):
        summa = sum(prece.cena for prece in self.preces)
        return summa
    
    def izvadīt_grozu(self):
        if not self.preces:
            print("Grozs ir tukšs.")
            return
        print("Pirkumu grozs:")
        for prece in self.preces:
            print(prece.get_info())
        print(f"Kopējā summa: {self.aprēķināt_summu()} EUR")

# Galvenā programma
if __name__ == "__main__":
    grozs = PirkumuGrozs()  # Izveido objektu
    prece1 = Prece("Āble", 1.5)  # Izveido preci
    prece2 = Prece("Banāns", 2.0)
    
    grozs.pievienot_preci(prece1)  # Izsauc metodi
    grozs.pievienot_preci(prece2)
    
    if grozs.aprēķināt_summu() > 0:  # Pārbauda nosacījumu
        grozs.izvadīt_grozu()  # Izvada rezultātu
    else:
        print("Nav preču grozā.")
