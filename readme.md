# Introduktion till C++

## Löneökning

Den här uppgiften är tänkt att ge en liten introduktion till C++ och visa hur man kan skapa små enkla program.

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

## 
