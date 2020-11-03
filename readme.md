# Introduktion till C++

## Löneökning

Den här uppgiften är tänkt att ge en liten introduktion till C++ och visa hur man kan skapa små enkla program.

### Uppgift

Skriv av lösningen, men lista ut vad den gör och kommentera koden.
Spara filen med namnet uppgift1.cpp

### Problem

Företaget du jobbar på har haft en utdragen löneförhandling men har landat i en löneökning för samtlig personal på 2,6%.
Skapa ett program som frågar efter nuvarande lön och sedan räknar ut den retroaktiva utbetalningen samt vad den nya lönen blir.
Använd en konstant för att spara procentsatsen för löneökningen.
Man ska kunna köra om uträkningen utan att behöva starta om programmet.

### Testcase

Om en anställd har 23000:- i lön ska den retroaktiva utbetalningen för de senaste 6 månaderna vara 3682:- och den nya månadslönen ska vara 24214:-.

### Lösning

```c++
#include <iostream>

using namespace std;

const double PERCENT = 2.6;

int main(void){
    int currentWage = 0;
    int newWage = 0;
    int retroactiveWage = 0;
    char again;
    
    do{
        cout << "Welcome to the salary system!" << endl;
        cout << "-----------------------------" << endl << endl;
        cout << "What is the employees current salary? ";
        cin >> currentWage;
        
        newWage = int(currentWage + (currentWage * (PERCENT/100)) + 0.5);
        retroactiveWage = int(6 * (currentWage * (PERCENT/100)) + 0.5);

        cout << "=============================" << endl
             << "The current wage is: " << currentWage << endl
             << "The new wage is: " << newWage << endl
             << "The retroactive wage is: " << retroactiveWage << endl << endl;
             
        cout << "Would you like to calculate the wage for a new employee? (Y/N)";
        cin >> again;
    
    }while(again == 'y' || again == 'Y');
    
    return 0;

}

```

---

## Fyra nummer

### Uppgift

Skriv av lösningen, men lista ut vad den gör och kommentera koden.
Spara filen med namnet uppgift2.cpp

### Problem

Skriv ett program som läser in 4 heltal från användare. Programmet ska räkna ut summan, medelvärdet och produkten av de fyra heltalen. Programmet ska kunna köras flera gånger utan att behöva starta om det.
Använd en funktion för att hantera input, output och beräkning.

### Lösning

```c++
#include <iostream>
#include <iomanip>

void statistics(void);

int main(void) {
    char again = 'y';
    while(again == 'y' || again == 'Y')
    {
        statistics();
        std::cout << "One more time? (Y/N)? ";
        std::cin >> again;
    }
    return 0;
}

void statistics()
{
    int numbers[4];
    int sum = 0;
    double product = 1;
    double average;

    std::cout << "Enter four integers: ";
    std::cin >> numbers[0] >> numbers[1] >> numbers[2] >> numbers[3];

    std::cout << std::fixed << std::endl;
    std::cout << "Entered numbers:";

    for(auto num : numbers)
    {
        std::cout << std::setw(6) << num;
        sum += num;
        product *= num;
    }

    average = sum/4.0;

    std::cout << std::endl << std::endl;
    std::cout << "STATISTICS" << std::endl
              << "==========" << std::endl << std::endl;
    std::cout << std::setw(8) <<"Sum" << std::setw(8) << "Average" << std::setw(12) << "Product" << std::endl;
    std::cout << std::setw(8) << "---" << std::setw(8) << "-------" << std::setw(12) << "-------" << std::endl;
    std::cout << std::setw(8) << sum << std::setw(8) << std::setprecision(2) << average << std::setw(12) << std::setprecision(0) << product << std::endl << std::endl;

}

```

---


## Hitta felen

Rätta till syntaxfelen i följande program så att det går att köra korrekt.
Spara filen med namnet uppgift3.cpp

```c++
#include <iostream>
#include <iomanip>
using namespace std;

void main(){

    // Define and initialize variables
    int hoursPerWeek = 35;
    double hourlyWages = 83;

    // Calculate weekly salary
    weeklyWages = hoursPerWeek * hourlyWages;

    // Display results
    cout << fixed           // Floating point format
         << setprecision(2) // 2 decimals
         << showpoint;      // Show trailing zeroes

    cout << "Given an hourly wage of " >> hourlyWages << " kr" << endl
        << " and the number of hours per weeek " << hoursPerWeek << endl
        << "the weekly wages will be: " << weeklyWages << " kr" >> endl

    cout << "\nPress return!";
    cin.get(); // Wait for return

    return 0;
}
```
---

## Hitta felen 2

Rätta till logiska fel i följande program.
Spara filen med namnet uppgift4.cpp

```c++
#include <iostream>
#include <iomanip>
using namespace std;

// Prototypes
void priceCalculation();

int main()
{
    char answer;
    do
    {
        priceCalculation();
        cout << "One more time? (Y/N): ";
        cin >> answer;
    } while(answer = 'Y' || answer == 'y');
    return 0;
}

void priceCalculation()
{
    // Define and initialize constants and variables
    const int RATE = 25; // Tax rate in percent

    double price = 0; // price per piece
    int nrOfArticles = 0; // number of articles
    double rateSEK = 0; // tax rate in SEK
    double totalPrice = 0; // price incl. tax rate

    // Read price and number of articles
    cout << "Enter the price excl. the tax rate (swedish moms): ";
    cin >> price;
    cin.ignore(80,'\n');

    cout << "Enter the number of articles: ";
    cin >> nrOfArticles;

    rateSEK = totalPrice * RATE;
    totalPrice = nrOfArticles * price & (1 + RATE);

    //  Display results with 2 decimals
    cout << fixed << showpoint << setprecision(2);

    cout << nrOfArticles << " number of articles cost " << totalPrice << " kr. "
        << endl << "Of this " << rateSEK << " kr is the tax rate" << endl;
}
```
