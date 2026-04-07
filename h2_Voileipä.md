# H2 Voileipä
## Sudo without password
- Suositellaan tekemään sudo -i toisessa ikkunnassa jos sudo menee rikki niin saa korjattua
- komennolla sudo visudo /etc/sudoers.d/sudoless tehdään kansio johon lisätään %sudoless ALL = (ALL) NOPASSWD: ALL jotta saadaan uusi ryhmä mikä ei tarvitse käyttää sudon salasanaa
- Olisiko turvallisempaa sallia vain tietyt komennot täyden ALL sijasta?

## xkcd 149: Sandwich
- Nopeasti kuvaava sarjakuva sudon voimasta
- sudo = taikasana jolla pystyy käskemään konetta

## Passwordless Sudo with Ansible
- Suositeltavaa tehdä manuaalisena ennen automatisointia
- komennossa ansible-playbook site.yml "--ask-become-password" voidaan lvoidaan lyhentää -K parametriin

## ansible-doc

### copy
**Johdanto:**  
Kopioi tiedostoja tai sisältöä kohdekoneelle.

**Optiot:**
- *content*: tiedoston sisältö suoraan playbookista  
- *dest*: kohdepolku  
- *src*: lähdetiedosto ohjauskoneella  
- *owner*: omistaja  
- *group*: ryhmä  
- *mode*: käyttöoikeudet  

**Esimerkki:**  
- copy: content: "Hello\n", dest: /tmp/hello.txt

---

### apt
**Johdanto:**  
Hallitsee paketteja Debian-pohjaisissa järjestelmissä.

**Optiot:**
- *name*: paketin nimi  
- *state*: haluttu tila (present, absent, latest)  
- *update_cache*: päivittää pakettivaraston  

**Esimerkki:**  
- apt: name: tree, state: present, update_cache: yes

---

### file
**Johdanto:**  
Hallitsee tiedostojen ja hakemistojen ominaisuuksia.

**Optiot:**
- *path*: kohdepolku  
- *recurse*: rekursiivinen käsittely  
- *src*: lähde (esim. linkeissä)  
- *state*: tila (file, directory, link, absent)  
- *owner*: omistaja  
- *group*: ryhmä  
- *mode*: käyttöoikeudet  

**Esimerkki:**  
- file: path: /tmp/testdir, state: directory

---

### user
**Johdanto:**  
Hallitsee käyttäjätilejä kohdekoneella.

**Optiot:**
- *name*: käyttäjän nimi  
- *create_home*: luodaanko kotihakemisto  
- *comment*: kuvaus  
- *groups*: ryhmät  
- *shell*: oletus shell  
- *state*: present/absent  
- *system*: onko järjestelmäkäyttäjä  

**Esimerkki:**  
- user: name: testuser, state: present, create_home: yes

---

### authorized_key
**Johdanto:**  
Lisää SSH-avaimia käyttäjän authorized_keys-tiedostoon.

**Optiot:**
- *user*: käyttäjä  
- *key*: julkinen avain  

**Esimerkki:**  
- authorized_key: user: testuser, key: "ssh-rsa AAAA..."

## Tehtävät
**a)**  
Ensimmäisenä loin käyttäjän komennolla _sudo adduser_.  
Sitten loin ryhmän **sudoless** komennolla _sudo groupadd sudoless_ jonka jälkeen lisäsin uuden käyttäjän jakdebi tähän ryhmään komennolla _sudo adduser jakdebi_ sudoless.  
Tämän jälkeen menin /etc/sudoers.d/sudoless visudo editorilla jossa lisäsin %sudoless _ALL = (ALL) NOPASSWD: ALL_ säännön **sudoless** ryhmälle mikä sallii sudon käytön ilman salasanaa.  
<img width="1063" height="229" alt="image" src="https://github.com/user-attachments/assets/f9ec44ef-f03c-418f-bcaa-c7ebdab2fc29" /><br/> 
    
---
    
