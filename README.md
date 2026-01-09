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

Para mapear los items:


```
{products?.map(products => (
<div class="rounded pt-2 pb-2 w-[276px] flex flex-col justify-start items-center">
	<div class="bg-[#F4f4f4] w-[256px] h-[256px] flex justify-center items-center">
		<img class="" src={products.image_url} alt={products.name}/>
	</div>

	<div class=" ml-8 mt-2" style="font-family: Outfit;">
		<h3 class="font-semibold">{products.name}</h3>
		<p class="font-light truncate w-[200px]">{products.description}</p>
		<strong>${products.price}</strong>
	</div>				
</div>

))}

```


