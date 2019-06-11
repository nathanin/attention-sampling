FROM tensorflow/tensorflow:latest-gpu-py3

WORKDIR /
RUN apt-get update && \
    apt-get install -y git g++

RUN git clone https://github.com/nathanin/attention-sampling attention-sampling

RUN g++ --version && \
    python --version && \
    python -c "import tensorflow; print(tensorflow.__version__)"

RUN cd attention-sampling && \
    pip install -e . && \
    cd ats/ops/extract_patches && \
    mkdir build && \
    cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release .. && \
    make && make install && \
    cd ../../.. && \
    python -m unittest discover -s tests/ && \