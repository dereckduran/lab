FROM ubuntu:24.04

RUN apt-get update && apt-get install -y nginx && \
	rm -rf /var/kib/apt/lists/*

# Create non root user
RUN useradd --create-home appuser

# Switch to non root
USER appuser

CMD ["nginx", "-g", "daemon off;"]
