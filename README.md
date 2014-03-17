Tarea1
======
#include <iostream>
#include <stdlib.h>
#include <string.h>
#include <time.h>

using namespace std;

int ingresar1(){
    char fecha[15], *p;
    int longitud=0, anio=0, multanio=1000, anio1=0;
    cout << endl << "Ingrese fecha: ";
    cin>>fecha;
    cout << endl;
    p=fecha;
    while (*p != '-'){
        longitud++;
        anio=*p;
        char a = anio;
        int ia = a - '0';
        anio=ia;
        anio=anio*multanio;
        anio1=anio1+anio;
        multanio=multanio/10;
        p++;
    }
    return anio1;
}

int ingresar2(){
    char fecha[15], *p;
    int multmes=10, mes=0, mes1=0;
    p++;
    while(*p!= '-'){
        mes=*p;
        char m = mes;
        int ma = m - '0';
        mes= ma;
        mes=mes*multmes;
        mes1=mes1+mes;
        multmes=multmes/10;
        p++;
    }
    return mes1;
}

int ingresar3(){
    char fecha[15], *p;
    int multdia=10, dia=0, dia1=0;
    p++;
    while(*p!= '\0'){
        dia=*p;
        char m = dia;
        int ma = m - '0';
        dia= ma;
        dia=dia*multdia;
        dia1=dia1+dia;
        multdia=multdia/10;
        p++;
    }
    return dia1;
}

int actualidad(){
    struct tm *tiempo;
        int dd;
        int mm;
        int aaaa;
        time_t fecha_sistema;
        time(&fecha_sistema);
        tiempo=localtime(&fecha_sistema);
        aaaa=tiempo->tm_year + 1900;
        mm=tiempo->tm_mon + 1;
        dd=tiempo->tm_mday;
        return aaaa;
}

int bisiesto(int anio1){
    if (anio1%4==0){
        return 1;
    }
    else{
        return 0;
    }
}

int main(int argc, char **argv)
 {
    if(strcmp(*(argv+1),"-f")==0){
        int aaaa, anio1, mes1, dia1, bis;
        anio1 = ingresar1();
        bis = bisiesto(anio1);
        mes1 = ingresar2();
        dia1 = ingresar3();
        if(mes1==1 || mes1==3 || mes1==5 || mes1==7 || mes1==8 || mes1==10 || mes1==12){
            while(dia1<1 || 31<dia1){
                cout << "Fecha inexistente" << endl;
                cout << "Ingrese nuevamente" << endl;
                anio1 = ingresar1();
                mes1 = ingresar2();
                dia1 = ingresar3();
            }
        }
        if(mes1==4 || mes1==6 || mes1==9 || mes1==11){
            while(dia1<1 || 30<dia1){
                cout << "Fecha inexistente" << endl;
                cout << "Ingrese nuevamente" << endl;
                anio1 = ingresar1();
                mes1 = ingresar2();
                dia1 = ingresar3();
            }
        }
        if(mes1==2){
                if(bis==1){
                    while(dia1<1 || 29<dia1){
                        cout << "Fecha inexistente" << endl;
                        cout << "Ingrese nuevamente" << endl;
                        anio1 = ingresar1();
                        mes1 = ingresar2();
                        dia1 = ingresar3();
                    }
                }
                else {
                    while(dia1<1 || 28<dia1){
                        cout << "Fecha inexistente" << endl;
                        cout << "Ingrese nuevamente" << endl;
                        anio1 = ingresar1();
                        mes1 = ingresar2();
                        dia1 = ingresar3();
                    }
                }
        }
        aaaa = actualidad();
        cout<<"La cantidad de anios a la fecha actual son: "<<(aaaa-anio1)-1<< " anios"<<endl;
        cout<<"La cantidad de meses a la fecha actual son: " <<((aaaa-anio1)*12)-1<< " meses" <<endl;
        cout<<"La cantidad de dias a la fecha actual son: " <<(aaaa-anio1)*365<< " dias" <<endl;
        if (bis==1){
            cout << "El anio "<<anio1<<" es bisiesto"<<endl;
        }
        else{
            cout<< "El anio "<<anio1<<" no es bisiesto"<<endl;
        }
            system("PAUSE");
    }
	else if(strcmp(*(argv+1),"-v")==0){
        cout << endl;
        cout << "Integrantes : - Dominique Huenteleo" << endl;
        cout << "              - David Martinez" << endl;
        cout << endl;
        system("pause");
    }
}
