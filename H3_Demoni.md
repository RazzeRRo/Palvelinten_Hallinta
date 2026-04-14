# H3 DEMONI

## Tiivistykset 

### Apache installed with Ansible - quick notes
- Apache2 on verkkopalvelin
- Apachen voi asentaa ja konfiguroida ansiblella
- Muutokset kofiguraatioon tulee voimaan vasta uudelleenkäynnistyksen jälkeen
- Onkohan Apache2 eniten käytetty webbipalvelin

### Handlers: running operations on change

#### Handlers johdanto
- Handlerit tulevat toimintaan jos muuhun ohjelmaan tulee muutoksia
- Handlerit voivat esim. restarttaa palvelimen
- Handlerit nopeuttavat toimintaa huomattavasti

#### Notifying handlers
- Tehtävä voi kutsua yhden tai useamman handlerin
- Handleri suoritetaan vain jos jotain muuttuu
- Handlerit suoritetaan siinä järjestyksessä missä ne kutsutaan tehtävässä

### ansible-doc service
- Hallitsee palveluiden tilaa
- **Enabled** määrittää käynnistyykö palvelu bootin yhteydessä
- **Name** palvelun nimi (pitää olla muodossa str) esim. apache2
- **State** palvelun tila esim. _started, stopped, restarted, reloaded_
#### Examples
 - name: start service hhtpd, if not started  
    ansible.builtin.service:  
      name: httpd  
      state: started

---

### Tehtävät

**a)**
Ensimmäisen kuten aina tein _sudo apt update_ jonka jälkeen asensin apachen komennolla _sudo apt install apache2_  
Loin kotihakemistooni hakemiston _/publicsite_ johon loin _index.html_ nimisen tiedoston. Tiedostoon laitoin vain simppeliä tekstiä.  
Seuraavaksi loin _/etc/apache2/sites-available_ kansioon tiedoston _etusivu.com.conf_ jonne laitoin seuraavan tekstin  
<img width="524" height="202" alt="image" src="https://github.com/user-attachments/assets/46473adc-5782-4794-9c07-1c35ba292852" />  
Seuraavaksi linkitin tiedoston _sites-enabled_ hakemistoon komennolla _sudo ln -s /etc/apache2/sites-available/etusivu.com.conf /etc/apache2/sites-enabled/_  
<img width="571" height="58" alt="image" src="https://github.com/user-attachments/assets/7296c14d-8adc-4a71-9bf7-9a2636546c70" />  
Ennen testausta annoin ohjeiden mukaisille hakemistoille ja tiedostoille  
<img width="496" height="73" alt="image" src="https://github.com/user-attachments/assets/17d57a80-169c-499c-ac6a-32b08e7dee70" />  
Tein configtestin joka antoin positiivista  
<img width="1222" height="86" alt="image" src="https://github.com/user-attachments/assets/caec9a41-2992-4bc9-a86f-6c7dc28efebe" />  
Syntaksi OK!  
Tämän jälkeen käynnistin apachen uudelleen komennolla _sudo systemctl testart apache2_ ja kävin katsomassa sivuston  
<img width="560" height="217" alt="image" src="https://github.com/user-attachments/assets/90871c06-2d6e-45a3-a8b7-56d265bb000b" />  
Sivu toimii mutta ei tykkää ääkkösistä :)

---

**b)**
Kuten aikaisemmassa aloitin tekemällä _sudo apt update_ jonka jälkeen asensin nginx  
Tämän jälkeen menin _/etc/nginx/sites-available_ jossa muokkasin tiedostoa _default_ seuraavasti  
<img width="293" height="56" alt="image" src="https://github.com/user-attachments/assets/ffd2b0c4-a3be-4f81-8204-b6b6bf2fffbf" />  
Pystyin käyttämään aiemmin luomaani hakemistoa ja tiedostoa jota hieman muokkasin nähdääkseni eron  
<img width="317" height="79" alt="image" src="https://github.com/user-attachments/assets/409eb7a7-8569-4077-9a90-f9acfdde6b82" />  
Ja hienosti toimii!

---

**c)**
Aloitin luomalla kuvassa olevan hakemistorakennuksen ansible hakemistooni  
<img width="251" height="197" alt="image" src="https://github.com/user-attachments/assets/c4b843e6-5611-4913-be33-d8058722c8b3" />  
Laitoin seuraavan sisällön _/tasks/main.yml_ tiedostoon  
<img width="424" height="286" alt="image" src="https://github.com/user-attachments/assets/dc6f95ae-240e-49d1-a9e4-ffb2ce4fd7a9" />  
Seuraavassa _/handlers/main.yml_  
<img width="214" height="93" alt="image" src="https://github.com/user-attachments/assets/f3fac2d0-824c-470e-b487-9fe7eefd3f18" />  
Viimeisenä _/files/default_ jonka sisällön hain komennolla _cat /etc/nginx/sites-available/default | grep -v '#'_  
<img width="557" height="405" alt="image" src="https://github.com/user-attachments/assets/6ef646e2-f9f8-4ce2-8217-e13a6df2ed49" />  
Ensimmäinen playbookin toisto  
<img width="914" height="231" alt="image" src="https://github.com/user-attachments/assets/73db8001-31ca-489b-8919-c68738488461" />  
Ja toinen perään  
<img width="911" height="328" alt="image" src="https://github.com/user-attachments/assets/7a5b827a-8e83-4f9a-9788-9871da0bd21b" />  
<img width="298" height="73" alt="image" src="https://github.com/user-attachments/assets/7be8ccd3-7492-462a-afdf-25f45d57a4ab" />  
Näyttäisi toimivan

---

## Lähteet
Apache installed with Ansible - quick notes Luettavissa: https://terokarvinen.com/apache-ansible/ Luettu: 14.4.2026  
Handlers: running operations on change Luettavissa: https://docs.ansible.com/projects/ansible/latest/playbook_guide/playbooks_handlers.html Luettu: 14.4.2026  
