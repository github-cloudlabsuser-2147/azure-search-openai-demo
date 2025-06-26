# Backend App Documentation

## Overview

This backend is a Python/Quart application designed for Azure-integrated AI search and chat experiences. It provides RESTful endpoints for chat, Q&A, file upload, speech synthesis, and integrates with Azure OpenAI, Azure Cognitive Search, Azure Blob Storage, and other Azure services. The backend supports authentication, user file uploads, and advanced RAG (Retrieval-Augmented Generation) approaches.

## Main Features

- **Chat and Q&A Endpoints**: Supports both single-turn and multi-turn chat using advanced retrieval and reasoning approaches.
- **Azure Integration**: Uses Azure Cognitive Search, Azure OpenAI, Azure Blob Storage, Azure Speech, and more.
- **Authentication**: Supports Azure AD authentication and access control for content.
- **User File Uploads**: Allows authenticated users to upload, list, and delete files, which are processed and indexed for search.
- **Speech Synthesis**: Converts text to speech using Azure Speech services.
- **Configurable Approaches**: Supports multiple RAG approaches, including vision-enabled models (GPT-4V).
- **Telemetry**: Integrates with Azure Monitor and OpenTelemetry for observability.

## Key Endpoints

- `/ask` (POST): Single-turn Q&A with RAG.
- `/chat` (POST): Multi-turn chat with RAG.
- `/chat/stream` (POST): Streaming chat responses.
- `/upload` (POST): Upload user files (authenticated).
- `/list_uploaded` (GET): List uploaded files for the user.
- `/delete_uploaded` (POST): Delete a user-uploaded file.
- `/speech` (POST): Text-to-speech synthesis.
- `/content/<path>` (GET): Serve content files from storage (authenticated).
- `/config` (GET): Get feature/configuration flags for the frontend.
- `/auth_setup` (GET): Get authentication setup for the frontend.

## Configuration

The backend is configured via environment variables, including Azure service credentials, feature flags, and model/deployment names. See the `setup_clients` function in `app.py` for all supported variables.

## Main Files

- `app.py`: Main Quart app, routes, and setup logic.
- `main.py`: Entrypoint for running the app.
- `config.py`: Configuration constants.
- `prepdocs.py` and `prepdocslib/`: Document processing and ingestion logic.
- `requirements.txt`: Python dependencies.
- `approaches/approach.py`: Base classes and logic for retrieval-augmented generation (RAG) approaches, with detailed comments and docstrings for maintainability.

## Running Locally

1. Set required environment variables for Azure services and models.
2. Install dependencies: `pip install -r requirements.txt`
3. Start the backend (from the `app` directory):
   ```powershell
   pwsh ./start.ps1
   ```

## Requirements

The following Python packages are required by the backend (see `requirements.txt`):

