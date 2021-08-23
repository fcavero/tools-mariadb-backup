# Backups automágicos de BBDD MariaDB / MySQL

Pequeño *script* de *bash* para llevar a cabo copias de seguridad de bases de datos MariaDB y MySQL, al que acompaña un fichero de configuración donde se definen los modos de ejecución de


## Opciones del «backup» a partir del fichero de configuración

* BACKUP_USER (opcional, en blanco por defecto) → Usuario que ejecuta el _backup_; si el usuario que lanza el _script_ no coincide con lo indicado en esta opción, la ejecución se aborta. Si se deja en blanco no se chequea.
* HOSTNAME (opcional, en blanco o _localhost_ por defecto) → El nombre de la máquina donde se encuentra la BBDD.
* USERNAME y PASSWORD → Credenciales de conexión a MariaDB / MySQL
* BACKUP_DIR → Directorio donde se almacena el _backup_; se crea si no existe, y el usuario de BACKUP_USER debe poder escribir en él.
* D_SCHEMA_ONLY_DB_LIST, W_SCHEMA_ONLY_DB_LIST y M_SCHEMA_ONLY_DB_LIST → Lista de BBDD cuyo esquema debe ser copiado, según la periodicidad indicada en el nombre: _D_, _daily_; _W_, _weekly_; _M_, _monthly_.
* D_FULL_BACKUP_DB_LIST, W_FULL_BACKUP_DB_LIST y M_FULL_BACKUP_DB_LIST → Lista de BBDD cuyo esquema y datos deben ser copiados, según la periodicidad indicada en el nombre: _D_, _daily_; _W_, _weekly_; _M_, _monthly_.
* DAY_OF_WEEK_TO_KEEP (1-7, _Monday-Sunday_)→ Día de la semana en el que se ejecuta el _backup_ diario.
* DAYS_TO_KEEP → Número de días que se conserva el _backup_ diario.
* WEEKS_TO_KEEP → Número de semanas que se conserva el _backup_ semanal.

Ejemplo de fichero de configuración:
<pre>
BACKUP_USER=

HOSTNAME=
 
USERNAME=teto
PASSWORD="xL0rA7dEGU8vs6H6vgh9GFqwnC"

BACKUP_DIR=/u01/backup/mariadb/
 
D_SCHEMA_ONLY_DB_LIST="db-2"
D_FULL_BACKUP_DB_LIST="db-1 db-2"
W_SCHEMA_ONLY_DB_LIST="db-2"
W_FULL_BACKUP_DB_LIST="db-1 db-2"
M_SCHEMA_ONLY_DB_LIST="db-1 db-2"
M_FULL_BACKUP_DB_LIST="db-1 db-2 db-3"
 
#### SETTINGS FOR ROTATED BACKUPS ####
DAY_OF_WEEK_TO_KEEP=7
 
DAYS_TO_KEEP=7
 
WEEKS_TO_KEEP=5
</pre>
