
## Two ways on installing Tailwind in Laravel

- Using Vite
- Using Laravel Mix


### Using Vite

#### A. Create your Project

**Terminal:**
```
laravel new my-project
cd my-project
```

Cd that project and open it to vs code using `code .` commmand.

**Terminal:**
```
cd my-project
code .
```

#### B. Install Tailwind CSS

**Project Terminal:**
```
npm install tailwindcss @tailwindcss/vite
```


#### C. Configure the Vite plugin

**vite.config.ts**
```
import { defineConfig } from 'vite'
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
  plugins: [
    tailwindcss(),
  ],
})
```


#### D. Import Tailwind
Add an `@import` to your CSS file that imports Tailwind CSS.

**CSS**
```
@import "tailwindcss";
```


#### E. Start your Build process
Run your build process with `npm run dev` or whatever command is configured in your `package.json` file.

**Terminal:**
```
npm run dev
```

Or

**Terminal:**
```
php artisan serve
```


#### F. Start using Tailwind in your HTML
Make sure your compiled CSS is included in the `<head>` _(your framework might handle this for you)_, then start using Tailwind’s utility classes to style your content.

**Html**
```
<!doctype html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="/src/style.css" rel="stylesheet">
</head>
<body>
  <h1 class="text-3xl font-bold underline">
    Hello world!
  </h1>
</body>
</html>
```