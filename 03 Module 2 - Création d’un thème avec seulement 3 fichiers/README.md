# style.css


## du thème twentytwentytwo
```css
/*
Theme Name: Twenty Twenty-Two
Theme URI: https://wordpress.org/themes/twentytwentytwo/
Author: the WordPress team
Author URI: https://wordpress.org/
Description: Built on a solidly designed foundation, Twenty Twenty-Two embraces the idea that everyone deserves a truly unique website. The theme’s subtle styles are inspired by the diversity and versatility of birds: its typography is lightweight yet strong, its color palette is drawn from nature, and its layout elements sit gently on the page. The true richness of Twenty Twenty-Two lies in its opportunity for customization. The theme is built to take advantage of the Site Editor features introduced in WordPress 5.9, which means that colors, typography, and the layout of every single page on your site can be customized to suit your vision. It also includes dozens of block patterns, opening the door to a wide range of professionally designed layouts in just a few clicks. Whether you’re building a single-page website, a blog, a business website, or a portfolio, Twenty Twenty-Two will help you create a site that is uniquely yours.
Requires at least: 5.9
Tested up to: 6.5
Requires PHP: 5.6
Version: 1.7
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html
Text Domain: twentytwentytwo
Tags: one-column, custom-colors, custom-menu, custom-logo, editor-style, featured-images, full-site-editing, block-patterns, rtl-language-support, sticky-post, threaded-comments, style-variations, wide-blocks, block-styles, accessibility-ready, blog, portfolio, news

Twenty Twenty-Two WordPress Theme, (C) 2021 WordPress.org
Twenty Twenty-Two is distributed under the terms of the GNU GPL.
*/
```

## du thème kiwi
```css
/*
Theme Name: Le Kiwi de Bretagne
Theme URI: 
Author: Jean-Frédéric
Author URI: 
Description: Thème one page - simple et efficace.
Requires at least: 5.9
Tested up to: 6.5
Requires PHP: 5.6
Version: 1.01
License: 
License URI: 
Text Domain: kiwi
Tags: onepage, bootstrap

*/
h1 { color:tomato}
```
# index.php
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> Mon site</title>
    <?php
        $theme_url = get_stylesheet_directory_uri(); 
    ?>
    <link rel="stylesheet" href="<?=$theme_url?>/style.css">
</head>
<body>
    <h1>Hello WordPress !</h1>
    <?php 
   $query = new WP_Query([
    "post_type"  => "page",
    "posts_per_page" => 4,
    "orderby"  => "menu_order",
    "order"  => "ASC" // DESC
    ] ); 
   if ( $query->have_posts() ) // si il y a des résultats dans la pile 
   {
      while( $query->have_posts() )
      {
         $query->the_post(); // enlever le résultat de la pile 
         the_title() ; // affiche le titre de la page
         echo '<br>'; 
      } 
   } 
 ?>
</body>
</html>
```