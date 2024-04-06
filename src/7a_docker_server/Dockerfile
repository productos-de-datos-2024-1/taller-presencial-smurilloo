# 
# Docker Server
# =============================================================================
#
# Implementa un servicio API en Docker que se ejecuta en el puerto 5000.
#
# Para la comunicación entre el cliente y el servidor se debe crear una red 
# privada en Docker y ejecutarlos en dicha red:
#
# $En el terminal correr: docker network create mynetwork
# 50576e056bb697ad67783e211d5c55f0c92c96a1d49d28bb02476f6ef9790b63

# Para consturir la imagen del servidor se ejecuta:
#
# Esta linea para crear la imagen requiere estar ubicado con "cd" en la carpeta donde esta el dockerfile
# La siguiente línea el nombre del repositorio y el nombre de la aplicación, adicional el espacio y punto al final indica el directorio actual

# $ docker build --tag=netdkr753159/api-server:0.1 . 
#
# Las imagenes actuales se pueden listar con:
#
# $ docker image ls
#
# Para lanzar el servidor se ejecuta:
#
# $ docker run --network=mynetwork --rm -it --name=api-server -p 5001:5000 -v "$PWD"/datalake:/datalake netdkr753159/api-server:0.1
# El correcto es:
# docker run --network=mynetwork --rm -it --name=api-server -p 5001:5000 -v /c/Users/livei/OneDrive/Escritorio/Maestria_tes/Semestre_3/Talleres/TallerV2/taller-presencial-smurilloo/datalake/:/datalake netdkr753159/api-server:0.1

# 50576e056bb697ad67783e211d5c55f0c92c96a1d49d28bb02476f6ef9790b63

# Definición de la imagen base
FROM python:3.9-alpine

# Folder de la app dentro del contenedor
WORKDIR /app
COPY . /app/

# Instalación de dependencias
RUN pip install --upgrade pip
RUN pip install pandas flask 
RUN apk update && apk add python3-dev gcc g++ libc-dev libffi-dev
RUN pip install scikit-learn==1.4.0 

# Datalake
RUN mkdir /datalake

# Punto de entrada
EXPOSE 5000
WORKDIR /workspace
ENTRYPOINT ["python", "/app/server.py"]

