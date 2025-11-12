FROM nvcr.io/nvidia/tritonserver:24.01-py3

WORKDIR /opt

RUN git clone https://github.com/sgl-project/sglang.git

WORKDIR /opt/sglang
RUN pip install --upgrade pip && \
    pip install -e "python[all]" && \
    pip install datasets

# Create unprivileged user and set ownership
RUN groupadd -r iam32 \
    && useradd --no-log-init -r -g iam32 -d /sgl-workspace -s /sbin/nologin iam32 \
    && chown -R iam32:iam32 /opt/sglang || true \
    && chown -R iam32:iam32 /sgl-workspace || true

USER iam32