**b)**  
Loin uuden hakemiston jakans joka luodaan automaattisesti sekä saa salasanottaman sudon automaattisesti  
<img width="287" height="208" alt="image" src="https://github.com/user-attachments/assets/9cba3f35-88b4-45b3-baab-2c161d046c15" />  
Seuraavaksi lisäsin nämä jakans main.yml tiedostoon   
<img width="1247" height="327" alt="image" src="https://github.com/user-attachments/assets/fc15d10b-b2c8-496a-8486-9b4ae609f515" />  
Ensimmäinen ansible-playbook suoritus  
<img width="1228" height="493" alt="image" src="https://github.com/user-attachments/assets/5dddf00b-0237-4da9-ba15-3c58fbdd3a49" />  
Tarkistetaan tuleeko uudelleen muutoksia  
<img width="1224" height="492" alt="image" src="https://github.com/user-attachments/assets/f23cafc5-a0cb-4ad4-b69a-fa3d470c5754" />
Ei tullut eli pitäisi olla uusi käyttäjä luotu  
<img width="1106" height="295" alt="image" src="https://github.com/user-attachments/assets/197e180c-53ca-401b-9983-a5b6a9288850" />  
Ja uusi käyttäjä on luotu automaattisesti  

---

**c)**
Tein kokonaan uuden roolin nimeltä packages jonka main.yml lisäsin seuraavan  
<img width="299" height="110" alt="image" src="https://github.com/user-attachments/assets/a9aece46-2d84-4fb1-93e7-99ab037cdcb1" />  
Ensimmäinen suoritus
<img width="1175" height="548" alt="image" src="https://github.com/user-attachments/assets/fcc12d74-b505-4eb4-a31f-b74c437a545e" />  
Ja perään uudelleen testiksi  
<img width="1202" height="548" alt="image" src="https://github.com/user-attachments/assets/072ac1cf-3cb8-4f16-8cd6-68cf2cd13a14" />  
Kaikki ok joten tarkistetaan asensiko
<img width="1261" height="714" alt="image" src="https://github.com/user-attachments/assets/2088e4b5-14fc-4d8d-980e-ffa79adb85a8" />  
Asensi oikein. Yllä olevassa kuvassa htop  

---

**d)**
Loin taas uuden roolin nimeltä _filedemo_ johon laitoin seuraavan  
<img width="766" height="105" alt="image" src="https://github.com/user-attachments/assets/72fdd658-2a36-493e-adb4-cadc9be0dee8" />  
Tässä ensimmäinen ja toinen suoritus playbookilla  
<img width="1188" height="597" alt="image" src="https://github.com/user-attachments/assets/a8a230ce-84f1-4547-af04-573a6c5f35d4" />  
<img width="1241" height="615" alt="image" src="https://github.com/user-attachments/assets/38397ce0-3e06-43f6-bd01-ce4079365425" />  
Tässä onnistunut suoritus  
<img width="777" height="61" alt="image" src="https://github.com/user-attachments/assets/22fb2080-171c-426f-86bd-7b8816ae83ba" />  
<img width="551" height="22" alt="image" src="https://github.com/user-attachments/assets/f76ed957-84c0-4f30-896c-ecca40890896" />  
Tiedoston oikeuden menevät seuraavanlaisesti: Tiedoston omistaja eli jaakko saa lukea ja kirjoittaa. ryhmä saa lukea ja muut saavat lukea.  


---

**e)** 
Päätin tehdä _cron_ testin muistaakseni sitä ei ole oltu tehty kurssilla. cron suorittaa skripteja ja komentoja tiettyjen aikavälien välein  
Tässä minulla cron tulostaa tekstin joka minuutti tiedostoon tmp hakemistossa.  
<img width="599" height="149" alt="image" src="https://github.com/user-attachments/assets/4a88cb2d-9d48-403f-b8d0-5053e3e0424a" />  
Tässä ensimmäinen ja toinen playbookin suoritus  
<img width="1248" height="676" alt="image" src="https://github.com/user-attachments/assets/f4b90652-7997-4e4e-bc26-1465fc81c1b7" />  
<img width="1222" height="665" alt="image" src="https://github.com/user-attachments/assets/8d767608-2425-4e93-bdd2-8d8bf8729901" />  
Tarkistetaan vielä että toimii  
<img width="565" height="73" alt="image" src="https://github.com/user-attachments/assets/aac317a9-a6a8-4edd-b359-765a416b1783" />  
Toimii!

---

## Lähteet

Tero Karvinen Sudo without password. Luettavissa: https://terokarvinen.com/passwordless-sudo/ Luettu 7.4.2026  
Munroe Sandwich. Luettavissa: https://xkcd.com/149/ Luettu 7.4.2026  
Tero Karvinen Passwordless Sudo with Ansible. Luettavissa: https://terokarvinen.com/passwordless-sudo-with-ansible/ Luettu: 7.4.2026  
ansible.builtin.cron module – Manage cron.d and crontab entries. Luettavissa: https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/cron_module.html Luettu: 7.4.2026  



