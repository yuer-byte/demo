# 使用官方 Python 3.12 基础镜像
FROM python:3.12-slim

# 安装最小系统依赖
RUN apt-get update && \
    apt-get install -y \
    libgl1 \
    && rm -rf /var/lib/apt/lists/*

# 设置工作目录
WORKDIR /app

# 强制安装无头版OpenCV
RUN pip install --no-cache-dir numpy>=1.26.0 opencv-python-headless>=4.8.0

# 复制依赖文件
COPY requirements.txt .

# 安装 Python 依赖
RUN pip install --no-cache-dir -r requirements.txt

# 复制应用代码和模型文件
COPY . .

# 设置环境变量强制无头模式
ENV QT_QPA_PLATFORM=offscreen
ENV OPENCV_VIDEOIO_DEBUG=0
ENV OPENCV_LOG_LEVEL=ERROR

# 指定容器启动命令
CMD ["python", "yolov4.py"]
