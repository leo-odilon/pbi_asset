# Etapa 1: Construir a aplicação
FROM node:20 AS build

# Definir o diretório de trabalho dentro do container
WORKDIR /app

# Copiar o package.json e o package-lock.json para o diretório de trabalho
COPY package*.json ./

# Instalar as dependências do projeto
RUN npm install

# Copiar todo o código-fonte para o diretório de trabalho
COPY ./public ./public
COPY ./src ./src

# Construir a aplicação React
RUN npm run build

# Etapa 2: Servir a aplicação já construída
FROM node:20-alpine

# Instalar o servidor estático `serve`
RUN npm install -g serve

# Definir o diretório de trabalho dentro do container
WORKDIR /app

# Copiar os arquivos construídos da etapa anterior
COPY --from=build /app/build ./build

# Expor a porta em que o servidor estará rodando
EXPOSE 3000

# Comando para iniciar o servidor de arquivos estáticos
CMD ["serve", "-s", "build", "-l", "3000"]


