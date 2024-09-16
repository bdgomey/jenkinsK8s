FROM gcr.io/kaniko-project/executor:debug AS kaniko
FROM amazonlinux:2

# Install AWS CLI
RUN yum install -y unzip && \
    curl "https://d1vvhvl2y92vvt.cloudfront.net/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install

# Copy Kaniko executor
COPY --from=kaniko /kaniko /kaniko

ENTRYPOINT ["/kaniko/executor"]