# Getting Started with Development: Gutenberg AJAX Search Block

A [gutenberg block-only plugin](https://developer.wordpress.org/plugins/wordpress-org/block-specific-plugin-guidelines/#definitions) that implements an AJAX-based live suggestion search bar for WordPress and Woocommerce. 

## Gutenberg Development Resources

- [High-Level Block Development Guide from Kinsta](https://kinsta.com/blog/gutenberg-blocks/)
- [WordPress In-Depth Block Editor Handbook](https://developer.wordpress.org/block-editor/)
- [WordPress Built In React Component Library](https://developer.wordpress.org/block-editor/reference-guides/components/)
- [WordPress Native NPM Modules (these are obscure but occasionally really useful)](https://www.npmjs.com/search?q=%40wordpress)

## Similar Open Source Projects

Everything on [the WordPress plugin repository](https://wordpress.org/plugins/) is under [the GPL license](https://torquemag.io/2019/04/wordpress-licensing/), so we're free to use any source code from there as long as we attribute it. This can be hugely helpful, as we may only need to write thin wrappers around existing logic. Here are a few similar projects that we may want to pull logic from:

- [FiboSearch – Ajax Search for WooCommerce](https://wordpress.org/plugins/ajax-search-for-woocommerce/)
- [Ivory Search – WordPress Search Plugin](https://wordpress.org/plugins/add-search-to-menu/)
- [Relevanssi – A Better Search](https://wordpress.org/plugins/relevanssi/)
- [Advanced Woo Search](https://wordpress.org/plugins/advanced-woo-search/)

Most of this server-side logic will be written in PHP 🙄 but that's just WordPress development. It's a terrible language to write, but fortunately it's reasonably easy to read and understand!

As far as I can tell, this is the only plugin in [the block directory](https://wordpress.org/support/article/block-directory/) that currently has search functionality: https://wordpress.org/plugins/vk-filter-search/ It looks useful, but it's a different use case than the plugins listed above. I'm hoping that there's a hole in the market here!

## React Autocomplete Libraries

There are a number of options to choose from for building an autocomplete component in React. Here are a few libraries that look promising:

- https://www.npmjs.com/package/downshift
- https://www.npmjs.com/package/react-autocomplete
- https://www.npmjs.com/package/react-bootstrap-typeahead

## Working with Docker Compose

Just make sure that you have Docker and Docker Compose installed, then change to this directory and use these commands to get things running:

- START: `docker-compose up` (WordPress will be available at http://localhost:80/wp-admin)
- RESET AND START FROM SCRATCH: `docker-compose down --volumes --remove-orphans` (this is useful if Docker starts to throw strange errors)

Docker Compose is usually easy, but occasionally there's some weirdness. If you run into any bugs I'm happy to help with debugging!

## Setting Up for Development

To start everything up for development, install the dependencies with `npm install`. Then start WordPress in one terminal with `docker-compose up` and start the React build process at the same time in another terminal with `npm start`. Go to http://localhost/wp-admin/ and set up WordPress, then go to http://localhost/wp-admin/plugins.php and activate "Gutenberg Ajax Search". After that, you'll be able to use the block within the Gutenberg editor - hopefully with hot reloading. The Kinsta guide linked above is really helpful as you're getting a feel for this type of development.