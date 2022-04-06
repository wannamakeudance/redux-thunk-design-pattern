## why
At first, we ought to know why we need redux-thunk? 
- when we trigger a dispatch by normal redux, the parameters can only be `{type: ACTION_TYPE, payload: PAYLOAD_DATA}`. 
- However, in some specific situation, we actually need async in the logic code.
- In order to meet these requirements, it's necessary to use redux-thunk.

```javascript
import { createStore, applyMiddleware } from 'redux'
import thunk from 'redux-thunk'
import rootReducer from './reducers/index'

const store = createStore(rootReducer, applyMiddleware(thunk));
```

## How

