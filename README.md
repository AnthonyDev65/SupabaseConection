Lo que hice fue crear mi proyecto en Astro, instale las librerias de SupaBase, Tailwind y listo

| Command                               | Action                                           |
| :------------------------------------ | :----------------------------------------------- |
| `pnpm install @supabase/supabase-js`  | Instala Supabase                                 |


Cree el .env en carpeta Raiz

Contenido:

```
PUBLIC_SUPABASE_URL= [Key]
PUBLIC_SUPABASE_PUBLISHABLE_DEFAULT_KEY= [Key]
```

Cree la ruta " `src/lib/supabase.js`

Contenido:  

```
import { createClient } from '@supabase/supabase-js'

const supabaseUrl = import.meta.env.PUBLIC_SUPABASE_URL
const supabaseKey = import.meta.env.PUBLIC_SUPABASE_PUBLISHABLE_DEFAULT_KEY

export const supabase = createClient(supabaseUrl, supabaseKey)
```
En mi Index.html

```
import { supabase } from '../lib/supabase'

const { data: <El Objeto que quieres exportar>, error } = await supabase
	.from('<El Objeto que quieres exportar>')
	.select('*')

```
