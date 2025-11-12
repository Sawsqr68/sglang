FROM nvcr.io/nvidia/tritonserver:24.01-py3

WORKDIR /opt

RUN git clone https://github.com/sgl-project/sglang.git

WORKDIR /opt/sglang
RUN pip install --upgrade pip && \
    pip install -e "python[all]" && \
    pip install datasets

# Create unprivileged user and set permissions
RUN groupadd -r appuser \
    && useradd --no-log-init -r -g appuser -d /opt -s /sbin/nologin appuser \
    && chown -R appuser:appuser /opt/sglang

# Switch to unprivileged user
USER appuser
