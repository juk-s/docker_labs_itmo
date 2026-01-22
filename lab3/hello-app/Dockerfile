FROM python:3.14-alpine
RUN adduser -D -u 10001 appuser
WORKDIR /app
COPY hello.html /app/
USER appuser
EXPOSE 8000

CMD ["python", "-m", "http.server", "8000"]
