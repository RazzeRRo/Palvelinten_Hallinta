# H4 Pizza Fantasia

## Tiivistykset

### 4.12.1 Size and Complexity of Some DSLs  
- DSL:t voi olla erittäin laajoja (esim. Salt ~510 funktiota)  
- Dokumentaatio todella pitkä -> Vaikea hallita
- Monimutkaisuutta lisää useat kerrokset (Jinja2 -> YAML -> Python)
- Puppet: vähemmän funktiota, mutta omat erikoisrakenteet
- Kontrollirakenteet ei vastaa tavallisia ohjemointikieliä

### 4.12.2 Use od DSL Functions in Case Configuration  
- Käytössä vain pieni osa kaikista funktioista  
- yleisimmät: package, file, service, exec  
- Toistuvat mallit (esim. package-file-service)  
- ~87% käytöstä katetaan pienellä joukolla  
- Osa funktioista lähes turhia käytännössä  
- Kontrollirakenteista yleisiä: if, case  

### 4.12.3.1 Dependencies Between Main Functions  
- Tärkeimmät funktiot: file ja exec  
- Muut (package, service, user group) rakentuu näiden päälle  
- Funktiot riippuvat toisistaan (dependency graph)  
- Järjestelmän oltava idempotentti  
- Monet funktiot cain ajavat järjestelmän komentoja  
- Korkeamman tason abstraktiot voidaan rakentaa perusfunktioista

---

## Tehtävät

### A) Räpylä  
Valitsin tähän tehtävään **postresql** demonin.  
Kuten aina ensimmäiseksi suoritin _sudo apt-get update_ jonka jälkeen asensin postgresql:n komennolla _sudp apt install postresql_  
Seuraavaksi loin uuden databasen ja käyttäjän.  
<img width="607" height="55" alt="image" src="https://github.com/user-attachments/assets/88f32fd9-6f5a-4559-a5ad-a29a030da773" />  
Kuvassa näkyy miten psql ((Postgresql) tulen käyttämään kyseistä lyhennettä jatkossa) on asennettuna ja valmiina toimintaan.  
<img width="368" height="104" alt="image" src="https://github.com/user-attachments/assets/61379f95-8308-4b22-9507-549e5ea1a46f" />  

### B) Automaatti  
Tehtävää varten tein uuden roolin ansibleen jotta se helpottaisi tulevaisuudessa hahmottamista.  
<img width="229" height="86" alt="image" src="https://github.com/user-attachments/assets/259bdb67-e799-4f80-b888-7c3a9e6e81a3" />  
Kyseiseen main.yml tiedostoon laitoin seuraavanlaisen sisällön.  
<img width="335" height="135" alt="image" src="https://github.com/user-attachments/assets/42e29d42-997e-4eb1-9ea8-94f95c0f6f25" />  
Ensimmäinen suoritus ei tuottanut mitään sillä psql oli jo asennettu  
<img width="1150" height="271" alt="image" src="https://github.com/user-attachments/assets/43cb1ace-af99-4824-a6ce-cb52a7469afb" />  

### C) Asetus
Tätä tehtävää varten loin psql sisään handlers ala hakemiston jonka main.yml tiedostoon laitoin seuraavan tekstin.  
<img width="334" height="103" alt="image" src="https://github.com/user-attachments/assets/5e190106-f530-4e0d-823c-85412e921a32" />
Jotta tämä toimisi minun täytyy myös muokata tasks:in main.yml tiedostoa. Sinne laitoin näin.  
<img width="554" height="293" alt="image" src="https://github.com/user-attachments/assets/0fb24ecb-5da2-4ded-8106-0201a1f9b84c" />  
Sitten aika tehdä ensimmäinen testi.  
<img width="1156" height="343" alt="image" src="https://github.com/user-attachments/assets/89c8d312-74fd-4405-91e9-826105633888" />  
Suoritus heitti virheen josta huomasin simppelin typon. Kokeillaan uudestaan.  
<img width="1126" height="409" alt="image" src="https://github.com/user-attachments/assets/fe27d195-a288-4a02-bf7f-1158705f74fb" />  
Ansible selkeästi teki jotain käydään katsomassa mitä.  
<img width="724" height="117" alt="image" src="https://github.com/user-attachments/assets/1aff5f14-7486-40bc-9a8e-6e26a0cf8a09" />  
Arvo on muuttunut mutta unohdin katsoa mikä se oli ennen muuttamista.  

### D) Paikka remonttiin
Tässä tehtävässä poistin koko psql:n komennolla _sudo apt purge postgresql -y_  
<img width="672" height="294" alt="image" src="https://github.com/user-attachments/assets/7e94a91f-97bb-4ea9-938d-aebd98d9aa37" />  
Suoritin ansiblen uudelleen.  
<img width="1104" height="356" alt="image" src="https://github.com/user-attachments/assets/4d423e5d-c251-4ce1-bbe4-0ec7322c52fa" />  
Ja varmistetaan vielä ettei tapahdu kummia kun suoritetaan vielä kerran  
<img width="1117" height="376" alt="image" src="https://github.com/user-attachments/assets/70c56391-b438-49cf-9216-1ce4a1c0f6c2" />  
Ei tapahtunut ja psql toimii  
<img width="406" height="127" alt="image" src="https://github.com/user-attachments/assets/0c010ede-3012-47c3-831b-bfc1a3dc320d" />  

### E) Idempotentti
Tässä tehtävässä ajetaan ansible 2 kertaa 
<img width="1105" height="746" alt="image" src="https://github.com/user-attachments/assets/adac7bed-4216-4f2e-b01f-c43fad5b21ec" />  
Idempotenssi on saavutettu.  

---

## Lähteet
Karvinen 2023: Configuration Management of Distributed Systems over Unreliable and Hostile Networks Luettavissa: https://westminsterresearch.westminster.ac.uk/item/w7vvz/configuration-management-of-distributed-systems-over-unreliable-and-hostile-networks Luettu 20.4.26  
Karvinen 2016: Install PostgreSQL on Ubuntu – New user and database in 3 commands Luettavissa: https://terokarvinen.com/2016/install-postgresql-on-ubuntu-new-user-and-database-in-3-commands/?fromSearch=postgresql Luettu 20.4.26
