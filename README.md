1. Proiectul MIPS cu ciclu unic
Acest document oferă o descriere detaliată a proiectului MIPS cu ciclu unic pe 32 de biți, inclusiv componentele folosite, funcționalitatea acestora, instrucțiunile implementate și semnalele de control.
2. Componente folosite și funcționalitatea acestora
2.1 Generator de Monopuls Sincron (MPG.vhd)
•	Descriere: Generează un impuls sincron la o apăsare de buton.
•	Funcționalitate: Utilizează un numărător și 3 bistabile D Flip-Flop pentru a produce un impuls de o singură dată când un buton este apăsat.
2.2 Afișaj pe 7 segmente (SSD.vhd)
•	Descriere: Afișează cifrele pe un display de 7 segmente.
•	Funcționalitate: Folosește 7 LED-uri active (catozi) pentru a afișa cifrele. Catozii sunt comuni tuturor afișoarelor, iar afișajul este realizat prin activarea alternativă a diferitelor segmente.
2.3 Unitatea de extragere a instrucțiunilor (IFetch.vhd)
•	Descriere: Extrage instrucțiunile din memoria de instrucțiuni.
•	Funcționalitate: Primește adresele de salt și pune la dispoziție adresa următoare (PC+4) și conținutul instrucțiunii curente.
2.4 Unitatea de decodificare a instrucțiunilor (ID.vhd)
•	Descriere: Decodează instrucțiunile pentru a putea fi executate.
•	Funcționalitate: Primește instrucțiunea curentă și valoarea WD, care se scrie în RF. Pune la ieșire operanzii RD1, RD2, imediatul extins Ext_Imm, câmpurile function și sa.
2.5 Unitatea de control (UC1.vhd)
•	Descriere: Generează semnalele de control pentru unitățile din calea de date.
•	Funcționalitate: Determină funcționalitatea unităților în funcție de tipul de instrucțiune.
2.6 Unitatea de execuție (EX.vhd)
•	Descriere: Realizează operațiile aritmetice și logice necesare instrucțiunii.
•	Funcționalitate: Primește registrele RD1 și RD2, imediatul extins Ext_imm și adresa de instrucțiune următoare PC+4. Pune la dispoziție rezultatul ALU, semnalul de validare Zero și adresa de salt condiționat.
2.7 Unitatea de memorie (MEM.vhd)
•	Descriere: Stocăre a datelor.
•	Funcționalitate: Scrierea în memorie este sincronă pe frontul de ceas ascendent, iar citirea este asincronă.
2.8 Arhitectura completă a procesorului (test_env.vhd)
•	Descriere: Asamblează întregul procesor folosind componentele enumerate anterior.
•	Funcționalitate: Integrează toate componentele pentru a forma un procesor funcțional.

Toate componentele enumerate sunt funcționale, fără a prezenta probleme de funcționare. Acestea au fost testate integral în simulatorul din VIVADO pentru a asigura corectitudinea proiectului.
Pe parcursul dezvoltării proiectului au apărut diverse probleme de proiectare, cum ar fi atribuirea incorectă a unor valori sau erori în implementarea programului MIPS32. Aceste probleme au fost identificate și remediate treptat.
