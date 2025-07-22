# UI Suite DaisyUI Starterkit

This starterkit serves as a foundation for building your own theme based on DaisyUI. It utilizes Vite for CSS compilation and provides best practices for organizing your CSS files.

## Usage

See the [Starterkit documentation on Drupal.org](https://www.drupal.org/docs/core-modules-and-themes/core-themes/starterkit-theme).

Example command to generate your theme from your `web` folder

```bash
php core/scripts/drupal generate-theme my_daisyui_theme --starterkit ui_suite_daisyui_starterkit --path themes/custom
```

Then go to the new theme and run these commands to generate the CSS files: 
- `npm install`
- `npm run build`

After that you can enable your theme under: `/admin/appearance` in the Drupal UI.

## CSS structure:

### File Types
* `.pcss files`: These are source files that are imported into other files. They are not directly processed by Vite to create standalone CSS files.
* `.pcss.css files under css`: These files are processed by Vite to generate the final CSS output. They are included in the build process and result in standalone CSS files.
* `.pcss.css files within the components directory` are automatically loaded by SDC, ensuring that the resulting CSS is available for use in your theme.
```
# Example Card component CSS file.
@reference '../../css/app.pcss';

.card-title {
  @apply text-2xl;
}
```
### Configure TailwindCSS and DaisyUI
Tailwind CSS can be configured under `tailwind.config.pcss` and DaisyUI can be configured under `css/plugins/daisyui.config.pcss`.
Additional Tailwind CSS plugins should included in the app.pcss as Tailwind Typography plugin that is already in the starterkit under `css/plugins/tailwindcss.typography.config.pcss`.

### DaisyUI themes:
DaisyUI themes are placed under css/themes/theme.pcss.css and must included in `ui_suite_daisyui_starterkit.libraries.yml`

### Using NPM

#### Setup NPM
- `npm install`

#### Build CSS (uses Vite)
- `npm run build`
```
❯ npm run build

> build
> NODE_ENV=production  vite build --emptyOutDir
```

#### Development (with watching, without mimyifing/compressing CSS)
- ```npm run dev``` to build both a CSS file and rebuild when a file is updated
```
❯ npm run dev
```

## Update DaisyUI and/or TailwindCSS

- ```npm update```
- ```npm run build```

### Clear cache
- ```drush cache:rebuild```

