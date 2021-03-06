# cs-xhr-wrapper
wrap xhr with authorization and cancel

## Install

```
npm install --save github:ControlSpaceSoftware/cs-xhr-wrapper
```

## Usage

```
import {getServiceFactory} from 'cs-xhr-wrapper'
const getAuthorization = () => {/* return jwt*/};
const get = getServiceFactory({getAuthorization});
const api = get(url, headers)
	.then((response) => response.json())
	.then((result) => console.log(result))
	.catch(console.error);
	// if you need to abort request
	api.abort();
```


```
import {getServiceFactory} from 'cs-xhr-wrapper'
const getAuthorization = () => {/* return jwt*/};
const get = getServiceFactory({getAuthorization, abortLast: true});
get(url, headers);
const api = get(url, headers)// previous get aborted
	.then((response) => response.json())
	.then((result) => console.log(result))
	.catch(console.error);
	// if you need to abort this last request
	api.abort();
```


```
import {postServiceFactory} from 'cs-xhr-wrapper'
const getAuthorization = () => {/* return jwt*/};
const post = postServiceFactory({getAuthorization});
post(url, body, headers)
	.then((response) => response.json())
	.then((result) => console.log(result))
	.catch(console.error);
// no abort api on post service
```
