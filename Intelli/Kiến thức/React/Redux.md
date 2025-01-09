Tags: #redux #react 

# Introduce
- Là thư viện quản lý trạng thái toàn cục

Khái niệm cơ bản
- **`Store`**: Nơi lưu trữ cục bộ
- **`Action`**: Là một Object mô tả một sự kiện xảy ra trong ứng dụng.
- **`Reducer`** Là một Fuction nhận state của 1 action và trả về new State
- **`Dispatch`**: Là cách gửi actions tới store để cập nhật new State

# Cài đặt redux
 ```bash
 npm install redux react-redux
```

# Cấu trúc ứng dụng Redux

```bash
/src
  ├── actions/
  │     └── index.js
  ├── reducers/
  │     └── index.js
  ├── store.js
  └── App.js
```

## Tạo store
Store để lưu trữ states
```js
// store.js
import { createStore } from 'redux';
import rootReducer from './reducers';

const store = createStore(rootReducer);

export default store;
```

## Tạo action

Action là những Object mô tả những gì xảy ra trong ứng dụng.

```js
// actions/index.js
export const ADD_TODO = 'ADD_TODO';

export const addTodo = (text) => ({
  type: ADD_TODO,
  payload: { text },
});
```

## Tạo Reducer

Reducer là một function nhận vào state hiện tại và action, sau đó trả về trạng thái mới.

```js
// reducers/index.js
import { ADD_TODO } from '../actions';

const initialState = {
  todos: [],
};

const rootReducer = (state = initialState, action) => {
  switch (action.type) {
    case ADD_TODO:
      return {
        ...state,
        todos: [...state.todos, action.payload.text],
      };
    default:
      return state;
  }
};

export default rootReducer;

```
## Kết nối Redux với React
Sử dụng `Provider` từ `react-redux` để cung cấp store cho ứng dụng.

```js
// App.js
import React from 'react';
import { Provider } from 'react-redux';
import store from './store';
import TodoApp from './TodoApp';

const App = () => (
  <Provider store={store}>
    <TodoApp />
  </Provider>
);

export default App;

```
## Tạo component và kết nối với Redux:

Sử dụng `connect` từ `react-redux` để kết nối component với Redux.

```js
// TodoApp.js
import React from 'react';
import { connect } from 'react-redux';
import { addTodo } from './actions';

const TodoApp = ({ todos, addTodo }) => {
  const handleAddTodo = () => {
    const text = prompt('Enter todo:');
    addTodo(text);
  };

  return (
    <div>
      <h1>Todo List</h1>
      <button onClick={handleAddTodo}>Add Todo</button>
      <ul>
        {todos.map((todo, index) => (
          <li key={index}>{todo}</li>
        ))}
      </ul>
    </div>
  );
};

const mapStateToProps = (state) => ({
  todos: state.todos,
});

const mapDispatchToProps = {
  addTodo,
};

export default connect(mapStateToProps, mapDispatchToProps)(TodoApp);

```

Cách sử dụng redux trong arcgis :
```js
dispatch(  
    appActions.widgetStatePropChange(  
        "chartParseDate",  
        "colChartParseDate",  
        previousFilter !== undefined && previousFilter?.timestamp === messageColumnChart?.timestamp  
            ? undefined  
            : messageColumnChart  
    )  
);
```
Nhận thông tin redux
```js
const colChartParseDateMessage = useSelector(  
    () =>  
        getAppStore().getState().widgetsState?.["chartParseDate"]?.["colChartParseDate"]  
);
```

