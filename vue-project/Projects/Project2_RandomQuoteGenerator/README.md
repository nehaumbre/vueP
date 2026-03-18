# Project2 Random Quote Generator

## Files
- `App.vue` (entry component)
- `components/RQG.vue` (Random Quote Generator component)

## Run this project in the current Vite app

In `vue-project/src/main.js`, set:

```js
import { createApp } from 'vue'
import App from '../Projects/Project2_RandomQuoteGenerator/App.vue'

createApp(App).mount('#app')
```

Then run:

```bash
cd vue-project
npm run dev
```

Open browser at `http://localhost:5173`.

## Switch between Project1 and Project2

In `vue-project/src/main.js`, change the `import App ...` path to either:
- `../Projects/Project1_TODO/App.vue`
- `../Projects/Project2_RandomQuoteGenerator/App.vue`

Then restart `npm run dev`.
