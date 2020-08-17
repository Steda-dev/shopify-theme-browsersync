# Shopify Theme with Browsersync
This repo is a basic structure for [shopify](https://www.shopify.de/) projects with [Browsersync](https://www.browsersync.io/).

# Config
1. Install [Theme Kit](https://shopify.github.io/themekit/) and [Browsersync](https://www.browsersync.io/).
2. Change the `config.yml` to your theme properties.
    - `store`: Your store’s Shopify domain with the `.myshopify.com` postfix. Please see the [setup docs](https://shopify.github.io/themekit/#get-api-access) on how to get this value.
    - `password`: Your API password. Please see the [setup docs](https://shopify.github.io/themekit/#get-api-access) on how to get this value.
    - `theme_id`: The theme that you want the command to take effect on. Please see the [setup docs](https://shopify.github.io/themekit/#get-api-access) on how to get this value.
    - `ignore_files`: If you use a Linux you have to change the backslash (\\) to a slash (/).
3. Get the theme. (Console command `theme get`)
4. Create a file, that will be the trigger, to update your browser. (e.g. `project-path/theme.update`)
5. Change in the `bs-config.js` file.
    - `proxy`: `https://{SHOP_URL}.myshopify.com?preview_theme_id={THEME_ID}`
    - `files`: The path of the new created file. (e.g. `project-path/theme.update`)
6. Open new CMD and let this command `theme watch --notify=project-path/theme.update` run in the background. Now your changes will be uploaded and afterward the created trigger file (`theme.update`) will be change.
7. Run the listener command in a new CMD `browser-sync start --config bs-config.js`.
8. That's it. :smile:

# Needed

[Themekit](https://shopify.github.io/themekit/) from Shopify, to edit this theme local with your favourite text editor.

[Browser-sync](https://www.browsersync.io/) Automatic reload of the page by editing the code.


# Recermendet

[Visual Studio Code](https://code.visualstudio.com/) is the recermendet text editor.

### VS Code Rrecermendet plugins

`Liquid` For automatic formatting, syntax highlighting and snippet.


# Commands

`theme get` Download the dev theme. Ignore the `config\settings_data.json` file.

`theme download config\settings_data.json --no-ignore` Downloading `config\settings_data.json` witch can only modify online by the theme configurator.

`theme deploy` Upload theme to the dev theme.

`theme deploy --env=production` **Upload theme to the _live_ theme.**

`theme watch` Monitors all files and uploads the changes to the dev theme.

`theme watch --notify=project-path/theme.update` Change the theme.update file if relevant files are uploaded.

`browser-sync start --config bs-config.js` If theme.update file change, the Browser will be reload and mutch more.
