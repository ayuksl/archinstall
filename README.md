#Archlinux Installation (Virtualbox)
### Tastatur Layout
	 loadkeys de-latin1
### Erstes Bild
![Alt-text](Bilder/git-repository.png)
### Überprüfen wie die Festplatte heißt
	losblk
### Datenbank refresh
	pacman -Syy
### Mirrors aktualisieren (reflector)
	reflector -c Germany -a 6 --sort nach rate --save /etc/pacman.d/mirrorlist
### Datenbank refresh
	pacman -Syy
### Partitionstools starten
	cfdisk /dev/sda
gpt Partitionstabelle erstellen
1. 300MB >> EFI System
2. 4GB >> SWAP >> Swapfile
3. 30GB >> / >> LinuxFileSystem
4. Rest >> /home >> LinuxFileSystem
5. Write >> Quit
### List Block
	lsblk
### Partitionsformat
#### EFI Format
	mkfs.fat -f32 /dev/sda1
#### SWAP Format
	mkswap /dev/sda2
#### SWAP aktivieren
	swapon /dev/sda2
#### Root Format ext4
	mkfs.ext4 /dev/sda3
#### /home Format ext4
	mkfs.ext4 /dev/sda4
