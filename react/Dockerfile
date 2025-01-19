FROM node:18.13.0-alpine

WORKDIR /app

COPY package.json /app/package.json
COPY package-lock.json /app/package-lock.json


RUN npm install

COPY . .

# Собираем проект
#RUN npm run build
CMD ["npm" , "run", "build"]


FROM nginx:latest

# Копируем скомпилированное приложение в директорию Nginx
COPY --from=build /app/build /usr/share/nginx/html

# Устанавливаем конфигурацию Nginx
COPY ./nginx/nginx.conf /etc/nginx/nginx.conf

# Экспонируем порты 80 и 443 для HTTP и HTTPS
EXPOSE 80 443

# Стартуем Nginx
CMD ["nginx", "-g", "daemon off;"]