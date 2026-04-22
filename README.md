# Pràctica de Configuració i Gestió de Correu amb iRedMail

Aquest repositori documenta el procés d'instal·lació, configuració i proves realitzades amb el servidor de correu **iRedMail** en un entorn de proves local.

## 🚀 1. Configuració del Domini
Abans de la instal·lació, és necessari configurar el domini local al fitxer d'hosts per permetre la resolució interna:

```bash
sudo nano /etc/hosts
# Afegir la IP i el domini: 127.0.0.1 mail.serveis11.test serveis11
```

## 📦 2. Instal·lació d'iRedMail
S'ha descarregat i executat l'script d'instal·lació de la versió 1.8.0:

```
# Descarregar la versió estable
wget [https://github.com/iredmail/iRedMail/archive/refs/tags/1.8.0.tar.gz](https://github.com/iredmail/iRedMail/archive/refs/tags/1.8.0.tar.gz) -O iRedMail.tar.gz

# Descomprimir i entrar al directori
tar zxf iRedMail.tar.gz
cd iRedMail-1.8.0/

# Executar l'instal·lador
sudo bash iRedMail.sh
```
## ⚙️ 3. Accessos al Sistema
Un cop finalitzada la instal·lació, els punts d'accés principals són:

Webmail (Roundcube): ``https://<LA_TEVA_IP>/mail/``

Panell d'Administració (iRedAdmin): ``https://<LA_TEVA_IP>/iredadmin/``

## 📝 4. Activitats i Respostes

A. Primers correus rebuts (Postmaster)
En accedir per primer cop al compte de ``postmaster``, trobem tres correus de configuració generats automàticament:

How to configure your mail client applications (MUA): Dades tècniques per configurar Outlook/Thunderbird.

Useful resources for iRedMail administrator: Enllaços a la documentació oficial i fòrums.

Details of this iRedMail installation: Detalls crítics sobre rutes de fitxers i contrasenyes de la base de dades.

B. Investigació: Per què el correu a Gmail va a "Correu Brossa"?
En enviar un correu des del servidor local cap a un compte de Gmail, aquest es marca com a spam. Els motius principals són:

Manca d'autenticació: No hi ha registres SPF, DKIM ni DMARC configurats en un servidor DNS públic que validin la identitat del servidor.

Reputació de la IP: La IP des de la qual enviem no té historial o és una IP privada/dinàmica sense registre PTR (Reverse DNS).

Domini no oficial: L'ús de l'extensió ``.test`` genera desconfiança en els filtres de Google.

C. Investigació: Per què no podem rebre respostes des de Gmail?
En intentar respondre el correu des de Gmail, rebem un error de lliurament (NXDOMAIN).

Motiu: El domini ``serveis11.test`` no existeix als servidors DNS globals d'Internet. Gmail no pot trobar la "ruta" per arribar al nostre servidor local.

D. Consulta de Logs del Sistema
Per analitzar el comportament del servidor en temps real i detectar errors, utilitzem el fitxer de registre de correu:

```
# Monitoritzar els logs de Postfix i Dovecot
tail -f /var/log/mail.log
```
En aquest fitxer podem veure si un correu ha sortit amb èxit (status=sent) o si ha estat rebutjat pel servidor de destinació.

[Guia](guia.md)