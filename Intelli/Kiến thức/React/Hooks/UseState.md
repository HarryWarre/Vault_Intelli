Tags: #react #hooks
# Introduce
- `useState` is a React Hook that lets you add a state variable to your component

```js
const [nodes, setNodes] = useState(initialNodes);
const [edges, setEdges] = useState(initialEdges);
```

2 function to access and modify state, which re use in Components

```js
const onNodesChange = useCallback(  
(changes) => setNodes((nds) => applyNodeChanges(changes, nds)),  
[],);

const onEdgesChange = useCallback(  
(changes) => setEdges((eds) => applyEdgeChanges(changes, eds)),  
[],);
```
