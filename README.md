# check_dois_in_hal
<h1>Vérification de la présence de DOIs dans Hal, par lot</h1>
<h2>En un mot</h2>
L'objectif de l'outil est de pointer, parmi un <b>lot</b> de DOIs stockés dans un fichier .csv, ceux  qui sont <b>absents</b> de Hal. 
<br/>
Il est destiné à des administrateurs Hal
<br/>
Il est construit sur les API ROR et OpenAlex
<br/>
Il a été testé avec en entrée un fichier .csv contenant 1000 DOIs. Temps de traitement dans ce cas : environ 2.30 minutes
<h2>Utilisation</h2>
Sur la page d'accueil l’utilisateur est invité à uploader un fichier .csv contenant une colonne de DOIs
<br/>
Dès que le choix du fichier est fait, le processus s’enclenche. A la fin du processus, l’utilisateur peut décharger les DOIs manquants dans Hal sous la forme d’un fichier .csv
<br/>
<h2>Langage</h2>
HTML, JavaScript<br/>
N'importe quel browser permet d'utiliser le code
<h2>Fichiers</h2>
Pour permettre une instalation la plus facile possible tout le code (toutes les fonctions) se trouve dans un seul fichier, ror_affiliations_to_openalex_primary_topics.html
<h2>Dépendance</h2>
L'outil est dépendant des API ROR et OpenAlex telle qu'elles existent aujourd'hui (février 2025) avec les points d'entrée https://api.ror.org/organizations/ et https://api.openalex.org/works
<p/>
Il met en oeuvre l'outil de visualisation Plotly : https://plotly.com/
<h2>Fonctionnalités, fonctions</h2>
La fonction upload_files_function() sert à uploader le fichier<br/>
A l'intérieur de cette fonction, la fonction csv_to_array_function() sert à nettoyer les données entrantes afin qu'à la fin de chaque ligne il y ait un \r et rien d'autre<br/>
La fonction download_file_function() sert à downloader le fichier de résultat<br/>
A l'intériure de cette fonction, la fonction array_to_csv_function() transforme l'array dans laquelle ont été stockés les résultats (dois_missing_in_hal) en une chaîne de caractère qui sera comprise comme un .csv à une seule colonne : des données séparées par un \n\r, ie un passage à la ligne<br/>
La fonction get_hal_data_function() prend une array de DOIs en entrée, les passe en revue via un while et, chaque fois, interroge l'API Hal à la recherche de la donnée "response" >>> "numFound". Si cette donnée est à zéro, cela signifie que le DOI n'est pas dans Hal, et donc mérite d'êtres stocké (dans l'array dois_missing_in_hal). A noter, le while mis en oeuvre ici est ralenti par la commande await new Promise(r => setTimeout(r, 10)); : on attend un centième de seconde avant de lancer un nouvelle commande fetch
# bibliometrics_openalex_ror-id-to-primary-topic
