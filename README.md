# Serverless Framework Node Express API on AWS

Develop and deploy a Node Express API service running on AWS Lambda using the Serverless Framework.

Available at https://fve430rljd.execute-api.us-east-1.amazonaws.com/

## Usage

### Setup

Install dependencies with:

```bash
npm install
```

### Check info

```bash
serverless info
```

### Run locally

```bash
npm start
```

### Deployment

```bash
serverless deploy
```

Note: the API is public

### Invocation

After successful deployment, you can call the created application via HTTP:

```bash
curl https://xxxxxxx.execute-api.us-east-1.amazonaws.com/
```

Which should result in the following response:

```
{"message":"Hello from root!"}
```

Calling the `/path` path with:

```bash
curl https://fve430rljd.execute-api.us-east-1.amazonaws.com/path
```

Should result in the following response:

```bash
{"message":"Hello from path!"}
```

If you try to invoke a path or method that does not have a configured handler, e.g. with:

```bash
curl https://fve430rljd.execute-api.us-east-1.amazonaws.com/nonexistent
```

You should receive the following response:

```bash
{"error":"Not Found"}
```

## Anatomy of the template

This template configures a single function, `api`, which is responsible for handling all incoming requests thanks to the `httpApi` event. To learn more about `httpApi` event configuration options, please refer to [httpApi event docs](https://www.serverless.com/framework/docs/providers/aws/events/http-api/). As the event is configured in a way to accept all incoming requests, `express` framework is responsible for routing and handling requests internally. Implementation takes advantage of `serverless-http` package, which allows you to wrap existing `express` applications. To learn more about `serverless-http`, please refer to corresponding [GitHub repository](https://github.com/dougmoscrop/serverless-http).
