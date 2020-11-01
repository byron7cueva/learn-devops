FROM node:12

# Copiar los archivos que necesita el comando npm install
COPY ["package.json", "package-lock.json", "/usr/src/"]

WORKDIR /usr/src

# Cuando se construye la aplicacion nuevamente las cosas que ya tiene las saca de cache no es necesario bajarlas o hacerlas
# nuevamente
RUN npm install

# Aca no es necesario diferenciar los archivos que ya fueron copiados, ya que docker se da cuenta de eso
# Con esto solo copio los archivos que faltan
COPY [".", "/usr/src/"]

EXPOSE 3000

CMD ["npx", "nodemon", "index.js"]
