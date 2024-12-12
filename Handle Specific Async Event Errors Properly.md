
Errors related to asynchronous events should be handled properly to ensure that the application remains robust and provides good user experience. Using specific catch blocks for each error type, as exported by the @forge/events package, allows developers to implement targeted solutions for each kind of error, maintaining the stability and functionality of the application. 

[See more](https://developer.atlassian.com/platform/forge/runtime-reference/async-events-api-error-handling/)


### Positive example
```javascript
import { RateLimitError } from '@forge/events';

try {
  const queue = new Queue({ key: "queue-name"});
  queue.push(["/* payload for this event */"]);
} catch (error) {
  if (error instanceof RateLimitError) {
	// Handle rate limit error
  }
}
```

### Negative example

```javascript
try { await queue.push([/* payload of the events */]); } catch (error) { // Generic error handling that does not consider specific errors }
```
