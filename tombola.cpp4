#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

bool usciti[91] = {false}; // per capire quali numeri sono usciti

// DUE SCHEDDE 
int scheda1[15];
int scheda2[15];



void generaScheda(int scheda[])
{
    int z;

    for(int gruppo = 0; gruppo < 3; gruppo++)
    {
        int decine[5] = {-1, -1, -1, -1, -1};

        for(int j = 0; j < 5; j++)
        {
            int decina;
            int ripetuta;

            do {
                z = rand() % 90 + 1;
                decina = z / 10;
                ripetuta = 0;

                // controllo decine già usate nel gruppo
                for(int k = 0; k < j; k++)
                {
                    if(decine[k] == decina)
                    {
                        ripetuta = 1;
                        break;
                    }
                }

                // controllo numeri già presenti nella scheda
                for(int k = 0; k < gruppo * 5 + j; k++)
                {
                    if(scheda[k] == z)
                    {
                        ripetuta = 1;
                        break;
                    }
                }

            } while(ripetuta == 1);

            decine[j] = decina;
            scheda[gruppo * 5 + j] = z;
        }
    }
}
//////////////////////////////////////////

// STAMPA UNA SCHEDA (senza rigenerarla)

void stampaScheda(int scheda[])
{
    for(int i = 0; i < 15; i++)
    {
        int val = scheda[i];

        if (usciti[val])
            cout << "|\033[32m" << val << "\033[0m|";  // verde se estratto
        else
            cout << "|" << val << "|";

        if(i == 4)
            cout << endl << "_________________" << endl;
        else if(i == 9)
            cout << endl << "_________________" << endl;
        else if(i == 14)
            cout << endl << "_________________" << endl;
    }
}



// STAMPA TABELLA  1–90

int stampaTabella() 
{
    cout << "TOMBOLA" << endl;

    for (int i = 1; i <= 90; i++) 
    {
        if (usciti[i]) 
        {
            if (i < 10)
                cout << "|\033[32m" << i << "\033[0m |";
            else
                cout << "|\033[32m" << i << "\033[0m|";
        }
        else 
        {
            if(i < 10)
                cout << "|" << i << " |";
            else
                cout << "|" << i << "|";
        }

        if (i % 10 == 0)
            cout << endl;
    }

    cout << endl;
    return 0;
}



// ESTRAE UN NUMERO 

int estraiNumero()  
{
    int n;
    do 
    {
        n = rand() % 90 + 1;
    } while (usciti[n]);

    usciti[n] = true;
    return n;
}



// codice prencipale

int main() 
{
    srand(time(0));

    // GENERA LE DUE SCHEDDE UNA SOLA VOLTA
    generaScheda(scheda1);
    generaScheda(scheda2);

    char scelta;
    int numero;

    do {
    system("cls");  
   

    stampaTabella();

    numero = estraiNumero();
    cout << "Numero estratto: " << numero << endl;

    cout << "\nSCHEDA 1 "<<endl;
    stampaScheda(scheda1);

    cout << "\nSCHEDA 2"<<endl;
    stampaScheda(scheda2);

    
    // CONTROLLO TOMBOLA SCHEDA 1
  
    bool tombola1 = true;
    for(int i = 0; i < 15; i++) {
        if(!usciti[scheda1[i]]) {
            tombola1 = false;
            break;
        }
    }
    if(tombola1) {
        cout << " TOMBOLA PER 1"<<endl;
  
        break;
    }


    // CONTROLLO TOMBOLA SCHEDA 2

    bool tombola2 = true;
    for(int i = 0; i < 15; i++) {
        if(!usciti[scheda2[i]]) {
            tombola2 = false;
            break;
        }
    }
    if(tombola2) {
        cout << "\n\n*** TOMBOLA PER 2! ***\n";
        break;
    }

    cout << "\nContinuare? s/n: ";
    cin >> scelta;

} while (scelta == 's');


    return 0;
}
