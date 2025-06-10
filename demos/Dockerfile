FROM python:3.9-slim

# Instalamos Flask (y una versión antigua vulnerable de 'requests' a propósito para que Trivy lo detecte)
RUN pip install flask==2.0.0 requests==2.19.1

# Creamos una app básica
RUN echo "\
from flask import Flask\n\
app = Flask(__name__)\n\
@app.route('/')\n\
def hello():\n\
    return 'Hola desde Harbor con Flask y Trivy'\n\
if __name__ == '__main__':\n\
    app.run(host='0.0.0.0', port=80)" > /app.py

EXPOSE 80
CMD ["python", "/app.py"]
