# H5 Gitar Hero

## Tiivistykset

### Pro Git- What is Git
- Git tallentaa projektin tilan kokonaisina snapshotteina, ei pelkkinä muutoksina.  
- Jos tiedosto ei muutu, Git viittaa vanhaan versioon mikä säästää tilaa.  
- Lähes kaikki toiminnot tehdään paikallisesti, koska koko historia on koneella.  
- Git käyttää SHA-1 hasheja eli muutokset huomataan aina.  
- Dataa ei yleensä poisteita, vaan uusi tila lisätään vanhan päälle.  
- **Gitin kolme tilaa:**  
  - Modified: tiedosto muokattu, ei vielä Gitissä.  
  - Staged: valittu seuraavaan committiin.  
  - Committed: tallennettu Gitin tietokantaan.
- **Perus workflow**
  - Muokataan tiedostoja.
  - Valitaan mitä halitaan mukaan (staging).
  - Commit eli snapshot talteen.

### Termit / komennot
#### git add --all
 - Lisää kaikki muutokset staging-alueelle.
 - Mukana myös poistot ja uudet tiedostot.
#### git commit
- Luo snapshotin staging-alueen sisällöstä.
- Tallentaa muutokset paikallisesti
#### git pull
- Hakee etärepositorion uusimmat muutokset.
- Yhdistää en omaan haaraan.
#### git push
- Lähettää omat commitit etärepoon.
- Muut näkevät muutokset tämän jälkeen.
#### &&
- Suorittaa seuraavan komennon vain jos edellinen onnistuu.

Nämä löydetty suoraan Gitin omasta cheat sheetista

---
## Tehtävät

### a) Online

Tein uuden reposition githubiin  
<img width="252" height="206" alt="image" src="https://github.com/user-attachments/assets/d72497c9-0739-4127-b11b-9ade93ac6422" />  
Annoin uudelle repolle nimen "GitarHerosunshine" ja kuvaukseen laitoin "sunshine" varmistin myös, että repo on julkinen, sinne lisätään README sekä GNU General Public Lincense V3 on valittuna  
<img width="889" height="710" alt="image" src="https://github.com/user-attachments/assets/cd60fe58-a914-465f-ad63-6ea9743075a2" />  
Seuraavaksi kävin kopioimassa julkisen SSH avaimen  
<img width="1098" height="48" alt="image" src="https://github.com/user-attachments/assets/e0d7b458-6c3e-4559-a581-ae159b294d43" />  
Virtuaalikoneeni SSH:n julkinen avain oli jo liitettynä githubiin mutta sen voisi lisätä painamalla oikealta ylhäältä "profiilikuvasta" siitä settingsiin josta osioon "SSH and GPG keys" joka avaa seuraavan näkymän  
<img width="901" height="182" alt="image" src="https://github.com/user-attachments/assets/20966ffb-3532-4793-8916-d5fb1c7a60a4" />  
"New SSH key" napista avautuu seuraava ikkuna mihin laittaisin julkisen avaimen seuraavanlailla  
<img width="899" height="373" alt="image" src="https://github.com/user-attachments/assets/06cf1eef-086b-4c33-966c-7c9e2d3b0761" />  
Nyt minulla olisi SSH avain valmiina githubissa käytettävissä kun olen painanut vihreää "Add SSH Key" nappia  

### b) Dolly
Kopion "Code" napin alta SSH linkin  
<img width="436" height="425" alt="image" src="https://github.com/user-attachments/assets/2c31d571-1846-4747-8e6b-99a6334c2f96" />  
Seuraavaksi terminaalissa menin gitille tarkoitettuun hakemistoon "code" jossa ajoin seuraavan komennon kloonatakseni hakemiston  
<img width="888" height="54" alt="image" src="https://github.com/user-attachments/assets/2cf795fb-8680-40e8-92d7-3243991a1287" />  
<img width="665" height="148" alt="image" src="https://github.com/user-attachments/assets/f72ce37d-e509-4446-9806-36f3fa67696b" />  
Kloonaus onnistui! Ja siirryin repoon.  
Loin repoon tiedoston "kissakoira.md" mihin laitoin seuraavan sisällön  
<img width="474" height="84" alt="image" src="https://github.com/user-attachments/assets/6507e212-f370-41a1-b19a-16e27ddee4af" />  
Seuraavaksi tein "git add --all" ja git commit jonka kommentiksti laitoin "Add newfile for learning"  
<img width="687" height="249" alt="image" src="https://github.com/user-attachments/assets/069e6183-3eab-4a66-9d14-72ad9b1ed739" />  
Seuraavaksi ajoin "git push" jonka jälkeen tiedoston pitäisti näkyä verkossa  
<img width="577" height="216" alt="image" src="https://github.com/user-attachments/assets/242d0c6b-7946-4450-8c01-d52a7dd1330d" />  
push onnistui tarkistetaan vielä weppipalvelin  
<img width="874" height="387" alt="image" src="https://github.com/user-attachments/assets/941c6293-f2e4-47f2-ad87-1f2ed7fdd032" />  
Tiedosto ilmeistyi weppiin tarkistetaan vielä sisältö  
<img width="605" height="409" alt="image" src="https://github.com/user-attachments/assets/ff8fb289-5504-4701-b5e8-81a6e1e8e945" />  
Kaikki onnistui!  

