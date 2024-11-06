# CTF Memo

## Nmap

```bash
nmap -A ip -p-
```

- `-A`: Essaye de découvrir le système hôte
- `-p-`: Test tous les ports de 1 à 65535

### Ports

- 135-139 : Windows car Remote Desktop
- 3389    : RDP
- 3306    : MySQL
- 80      : Web

## Searchsploit

```bash
searchsploit apache 2.4.57
```

## Metasploit

- `msfconsole` : Pour lancer Metasploit
- `setg` : Mettre des variables globales
  - Exemple : `setg RHOSTS (ip de cible)`
  - Exemple : `setg RHOSTS 1.1.1.1`
  - Exemple : `setg LHOSTS (mon ip)` pour reverse shell
  - Exemple : `setg LPORT 1234` pour le port du reverse shell

- `search (module)` : Rechercher un module
  - Exemple : `search tika`

- `use (numéro à utiliser)` : Utiliser un module
  - Exemple : `use 3`

- `info` : Explique la faille et comment la configurer

- `sessions` : Affiche les sessions ouvertes

- `jobs` : Affiche les jobs lancés

- `run` : Lancer un job
  - `run -j` : Lancer un job en arrière-plan

- `sessions 1` : Rejoindre la session 1 si le job a réussi

## FTP

```bash
ftp 1.1.1.1
```

- Utilisateur : `anonymous`
- Mot de passe : vide

## Feroxbuster

```bash
feroxbuster -u http://1.1.1.1:port/
```
- Cherche s'il y a d'autres pages

