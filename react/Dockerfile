FROM node:latest AS build

WORKDIR /app

COPY package.json /app/package.json
COPY package-lock.json /app/package-lock.json


#RUN npm install
CMD ["npm" , "install"]

COPY . .

# Собираем проект
#RUN npm run build
CMD ["npm" , "run", "build"]


FROM nginx:latest

# Копируем скомпилированное приложение в директорию Nginx
# Копируем собранное приложение в директорию Nginx
COPY --from=build /app/build /usr/share/nginx/html
# Экспонируем порты 80 и 443 для HTTP и HTTPS
EXPOSE 80 443

# Стартуем Nginx
CMD ["nginx", "-g", "daemon off;"]