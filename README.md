class Prece:
    def __init__(self, nosaukums, cena, daudzums):
        self.nosaukums = nosaukums
        self.cena = cena
        self.daudzums = daudzums
    
    def get_info(self):
        return f"{self.nosaukums}: {self.cena} EUR, daudzums: {self.daudzums}"

class Noliktava:
    def __init__(self):
        self.preces = []
    
    def pievienot_preci(self, prece):
        self.preces.append(prece)
        print(f"Prece '{prece.nosaukums}' pievienota.")
    
    def parādīt_preces(self):
        if not self.preces:
            print("Noliktava tukša.")
            return
        for prece in self.preces:
            print(prece.get_info())
    
    def kārtot_pēc_cenas(self):
        self.preces.sort(key=lambda x: x.cena)
        print("Kārtots pēc cenas.")
    
    def dzēst_preci(self, nosaukums):
        for prece in self.preces:
            if prece.nosaukums.lower() == nosaukums.lower():
                self.preces.remove(prece)
                print(f"Prece '{nosaukums}' dzēsta.")
                return
        print("Prece nav atrasta.")
    
    def meklēt_preci(self, nosaukums):
        for prece in self.preces:
            if prece.nosaukums.lower() == nosaukums.lower():
                print(prece.get_info())
                return
        print("Prece nav atrasta.")
    
    def statistika(self):
        if not self.preces:
            print("Nav preču.")
            return
        cenas = [p.cena for p in self.preces]
        print(f"Vidējā cena: {sum(cenas)/len(cenas):.2f} EUR")
        print(f"Lielākā cena: {max(cenas)} EUR")
        print(f"Mazākā cena: {min(cenas)} EUR")
        print(f"Kopējais daudzums: {sum(p.daudzums for p in self.preces)}")

def izvēlne():
    noliktava = Noliktava()
    # Pievienot sākotnējās preces ar cenām un daudzumiem
    noliktava.pievienot_preci(Prece("Āble", 1.5, 10))  # Prece: Āble, Cena: 1.5 EUR, Daudzums: 10
    noliktava.pievienot_preci(Prece("Banāns", 2.0, 15))  # Prece: Banāns, Cena: 2.0 EUR, Daudzums: 15
    noliktava.pievienot_preci(Prece("Apelsīns", 1.8, 20))  # Prece: Apelsīns, Cena: 1.8 EUR, Daudzums: 20
    
    while True:
        print("\n1. Pievienot preci\n2. Parādīt preces\n3. Kārtot pēc cenas\n4. Dzēst preci\n5. Meklēt preci\n6. Statistika\n7. Iziet")
        try:
            izvēle = int(input("Izvēle: "))
        except:
            print("Ievadiet skaitli.")
            continue
        if izvēle == 1:
            n = input("Nosaukums: ").strip()
            if not n: continue
            try:
                c = float(input("Cena: "))
                d = int(input("Daudzums: "))
                if c < 0 or d < 0: print("Negatīvs nav atļauts."); continue
            except: print("Skaitlis."); continue
            noliktava.pievienot_preci(Prece(n, c, d))
        elif izvēle == 2: noliktava.parādīt_preces()
        elif izvēle == 3: noliktava.kārtot_pēc_cenas(); noliktava.parādīt_preces()
        elif izvēle == 4: n = input("Nosaukums: ").strip(); noliktava.dzēst_preci(n)
        elif izvēle == 5: n = input("Nosaukums: ").strip(); noliktava.meklēt_preci(n)
        elif izvēle == 6: noliktava.statistika()
        elif izvēle == 7: break
        else: print("1-7.")

if __name__ == "__main__":
    izvēlne()
