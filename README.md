# ColorOS 介绍网站

一个基于 Vite + Vue 3 构建的 ColorOS 系统介绍网站，采用黑底白字的现代化设计风格。

## 技术栈

- **框架**: Vue 3 (Composition API)
- **构建工具**: Vite 5
- **样式**: 原生 CSS (响应式设计)
- **容器化**: Docker + Nginx

## 功能特点

- ✨ 现代化的黑底白字UI设计
- 🎨 流畅的动画效果和交互体验
- 📱 完全响应式，支持移动端和桌面端
- ⚡ 基于Vite的极速开发体验
- 🐳 Docker容器化部署

## 项目结构

```
frontend-test/
├── src/
│   ├── App.vue           # 主应用组件
│   ├── main.js           # 应用入口
│   └── style.css         # 全局样式
├── index.html            # HTML入口文件
├── vite.config.js        # Vite配置
├── package.json          # 项目依赖
├── Dockerfile            # Docker构建文件
├── nginx.conf            # Nginx配置文件
└── README.md             # 项目文档
```

## 本地开发

### 安装依赖

```bash
npm install
```

### 启动开发服务器

```bash
npm run dev
```

访问 http://localhost:5173 查看应用

### 构建生产版本

```bash
npm run build
```

构建产物将输出到 `dist` 目录

### 预览生产构建

```bash
npm run preview
```

## Docker 部署

### 构建 Docker 镜像

```bash
docker build -t coloros-showcase .
```

### 运行容器

```bash
docker run -d -p 80:80 --name coloros-app coloros-showcase
```

访问 http://localhost 查看应用

### 停止容器

```bash
docker stop coloros-app
```

### 删除容器

```bash
docker rm coloros-app
```

## Docker Compose 部署（可选）

创建 `docker-compose.yml` 文件：

```yaml
version: '3.8'

services:
  coloros-web:
    build: .
    ports:
      - "80:80"
    restart: unless-stopped
    container_name: coloros-showcase
```

运行：

```bash
docker-compose up -d
```

## 浏览器支持

- Chrome (最新版本)
- Firefox (最新版本)
- Safari (最新版本)
- Edge (最新版本)

## 许可证

MIT License

## 作者

ColorOS Showcase Team

