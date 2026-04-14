# AI-Crawler

[![AI-Crawler Header](https://github.com/oxylabs/ai-crawler-py/blob/main/Ai-studio%20.png)](https://aistudio.oxylabs.io/apps/crawl?utm_source=877&utm_medium=affiliate&utm_campaign=ai_studio&groupid=877&utm_content=ai-crawler-py-github&transaction_id=102f49063ab94276ae8f116d224b67) <!-- Replace with actual header image path -->


[![](https://dcbadge.limes.pink/api/server/Pds3gBmKMH?style=for-the-badge&theme=discord)](https://discord.gg/Pds3gBmKMH) [![YouTube](https://img.shields.io/badge/YouTube-Oxylabs-red?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@oxylabs)


The [**AI-Crawler**](https://aistudio.oxylabs.io/apps/crawl) is an experimental data extraction app by [**Oxylabs AI Studio**](https://aistudio.oxylabs.io/) that uses advanced AI algorithms to crawl a given domain. It identifies relevant pages based on a natural language prompt and extracts structured **JSON** or **Markdown** output data.  

This low-code tool is designed to simplify complex data acquisition tasks, allowing developers and data scientists to focus on analysis rather than building and maintaining custom web scrapers. The AI web crawler offers advanced filtering, schema-based parsing, and seamless integration with various automation pipelines.  

## Key features

- **Start a crawl from any given URL:** Begin your data extraction from any valid web address using the AI Crawler as a starting point.  
- **Natural language prompt:** Define your data needs in plain English, and the crawl agent will interpret the prompt to find relevant content.  
- **AI-assisted URL selection:** The AI web crawler intelligently explores the site, identifying and prioritizing pages most aligned with your prompt.  
- **Multiple output formats:** Choose between structured JSON or Markdown output for seamless integration into automation or AI workflows.  
- **Schema-based parsing:** For JSON output, you can define a parsing schema in natural language to ensure the extracted data is structured to fit your application.


## How it works

To get started with the AI Crawler, follow this four-step process:

1. **Provide a starting URL** of the website you want the web crawler to explore.  
2. **Describe the content** you want to retrieve using a natural language prompt for the crawl agent.  
3. **Select the output format.** Choose between structured JSON or Markdown.  
4. **If using JSON output,** provide a schema to guide the AI web crawler in parsing and structuring the extracted data.


### Installation

To begin, be sure you have access to an API key (or [get a free trial](https://aistudio.oxylabs.io/register) with **1,000 credits**) and `Python 3.10+` installed. You can install the `oxylabs-ai-studio` package using pip:

```bash
pip install oxylabs-ai-studio
```

### Code examples (Python)

The following examples demonstrate how to use the `AiCrawler` to perform common crawling tasks.

```python
from oxylabs_ai_studio.apps.ai_crawler import AiCrawler
import json

# Initialize the AI Crawler with your API key
crawler = AiCrawler(api_key="your_api_key")

# Generate a schema automatically from natural language
schema = crawler.generate_schema(prompt="want to parse name, platform, price")
print(f"Generated schema: {schema}")

# Crawl a website and extract structured data
url = "https://sandbox.oxylabs.io/products"
result = crawler.crawl(
    url=url,
    user_prompt="Find all Halo games for Xbox",
    output_format="json",
    schema=schema,
    render_javascript=False,
    return_sources_limit=3,
    geo_location="US",
)

# Print the crawl output as JSON
print("Results:")
print(json.dumps(result.data, indent=2))
```
Learn more about AI-Crawler and Oxylabs AI Studio Python SDK in our [PyPI repository](https://pypi.org/project/oxylabs-ai-studio/). You can also check out our [AI Studio JavaScript SDK](https://github.com/oxylabs/oxylabs-ai-studio-js) guide for JS users.

### Request parameters

| Parameter            | Description                                         | Default Value |
|----------------------|-----------------------------------------------------|---------------|
| `url`*              | Starting URL to crawl                               | –     |
| `user_prompt`*      | Natural language prompt to guide extraction          | –             |
| `output_format`     | Output format (`json`, `markdown`)                   | `markdown`    |
| `schema`            | OpenAPI schema for structured extraction (mandatory for JSON) | –   |
| `render_javascript` | Enable render JavaScript                             | `False`       |
| `return_sources_limit` | Max number of sources to return                   | `25`          |
| `geo_location`      | Proxy location in ISO2 format                        | –             |

 `*` – mandatory parameters  

### Output samples

The `AI-Crawler` can return parsed, ready-to-use output that is easy to integrate into your applications.

This is a structured JSON of the response output:

```json
Results:
[
  {
    "data": {
      "items": [
        {
          "name": "Halo: Reach",
          "platform": "Xbox platform",
          "price": 84.99
        }
      ]
    },
    "src": "https://sandbox.oxylabs.io/products/141"
  },
  {
    "data": {
      "items": [
        {
          "name": "Halo 3",
          "platform": "Xbox platform",
          "price": 81.99
        }
      ]
    },
    "src": "https://sandbox.oxylabs.io/products/28"
  },
  {
    "data": {
      "items": [
        {
          "name": "Halo: Combat Evolved",
          "platform": "Xbox platform",
          "price": 87.99
        }
      ]
    },
    "src": "https://sandbox.oxylabs.io/products/6"
  }
]
```
Alternatively, you can use `output_format=”markdown”` to receive Markdown results instead of parsed JSON.

## Practical use cases

The AI-Crawler is a versatile tool for a wide range of applications, including:

1. **Finding terms of service pages:** Quickly locate legal and policy pages across a domain.  
2. **Gathering pricing pages:** Collect pricing details for competitor analysis or market research.  
3. **Retrieving all “About” pages:** Automatically find and extract company information from a list of websites.  
4. **Listing AI-related news articles:** Scrape a news site to gather and archive articles on a specific topic.  

## FAQ

### How does AI-Crawler differ from a traditional web scraper?  
Unlike traditional scrapers that rely on static selectors (CSS/XPath) and custom scripts, AI-Crawler uses natural language prompts and AI-assisted URL selection to dynamically identify and extract relevant content. It returns Markdown results and also supports schema-based parsing for structured JSON outputs, reducing the need for manual parsing logic.  

### What websites can I crawl with Oxylabs AI-Crawler?  
You can crawl most publicly accessible websites. AI-Crawler is designed to handle both static and JavaScript-rendered pages, and it can be configured with geo-targeting. However, be sure your use case complies with the website’s terms of service and local laws.  

### Is AI-Crawler free?  
Oxylabs AI Studio AI-Crawler is free to try by signing up for a [free trial](https://aistudio.oxylabs.io/register) that includes 1,000 credits. After the trial, the [monthly plans](https://aistudio.oxylabs.io/pricing) start at $12/month with 3,000 credits and 1 request/s, with higher plans offering more credits and higher request rates.  

### Can I generate my own schema for JSON output?  
Yes, you can either provide your own schema in OpenAPI format or let AI-Crawler generate one automatically from a natural language prompt. This allows your extracted data to match the exact structure your application needs.  

## Learn more

For a deeper dive into available parameters, advanced integrations, and additional examples, check out the [AI Studio documentation](https://aistudio.oxylabs.io/apps/crawl).  

## Contact us

If you have questions or need support, reach out to us at support@oxylabs.io, or through live chat, accessible via [Oxylabs Dashboard](https://dashboard.oxylabs.io/en/), or join our [Discord community](https://discord.gg/Pds3gBmKMH). For enterprise-related inquiries, contact your dedicated account manager.
