
# TP 06 synchro et plugin
- Créer une tache add-serie.php
- Ajouter 3 série
  - https://www.omdbapi.com/?apikey=efdc2275&t=dark%20matter&type=series  
  - https://www.omdbapi.com/?apikey=efdc2275&t=arnold&type=series
  - https://www.omdbapi.com/?apikey=efdc2275&t=toto&type=series
- ajouter l'image de la série dans un champ ACF de type texte

# plugin
- Mettre le CPT Custom Série dans un plugin

```php
 $api_url='https://www.omdbapi.com/?apikey=efdc2275&t=dark%20matter&type=series';
 $json_data = file_get_contents($api_url); 
 $serie = json_decode($json_data); 
 var_dump( $serie);
 ```

 ```php
  $base_url ='https://serie-nantes-default-rtdb.europe-west1.firebasedatabase.app/'; 
 $api_url = 
 $base_url.$database.'.json'; 
 $json_data = file_get_contents($api_url); 
 $series = json_decode($json_data);
 var_dump($series);
 ```