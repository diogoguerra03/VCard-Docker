# Etapa 1: Construção do projeto
FROM node AS build
WORKDIR /app

# Copiar arquivos para dentro do container
COPY package.json package-lock.json ./
RUN npm install --frozen-lockfile

COPY . .
RUN npm run build

# Etapa 2: Servir a aplicação com Nginx
FROM nginx
COPY --from=build /app/dist /usr/share/nginx/html


CMD ["nginx", "-g", "daemon off;"]
