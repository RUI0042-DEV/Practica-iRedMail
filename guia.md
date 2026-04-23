# Pràctica iRedMail



## 1. Configuració dominis

Abans d'instal·lar el servei configurarem el domini.

```
# obrirem aquest arxiu per configurar el nostre domini
sudo nano /etc/hosts
```

![alt text](<pics/Captura de pantalla 2026-04-16 195047.png>)


## 2. Instalació iRedMail

Per instal·lar iRedMail haurem d'executar aquests ordres:

```
# Descarregar la darrera versió estable (1.8.0)

wget https://github.com/iredmail/iRedMail/archive/refs/tags/1.8.0.tar.gz -O iRedMail.tar.gz

# Descomprimir

tar zxf iRedMail.tar.gz

# Entrar al directori (ajusta el nom si la carpeta varia)

cd iRedMail-1.8.0/

# Donar permisos i executar l'script

sudo bash iRedMail.sh
```

![alt text](<pics/Captura de pantalla 2026-04-16 195055.png>)

![alt text](<pics/Captura de pantalla 2026-04-16 195209.png>)


Un cop instal·lat apareixerà una interfície per configurar el nostre iredmail.

![alt text](<pics/Captura de pantalla 2026-04-16 195638.png>)

![alt text](<pics/Captura de pantalla 2026-04-16 195751.png>)

![alt text](<pics/Captura de pantalla 2026-04-16 195806.png>)

![alt text](<pics/Captura de pantalla 2026-04-16 195842.png>)

Un cop acabat la instal·lació ens demanarà actuar el firmware i reniciar el sistema.

## 3. Panell administració

Per poder entrar el tauler de control per configurar haureu de posar:

```
Ip host only/iredmail/

#exemple 192.168.56.202/iredmail/
```

![alt text](<pics/Captura de pantalla 2026-04-16 201015.png>)

### 3.1 Creació d'usuaris

Add --> User

![alt text](<pics/Captura de pantalla 2026-04-22 203012.png>)

I aquí podreu crear l'usuari.

![alt text](<pics/Captura de pantalla 2026-04-16 201759.png>)

## 4. Webmail

Ara per poder entrar al correu hauràs d'anar al navegador i cercar:

```

Ip host only/mail/

exemple: 192.168.56.202/mail/

```

![alt text](<pics/Captura de pantalla 2026-04-16 201929.png>)

![alt text](<pics/Captura de pantalla 2026-04-16 201936.png>)

## 5.Activitats

- Configurar el servidor de correu per tal de donar servei a un domini serveisX.test on X sigui el vostre nº de llista.

![alt text](<pics/Captura de pantalla 2026-04-16 195751.png>)

- Entrar al webmail com postmaster (administrador), quins correus s’han rebut?

  - How to configure your mail client applications (MUA): Instruccions per configurar programes de correu externs.

  - Useful resources for iRedMail administrator: Recursos i enllaços d'ajuda per a l'administrador del sistema.

  - Details of this iRedMail installation: Detalls tècnics i accessos de la instal·lació d'iRedMail realitzada.

![alt text](<pics/Captura de pantalla 2026-04-22 204217.png>)


---

- Donar d’alta dos usuaris i comprovar com poden rebre correus entre sí.

![alt text](<pics/Captura de pantalla 2026-04-22 205304.png>)

![alt text](<pics/Captura de pantalla 2026-04-22 204725.png>)

---

- Enviar un correu a un correu vostre de gmail des d’un dels usuaris. Veuràs que va a correu brossa. Investiga perquè.

![alt text](<pics/Captura de pantalla 2026-04-16 202000.png>)

El fet que els correus enviats des del teu servidor (iRedMail) vagin a la bústia de correu brossa (spam) de Gmail és un comportament molt comú en servidors nous o de prova. Això passa perquè Google aplica filtres de seguretat molt estrictes per evitar el phishing i el correu brossa.

---

- Podeu enviar un correu de resposta cap el vostre servidor? Per què?

![alt text](<pics/Captura de pantalla 2026-04-16 202153.png>)

Perquè el domini que el domini (serveis11.test) no existeix a la xarxa pública d'Internet. Com es veu a la captura de pantalla de Gmail, l'error és de tipus NXDOMAIN (Non-Existent Domain).

Els servidors de correu externs (com Gmail) necessiten consultar els registres DNS mundials per saber a quina adreça IP han d'enviar el missatge. Com que l'extensió .test està reservada per a proves locals i no està registrada oficialment, Gmail no pot "trobar" el teu servidor i el missatge és retornat com a fallit.

---

- Crear un segon domini que es digui alumneX.test i fer un usuari de prova (usuari). Envieu correus entre usuaris dels dos dominis.

![alt text](<pics/Captura de pantalla 2026-04-22 195018.png>)

---

- Crear i eliminar un usuari de correu d’algun dels dominis.

![alt text](<pics/Captura de pantalla 2026-04-22 205538.png>)

![alt text](<pics/Captura de pantalla 2026-04-22 205534.png>)

---

- Mirar quina informació es disposa als logs.

![alt text](<pics/Captura de pantalla 2026-04-22 205803.png>)


[Tornar enrere](README.md)