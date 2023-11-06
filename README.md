# ellenorzo
Feladat Írj egy C# osztályt, ami egy
Legendás Vitéz objektumot valósít meg.


A Legendás Vitéznek az alábbi
tulajdonságai vannak:

Titkos Kód:
Azonosító a vitéz számára (string típusú).
Varázserő:
Az erő, amellyel a vitéz rendelkezik (egész szám, 10 és 20 közötti
véletlenszám).
Küzdőkészség:
A vitéz ügyessége a harcban (egész szám, 10 és 20 közötti véletlenszám).



Az osztálynak legyen egy
konstruktora, ami a vitéz nevét kapja paraméterként, és inicializálja a
varázserőt és a küzdőkészséget véletlenszerű értékekkel 10-20 között.


Az osztálynak legyen egy harcol metódusa, amiben legyen a következő:
Készíts
két változót, ami 1-6 közötti véletlen értékeket vesz fel. Az egyikkel
az egyik vitéz küzdőkészségét csökkentsd, a másikkal a másikét. Készíts
egy változót, amiben eltárolod a két vitéz küzdelemkészségének a
különbségét. Amennyiben a különbség pozitív, az első vitéz győzött, ha
pedig negatív, akkor a másik.

Készíts egy Main metódust, ahol létrehozol két Legendás Vitézt és őket
küzdelemre
bocsátod, amíg a küzdelem döntetlen nem lesz. (tehat amig a harc
visszatero erteke nem false) és írasd ki a megfelelő kimenetelt.


/******************/
using System;

class vitezek
{
    private string titkoskkod;
    private int varazsero;
    private int kepesseg;

    public vitezek(string name)
    {
        titkoskkod = name;
        Random random = new Random();
        varazsero = random.Next(10, 21);
        kepesseg = random.Next(10, 21);
    }

    public bool harc(vitezek ellenseg)
    {
        Random random = new Random();
        int tamadas = random.Next(1, 7);
        int ellensegestamadas = random.Next(1, 7);

        kepesseg -= ellensegestamadas;
        ellenseg.kepesseg -= tamadas;

        int tehetsegkulonbozes = kepesseg - ellenseg.kepesseg;

        if (tehetsegkulonbozes > 0)
        {
            Console.WriteLine(titkoskkod + " gyozott a kuzdelemben");
        }
        else if (tehetsegkulonbozes < 0)
        {
            Console.WriteLine(ellenseg.titkoskkod + " gyozott a kuzdelemben");
        }
        else
        {
            Console.WriteLine("A kuzdelem dontetlen");
            return false;
        }

        return true;
    }
}

class Program
{
    static void Main()
    {
        vitezek lovag1 = new vitezek("Vitez Janos");
        vitezek lovag2 = new vitezek("Vitez Peter");

        bool harcvege;
        do
        {
            harcvege = lovag1.harc(lovag2);
        } while (harcvege);
        Console.ReadKey();
    }
}
