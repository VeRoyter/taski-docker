FROM node:18
WORKDIR /app

COPY package.json package.json
COPY package-lock.json package-lock.json

RUN npm install

COPY . .
RUN npm run build

# Теперь фронтенд только собирает файлы и копирует их в общую папку (volume)
# После копирования контейнер закончит свою работу.
CMD ["cp", "-r", "build/.", "/frontend_static/"]
