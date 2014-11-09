# JOB 40

Get jobs listing of CAC 40 companies.

## Keynote

From CAC 40 companies, get the a jobs listing according criterias as well-defined url or keyword.

### CAC 40 Companies

#### JSON schema

```
{
  "title": "CAC 40 company definition",
  "type": "object",
  "properties": {
    "name": {
      "type": "string",
      "description": "Company name"
    },
    "search": {
        "type": "object",
        "description": "Get jobs from listed keywords",
        "properties": {
            "url": {"type": "string"},
            "keywords": {
                "type": "array",
                "description": "Keywords to search",
                "items": {
                    "type": "string"
                },
                "uniqueItems": true
            }
        },
        "required": ["url", "fields"]
    },
    "fields": {
        "type": "array",
        "description": "Get jobs from listed fields",
        "items": {
            "type": "string"
        },
        "uniqueItems": true
    }
  },
  "required": ["name"]
}
```

#### JSON Example

```
{
  "name": "AXA",
  "search":{
    "url":"http://company.com?search=",
    "keywords":["javascript","webmarketing"]
  },
  "fields":["http://company.com/it","http://company.com/legals"]
}
```

### Jobs listing

#### JSON Schema

```
{
  "title": "Job definition",
  "type": "object",
  "properties": {
    "date": {
      "type": "string",
      "description": "Job date publication"
    },
    "title": {
      "type": "string",
      "description": "Job title"
    },
    "url": {
      "type": "string",
      "description": "Job url"
    }
  },
  "required": ["date", "title", "url"]
}
```

#### JSON Example

```
{
  "date": "09/11/14",
  "title": "Software developer",
  "url": "http://company.com/software-developer"
}
```

## Methods

```
CacFactory.create('axa');
```

```
alstom.jobs(callback);
```

```
airbus.jobs(['keyword1,keyword2...,keywordn'],callback);
```

```
airbus.print(jobs);
```


## Usage

```
var job40 = require('job40');
var cacFactory = job40.cacFactory;

// Initialize a scraper for given company
var axa = cacFactory.create('axa');

// Get jobs according keywords
axa.jobs(['javascript','webdesigner'],callback);

// Get jobs according fields url
axa.jobs(callback);

// Print listing to console
airbus.print(jobs);

```

### Callback results example

```
[{
  "date": "09/11/14",
  "title": "Software developer",
  "url": "http://company.com/software-developer"
},
{
  "date": "10/11/14",
  "title": "Web designer,
  "url": "http://company.com/web-designer"
}]
```
