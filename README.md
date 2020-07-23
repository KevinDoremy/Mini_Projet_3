
```plantuml
@startuml DiagrammeClassMarwan

skinparam monochrome true
skinparam linetype polyline
skinparam classAttributeIconSize 0



interface LuminaireDecorateur{
    - emplacement : String
    + allumer() : void
    + eteindre() : void
    + augmenterIntensite() : void
    + diminuerIntensite() : void

}
class SimpleLuminaire implements LuminaireDecorateur {
- emplacement : String

}

class LuminaireAccessoire implements LuminaireDecorateur{
- emplacement : String
}

class Ventilateur extends LuminaireAccessoire{
- emplacement : String

}

interface BoutonCommande {
    + execute() : void
}

class On implements BoutonCommande {
- LuminaireDecorateur: Luminaire
    + execute() : void
}

class Off implements BoutonCommande {
    - LuminaireDecorateur: Luminaire
    + execute() : void
}

class IntensitePlus implements BoutonCommande {
    - LuminaireDecorateur: Luminaire
+ execute() : void
}

class IntensiteMoins implements BoutonCommande { 
    - LuminaireDecorateur: Luminaire
+ execute() : void
}

class Telecommande {
    - boutonsListe : ArrayList<BoutonCommande>
    + addBouton() : ArrayList<BoutonCommande>
}

class Configuration {
    - telecommande : Telecommande
    - luminaires : ArrayList<Luminaire>
    + associerLuminaireAvecBoutons(luminaire : LuminaireDecorateur) : void
}


On *-- LuminaireDecorateur
Off *-- LuminaireDecorateur
IntensitePlus *-- LuminaireDecorateur
IntensiteMoins *-- LuminaireDecorateur

Configuration "1" --> "1" Telecommande
Telecommande --* "*" BoutonCommande
Configuration --> LuminaireDecorateur
LuminaireAccessoire o--  "1" LuminaireDecorateur: Decorate
@enduml
```

# Pseudo-Code

ArrayList<LuminaireDecorateur> luminairesDecorateurs = new ArrayList<LuminaireDecorateur>();
luminaireDecocateurs.add(Luminaire )


for (LuminaireDecorateur luminaire : luminairesDecorateurs) {
    if(luminaire instanceof simpleLuminaire){
        Commande allumerLumiere = new On(luminaire);
        Commande eteindreLumiere = new OFF(luminaire);
        Commande augmenterIntensiteLuminaire = new IntensitePlus(luminaire);
        Commande diminuerIntensiteLuminaire = new IntensiteMoins(luminaire);
        telecommande.addBouton(allumerLumiere);
        telecommande.addBouton(eteindreLumiere);
        telecommande.addBouton(augmenterIntensiteLuminaire);
        telecommande.addBouton(diminuerIntensiteLuminaire);
    }
    if (luminaire instance LuminaireAccessoire) {
        Commande allumerAccessoire = new On(luminaire);
        Commande eteindreAccessoire = new OFF(luminaire);
        Commande augmenterIntensiteAccessoire = new IntensitePlus(luminaire);
        Commande diminuerIntensiteAccessoire = new IntensiteMoins(luminaire);
        telecommande.addBouton(allumerAccessoire);
        telecommande.addBouton(eteindreAccessoire);
        telecommande.addBouton(augmenterIntensiteAccessoire);
        telecommande.addBouton(diminuerIntensiteAccessoire);
    }
    
}


