# Use uma imagem oficial do Node.js
FROM node:18-alpine

# Define o diretório de trabalho no contêiner
WORKDIR /app

# Copia o arquivo package.json e package-lock.json
COPY package*.json ./

# Instala as dependências do projeto
RUN npm install

# Copia o restante dos arquivos do projeto
COPY ./src ./src

# Expõe a porta que o React usa
EXPOSE 3000

# Comando para iniciar a aplicação
CMD ["npm", "start"]
