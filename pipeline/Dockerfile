FROM python:3.13.13-slim

COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/

WORKDIR /code
ENV PATH="/code/.venv/bin:$PATH" 

# using this, there will be no need to add uv to ENTRYPOINT

COPY pyproject.toml .python-version uv.lock ./

# RUN pip install pandas pyarrow

RUN uv sync --locked 

COPY pipeline.py .

ENTRYPOINT ["python", "pipeline.py"]