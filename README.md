# AI Text Sentiment Analysis

## Introduction

Welcome to the AI Text Sentiment Analysis API documentation! This API allows you to perform sentiment analysis on textual content, providing detailed sentiment analysis reports and insights. Whether you're a developer building sentiment analysis tools or an organization looking to understand the sentiment of your text data, this API is designed to meet your needs.

## Base URL

```
https://ai-text-sentiment-analysis.onrender.com
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
  https://ai-text-sentiment-analysis.onrender.com/analyze_text \
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

url = "https://ai-text-sentiment-analysis.onrender.com/analyze_text"
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

### JavaScript (Node.js)

```javascript
const fetch = require('node-fetch');

const url = 'https://ai-text-sentiment-analysis.onrender.com/analyze_text';
const data = { text: 'Text to be analyzed for sentiment.' };

fetch(url, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify(data),
})
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error('Error:', error));
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

### PHP

```php
<?php

$url = 'https://ai-text-sentiment-analysis.onrender.com/analyze_text';
$data = array('text' => 'Text to be analyzed for sentiment.');

$options = array(
    'http' => array(
        'header'  => "Content-Type: application/json\r\n",
        'method'  => 'POST',
        'content' => json_encode($data)
    )
);

$context  = stream_context_create($options);
$result = file_get_contents($url, false, $context);
$response = json_decode($result);

var_dump($response);

?>
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
            HttpPost request = new HttpPost("https://ai-text-sentiment-analysis.onrender.com/analyze_text");
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

With the AI Text Sentiment Analysis API, you can effortlessly analyze the sentiment of textual content, gaining valuable insights into the emotions conveyed within the text. Integrate this API into your applications to enhance user experiences, optimize content strategies, and make data-driven decisions.

---

Created by developer for developers.
