# supermarket
Java project that simulates a supermarket. 
Am grupat clasele in functie de rolul fiecareia. Voi incepe cu a prezenta ce cuprinde  
package-ul store:

1) Clasa Store: (cu Singleton Pattern) --> implementata ca in cerinta, are un nume, 
o lista de departamente, o lista de clienti si un instance ( pe care il folosesc 
pentru ca s-a cerut sa folosesc Singleton)

2) Clasa Customer: (care implementeaza interfata Observer) --> are functia de update 
unde adaug mai intai notificarea la lista de notificari, apoi verific: daca tipul 	  notificarii e ADD, nu fac nimic, daca e REMOVE atunci sterg produsul din wishList 
si din ShoppingCart, si daca e MODIFY atunci doar modific pretul. Pentru update am 	   facut separat in ShoppingCart doua functii: una e removeAllItems in care parcurg 
lista cautand dupa ID, sterg elementul si modific bugetul(adaug ce am sters ca pret) 	     si cea de-a doua e modifyPrice(parcurg lista cautand elem dupa ID,modific bugetul 		adaugand diferenta dintre pretul actual si modificarea si actualizez noul pret). 

3) Item

4) ItemList: cea mai grea clasa dintre toate. ItemList-ul mare are ca elemente: head,
tail, size si un comparator. El este compus din doua clase interne: Node si 		ItemIterator. Node e simpla, e ca un nod dintr-o lista, are next, prev si info, 	constuctori si niste getteri si setteri. ItemIterator are ca elemente: nodCurent, 	  nodPrev, index. Fac override la multe metode aici pentru ca implementeaza 			ListIterator. 

5) Notification: contine data la care se face modificare, o enumerare cu cele 3 	notificari posibile, un obiect de tip TipNotificare, si ID pt departament, produs si
o variabila pt pretul modificat. In rest, constructori, toString, gettTipNotificare. 

6) ShoppingCart: implementeaza Visitor. In ShoppingCart am un buget si am folosesc 
iar de comparator pentru ca vreau sa sortez dupa pret si daca au acelasi pret, 
sortez dupa nume. Am rescris o parte din metodele din ItemList: addItem(cu 		actualizarea bugetului), removeItem. Am mai facut o metoda getTotalPrice care face 	   suma totala din lista. In ShoppingCart se gasesc cele 4 functii de visit pentru 		fiecare departament care se ocupa cu modificarile de pret. 

7) WishList : are un element de tip Strategy. Am implementat si bonusul cu cele trei
strategii: A, care returneaza produsul cel mai ieftin si il sterge din lista, C: cel
mai recent adaugat ( adica ultimul din wishList si la fel, il sterge din wishList si
il returneaza) si B: am un comparator dupa nume, alfabetic ( iau elem din wishList, le
adaug alfabetic intr-o lista si returnez primul element).  

Package-ul Departments:
8) BookDepartment, MusicDep, SoftDep, VideoDep - au doar un constructor si metoda de 	     accept. 
	
9) Department: implementeaza Subject, deci vom gasi in el metodele de addObserver, 	   removeObserver si notifyObserver. Presupune un nume,o lista de itemuri, de clienti 
si de observatori si un ID unic. In department am o functie care se numeste 		RemanageCustomer si pe care o folosesc la comezi la testare. Atunci cand cineva are
un produs dintr-un departament, devine un customer. Daca doar isi doreste un produs,
atunci e observer. Metoda verifica daca mai are produse din departament si daca nu mai 
are, il scoate. 

Fisierul Test: 
Implementeaza interfata Command. Avem un package de comezi posibile care respecta sintaxa din cerinta: 
	- Comanda are rolul de a executa actiunea, ca de exemplu: GetItemCommand intoarce produsul ales conform strategiei. Mai intai aflu care este clientul, apoi execut strategia si determin itemul si il afisez(si dupa ma duc cu remanageCustomer sa vad daca mai are in wishList produse sau nu). Apoi,  in inputParser am metodele pe care le folosesc in main ca sa testez, verificand ce comanda am si preluand argumentele. 
Timp de rezolvare: 5-6 zile
