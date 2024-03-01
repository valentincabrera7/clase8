# Manejo de datos 

# Convertir diccionario a formato JSON
import json
clientes = {}
cadena_json = json.dumps(clientes)
print(cadena_json)

# Convertir diccionario a formato JSON codificado en UTF-8, con dumps
cadena_json = json.dumps(clientes, ensure_ascii=False)
print(cadena_json)

import json
from pathlib import Path 

clientes = {}
clientes["clientes"] = []
clientes["clientes"].append({"Nombre": "Valentin Cabrera", "Edad": 25, "Pais": "Argentina"})
clientes["clientes"].append({"Nombre": "Valen C", "Edad": 25, "Pais": "Argentina"})

# Establecer ruta
BASE_DIR = Path(__file__).resolve().parent
ruta_archivo = BASE_DIR / "clientes.json"

# Guardar el diccionario en un archivo json
# Escritura de archvio json
archivo = open(ruta_archivo, "w", encoding="UTF-8") 
json.dump(clientes, archivo, indent=4, ensure_ascii=False) # dump necesita 2 argumentos: clientes y archivo
archivo.close()
# Forma mas comun de manejar archivos: with, nos despreocupa de usar close()
#with open(ruta_archivo, "w", encoding="UTF-8") as archivo:
    #json.dump(clientes, archivo, indent=4, ensure_ascii=False)

# Lectura de archivo json 
import json 
from pathlib import Path

# Establecer ruta 
BASE_DIR = Path(__file__).resolve().parent

with open(BASE_DIR / "clientes.json", "r") as archivo:
    clientes = json.load(archivo)

print(clientes)

# Ejercicio
import json
from pathlib import Path

BASE_DIR = Path(__file__).resolve().parent
notas = []

while True:
    nombre = input("Ingrese el nombre del alumno o s para salir: ")
    if nombre == "s":
        break
    nota = float(input("Ingrese la nota del alumno: "))
    alumno = {"Nombre": nombre, "Nota": nota}
    notas.append(alumno)

with open(BASE_DIR / "notas.json", "w") as archivo:
    json.dump(notas, archivo)

print("Las notas se han guardado en notas.json")

# Pandas (como usarlo sin usar jupyter)

from pathlib import Path
import pandas

BASE_DIR = Path(__file__).resolve().parent
ruta_archivo = BASE_DIR / "dataset.turnos.csv"

# Cargamos los datos en la memoria pandas
datos = pandas.read_csv(ruta_archivo)
