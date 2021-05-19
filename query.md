# Query
Sviluppi in linguaggio SQL delle query che consentano di ottenere le seguenti 
informazioni:

○ tutti i canali tematici a cui si è iscritto l’utente XYZ

SELECT  C.nome, U.nome, U.cognome 
FROM Canali_Tematici AS C, Utenti AS U, Iscrizioni AS I 
WHERE I.id_Utente=U.id_Utente AND I.id_Canale=C.id_Canale AND I.id_Utente=1;

○ tutti gli utenti che hanno messo più di 10 “mi piace” nell’ultimo mese

SELECT U.nome,U.Cognome, COUNT(id_Like) 
FROM Utenti AS U, Likes AS L, Podcast AS P 
WHERE U.id_Utente=L.id_Utente AND P.id_Podcast=L.id_Podcast AND L.data BETWEEN '2021-05-16' AND '2021-06-16' 
GROUP BY U.nome,U.Cognome HAVING COUNT(id_Like)>10;
