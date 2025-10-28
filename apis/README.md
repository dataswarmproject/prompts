# AI APIs and Integrations

**Programmatic access to AI models for building intelligent applications.**

## Major AI API Providers

### 1. Anthropic Claude API

**Models**: Claude 3.5 Sonnet, Claude 3 Opus, Claude 3 Haiku

**Key Features**:
- 200K context window
- Function calling (tool use)
- Vision capabilities
- Streaming responses
- JSON mode
- Safety built-in

**Pricing** (per million tokens):
- Claude 3.5 Sonnet: $3 input / $15 output
- Claude 3 Opus: $15 input / $75 output
- Claude 3 Haiku: $0.25 input / $1.25 output

**Quick Start**:
```python
from anthropic import Anthropic

client = Anthropic(api_key="your_api_key")

message = client.messages.create(
    model="claude-3-5-sonnet-20241022",
    max_tokens=1024,
    messages=[
        {"role": "user", "content": "Hello, Claude!"}
    ]
)

print(message.content[0].text)
```

**Use Cases**:
- Code generation and analysis
- Long document processing
- Complex reasoning tasks
- Content creation

**Documentation**: https://docs.anthropic.com

---

### 2. OpenAI API

**Models**: GPT-4 Turbo, GPT-4, GPT-3.5 Turbo, DALL-E, Whisper, TTS

**Key Features**:
- Function calling
- JSON mode
- Vision (GPT-4V)
- Image generation (DALL-E)
- Speech-to-text (Whisper)
- Text-to-speech
- Embeddings
- Fine-tuning

**Pricing** (per million tokens):
- GPT-4 Turbo: $10 input / $30 output
- GPT-4: $30 input / $60 output
- GPT-3.5 Turbo: $0.50 input / $1.50 output

**Quick Start**:
```python
from openai import OpenAI

client = OpenAI(api_key="your_api_key")

response = client.chat.completions.create(
    model="gpt-4-turbo",
    messages=[
        {"role": "user", "content": "Hello, GPT!"}
    ]
)

print(response.choices[0].message.content)
```

**Use Cases**:
- General chatbots
- Content generation
- Image creation
- Voice applications

**Documentation**: https://platform.openai.com/docs

---

### 3. Google Gemini API

**Models**: Gemini Pro, Gemini Pro Vision, Gemini Ultra

**Key Features**:
- Multimodal (text, image, video, audio)
- Long context (up to 2M tokens)
- Function calling
- Streaming
- Embeddings
- Free tier available

**Pricing**:
- Gemini Pro: Free (rate limited) or pay-as-you-go
- Gemini Pro Vision: $0.002 per image
- Gemini Ultra: Coming soon

**Quick Start**:
```python
import google.generativeai as genai

genai.configure(api_key="your_api_key")

model = genai.GenerativeModel('gemini-pro')
response = model.generate_content("Hello, Gemini!")

print(response.text)
```

**Use Cases**:
- Multimodal analysis
- Long document processing
- Free tier projects
- Google Cloud integration

**Documentation**: https://ai.google.dev

---

### 4. Cohere API

**Models**: Command, Command R, Command R+, Embed, Rerank

**Key Features**:
- Enterprise-focused
- Retrieval-augmented generation (RAG)
- Embeddings optimized for search
- Reranking
- Classification
- Multilingual support

**Pricing**:
- Command: $1 per million tokens
- Embed: $0.10 per million tokens
- Free tier: 100 requests/month

**Quick Start**:
```python
import cohere

co = cohere.Client('your_api_key')

response = co.generate(
    model='command',
    prompt="Write a product description",
    max_tokens=300
)

print(response.generations[0].text)
```

**Use Cases**:
- Enterprise search
- RAG applications
- Document classification
- Semantic search

**Documentation**: https://docs.cohere.com

---

## Specialized APIs

### 5. Stability AI (Stable Diffusion)

**Purpose**: Image generation and editing

**Models**: SDXL, SD 1.5, SD 2.1

**Features**:
- Text-to-image
- Image-to-image
- Inpainting
- Upscaling
- Control over style

**Pricing**: Credit-based, ~$0.002-0.08 per image

**Quick Start**:
```python
import stability_sdk.interfaces.gooseai.generation.generation_pb2 as generation

# Initialize client
stability_api = client.StabilityInference(
    key=os.environ['STABILITY_KEY'],
    engine="stable-diffusion-xl-1024-v1-0",
)

# Generate image
answers = stability_api.generate(
    prompt="A serene landscape with mountains",
    steps=30,
)
```

**Use Cases**:
- Marketing visuals
- Product mockups
- Concept art
- Design assets

