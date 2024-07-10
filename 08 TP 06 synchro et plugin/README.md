### Documentation WordPress
https://developer.wordpress.org/  
  
### lien crée un pluggin
https://developer.wordpress.org/plugins/plugin-basics/

# TP 06 synchro et plugin
- Créer une tache add-serie.php
- Ajouter 3 série
  - https://www.omdbapi.com/?apikey=efdc2275&t=dark%20matter&type=series  
  - https://www.omdbapi.com/?apikey=efdc2275&t=arnold&type=series
  - https://www.omdbapi.com/?apikey=efdc2275&t=toto&type=series
- ajouter l'image de la série dans un champ ACF de type texte
- ajouter l'étiquette home
# plugin
- Mettre le CPT Custom Série dans un plugin

```php
 $api_url='https://www.omdbapi.com/?apikey=efdc2275&t=dark%20matter&type=series';
 $json_data = file_get_contents($api_url); 
 $serie = json_decode($json_data); 
 var_dump( $serie);
 ```

 ```php
 $database = "toto"; 
$base_url ='https://serie-nantes-default-rtdb.europe-west1.firebasedatabase.app/'; 
 $api_url = 
 $base_url.$database.'.json'; 
 $json_data = file_get_contents($api_url); 
 $series = json_decode($json_data);
 var_dump($series);
 ```

 **add-serie.php**
 ```php
 <h1> DEBUG CRON TAB 2<h1>
      <?php
      require_once 'wp-load.php';
        //--------------------------------------------
        // EFFACER TOUTES LES SERIES !!!
        //--------------------------------------------
        $allposts = get_posts(
         [
            'post_type' => 'serie',
            'numberposts' => -1
         ]
      );
      foreach ($allposts as $s) {
         wp_delete_post($s->ID, true);
      }
      //--------------------------------------------
      $tab=[
      'https://www.omdbapi.com/?apikey=efdc2275&t=dark%20matter&type=series',
      'https://www.omdbapi.com/?apikey=efdc2275&t=arnold&type=series',
      'https://www.omdbapi.com/?apikey=efdc2275&t=toto&type=series'];

      foreach ($tab as $url){
      $json_data = file_get_contents($url);
      $serie = json_decode($json_data);
    
      $id= wp_insert_post([
         'post_title' => $serie->Title,
         'post_status' =>  'publish',
         'post_type' => 'serie',
      ]);
      $test =wp_set_post_terms($id, [4], 'serie-etiquette');
      var_dump($test);
      update_field('image_api',$serie->Poster,$id);

   }
      
      ?>
 ```

 # exemple page contact

 ```php
 
<?php  get_header();   ?>
<div class="container">

<?php
while(have_posts()):
 the_post();
 ?>
   <h1><?php the_title() ?></h1>
   <p><?php the_content() ?></p>
   <div class="col-4">
   <form action="envoyer.php" method="post">
    <input class="form-control" name="Prénom" placeholder="Prénom">
    <buton type="submit" class="btn btn-primary my-3"> Valider</buton>
   </form>
   </div>
 <?php
endwhile;
?>
</div>
<?php   get_footer(); ?>
```