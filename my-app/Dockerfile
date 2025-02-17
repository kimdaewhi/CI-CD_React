# Node.js 18 경량 이미지 사용
FROM node:19-alpine

# 작업 디렉토리 설정
WORKDIR /app

# package.json과 package-lock.json 복사 후 의존성 설치
COPY package.json package-lock.json ./
RUN npm install --frozen-lockfile

# 앱 소스 코드 복사
COPY . .

# React 빌드 실행
RUN npm run build

# Nginx를 이용한 정적 파일 서빙
FROM nginx:alpine
COPY --from=0 /app/build /usr/share/nginx/html

# Nginx 실행
CMD ["nginx", "-g", "daemon off;"]

EXPOSE 80
