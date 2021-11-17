Create database pr1_samokhvalov;
use pr1_samokhvalov;
1.

Create table Tovari (id_tov int not null auto_increment, name_tovar varchar(100), price float, PRIMARY KEY (id_tov)); 
Create table TTN_nikita(N_Nakladnoi int, DataP date, Postavchik varchar(100), id_tov int,kol_vo int, FOREIGN KEY (id_tov) REFERENCES Tovar (id_tov));

2.
Create user nikita_user1;
Create user nikita_user2;

3.
Set password for nikita_user1 = “12345”;
Set password for nikita_user2 = ”12345”;

7.
Grant select on pr1_samokhvalov * to nikita_user1  with grant option;
Grant update on pr1_samokhvalov * to nikita_user2  with grant option;

8. 
Под nikita_user1
set password=11111;
select * from TTN_nikita;

9. 
Под nikita_user2
UPDATE Tovari
SET    price = 9999
WHERE  id_tov = (SELECT Max(id_tov) 
               FROM   TTN_nikita)
UPDATE TTN_nikita
SET    DataP = 19.06.2002
WHERE  N_Nakladnoi = (SELECT Max(N_Nakladnoi) 
               FROM   TTN_nikita)

