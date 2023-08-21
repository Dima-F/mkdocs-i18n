# Практикум

Практичні приклади

## Приклади коду

```javascript
const {
    cors,
    helmet,
    koaBody,
    httpLogger,
    errors
} = require('./middlewares');

const {
    public,
    email,
    // email2,
    // whatsapp,
    // viber,
    swagger,
    sms,
    err,
    stats,
    profile,
    files,
    health
} = require('./routes');

module.exports = async app => {
    app.use(helmet({ contentSecurityPolicy: false }));
    app.use(cors());
    app.use(errors());
    // httpLogger configured by global winston logger
    app.use(httpLogger(logger));
    // includeUnparsed for crytopgraphic verification of request body in webhooks
    app.use(koaBody({
        includeUnparsed: true,
        jsonLimit: 10000000,
        multipart: true
    }));
    
    //routes
    public(app);
    email(app);
    // email2(app);
    // whatsapp(app);
    // viber(app);
    sms(app);
    swagger(app);
    err(app);
    stats(app);
    profile(app);
    files(app);
    health(app);

    // error handling
    // app.use(HandleErrors);
}
```
