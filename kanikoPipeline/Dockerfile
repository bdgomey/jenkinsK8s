FROM gcr.io/kaniko-project/executor:debug AS kaniko
FROM amazonlinux:2

# Install AWS CLI
RUN yum install -y unzip && \
    curl "https://d1vvhvl2y92vvt.cloudfront.net/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
RUN chmod +x kubectl
RUN mv kubectl /usr/local/bin/

# Copy Kaniko executor
COPY --from=kaniko /kaniko /kaniko

ENTRYPOINT ["/kaniko/executor"]