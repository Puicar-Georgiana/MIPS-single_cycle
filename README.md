MIPS32 Single Cycle Processor
Descriere
Acest proiect reprezintă implementarea unui procesor MIPS32 cu ciclu unic (Single Cycle) realizat în VHDL, în cadrul disciplinei Arhitectura Calculatoarelor de la Universitatea Politehnica din București, Facultatea de Automatică și Calculatoare, specializarea Calculatoare și Tehnologia Informației.
Procesorul implementează o arhitectură MIPS32 architecture pe 32 de biți, în care fiecare instrucțiune este executată într-un singur ciclu de ceas. Proiectul include toate componentele principale ale unui procesor: unitatea de extragere a instrucțiunilor, decodificare, execuție, memorie și unitatea de control.
Designul a fost realizat și testat utilizând Xilinx Vivado.

Structura proiectului
Proiectul este împărțit în mai multe module VHDL, fiecare reprezentând o componentă a procesorului.
1. MPG – Generator de Monopuls Sincron
Fișier: MPG.vhd
Generează un impuls sincron la apăsarea unui buton.
Funcționalitate:
•	utilizează un numărător
•	folosește 3 bistabile D Flip-Flop
•	produce un singur impuls la detectarea unei apăsări de buton

2. SSD – Afișaj pe 7 segmente
Fișier: SSD.vhd
Controlează afișarea valorilor pe un display cu 7 segmente.
Funcționalitate:
•	utilizează 7 LED-uri (catozi activi)
•	permite afișarea cifrelor prin activarea segmentelor corespunzătoare
•	afișajul este multiplexat între mai multe display-uri

3. IFetch – Instruction Fetch
Fișier: IFetch.vhd
Unitatea responsabilă pentru extragerea instrucțiunilor din memoria de instrucțiuni.
Funcționalitate:
•	gestionează Program Counter (PC)
•	calculează PC + 4
•	furnizează instrucțiunea curentă pentru etapa de decodificare

4. ID – Instruction Decode
Fișier: ID.vhd
Decodează instrucțiunile și pregătește operanzii pentru execuție.
Funcționalitate:
•	citește registrele din Register File
•	generează:
o	RD1
o	RD2
o	Ext_Imm (imediat extins)
o	câmpurile function și sa
•	primește valoarea WD pentru scriere în registre

5. UC1 – Unitatea de Control
Fișier: UC1.vhd
Generează semnalele de control pentru toate unitățile din datapath.
Funcționalitate:
•	analizează opcode-ul instrucțiunii
•	activează semnalele necesare pentru:
o	ALU
o	memorie
o	registre
o	salturi condiționate

6. EX – Execution Unit
Fișier: EX.vhd
Realizează operațiile aritmetice și logice ale instrucțiunilor.
Funcționalitate:
•	execută operații în ALU
•	primește:
o	RD1
o	RD2
o	Ext_Imm
o	PC + 4
•	generează:
o	rezultatul ALU
o	semnalul Zero
o	adresa pentru salt condiționat

7. MEM – Memory Unit
Fișier: MEM.vhd
Gestionează memoria de date.
Funcționalitate:
•	scriere sincronă pe frontul ascendent al ceasului
•	citire asincronă
•	suport pentru instrucțiuni de tip load/store

8. test_env – Arhitectura completă
Fișier: test_env.vhd
Acest modul integrează toate componentele procesorului pentru a forma arhitectura completă.
Funcționalitate:
•	conectează toate modulele
•	permite testarea funcționalității procesorului
•	servește ca mediu de simulare

Instrucțiuni implementate
Procesorul implementează un subset de instrucțiuni MIPS32, inclusiv:
•	instrucțiuni aritmetice
•	instrucțiuni logice
•	instrucțiuni de acces la memorie
•	instrucțiuni de salt și ramificare
Pentru fiecare instrucțiune sunt definite semnalele de control corespunzătoare generate de unitatea de control.

Program de test
Programul de test verifică dacă elementele unui șir sunt ordonate crescător.
Enunț
Se consideră un șir de N elemente stocat în memorie începând cu adresa A (A ≥ 12).
•	A se citește din adresa 0
•	N se citește din adresa 4
•	rezultatul este scris la adresa 8
Rezultat
•	1 -> șirul este ordonat crescător
•	0 -> șirul nu este ordonat crescător

Testare și simulare
Proiectul a fost testat în simulatorul din Xilinx Vivado.
Pe parcursul dezvoltării au fost întâlnite diverse probleme de proiectare, precum:
•	atribuirea incorectă a unor semnale
•	erori în implementarea programului MIPS
Acestea au fost identificate și corectate prin simulări succesive.

Schema RTL
Proiectul include și schema RTL (Register Transfer Level) a procesorului, care ilustrează conexiunile dintre toate modulele principale ale arhitecturii.

