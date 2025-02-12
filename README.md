# ror_affiliations_to_openalex_primary_topics.html
<h1>sujets travaillées par un laboratoire selon OpenAlex</h1>
<h2>En un mot</h2>
L'objectif de l'outil est de se faire une idée des sujets travaillés par un laboratoire
<br/><br/>
La source est OpenAlex. A chaque notice d’OpenAlex est attribué automatiquement un sujet et un seul, le “primary topic”, qui comporte quatre niveaux de précisions
<br/><br/>
La façon dont les articles d’un laboratoire dans OpenAlex se distribuent selon les primary topics est réputé ici donner une image des sujets travaillés par ce laboratoire
<h2>Utilisation</h2>
L’utilisateur se voit présenter l’arborescence ROR de l’Université de Versailles Saint Quentin en Yvelines
<br/><br/>
Mais il peut choisir une autre institution et à ce moment là ce sera l’arborescence ROR de cette institution qui lui sera présentée
<br/><br/>
Il choisit n’importe quel item de cette arborescence, une fourchette d’années, ainsi que les éléments de recherche (numéro ROR, nom, sigle, etc.). Il lui est alors présenté le nombre d’articles OpenAlex correspondant à sa demande selon chacun des primary topics de premier niveau
<br/><br/>
Il peut développer pour afficher les primary topics de deuxième, troisième et quatrième niveau
<br/><br/>
Si le nombre d'articles est supérieur à une certaine limite, il peut afficher un graphe en anneau.
<h2>Langage</h2>
HTML, JavaScript
<br/><br/>
N'importe quel browser permet d'utiliser le code
<h2>Fichiers</h2>
Pour permettre une instalation la plus facile possible tout le code (toutes les fonctions) se trouve dans un seul fichier, ror_affiliations_to_openalex_primary_topics.html
<h2>Dépendance</h2>
L'outil est dépendant des API ROR et OpenAlex telle qu'elles existent aujourd'hui (février 2025) avec les points d'entrée https://api.ror.org/organizations/ et https://api.openalex.org/works
<br/><br/>
Il met en oeuvre l'outil de visualisation Plotly : https://plotly.com/
<h2>Fonctionnalités, fonctions</h2>
La fonction upload_files_function() sert à uploader le fichier<br/>
A l'intérieur de cette fonction, la fonction csv_to_array_function() sert à nettoyer les données entrantes afin qu'à la fin de chaque ligne il y ait un \r et rien d'autre<br/>
La fonction download_file_function() sert à downloader le fichier de résultat<br/>
A l'intériure de cette fonction, la fonction array_to_csv_function() transforme l'array dans laquelle ont été stockés les résultats (dois_missing_in_hal) en une chaîne de caractère qui sera comprise comme un .csv à une seule colonne : des données séparées par un \n\r, ie un passage à la ligne<br/>
La fonction get_hal_data_function() prend une array de DOIs en entrée, les passe en revue via un while et, chaque fois, interroge l'API Hal à la recherche de la donnée "response" >>> "numFound". Si cette donnée est à zéro, cela signifie que le DOI n'est pas dans Hal, et donc mérite d'êtres stocké (dans l'array dois_missing_in_hal). A noter, le while mis en oeuvre ici est ralenti par la commande await new Promise(r => setTimeout(r, 10)); : on attend un centième de seconde avant de lancer un nouvelle commande fetch
# bibliometrics_openalex_ror-id-to-primary-topic