```
aiofiles==24.1.0
aiohappyeyeballs==2.4.4
aiohttp==3.10.11
aiosignal==1.3.1
annotated-types==0.7.0
anyio==4.4.0
asgiref==3.8.1
async-timeout==5.0.1
attrs==24.2.0
azure-ai-documentintelligence==1.0.0b4
azure-cognitiveservices-speech==1.40.0
azure-common==1.1.28
azure-core==1.30.2
azure-core-tracing-opentelemetry==1.0.0b11
azure-cosmos==4.9.0
azure-identity==1.17.1
azure-monitor-opentelemetry==1.6.1
azure-monitor-opentelemetry-exporter==1.0.0b32
azure-search-documents==11.6.0b12
azure-storage-blob==12.22.0
azure-storage-file-datalake==12.16.0
beautifulsoup4==4.12.3
blinker==1.8.2
certifi==2024.7.4
cffi==1.17.0
charset-normalizer==3.3.2
click==8.1.7
cryptography==44.0.1
deprecated==1.2.14
distro==1.9.0
exceptiongroup==1.3.0
fixedint==0.1.6
flask==3.0.3
frozenlist==1.4.1
h11==0.14.0
h2==4.1.0
hpack==4.0.0
httpcore==1.0.5
httpx[http2]==0.27.0
hypercorn==0.17.3
hyperframe==6.0.1
idna==3.10
importlib-metadata==8.0.0
isodate==0.6.1
itsdangerous==2.2.0
jinja2==3.1.6
jiter==0.8.2
markdown-it-py==3.0.0
markupsafe==2.1.5
mdurl==0.1.2
microsoft-kiota-abstractions==1.9.3
microsoft-kiota-authentication-azure==1.9.3
microsoft-kiota-http==1.9.3
microsoft-kiota-serialization-form==1.9.3
microsoft-kiota-serialization-json==1.9.3
microsoft-kiota-serialization-multipart==1.9.3
microsoft-kiota-serialization-text==1.9.3
msal==1.30.0
msal-extensions==1.3.1
msgraph-core==1.3.3
msgraph-sdk==1.26.0
msrest==0.7.1
multidict==6.0.5
oauthlib==3.2.2
openai==1.63.0
opentelemetry-api==1.31.1
opentelemetry-instrumentation==0.52b1
opentelemetry-instrumentation-aiohttp-client==0.52b1
opentelemetry-instrumentation-asgi==0.52b1
opentelemetry-instrumentation-dbapi==0.52b1
opentelemetry-instrumentation-django==0.52b1
opentelemetry-instrumentation-fastapi==0.52b1
opentelemetry-instrumentation-flask==0.52b1
opentelemetry-instrumentation-httpx==0.52b1
opentelemetry-instrumentation-openai==0.39.0
opentelemetry-instrumentation-psycopg2==0.52b1
opentelemetry-instrumentation-requests==0.52b1
opentelemetry-instrumentation-urllib==0.52b1
opentelemetry-instrumentation-urllib3==0.52b1
opentelemetry-instrumentation-wsgi==0.52b1
opentelemetry-resource-detector-azure==0.1.5
opentelemetry-sdk==1.31.1
opentelemetry-semantic-conventions==0.52b1
opentelemetry-semantic-conventions-ai==0.4.3
opentelemetry-util-http==0.52b1
packaging==24.1
pillow==10.4.0
priority==2.0.0
prompty==0.1.50
propcache==0.2.0
psutil==5.9.8
pycparser==2.22
pydantic==2.8.2
pydantic-core==2.20.1
pygments==2.18.0
pyjwt[crypto]==2.10.1
pymupdf==1.26.0
pypdf==4.3.1
python-dotenv==1.0.1
pyyaml==6.0.2
quart==0.20.0
quart-cors==0.7.0
regex==2024.11.6
requests==2.32.3
requests-oauthlib==2.0.0
rich==13.9.4
six==1.16.0
sniffio==1.3.1
soupsieve==2.6
std-uritemplate==2.0.3
taskgroup==0.2.2
tenacity==9.0.0
tiktoken==0.8.0
tomli==2.2.1
tqdm==4.66.5
types-beautifulsoup4==4.12.0.20240511
types-html5lib==1.1.11.20241018
types-pillow==10.2.0.20240822
typing-extensions==4.13.2
urllib3==2.5.0
uvicorn==0.30.6
werkzeug==3.0.6
wrapt==1.16.0
wsproto==1.2.0
yarl==1.17.2
zipp==3.21.0
```

> **Note:** This list is auto-generated and may include transitive dependencies. For the most up-to-date list, see the actual `requirements.txt` file.

## Security

- Authentication and access control are enforced for sensitive endpoints.
- Uploaded files are stored per-user and access-controlled.

## Telemetry

- Azure Monitor and OpenTelemetry are enabled if configured via environment variables.

## Developer Notes

- The `approaches/approach.py` file now includes detailed module-level and class-level comments, explaining its structure and responsibilities. This improves maintainability and onboarding for new contributors.

---
For more details, see the code and comments in `app.py`, `approach.py`, and related modules.
