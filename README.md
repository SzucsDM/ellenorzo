# ellenorzo
Hazi:
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


/**************/
A csoport
1. Csinálj egy mátrixot(3x3). Függvényben számítsd ki az átló szorzatát. Mainben számold ki a második sor összegét. Kérd be a felhasználótól az egyik sor indexét és azt a sort irasd ki.

using System;

class Program
{
    static int[,] CreateMatrix()
    {
        int[,] matrix = new int[3, 3];

        Console.WriteLine("Mátrix feltöltése:");
        for (int i = 0; i < 3; i++)
        {
            for (int j = 0; j < 3; j++)
            {
                Console.Write($"Mátrix[{i}][{j}]: ");
                matrix[i, j] = int.Parse(Console.ReadLine());
            }
        }

        return matrix;
    }

    static int CalculateDiagonalProduct(int[,] matrix)
    {
        int product = 1;
        for (int i = 0; i < 3; i++)
        {
            product *= matrix[i, i];
        }
        return product;
    }

    static void Main(string[] args)
    {
        int[,] matrix = CreateMatrix();
        int diagonalProduct = CalculateDiagonalProduct(matrix);

        Console.WriteLine("Az átlók szorzata: " + diagonalProduct);

        int secondRowSum = 0;
        for (int j = 0; j < 3; j++)
        {
            secondRowSum += matrix[1, j];
        }

        Console.WriteLine("A második sor összege: " + secondRowSum);

        Console.Write("Kérem a kívánt sor indexét (0, 1 vagy 2): ");
        int rowIndex = int.Parse(Console.ReadLine());

        if (rowIndex >= 0 && rowIndex < 3)
        {
            Console.Write("A kiválasztott sor: ");
            for (int j = 0; j < 3; j++)
            {
                Console.Write(matrix[rowIndex, j] + " ");
            }
        }
        else
        {
            Console.WriteLine("Érvénytelen sor index.");
        }
    }
}
/*****************/
2. Csinálj egy karakter típusú mátrixot (4x5) amelyben 4 darab 5 betűs szót adsz meg. (char[ , ] matrix = new matrix [4,5] = {'a', 'a',  'a', 'a', 'a', 
-II-,
-II-,
-II-};. Ezt a mátrixot függvényében alakitsd át úgy hogy az első és a második sor helyet cserél. Függvényben irasd ki. Majd csinálj egy függvényt amely megforditja a szavakat. Ezt is függvényben irasd ki.

using System;

class Program
{
    static void PrintMatrix(char[,] matrix)
    {
        for (int i = 0; i < 4; i++)
        {
            for (int j = 0; j < 5; j++)
            {
                Console.Write(matrix[i, j] + " ");
            }
            Console.WriteLine();
        }
    }

    static void SwapRows(char[,] matrix)
    {
        for (int j = 0; j < 5; j++)
        {
            char temp = matrix[0, j];
            matrix[0, j] = matrix[1, j];
            matrix[1, j] = temp;
        }
    }

    static void ReverseWords(char[,] matrix)
    {
        for (int i = 0; i < 4; i++)
        {
            string word = "";
            for (int j = 0; j < 5; j++)
            {
                word += matrix[i, j];
            }

            char[] charArray = word.ToCharArray();
            Array.Reverse(charArray);
            word = new string(charArray);

            for (int j = 0; j < 5; j++)
            {
                matrix[i, j] = word[j];
            }
        }
    }

    static void Main(string[] args)
    {
        char[,] matrix = new char[4, 5]
        {
            {'a', 'a', 'a', 'a', 'a'},
            {'b', 'b', 'b', 'b', 'b'},
            {'c', 'c', 'c', 'c', 'c'},
            {'d', 'd', 'd', 'd', 'd'}
        };

        Console.WriteLine("Eredeti mátrix:");
        PrintMatrix(matrix);

        SwapRows(matrix);
        Console.WriteLine("Mátrix a sorok felcserélése után:");
        PrintMatrix(matrix);

        ReverseWords(matrix);
        Console.WriteLine("Mátrix a szavak megfordítása után:");
        PrintMatrix(matrix);
    }
}
/**************/
3. 
Csinálj egy torta classt, aminek van egy string fajtája, int emelete és bool díszített. Ezeket rakd be egy paraméterbe. Egy metoduson belül ellenőrizd hogy a torta díszítve van vagy nincs, amennyiben nincs állítsd be hogy díszítve legyen. Csinálj egy metódust ami ellenőrzi hogy a szintek száma páros vagy páratlan, és ezt a végén írd oda az elméletek mellé. Hívd meg ezeket az adatokat egy toStringbe, és a Main programban hozz létre három tortát és irasd ki az adatait.

using System;

class Torta
{
    public string Fajta { get; set; }
    public int Emelet { get; set; }
    public bool Diszitett { get; set; }

    public Torta(string fajta, int emelet, bool diszitett)
    {
        Fajta = fajta;
        Emelet = emelet;
        Diszitett = diszitett;
    }

    public void EllenorizDiszites()
    {
        if (!Diszitett)
        {
            Diszitett = true;
            Console.WriteLine("A tortát most díszítették meg.");
        }
        else
        {
            Console.WriteLine("A torta már díszítve van.");
        }
    }

    public void EllenorizEmeletekParos()
    {
        if (Emelet % 2 == 0)
        {
            Console.WriteLine("Az emeletek száma páros.");
        }
        else
        {
            Console.WriteLine("Az emeletek száma páratlan.");
        }
    }

    public override string ToString()
    {
        return $"Torta: Fajta: {Fajta}, Emelet: {Emelet}, Díszített: {Diszitett}";
    }
}

class Program
{
    static void Main(string[] args)
    {
        Torta torta1 = new Torta("Csokoládé", 2, false);
        Torta torta2 = new Torta("Málna", 3, true);
        Torta torta3 = new Torta("Vanília", 4, false);

        Console.WriteLine(torta1);
        torta1.EllenorizDiszites();
        torta1.EllenorizEmeletekParos();

        Console.WriteLine(torta2);
        torta2.EllenorizDiszites();
        torta2.EllenorizEmeletekParos();

        Console.WriteLine(torta3);
        torta3.EllenorizDiszites();
        torta3.EllenorizEmeletekParos();
    }
}
/***********/

B. csoport
1. Csináljd egy 5x5 matrixot, toltsd fel 25-100 ig random szamokkal. Függvényben számitsd ki az átlójának összegét.

2. Csinálj egy 3x5 karaktertipusu matrixot, függvényben cseréld fel 2 sorát, függvénnyel irasd ki és függvénnyel ird ki valamelyik sort visszafelé.

3. Csinálj egy auto osztályt, megvoltak adva a tulajdonsagai, csinálj metodusokat amik beállitjak az egyik tulajdonsagot alapbol true ra, egy masik metodus megnézi hogy az auto regisztrációs száma 6 karakterből áll e, ha nem akkor átírja "000000". Az utolsó metódus a kiiratás.
A main programban letre kell hozni 3 autot.

1. using System;

class Program
{
    static void Main(string[] args)
    {
        int[,] matrix = GenerateRandomMatrix(5, 5, 25, 100);
        int diagonalSum = CalculateDiagonalSum(matrix);

        Console.WriteLine("5x5 mátrix:");
        PrintMatrix(matrix);

        Console.WriteLine("Az átló összege: " + diagonalSum);
    }

    static int[,] GenerateRandomMatrix(int rows, int cols, int min, int max)
    {
        Random rand = new Random();
        int[,] matrix = new int[rows, cols];
        for (int i = 0; i < rows; i++)
        {
            for (int j = 0; j < cols; j++)
            {
                matrix[i, j] = rand.Next(min, max + 1);
            }
        }
        return matrix;
    }

    static int CalculateDiagonalSum(int[,] matrix)
    {
        int sum = 0;
        for (int i = 0; i < matrix.GetLength(0); i++)
        {
            sum += matrix[i, i];
        }
        return sum;
    }

    static void PrintMatrix(int[,] matrix)
    {
        for (int i = 0; i < matrix.GetLength(0); i++)
        {
            for (int j = 0; j < matrix.GetLength(1); j++)
            {
                Console.Write(matrix[i, j] + "\t");
            }
            Console.WriteLine();
        }
    }
}
/*********/
2. using System;

class Program
{
    static void Main(string[] args)
    {
        char[,] charMatrix = CreateCharMatrix();
        Console.WriteLine("Eredeti mátrix:");
        PrintCharMatrix(charMatrix);

        SwapRows(charMatrix, 0, 1);
        Console.WriteLine("Mátrix az első és második sor felcserélése után:");
        PrintCharMatrix(charMatrix);

        PrintReversedRow(charMatrix, 2);
    }

    static char[,] CreateCharMatrix()
    {
        char[,] matrix = new char[3, 5]
        {
            {'a', 'b', 'c', 'd', 'e'},
            {'1', '2', '3', '4', '5'},
            {'f', 'g', 'h', 'i', 'j'}
        };
        return matrix;
    }

    static void SwapRows(char[,] matrix, int row1, int row2)
    {
        for (int i = 0; i < matrix.GetLength(1); i++)
        {
            char temp = matrix[row1, i];
            matrix[row1, i] = matrix[row2, i];
            matrix[row2, i] = temp;
        }
    }

    static void PrintCharMatrix(char[,] matrix)
    {
        for (int i = 0; i < matrix.GetLength(0); i++)
        {
            for (int j = 0; j < matrix.GetLength(1); j++)
            {
                Console.Write(matrix[i, j] + " ");
            }
            Console.WriteLine();
        }
    }

    static void PrintReversedRow(char[,] matrix, int rowIndex)
    {
        for (int j = matrix.GetLength(1) - 1; j >= 0; j--)
        {
            Console.Write(matrix[rowIndex, j]);
        }
        Console.WriteLine();
    }
}
/***********/
3. using System;

class Program
{
    static void Main(string[] args)
    {
        Auto auto1 = new Auto("ABC123", "VW", "Golf", 2010);
        Auto auto2 = new Auto("12345", "Ford", "Focus", 2015);
        Auto auto3 = new Auto("ABCD12", "Toyota", "Corolla", 2022);

        auto1.SetDefaultOption(true);
        auto1.CheckAndFixRegistrationNumber();
        auto1.PrintCarInfo();

        auto2.SetDefaultOption(true);
        auto2.CheckAndFixRegistrationNumber();
        auto2.PrintCarInfo();

        auto3.SetDefaultOption(true);
        auto3.CheckAndFixRegistrationNumber();
        auto3.PrintCarInfo();
    }
}

class Auto
{
    public string RegistrationNumber { get; set; }
    public string Make { get; set; }
    public string Model { get; set; }
    public int Year { get; set; }

    public Auto(string regNum, string make, string model, int year)
    {
        RegistrationNumber = regNum;
        Make = make;
        Model = model;
        Year = year;
    }

    public void SetDefaultOption(bool option)
    {
        // A metódus beállítja az alapértelmezett opciót
    }

    public void CheckAndFixRegistrationNumber()
    {
        if (RegistrationNumber.Length != 6)
        {
            RegistrationNumber = "000000";
        }
    }

    public void PrintCarInfo()
    {
        Console.WriteLine($"Autó: {Make} {Model}, Gyártási év: {Year}, Rendszám: {RegistrationNumber}");
    }
}




