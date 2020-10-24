[![Version](https://img.shields.io/npm/v/@jellyfish-commuting/risky-email)](https://www.npmjs.com/package/@jellyfish-commuting/risky-email)
[![Licence](https://img.shields.io/npm/l/@jellyfish-commuting/risky-email)](https://en.wikipedia.org/wiki/MIT_license)
[![Build](https://img.shields.io/travis/jellyfish-commuting/risky-email)](https://travis-ci.org/github/jellyfish-commuting/risky-email)
[![Coverage](https://img.shields.io/codecov/c/github/jellyfish-commuting/risky-email)](https://codecov.io/gh/jellyfish-commuting/risky-email)
[![Downloads](https://img.shields.io/npm/dt/@jellyfish-commuting/risky-email)](https://www.npmjs.com/package/@jellyfish-commuting/risky-email)

__*for internal use only - Draft idea to check trustworthiness of email account*__

# risky-email
Check if email is from disposable provider or has no DNS MX record

### Install

```bash
yarn add @jellyfish-commuting/risky-email
```
or
```bash
npm install @jellyfish-commuting/risky-email
```
### Usage

```javascript
const revokeIfRiskyEmail = require('@jellyfish-commuting/risky-email');

// Diposable email 
// Output "Risky email : Disposable email address"
revokeIfRiskyEmail('contact@yopmail.com')
  .then(() => console.log('Not risky'))
  .catch(error => console.log(`Risky email : ${error.message}`);
  
// Non-existent domain 
// Output "Risky email : queryMx ENOTFOUND he-llo-w-orld.com"
revokeIfRiskyEmail('contact@he-llo-w-orld.com')
  .then(() => console.log('Not risky'))
  .catch(error => console.log(`Risky email : ${error.message}`);
    
// Valid email -> Output "Not risky"
revokeIfRiskyEmail('contact@google.com')
  .then(() => console.log('Not risky'))
  .catch(error => console.log(`Risky email : ${error.message}`);
```

### Return value

Promise resolved with the email or rejected if risky email