---

### 6. ElevenLabs API

**Purpose**: Text-to-speech and voice cloning

**Features**:
- Natural-sounding voices
- Voice cloning
- Multiple languages
- Emotion control
- Streaming audio

**Pricing**: Character-based, starts at $5/mo

**Quick Start**:
```python
from elevenlabs import generate, play

audio = generate(
    text="Hello, this is a generated voice",
    voice="Bella",
    model="eleven_monolingual_v1"
)

play(audio)
```

**Use Cases**:
- Voiceovers
- Accessibility
- Audiobooks
- Voice assistants

---

### 7. Replicate

**Purpose**: Run AI models via API

**Features**:
- 1000s of open-source models
- No infrastructure management
- Pay per use
- Custom model deployment

**Pricing**: Varies by model, ~$0.0001-0.05 per run

**Quick Start**:
```python
import replicate

output = replicate.run(
    "stability-ai/sdxl:latest",
    input={"prompt": "A futuristic cityscape"}
)

print(output)
```

**Use Cases**:
- Experimenting with models
- Prototyping
- Comparing models
- Open-source models

---

### 8. Hugging Face Inference API

**Purpose**: Access to 150K+ models

**Features**:
- Transformers, Diffusers, etc.
- Free tier
- Serverless inference
- Custom model deployment
- AutoTrain

**Pricing**:
- Free: Rate-limited
- Pro ($9/mo): Higher limits
- Enterprise: Custom

**Quick Start**:
```python
from huggingface_hub import InferenceClient

client = InferenceClient(token="your_token")

response = client.text_generation(
    "Write a story about AI",
    model="meta-llama/Llama-2-7b-chat-hf"
)

print(response)
```

**Use Cases**:
- Open-source models
- Fine-tuned models
- Research
- Prototyping

---

## Development & Repository APIs

**A comprehensive collection of APIs for developers, including repository management, testing tools, and development utilities.**

