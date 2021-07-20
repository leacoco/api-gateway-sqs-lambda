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

Another example on how to test the API for different Team. Note that for the FiFo sqs Queue, we use a MessageGroupId
which is retrieve from the TeamName in the Request. So you have to provide a TeamName when sending message to the SQS Queue
Example
```
for team in si ft3 ft4 ft9; do echo $team; sleep 2;curl --location --request POST 'https://5vu65cv7ma.execute-api.eu-central-1.amazonaws.com/submit' --header 'Content-Type: application/json' --data-raw '{ "TeamName": "'$team'", "IsAdmin": "yes" }'; done
```
This is required for Grouping messages for a Teams.
