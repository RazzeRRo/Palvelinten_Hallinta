# Hei ansiblen maailma
## Tiivistelmät
**SSH PUBLIC KEY**
- Ensimmäiseksi pitää päivittää komennolla _sudo atp-get update _ jonka jälkeen asennetaan SSH komennolla _sudo apt-get -y install ssh _
- Tämän jälkeen kannattaa laittaa ssh päälle ja käskeä se käynnistymään aina bootin yhteydessä komennolla _sudo systemctl enable --now ssh_
- Avainparin pystyy luomaan komennolla _ssh-keygen_ ja kolme kertaa yes niin avainpari on luotu automaattisesti ssh hakemistoon
- Julkisen avaimen saa kopioitua komennolla _ssh-copy-id localhost_ authorised keys hakemistoon jonka jälkeen kirjautuminen on automatisoitu
  
**Hello Ansible**
- Ansible on kofiguraationhallintatyökalu jossa infrastruktuuri kuvataan koodia ja muutokset tehdään vain tarvittaessa
- Se toimii SSH:n kautta joten kohdetietokoneelle riittää vain SSH ja Python eikä agentteja tarvita
- Ensin kannattaa testata SSH-yhteys ilman ansiblea
- Päivitä aiemmin mainitulla komennolla ja asenna ansible _sudo apt-get install ansible_
- Luo hosts.ini (inventaario) joks määrittelee hallittavat tietokoneet
- Lopeta ansiblen valittaminen Pythonista _ansible_python_interpreter=/usr/bin/python3_
- Helpota käyttöä määrittämällä ansible.cfg tiedostoon inventory = hosts.ini. Tällöin ei tarvitse aina jokaiseen komentoon määrittää erikseen "-i hosts.ini"
- Pleybook (site.yml) kertoo mitä rooleja ajetaan millekkin koneille
- Roolit sijaitsevat roles/-kansiossa esim. tasks/main.yml sisältää tehtävät
- YAMK vaatii tarkan sisennyksen (kaksi välilyöntiä ensimmäisestä kirjaimesta ei tabulaattoria ja oikean sisennyksen)

## A) Sshecrets. Asenna SSH-demoni ja testaa se kirjautumalla SSH:lla.
Asensin SSH:n komennolla _sudo apt.get -y install ssh_ jonka jälkeen käynnistin sen ja laitoin sen käynnistämään jokaisella bootilla komennolla _sudo systemctl enable --now ssh_. 
Kirjauduin tämän jälkeen sisään komennolla _ssh localhost_
## B) Pubkey. Automatisoi ssh-kirjautuminen julkisella avaimella.
Loin avainparin komennolla _sudo-keygen_ jonka jälkeen kopioin julkisen avaimen komennolla _ssh-copy-id localhost_ authorised keys hakemistoon.
## C) Hei Ansible. Tee hei maailma ansiblella ja kokeile sitä SSH:n yli.
Lopputulokset
<img width="494" height="188" alt="image" src="https://github.com/user-attachments/assets/d3bf1333-a6f9-4b6f-9088-bcd0aeb27c52" />

<img width="1164" height="249" alt="image" src="https://github.com/user-attachments/assets/29bf6d18-b6c6-49f9-b234-cb2908d6bd98" />

## Lähteet

Tero Karvinen SSH public key - Login without password. Luettavissa: https://terokarvinen.com/ssh-public-key-login-without-password/ **Luettu 31.3.2026**
Tero Karvinen Hello Ansible. Luettavissa: https://terokarvinen.com/hello-ansible **Luettu 31.3.2026**
