# Sentiment Analysis API Documentation

## Introduction

Welcome to the Sentiment Analysis API documentation! This API allows you to analyze the sentiment of textual content, highlighting sentiments within sentences, calculating an overall sentiment score, and providing detailed sentiment counts. Whether you're a developer building a sentiment analysis tool or an organization looking to understand the sentiment of your content, this API is here to help.

## Base URL

```
https://sentiment-ai.com
```

## Endpoints

### Analyze Text (`POST /analyze_text`)

Analyzes the sentiment of the provided text, highlighting sentiments within sentences, calculating an overall sentiment score, and providing detailed sentiment counts.

#### Request

- Method: `POST`
- Endpoint: `/analyze_text`
- Content-Type: `application/json`

##### Request Body

```json
{
  "text": "Text to be analyzed for sentiment."
}
```

#### Response

##### Success Response (200 OK)

```json
{
  "sentiment": "Positive",
  "highlighted_text": {
    "Sentence 1": "joy",
    "Sentence 2": "sadness",
    ...
  },
  "overall_sentiment_score": 75.0,
  "sentiment_scores": {
    "joy": 3,
    "sadness": 2,
    "fear": 0,
    "neutral": 1,
    "surprise": 0,
    "anger": 0,
    "shame": 0,
    "disgust": 0
  },
  "sentiment_label": "Positive"
}
```

#### Response Fields

- `sentiment`: Overall sentiment of the analyzed text (`Positive` or `Negative`).
- `highlighted_text`: Sentences with sentiments highlighted.
- `overall_sentiment_score`: Overall sentiment score between 0 (negative) and 100 (positive).
- `sentiment_scores`: Detailed counts of each sentiment type within the text.
- `sentiment_label`: Overall sentiment label (`Positive` or `Negative`).

## Example Usage

### cURL

```bash
curl -X POST \
  https://sentiment-ai.com/analyze_text \
  -H 'Content-Type: application/json' \
  -d '{
    "text": "Text to be analyzed for sentiment."
  }'
```

#### Example Response

```json
{
  "sentiment": "Positive",
  "highlighted_text": {
    "Sentence 1": "joy",
    "Sentence 2": "sadness",
    ...
  },
  "overall_sentiment_score": 75.0,
  "sentiment_scores": {
    "joy": 3,
    "sadness": 2,
    "fear": 0,
    "neutral": 1,
    "surprise": 0,
    "anger": 0,
    "shame": 0,
    "disgust": 0
  },
  "sentiment_label": "Positive"
}
```

### Python Requests

```python
import requests

url = "https://sentiment-ai.com/analyze_text"
payload = {
  "text": "Text to be analyzed for sentiment."
}
headers = {
  "Content-Type": "application/json"
}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

#### Example Response

```json
{
  "sentiment": "Positive",
  "highlighted_text": {
    "Sentence 1": "joy",
    "Sentence 2": "sadness",
    ...
  },
  "overall_sentiment_score": 75.0,
  "sentiment_scores": {
    "joy": 3,
    "sadness": 2,
    "fear": 0,
    "neutral": 1,
    "surprise": 0,
    "anger": 0,
    "shame": 0,
    "disgust": 0
  },
  "sentiment_label": "Positive"
}
```

### Java

```java
// Make sure to import necessary libraries
import org.apache.http.HttpResponse;
import org.apache.http.client.HttpClient;
import org.apache.http.client.methods.HttpPost;
import org.apache.http.entity.StringEntity;
import org.apache.http.impl.client.HttpClientBuilder;

import java.io.BufferedReader;
import java.io.InputStreamReader;

public class SentimentAnalysis {

    public static void main(String[] args) {
        try {
            HttpClient httpClient = HttpClientBuilder.create().build();
            HttpPost request = new HttpPost("https://sentiment-ai.com/analyze_text");
            StringEntity params = new StringEntity("{\"text\":\"Text to be analyzed for sentiment.\"}");
            request.addHeader("content-type", "application/json");
            request.setEntity(params);
            HttpResponse response = httpClient.execute(request);
            BufferedReader reader = new BufferedReader(new InputStreamReader(response.getEntity().getContent()));
            String line;
            StringBuffer result = new StringBuffer();
            while ((line = reader.readLine()) != null) {
                result.append(line);
            }
            System.out.println(result.toString());
        } catch (Exception ex) {
            ex.printStackTrace();
        }
    }
}
```

#### Example Response

```json
{
  "sentiment": "Positive",
  "highlighted_text": {
    "Sentence 1": "joy",
    "Sentence 2": "sadness",
    ...
  },
  "overall_sentiment_score": 75.0,
  "sentiment_scores": {
    "joy": 3,
    "sadness": 2,
    "fear": 0,
    "neutral": 1,
    "surprise": 0,
    "anger": 0,
    "shame": 0,
    "disgust": 0
  },
  "sentiment_label": "Positive"
}
```

<!-- Add other language examples -->

## Error Handling

- **400 Bad Request**: If the request body is missing or malformed.
- **500 Internal Server Error**: If an unexpected error occurs on the server.

## Conclusion

With the Sentiment Analysis API, you can effortlessly analyze the sentiment of textual content, gaining valuable insights into the emotions conveyed within the text. Integrate this API into your applications to enhance user experiences, optimize content strategies, and make data-driven decisions.
