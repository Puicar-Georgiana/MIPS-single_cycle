MIPS32 Single-Cycle Processor (VHDL)
Descriere proiect
Acest proiect implementează un procesor MIPS32 cu arhitectură single-cycle (ciclu unic) utilizând VHDL. Procesorul este proiectat modular și este compus din mai multe unități funcționale care formează împreună calea de date și unitatea de control.
Proiectul a fost realizat și testat în Xilinx Vivado, iar toate componentele au fost verificate prin simulare pentru a asigura funcționarea corectă.

Arhitectura procesorului
Procesorul este construit din următoarele componente principale:
•	Generator de monopuls sincron
•	Afișaj pe 7 segmente
•	Instruction Fetch
•	Instruction Decode
•	Unitatea de control
•	Execution Unit
•	Memory Unit
•	Mediul de test / integrare procesor

Componente și funcționalitate
1. Generator de Monopuls Sincron (MPG.vhd)
Descriere
Generează un impuls sincron la apăsarea unui buton.
Funcționalitate
•	Utilizează un numărător și 3 bistabile D Flip-Flop
•	Produce un singur impuls pentru fiecare apăsare a butonului
•	Elimină problemele de debouncing ale butoanelor

2. Afișaj pe 7 segmente (SSD.vhd)
Descriere
Permite afișarea valorilor numerice pe un display cu 7 segmente.
Funcționalitate
•	Utilizează 7 LED-uri active (catozi)
•	Catozii sunt comuni pentru toate afișajele
•	Afișarea este realizată prin multiplexarea segmentelor

3. Instruction Fetch Unit (IFetch.vhd)
Descriere
Unitatea responsabilă pentru extragerea instrucțiunilor din memoria de instrucțiuni.
Funcționalitate
•	Primește adresa de salt
•	Calculează PC + 4
•	Returnează:
o	instrucțiunea curentă
o	adresa următoarei instrucțiuni

4. Instruction Decode Unit (ID.vhd)
Descriere
Decodează instrucțiunile și pregătește operanzii necesari execuției.
Funcționalitate
Primește:
•	instrucțiunea curentă
•	valoarea WD (Write Data) pentru registrul RF
Produce:
•	RD1
•	RD2
•	Ext_Imm (imediat extins)
•	câmpurile function
•	sa (shift amount)

5. Control Unit (UC1.vhd)
Descriere
Generează semnalele de control pentru toate unitățile procesorului.
Funcționalitate
Determină comportamentul procesorului în funcție de tipul instrucțiunii.
Controlează:
•	scrierea în registri
•	operația ALU
•	accesul la memorie
•	ramificațiile

6. Execution Unit (EX.vhd)
Descriere
Realizează operațiile aritmetice și logice ale procesorului.
Funcționalitate
Primește:
•	RD1
•	RD2
•	Ext_Imm
•	PC + 4
Produce:
•	rezultatul ALU
•	semnalul Zero
•	adresa de branch

7. Memory Unit (MEM.vhd)
Descriere
Unitatea de memorie pentru date.
Funcționalitate
•	Scriere sincronă pe frontul ascendent al ceasului
•	Citire asincronă

8. Arhitectura completă a procesorului (test_env.vhd)
Descriere
Integrează toate modulele într-un procesor funcțional.
Funcționalitate
•	conectează toate componentele
•	permite testarea procesorului
•	simulează execuția programelor MIPS

Testarea proiectului
Toate componentele au fost:
•	proiectate în VHDL
•	simulate în Vivado Simulator
•	verificate pentru funcționare corectă
În timpul dezvoltării au apărut diverse probleme, precum:
•	atribuirea incorectă a unor semnale
•	erori în implementarea programului MIPS
•	probleme de sincronizare
Acestea au fost identificate și corectate progresiv în timpul simulării.

Setul de instrucțiuni implementat
Procesorul suportă un subset al instrucțiunilor MIPS32, utilizate pentru implementarea și testarea arhitecturii single-cycle.
Exemple de tipuri de instrucțiuni:
R-Type
•	add
•	sub
•	and
•	or
•	sll
•	srl
I-Type
•	addi
•	lw
•	sw
•	beq
J-Type
•	jump

Semnale de control
Unitatea de control generează semnale pentru:
•	RegDst
•	ALUSrc
•	MemWrite
•	MemToReg
•	RegWrite
•	Branch
•	Jump
•	ALUOp
Aceste semnale determină modul de funcționare al procesorului pentru fiecare instrucțiune.

Program de test
Pentru testarea procesorului a fost utilizată problema:
Determinarea ordonării unui șir
Enunț:
Se verifică dacă valorile unui șir de N elemente sunt ordonate crescător.
Organizarea memoriei
Adresă	Conținut
0	A (adresa de început a șirului)
4	N (numărul de elemente)
8	rezultat (1 = ordonat, 0 = neordonat)
Condiții:
•	A ≥ 12
•	șirul este stocat în memorie începând cu adresa A
Rezultatul verificării este scris la adresa 8.

Schema RTL
Procesorul este implementat utilizând o arhitectură RTL (Register Transfer Level) în care toate componentele sunt conectate prin calea de date și semnale de control.
Schema RTL include:
•	PC
•	Instruction Memory
•	Register File
•	ALU
•	Data Memory
•	Multiplexoare
•	Control Unit

Tehnologii utilizate
•	VHDL
•	MIPS32 Architecture
•	Xilinx Vivado
•	RTL Design
•	Digital Logic Design