This section is curated from the excellent [public-apis](https://github.com/public-apis/public-apis) project.

### Repository & Version Control

| API | Description | Auth | HTTPS | CORS |
|:---|:---|:---|:---|:---|
| [GitHub](https://docs.github.com/en/free-pro-team@latest/rest) | Make use of GitHub repositories, code and user info programmatically | `OAuth` | Yes | Yes |
| [GitLab](https://docs.gitlab.com/ee/api/) | Automate GitLab interaction programmatically | `OAuth` | Yes | Unknown |
| [Bitbucket](https://developer.atlassian.com/bitbucket/api/2/reference/) | Bitbucket API | `OAuth` | Yes | Unknown |
| [Gitter](https://developer.gitter.im/docs/welcome) | Chat for Developers | `OAuth` | Yes | Unknown |

### DevOps & Deployment

| API | Description | Auth | HTTPS | CORS |
|:---|:---|:---|:---|:---|
| [Azure DevOps](https://docs.microsoft.com/en-us/rest/api/azure/devops) | The Azure DevOps basic components of a REST API request/response pair | `apiKey` | Yes | Unknown |
| [Docker Hub](https://docs.docker.com/docker-hub/api/latest/) | Interact with Docker Hub | `apiKey` | Yes | Yes |
| [Heroku](https://devcenter.heroku.com/articles/platform-api-reference/) | REST API to programmatically create apps, provision add-ons and perform other task on Heroku | `OAuth` | Yes | Yes |
| [Netlify](https://docs.netlify.com/api/get-started/) | Netlify is a hosting service for the programmable web | `OAuth` | Yes | Unknown |
| [DigitalOcean Status](https://status.digitalocean.com/api) | Status of all DigitalOcean services | No | Yes | Unknown |

### Package Management & CDN

| API | Description | Auth | HTTPS | CORS |
|:---|:---|:---|:---|:---|
| [npm Registry](https://github.com/npm/registry/blob/master/docs/REGISTRY-API.md) | Query information about your favorite Node.js libraries programatically | No | Yes | Unknown |
| [CDNJS](https://api.cdnjs.com/libraries/jquery) | Library info on CDNJS | No | Yes | Unknown |
| [jsDelivr](https://github.com/jsdelivr/data.jsdelivr.com) | Package info and download stats on jsDelivr CDN | No | Yes | Yes |
| [PageCDN](https://pagecdn.com/docs/public-api) | Public API for javascript, css and font libraries on PageCDN | `apiKey` | Yes | Yes |
| [Statically](https://statically.io/) | A free CDN for developers | No | Yes | Yes |

### Testing & Mocking APIs

| API | Description | Auth | HTTPS | CORS |
|:---|:---|:---|:---|:---|
| [Httpbin](https://httpbin.org/) | A Simple HTTP Request & Response Service | No | Yes | Yes |
| [Httpbin Cloudflare](https://cloudflare-quic.com/b/) | A Simple HTTP Request & Response Service with HTTP/3 Support by Cloudflare | No | Yes | Yes |
| [ReqRes](https://reqres.in/) | A hosted REST-API ready to respond to your AJAX requests | No | Yes | Unknown |
| [Mocky](https://designer.mocky.io/) | Mock user defined test JSON for REST API endpoints | No | Yes | Yes |
| [Beeceptor](https://beeceptor.com/) | Build a mock Rest API endpoint in seconds | No | Yes | Yes |
| [Gorest](https://gorest.co.in/) | Online REST API for Testing and Prototyping | `OAuth` | Yes | Unknown |
| [MicroENV](https://microenv.com/) | Fake Rest API for developers | No | Yes | Unknown |
| [Random Stuff](https://api-docs.pgamerx.com/) | Can be used to get AI Response, jokes, memes, and much more at lightning-fast speed | `apiKey` | Yes | Yes |
| [Postman](https://www.postman.com/postman/workspace/postman-public-workspace/documentation/12959542-c8142d51-e97c-46b6-bd77-52bb66712c9a) | Tool for testing APIs | `apiKey` | Yes | Unknown |

### Code Quality & Documentation

| API | Description | Auth | HTTPS | CORS |
|:---|:---|:---|:---|:---|
| [SonarQube](https://sonarcloud.io/web_api) | SonarQube REST APIs to detect bugs, code smells & security vulnerabilities | `OAuth` | Yes | Unknown |
| [APIs.guru](https://apis.guru/api-doc/) | Wikipedia for Web APIs, OpenAPI/Swagger specs for public APIs | No | Yes | Unknown |
| [Changelogs.md](https://changelogs.md) | Structured changelog metadata from open source projects | No | Yes | Unknown |
| [License-API](https://github.com/cmccandless/license-api/blob/master/README.md) | Unofficial REST API for choosealicense.com | No | Yes | No |

### Web Scraping & Screenshots

| API | Description | Auth | HTTPS | CORS |
|:---|:---|:---|:---|:---|
| [Screenshot](https://www.abstractapi.com/website-screenshot-api) | Take programmatic screenshots of web pages from any website | `apiKey` | Yes | Yes |
| [ApiFlash](https://apiflash.com/) | Chrome based screenshot API for developers | `apiKey` | Yes | Unknown |
| [Browshot](https://browshot.com/api/documentation) | Easily make screenshots of web pages in any screen size, as any device | `apiKey` | Yes | Yes |
| [Blitapp](https://blitapp.com/api/) | Schedule screenshots of web pages and sync them to your cloud | `apiKey` | Yes | Unknown |
| [SavePage.io](https://www.savepage.io) | A free, RESTful API used to screenshot any desktop, or mobile website | `apiKey` | Yes | Yes |
| [ScreenshotAPI.net](https://screenshotapi.net/) | Create pixel-perfect website screenshots | `apiKey` | Yes | Yes |
| [ScraperApi](https://www.scraperapi.com) | Easily build scalable web scrapers | `apiKey` | Yes | Unknown |
| [scraperBox](https://scraperbox.com/) | Undetectable web scraping API | `apiKey` | Yes | Yes |
| [scrapestack](https://scrapestack.com/) | Real-time, Scalable Proxy & Web Scraping REST API | `apiKey` | Yes | Unknown |
| [ScrapingAnt](https://scrapingant.com) | Headless Chrome scraping with a simple API | `apiKey` | Yes | Unknown |
| [ScrapingDog](https://www.scrapingdog.com/) | Proxy API for Web scraping | `apiKey` | Yes | Unknown |
| [ScrapeNinja](https://scrapeninja.net) | Scraping API with Chrome fingerprint and residential proxies | `apiKey` | Yes | Unknown |
| [WebScraping.AI](https://webscraping.ai/) | Web Scraping API with built-in proxies and JS rendering | `apiKey` | Yes | Yes |
| [ZenRows](https://www.zenrows.com/) | Web Scraping API that bypasses anti-bot solutions while offering JS rendering, and rotating proxies | `apiKey` | Yes | Unknown |
| [ProxyCrawl](https://proxycrawl.com) | Scraping and crawling anticaptcha service | `apiKey` | Yes | Unknown |
| [ProxyKingdom](https://proxykingdom.com) | Rotating Proxy API that produces a working proxy on every request | `apiKey` | Yes | Yes |
| [import.io](http://api.docs.import.io/) | Retrieve structured data from a website or RSS feed | `apiKey` | Yes | Unknown |
| [serpstack](https://serpstack.com/) | Real-Time & Accurate Google Search Results API | `apiKey` | Yes | Yes |

### Data & Storage APIs

| API | Description | Auth | HTTPS | CORS |
|:---|:---|:---|:---|:---|
| [Base](https://www.base-api.io/) | Building quick backends | `apiKey` | Yes | Yes |
| [Databricks](https://docs.databricks.com/dev-tools/api/latest/index.html) | Service to manage your databricks account,clusters, notebooks, jobs and workspaces | `apiKey` | Yes | Yes |
| [ExtendsClass JSON Storage](https://extendsclass.com/json-storage.html) | A simple JSON store API | No | Yes | Yes |
| [JSONbin.io](https://jsonbin.io) | Free JSON storage service. Ideal for small scale Web apps, Websites and Mobile apps | `apiKey` | Yes | Yes |
| [Micro DB](https://m3o.com/db) | Simple database service | `apiKey` | Yes | Unknown |
| [Google Firebase](https://firebase.google.com/docs) | Google's mobile application development platform that helps build, improve, and grow app | `apiKey` | Yes | Yes |

### Google Workspace APIs

| API | Description | Auth | HTTPS | CORS |
|:---|:---|:---|:---|:---|
| [Google Docs](https://developers.google.com/docs/api/reference/rest) | API to read, write, and format Google Docs documents | `OAuth` | Yes | Unknown |
| [Google Sheets](https://developers.google.com/sheets/api/reference/rest) | API to read, write, and format Google Sheets data | `OAuth` | Yes | Unknown |
| [Google Slides](https://developers.google.com/slides/api/reference/rest) | API to read, write, and format Google Slides presentations | `OAuth` | Yes | Unknown |
| [Google Keep](https://developers.google.com/keep/api/reference/rest) | API to read, write, and format Google Keep notes | `OAuth` | Yes | Unknown |
| [Google Fonts](https://developers.google.com/fonts/docs/developer_api) | Metadata for all families served by Google Fonts | `apiKey` | Yes | Unknown |
| [Sheetsu](https://sheetsu.com/) | Easy google sheets integration | `apiKey` | Yes | Unknown |

### Developer Utilities

| API | Description | Auth | HTTPS | CORS |
|:---|:---|:---|:---|:---|
| [Agify.io](https://agify.io) | Estimates the age from a first name | No | Yes | Yes |
| [Genderize.io](https://genderize.io) | Estimates a gender from a first name | No | Yes | Yes |
| [Nationalize.io](https://nationalize.io) | Estimate the nationality of a first name | No | Yes | Yes |
| [ApicAgent](https://www.apicagent.com) | Extract device details from user-agent string | No | Yes | Yes |
| [apilayer userstack](https://userstack.com/) | Secure User-Agent String Lookup JSON API | `OAuth` | Yes | Unknown |
| [Cloudflare Trace](https://github.com/fawazahmed0/cloudflare-trace-api) | Get IP Address, Timestamp, User Agent, Country Code, IATA, HTTP Version, TLS/SSL Version & More | No | Yes | Yes |
| [Icanhazip](https://major.io/icanhazip-com-faq/) | IP Address API | No | Yes | Yes |
| [Icanhazepoch](https://icanhazepoch.com) | Get Epoch time | No | Yes | Yes |
| [IPify](https://www.ipify.org/) | A simple IP Address API | No | Yes | Unknown |
| [IPinfo](https://ipinfo.io/developers) | Another simple IP Address API | No | Yes | Unknown |
| [ip-fast.com](https://ip-fast.com/docs/) | IP address, country and city | No | Yes | Yes |
| [ipfind.io](https://ipfind.io) | Geographic location of an IP address or any domain name along with some other useful information | `apiKey` | Yes | Yes |
| [MY IP](https://www.myip.com/api-docs/) | Get IP address information | No | Yes | Unknown |
| [MAC address vendor lookup](https://macaddress.io/api) | Retrieve vendor details and other information regarding a given MAC address or an OUI | `apiKey` | Yes | Yes |
| [DomainDb Info](https://api.domainsdb.info/) | Domain name search to find all domains containing particular words/phrases/etc | No | Yes | Unknown |
| [Host.io](https://host.io) | Domains Data API for Developers | `apiKey` | Yes | Yes |
| [host-t.com](https://host-t.com) | Basic DNS query via HTTP GET request | No | Yes | No |
| [IP2WHOIS Information Lookup](https://www.ip2whois.com/) | WHOIS domain name lookup | `apiKey` | Yes | Unknown |
| [Hunter](https://hunter.io/api) | API for domain search, professional email finder, author finder and email verifier | `apiKey` | Yes | Unknown |
| [NetworkCalc](https://networkcalc.com/api/docs) | Network calculators, including subnets, DNS, binary, and security tools | No | Yes | Yes |
| [HTTP2.Pro](https://http2.pro/doc/api) | Test endpoints for client and server HTTP/2 protocol support | No | Yes | Unknown |
| [Sonar](https://github.com/Cgboal/SonarSearch) | Project Sonar DNS Enumeration API | No | Yes | Yes |

### Code Compilers & Tools

| API | Description | Auth | HTTPS | CORS |
|:---|:---|:---|:---|:---|
| [Codex](https://github.com/Jaagrav/CodeX) | Online Compiler for Various Languages | No | Yes | Unknown |
| [Wandbox](https://github.com/melpon/wandbox/blob/master/kennel2/API.rst) | Code compiler supporting 35+ languages mentioned at wandbox.org | No | Yes | Unknown |
| [Lua Decompiler](https://lua-decompiler.ferib.dev/) | Online Lua 5.1 Decompiler | No | Yes | Yes |

### Image & Chart Generation

| API | Description | Auth | HTTPS | CORS |
|:---|:---|:---|:---|:---|
| [Glitterly](https://developers.glitterly.app) | Image generation API | `apiKey` | Yes | Yes |
| [Contentful Images](https://www.contentful.com/developers/docs/references/images-api/) | Used to retrieve and apply transformations to images | `apiKey` | Yes | Yes |
| [Image-Charts](https://documentation.image-charts.com/) | Generate charts, QR codes and graph images | No | Yes | Yes |
| [QuickChart](https://quickchart.io/) | Generate chart and graph images | No | Yes | Yes |
| [Supportivekoala](https://developers.supportivekoala.com/) | Autogenerate images with template | `apiKey` | Yes | Yes |
| [QR code](https://www.qrtag.net/api/) | Create an easy to read QR code and URL shortener | No | Yes | Yes |
| [QR code](http://goqr.me/api/) | Generate and decode / read QR code graphics | No | Yes | Unknown |
| [Qrcode Monkey](https://www.qrcode-monkey.com/qr-code-api-with-logo/) | Integrate custom and unique looking QR codes into your system or workflow | No | Yes | Unknown |
| [Kroki](https://kroki.io) | Creates diagrams from textual descriptions | No | Yes | Yes |
| [Serialif Color](https://color.serialif.com/) | Color conversion, complementary, grayscale and contrasted text | No | Yes | No |

### Productivity & Automation

| API | Description | Auth | HTTPS | CORS |
|:---|:---|:---|:---|:---|
| [IFTTT](https://platform.ifttt.com/docs/connect_api) | IFTTT Connect API | No | Yes | Unknown |
| [OneSignal](https://documentation.onesignal.com/docs/onesignal-api) | Self-serve customer engagement solution for Push Notifications, Email, SMS & In-App | `apiKey` | Yes | Unknown |
| [Pusher Beams](https://pusher.com/beams) | Push notifications for Android & iOS | `apiKey` | Yes | Unknown |
| [GETPing](https://www.getping.info) | Trigger an email notification with a simple GET request | `apiKey` | Yes | Unknown |
| [Rejax](https://rejax.io/) | Reverse AJAX service to notify clients | `apiKey` | Yes | No |
| [Ghost](https://ghost.org/) | Get Published content into your Website, App or other embedded media | `apiKey` | Yes | Yes |

### Miscellaneous Development Tools

| API | Description | Auth | HTTPS | CORS |
|:---|:---|:---|:---|:---|
| [24 Pull Requests](https://24pullrequests.com/api) | Project to promote open source collaboration during December | No | Yes | Yes |
| [API Grátis](https://apigratis.com.br/) | Multiples services and public APIs | No | Yes | Unknown |
| [Bored](https://www.boredapi.com/) | Find random activities to fight boredom | No | Yes | Unknown |
| [Brainshop.ai](https://brainshop.ai/) | Make A Free A.I Brain | `apiKey` | Yes | Yes |
| [Blague.xyz](https://blague.xyz/) | La plus grande API de Blagues FR/The biggest FR jokes API | `apiKey` | Yes | Yes |
| [Blynk-Cloud](https://blynkapi.docs.apiary.io/#) | Control IoT Devices from Blynk IoT Cloud | `apiKey` | No | Unknown |
| [Ciprand](https://github.com/polarspetroll/ciprand) | Secure random string generator | No | Yes | No |
| [CORS Proxy](https://github.com/burhanuday/cors-proxy) | Get around the dreaded CORS error by using this proxy as a middle man | No | Yes | Yes |
| [CountAPI](https://countapi.xyz) | Free and simple counting service. You can use it to track page hits and specific events | No | Yes | Yes |
| [GeekFlare](https://apidocs.geekflare.com/docs/geekflare-api) | Provide numerous capabilities for important testing and monitoring methods for websites | `apiKey` | Yes | Unknown |
| [Hasura](https://hasura.io/opensource/) | GraphQL and REST API Engine with built in Authorization | `apiKey` | Yes | Yes |
| [IBM Text to Speech](https://cloud.ibm.com/docs/text-to-speech/getting-started.html) | Convert text to speech | `apiKey` | Yes | Yes |
| [JSON 2 JSONP](https://json2jsonp.com/) | Convert JSON to JSONP (on-the-fly) for easy cross-domain data requests using client-side JavaScript | No | Yes | Unknown |
| [Logs.to](https://logs.to/) | Generate logs | `apiKey` | Yes | Unknown |
| [Open Page Rank](https://www.domcop.com/openpagerank/) | API for calculating and comparing metrics of different websites using Page Rank algorithm | `apiKey` | Yes | Unknown |
| [OpenAPIHub](https://hub.openapihub.com/) | The All-in-one API Platform | `X-Mashape-Key` | Yes | Unknown |
| [OpenGraphr](https://opengraphr.com/docs/1.0/overview) | Really simple API to retrieve Open Graph data from an URL | `apiKey` | Yes | Unknown |
| [oyyi](https://oyyi.xyz/docs/1.0) | API for Fake Data, image/video conversion, optimization, pdf optimization and thumbnail generation | No | Yes | Yes |
| [RSS feed to JSON](https://rss-to-json-serverless-api.vercel.app) | Returns RSS feed in JSON format using feed URL | No | Yes | Yes |
| [SHOUTCLOUD](http://shoutcloud.io/) | ALL-CAPS AS A SERVICE | No | No | Unknown |
| [StackExchange](https://api.stackexchange.com/) | Q&A forum for developers | `OAuth` | Yes | Unknown |
| [Tyk](https://tyk.io/open-source/) | Api and service management platform | `apiKey` | Yes | Yes |

### Quick Start Examples

#### Using the GitHub API

```python
import requests

# Get repository information
def get_repo_info(owner, repo):
    url = f"https://api.github.com/repos/{owner}/{repo}"
    headers = {
        "Accept": "application/vnd.github.v3+json",
        # Add your token for higher rate limits
        # "Authorization": "token YOUR_GITHUB_TOKEN"
    }

    response = requests.get(url, headers=headers)

    if response.status_code == 200:
        data = response.json()
        return {
            "name": data["name"],
            "description": data["description"],
            "stars": data["stargazers_count"],
            "forks": data["forks_count"],
            "language": data["language"]
        }
    else:
        return f"Error: {response.status_code}"

# Example usage
repo_info = get_repo_info("anthropics", "claude-code")
print(repo_info)
```

#### Using npm Registry API

```python
import requests

def get_package_info(package_name):
    url = f"https://registry.npmjs.org/{package_name}"
    response = requests.get(url)

    if response.status_code == 200:
        data = response.json()
        latest_version = data['dist-tags']['latest']
        return {
            "name": data["name"],
            "description": data["description"],
            "latest_version": latest_version,
            "license": data["license"]
        }
    else:
        return f"Error: {response.status_code}"

# Example usage
package_info = get_package_info("react")
print(package_info)
```

#### Screenshot API Example

```python
import requests

def take_screenshot(url, api_key):
    endpoint = "https://api.apiflash.com/v1/urltoimage"

    params = {
        "access_key": api_key,
        "url": url,
        "format": "png",
        "width": 1920,
        "height": 1080,
        "full_page": "true"
    }

    response = requests.get(endpoint, params=params)

    if response.status_code == 200:
        # Save the screenshot
        with open("screenshot.png", "wb") as f:
            f.write(response.content)
        return "Screenshot saved successfully"
    else:
        return f"Error: {response.status_code}"
```

#### Using Mock APIs for Testing

```python
import requests

# Using ReqRes for testing
def test_api_calls():
    # GET request
    response = requests.get("https://reqres.in/api/users/2")
    print("User data:", response.json())

    # POST request
    new_user = {
        "name": "John Doe",
        "job": "Developer"
    }
    response = requests.post("https://reqres.in/api/users", json=new_user)
    print("Created user:", response.json())

    # PUT request
    updated_user = {
        "name": "John Doe",
        "job": "Senior Developer"
    }
    response = requests.put("https://reqres.in/api/users/2", json=updated_user)
    print("Updated user:", response.json())

test_api_calls()
```

### Best Practices for Development APIs

1. **Authentication & Rate Limiting**
   - Store API keys in environment variables
   - Implement retry logic with exponential backoff
   - Monitor rate limits and implement caching when appropriate

2. **Version Control APIs**
   - Use specific API versions in production
   - Test API changes in staging environments
   - Keep track of deprecation notices

3. **Error Handling**
   - Always check response status codes
   - Implement proper error handling for network failures
   - Log API errors for debugging

4. **Testing**
   - Use mock APIs during development
   - Implement integration tests for API calls
   - Test rate limiting and error scenarios

5. **Security**
   - Never commit API keys to version control
   - Use HTTPS endpoints when available
   - Validate and sanitize API responses

---

## Integration Patterns

### Basic Chat Completion

```python
# Universal pattern for most APIs
def chat_completion(messages, model="gpt-4-turbo"):
    response = client.chat.completions.create(
        model=model,
        messages=messages,
        temperature=0.7,
        max_tokens=1000
    )
    return response.choices[0].message.content
```

### Streaming Responses

```python
# For real-time output
def stream_chat(prompt):
    for chunk in client.chat.completions.create(
        model="gpt-4-turbo",
        messages=[{"role": "user", "content": prompt}],
        stream=True
    ):
        if chunk.choices[0].delta.content:
            yield chunk.choices[0].delta.content
```

### Function Calling / Tool Use

```python
# Anthropic Claude example
tools = [{
    "name": "get_weather",
    "description": "Get weather for a location",
    "input_schema": {
        "type": "object",
        "properties": {
            "location": {"type": "string"}
        },
        "required": ["location"]
    }
}]

response = client.messages.create(
    model="claude-3-5-sonnet-20241022",
    max_tokens=1024,
    tools=tools,
    messages=[{"role": "user", "content": "What's the weather in SF?"}]
)

# Check if tool was called
if response.stop_reason == "tool_use":
    tool_use = next(block for block in response.content if block.type == "tool_use")
    # Execute function and send result back
```

### Embeddings for Semantic Search

```python
# Generate embeddings
from openai import OpenAI
client = OpenAI()

def get_embedding(text):
    response = client.embeddings.create(
        input=text,
        model="text-embedding-3-small"
    )
    return response.data[0].embedding

# Use for similarity search
import numpy as np

def cosine_similarity(a, b):
    return np.dot(a, b) / (np.linalg.norm(a) * np.linalg.norm(b))

query_embedding = get_embedding("search query")
doc_embedding = get_embedding("document text")
similarity = cosine_similarity(query_embedding, doc_embedding)
```

### RAG (Retrieval-Augmented Generation)

```python
# Simple RAG pattern
def rag_query(question, documents):
    # 1. Embed documents and question
    doc_embeddings = [get_embedding(doc) for doc in documents]
    question_embedding = get_embedding(question)

    # 2. Find most relevant documents
    similarities = [
        cosine_similarity(question_embedding, doc_emb)
        for doc_emb in doc_embeddings
    ]
    top_k = np.argsort(similarities)[-3:]  # Top 3

    # 3. Create context from relevant docs
    context = "\n\n".join([documents[i] for i in top_k])

    # 4. Generate answer with context
    prompt = f"Context:\n{context}\n\nQuestion: {question}\nAnswer:"
    return chat_completion([{"role": "user", "content": prompt}])
```

---

## Framework Integrations

### LangChain

```python
from langchain.chat_models import ChatOpenAI
from langchain.prompts import ChatPromptTemplate
from langchain.chains import LLMChain

llm = ChatOpenAI(model="gpt-4-turbo")

prompt = ChatPromptTemplate.from_template(
    "Translate {text} to {language}"
)

chain = LLMChain(llm=llm, prompt=prompt)

result = chain.run(text="Hello", language="Spanish")
```

### LlamaIndex

```python
from llama_index import VectorStoreIndex, SimpleDirectoryReader

# Load documents
documents = SimpleDirectoryReader('data').load_data()

# Create index
index = VectorStoreIndex.from_documents(documents)

# Query
query_engine = index.as_query_engine()
response = query_engine.query("What is the main topic?")
```

### Semantic Kernel

```python
import semantic_kernel as sk

kernel = sk.Kernel()

# Add AI service
kernel.add_text_completion_service(
    "gpt-4",
    OpenAIChatCompletion("gpt-4-turbo", api_key)
)

# Create semantic function
summarize = kernel.create_semantic_function(
    "Summarize: {{$input}}",
    max_tokens=100
)

result = summarize("Long text to summarize...")
```

---

## Best Practices

### Error Handling

```python
from anthropic import Anthropic, APIError, RateLimitError
import time

def safe_api_call(prompt, max_retries=3):
    for attempt in range(max_retries):
        try:
            return client.messages.create(
                model="claude-3-5-sonnet-20241022",
                max_tokens=1024,
                messages=[{"role": "user", "content": prompt}]
            )
        except RateLimitError:
            wait_time = 2 ** attempt  # Exponential backoff
            time.sleep(wait_time)
        except APIError as e:
            print(f"API error: {e}")
            raise

    raise Exception("Max retries exceeded")
```

### Cost Optimization

```python
# 1. Use cheaper models for simple tasks
def choose_model(complexity):
    if complexity == "simple":
        return "gpt-3.5-turbo"  # Cheaper
    elif complexity == "moderate":
        return "gpt-4-turbo"
    else:
        return "gpt-4"  # Most expensive but best

# 2. Limit max tokens
response = client.chat.completions.create(
    model="gpt-4-turbo",
    messages=[...],
    max_tokens=500  # Prevent excessive output
)

# 3. Cache responses
from functools import lru_cache

@lru_cache(maxsize=100)
def cached_completion(prompt):
    return client.chat.completions.create(...)
```

### Token Counting

```python
import tiktoken

def count_tokens(text, model="gpt-4"):
    encoding = tiktoken.encoding_for_model(model)
    return len(encoding.encode(text))

# Estimate cost before calling
def estimate_cost(prompt, max_tokens=1000):
    input_tokens = count_tokens(prompt)
    total_tokens = input_tokens + max_tokens

    # GPT-4 Turbo pricing
    input_cost = input_tokens * 0.01 / 1000
    output_cost = max_tokens * 0.03 / 1000

    return input_cost + output_cost
```

### Rate Limiting

```python
from ratelimit import limits, sleep_and_retry

# 60 requests per minute
@sleep_and_retry
@limits(calls=60, period=60)
def rate_limited_call(prompt):
    return client.chat.completions.create(...)
```

---

## Security Best Practices

### Environment Variables

```python
import os
from dotenv import load_dotenv

load_dotenv()

api_key = os.getenv("ANTHROPIC_API_KEY")
client = Anthropic(api_key=api_key)
```

### Input Sanitization

```python
def sanitize_input(user_input):
    # Remove potential injection attempts
    # Limit length
    # Validate format
    if len(user_input) > 10000:
        raise ValueError("Input too long")

    # Remove special characters if needed
    import re
    clean_input = re.sub(r'[<>]', '', user_input)

    return clean_input
```

### Output Validation

```python
def validate_output(output):
    # Check for sensitive data
    # Verify format
    # Content filtering

    sensitive_patterns = [
        r'\b\d{3}-\d{2}-\d{4}\b',  # SSN
        r'\b\d{16}\b',  # Credit card
    ]

    for pattern in sensitive_patterns:
        if re.search(pattern, output):
            return "Output contains sensitive data"

    return output
```

---

## Monitoring and Logging

```python
import logging
from datetime import datetime

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def tracked_api_call(prompt, model):
    start_time = datetime.now()

    try:
        response = client.chat.completions.create(
            model=model,
            messages=[{"role": "user", "content": prompt}]
        )

        duration = (datetime.now() - start_time).total_seconds()

        logger.info({
            "model": model,
            "prompt_length": len(prompt),
            "response_length": len(response.choices[0].message.content),
            "duration": duration,
            "tokens_used": response.usage.total_tokens,
            "timestamp": datetime.now().isoformat()
        })

        return response

    except Exception as e:
        logger.error(f"API call failed: {e}")
        raise
```

---

## Resources

- **Anthropic Docs**: https://docs.anthropic.com
- **OpenAI Docs**: https://platform.openai.com/docs
- **Google AI**: https://ai.google.dev
- **Cohere Docs**: https://docs.cohere.com
- **LangChain**: https://python.langchain.com
- **LlamaIndex**: https://docs.llamaindex.ai

---

**Last Updated**: 2025-10-28

**See Also**:
- [AI Agents](../agents/)
- [CLI Tools](../tools/cli-tools.md)
- [Best Practices](../AI-BEST-PRACTICES.md)
