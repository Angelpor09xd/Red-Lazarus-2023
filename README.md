# Red-Lazarus-2023
Una versión de Lazarus que permite la eliminación del CFW de las consolas 3ds
Red Lazarus se originó gracias a un error que permitio el descubrimiento de dicho script, mas detalladamente, se saco la targeta sd en un proceso exacto de Lazarus, dando como resultado una nadn limpia y perfecta, en la version 11.3 del sistema 3ds. Este scrpt permite la eliminacion de CFW de dicha consola, ya que no se enlazan las apliaciones principales al movable.sed, dando como resultado una nand limpia.

Instalación: 

Formatear Sd en FAT32, e introducir los archivos de la carpeta SD en la sd

En una consola brickeada, (brick azul o brick negro) ejecutar ntrboot, para abrir gm9

En gm9 buscamos en la sd la carpeta luma, en dicha carpeta entraremos dentro de payloads

En esa carpeta se encuentra un archivo llamado ¨GoodMode9.firm¨, seleccionamos ese archivo con el boton a

En la pantalla inferior se habilitara un muenu donde seleccionaremos ´´FIRM image options´´ con el boton a

Ahora bajaremos hasta ´´Boot Firm´´ y le damos dos veces seguidas al boton a

De nuevo en gm9, le daremos al boton Home de la consola

En este nuevo menu bajaremos hasta la opcion scripts, con dicha opcion le daremos al boton a

En este menu le daremos a la opcion ´´Red Lazarus 2023´´.

En esta nueva pantalla seguiremos los pasos hasta reinicar (10-15 mins)

Despues tendremos que configurar la consola, ya que estara formateada de fabrica

Cuando estemos en el menu home, tenemos que apagar la consola

Entraremos al modo recovery (L+R+Flecha arriba+A+Power)

En este menu seguiremos los pasos, hasta actualizar la consola



Y listo, ya hemos instalado Red Lazarus, podremos hacer de todo con la consola, incluso eliminar el CFW de ella.

Proceso script .gm9:

# Script que Resucita Consolas de la familia 3DS

# Créditos: 

# AnalogMan151, creador de Lazarus

# Angelpro09_xd, descubridor y cocreador de Red Lazarus y Red Lazarus 2023

# Yakara Colombia, aportador de Archivos Donantes y creador de la primera sismplificación de Lazarus en 2017

# Kelonio 3Ds, creador de la Segunda simplificación de Lazarus en 2022, cocreador estructural de Red Lazarus, autor de Movable-Format(usado para eliminar y restaurar el mobable)

set PREVIEW_MODE 0:/gm9/imagenes/RedLazarus.png

################# Red Red Lazarus 2.0 #################

ask "Este Script revive Consolas BRICKEADAS\nContinuar?"

set ERRORMSG "Cancelado por el usuario."

set ERRORMSG "Cancelado por el usuario."

allow -a S:

################# Comprobacion de Archivos ################# 

set ERRORMSG "ARCHIVOS NECESARIOS NO ENCONTRADOS. \n \nVUELVE A DESCARGAR O USA OTRA TARJETA SD "

find 0:/RedLazarus/twln.bin TWLN

find 0:/RedLazarus/twlp.bin TWLP

find 0:/RedLazarus/sighax_hdr_*.bin SIGHAX

find 0:/RedLazarus/boot9stra*.firm B9S

find 0:/RedLazarus/sector0x9*.bin SECRET

find 0:/RedLazarus/NAND_hdr.bin HDR

find 0:/RedLazarus/twlmbr.bin TWLMBR

find 0:/RedLazarus/ctrtransfer_o2ds.bin CTRNAND

################# Restaurando NAND, TWL, Formateando ################# 

set ERRORMSG "ERROR EN LA RESTAURACION. \n \nVUELVE A DESCARGAR O USA OTRA TARJETA SD"

cp -w -n $[HDR] S:/nand.bin

cp -w -n $[SIGHAX] S:/nand_hdr.bin

cp -w -n $[TWLMBR] S:/twlmbr.bin

cp -w -n $[TWLN] S:/twln.bin

cp -w -n $[TWLP] S:/twlp.bin

cp -w -n $[CTRNAND] S:/ctrnand_full.bin


fixcmac 1:/dbs

fixcmac 1:/title

fixcmac 1:/dbs		

fixcmac 1:/private

cp -w -o -s 0:gm9/Movable/Movable.sed 1:/private/movable.sed

fixcmac 1:/dbs

fixcmac 1:/title

fixcmac 1:/dbs			

fixcmac 1:/private							


###################### Instalando Boot9 #####################

set ERRORMSG "No se pudo inyectar boot9strap!\n \nUsar SafeB9SInstaller al terminar."

cp -w -o -n $[B9S] S:/firm0.bin

cp -w -o -n $[B9S] S:/firm1.bin

###################### Reparando SecretSector #####################

cp -w $[SECRET] S:/sector0x96.bin

###################### Finalizacion #####################

mv -w -o -s 0:/RedLazarus/GodMode9.firm 1:/rw/luma/payloads/GodMode9.firm

cp -w -o -s 0:/RedLazarus/luma.firm 0:/boot.firm

mv -w -o -s 0:/RedLazarus/luma.firm 1:/boot.firm

rm -o -s 0:/RedLazarus

echo "Consola Revivida. \n \nRecuerda actualizar consola\n desde Recovery"

reboot

Red Lazarus permite restaurar y limpiar cualquier nand de las consolas 3ds, ya que sobrescribe los archivos, podiendo eliminar y reparar cualquier tipo de error en la consola.

Red Lazarus solo esta disponible para las consolas old 2ds y new 3ds, en algun fututro llevare este script a mas consolas.
