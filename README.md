## AWS Api-Gateway -> sqs -> lambda

In this repository, i will deploy a severless queue introduced between an Api gateway and a lambda function

The Queue acts as a buffer to alleviate traffic spikes and ensure your workload ca sustain the arriving load by buffering all the requests durably. It also helps downstram consumers to process the incoming requests at a consistent pace


## Deploy

```
sam deploy --guided
```

## Testing
```
curl --location --request POST 'https://<API_URL>/submit' \
    --header 'Content-Type: application/json' \
    --data-raw '{ "IsAdmin": "yes" }'
```