### c) Doh!
Tässä testasin komentoa _git reset --hard_ kirjoitin jotain tekstiä vaan tiedostoon  
<img width="799" height="165" alt="image" src="https://github.com/user-attachments/assets/a114b4cb-c687-4fc1-ac24-920ff2195186" />  
Ajoin myös _git add --all_ jonka jälkeen ajoin _git reset --hard_ joka palautti version aikaisimpaa snapshottiin  
<img width="678" height="174" alt="image" src="https://github.com/user-attachments/assets/ac97254a-d788-4de7-975c-12b398dfdc40" />  

### d) Tukki
Tutkin aikaisempia muutoksia komennolla _git log --patch_ joka näytti sähköpostin ja kaikki muutkin tiedot oikein  
<img width="1046" height="378" alt="image" src="https://github.com/user-attachments/assets/8d95d559-b5ae-4005-b81e-3780866b4f88" />  

### e) Gitanible
Loin ansbile hakemistoon uuden hakemiston ansibleen jonka main.yml tiedostoon lisäsin seuraavan sisällön  
<img width="240" height="94" alt="image" src="https://github.com/user-attachments/assets/d35dd915-ee63-4af8-ad85-f38d67c79c65" />
<img width="630" height="144" alt="image" src="https://github.com/user-attachments/assets/8c4727e5-f963-41bd-b28b-f37d243c37c5" />  
Tähän meni hetki aikaa löytää miten tehdä mutta onneksi on olemassa Stack Overflow ja ansible community documentation  
ansible playbook saatiin myöskin idempotensiin  
<img width="1147" height="622" alt="image" src="https://github.com/user-attachments/assets/8bdf0c35-2ff4-43aa-8e0a-288dbf64cca1" />  
Testiksi loin uuden tiedoston repoon ja kokeillaan toimiiko pull  
<img width="574" height="259" alt="image" src="https://github.com/user-attachments/assets/2acdc227-5945-4daa-ab7c-db5de05e1228" />  
Uusi tiedosto luotu ja aika kokeilla ansiblea  
<img width="1205" height="625" alt="image" src="https://github.com/user-attachments/assets/21cc7d5b-2d63-447b-92ba-241e78e9f064" />  
Jotain muutettiin ja päästiin idempotenssiin käydään vielä katsomassa että varmasti onnistui  
<img width="727" height="128" alt="image" src="https://github.com/user-attachments/assets/e7c9b1ae-fa92-4a9c-ae35-2daa7792841f" />  
Nyt toimii!!  

### F) Pari löydetty

### H) yhteistyötä
Saatiin tehtyä parin kanssa yhteinen kirjoitus samaan repoon  
<img width="920" height="313" alt="image" src="https://github.com/user-attachments/assets/1ccb2f27-455c-4f80-84f6-4a9f61e13bf2" />  
<img width="657" height="487" alt="image" src="https://github.com/user-attachments/assets/52696880-5998-429e-83dc-fea7609e037a" />  
Kuvat logeista missä näkee molempien commitit repoon.  

---

## Lähteet
Chacon and Straub 2014: 1.3 Getting Started - What is Git? Luettavissa: https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F Luettu: 28.4.26  
Git Cheat Sheet Luettavissa: https://git-scm.com/cheat-sheet Luettu 28.4.26  
git pull command using Ansible Luettavissa: https://stackoverflow.com/questions/59500228/git-pull-command-using-ansible Luettu: 28.4.26
ansible.builtin.git module – Deploy software (or files) from git checkouts Luettavissa: https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/git_module.html Luettu 28.4.26  
