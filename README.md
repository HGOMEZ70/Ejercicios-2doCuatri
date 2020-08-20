# Ejercicios-2doCuatri
Ejercicios del 2do Cuatrimestre Lab2
//NOMBRE: HUGO FABIAN GOMEZ
//TP N�:
//EJ N�:
//Comentarios:
/**La Carrera de T�cnico Universitario en Programaci�n dispone de todas las
inscripciones a examen de la �ltima mesa de finales de sus 380 alumnos.
Por cada inscripci�n se registr�:
- Legajo del alumno (10000 a 50000)
- Nota
El fin de la carga de datos se indica con un n�mero de legajo igual a cero. */

#include <cstdlib>
#include <cstdio>
#include <cstring>
#include <iostream>
using namespace std;


void Cargar(int [][2], int, int, int);
void Mostrar(int [][2], int);
void Informe(int [][2], int[][2], int);

int main(void){
    const int b=2;
    int Inscripciones[300][b]={}, c=-1, Resumen[300][b]={};
    int Legajo, Nota;
    cout<<"Ingrese el Legajo y la Nota: ";
    cin>>Legajo;
    while(Legajo!=0){
        cin>>Nota;
        c++;
        Cargar(Inscripciones, Legajo, Nota, c);

        cin>>Legajo;
    }
    Mostrar(Inscripciones, c);
    Informe(Inscripciones, Resumen, c);
    return 0;
}


void Cargar(int M[][2], int L, int N, int c){
    cout<<"c: "<<c<<endl;
    for(int i=0; i<2; i++){
        M[c][0]=L;
        M[c][1]=N;
    }
}

void Mostrar(int M[][2], int c){
    for(int i=0; i<c; i++){
        cout<<endl<<"\t";
        for(int j=0; j<2; j++){
            cout<<M[i][j]<<"\t";
        }
    }
}

void Informe(int M[][2], int R[][2], int c){
    int d=0, e=0, f=0;
    for(int i=0; i<c; i++){
        d=0;
        for(int j=0; j<=e; j++){
            if(M[i][0]==R[j][0]){
                d++;
            }
        }
        if(d==0){
            R[e][0]=M[i][0];
            e++;
        }
    }
    cout<<"\nMuestro la carga de R: \n";
    for(int k=0; k<e; k++){
        for(int l=0; l<300; l++){
            if(R[k][0]==M[l][0]){
                R[k][1]++;
            }
        }
        cout<<"\nLegajo Nro: "<<R[k][0]<<" se incribio a "<<R[k][1];
    }
    cout<<"\nfin"<<endl;
}
