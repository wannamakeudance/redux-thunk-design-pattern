## why
At first, we ought to know why we need redux-thunk? 
- when we trigger a dispatch by normal redux, the parameters can only be `{type: ACTION_TYPE, payload: PAYLOAD_DATA}`. 
- However, in some specific situation, we actually need async in the logic code.
**If we use this like the code below, we can't realize the reuse of logic.**

```javascript
setTimeout(() => {
    store.dispatch({
        type: "ACTION_TYPE",
        payload: {
            number: 1
        }
    });
}, 1000);
```

- In order to meet the requirement, it's necessary to use redux-thunk middleware.

```javascript
import { createStore, applyMiddleware } from 'redux'
import thunk from 'redux-thunk'
import rootReducer from './reducers/index'

const store = createStore(rootReducer, applyMiddleware(thunk));
```

## How
- If you can't understand middlewares' theory, you can refer to [this aticle](https://github.com/wannamakeudance/redux-middleware-pattern)

```javascript
const thunk = store => next => action => {
    if (typeof action  === 'function') {
        return action(store);
    } else {
        // give this to next middleware
        return next(action);
    }
};
export default thunk;
```
