# Async wrapper middleware

A simple Express middleware to wrap async functions.

### Usage

```javascript
const express = require('express');
const asyncWrapper = require('async-wrapper-express');

const router = express.Router();

router.get('/', asyncWrapper(async function (req, res, next) {
    let objs = await getFromDb();

    res.send(objs);
}));
```

### Notes
The middleware will do Promise.resolve on the async function and then catch any error thrown, that will be then passed onto the next function in Express chain.
