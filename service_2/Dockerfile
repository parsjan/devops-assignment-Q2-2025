FROM python:3.12-slim

RUN apt-get update && apt-get install -y curl bash && \
    curl -Ls https://astral.sh/uv/install.sh | bash && \
    echo 'export PATH="/root/.cargo/bin:$PATH"' >> /root/.bashrc



WORKDIR /app

COPY pyproject.toml uv.lock requirements.txt ./

SHELL ["/bin/bash", "-lc"]
RUN uv pip install --system --requirements requirements.txt

COPY . .

EXPOSE 8002
ENV PATH="/root/.cargo/bin:$PATH"
CMD uv run app.py
