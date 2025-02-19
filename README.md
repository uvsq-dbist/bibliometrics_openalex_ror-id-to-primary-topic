# ror_affiliations_to_openalex_primary_topics.html
<h1>topics covered by a laboratory according to OpenAlex</h1>

<h2>In a nutshell</h2>

The goal of the tool is to get an idea of ​​the topics covered by a laboratory
<br/><br/>
The source is OpenAlex. Each OpenAlex notice is automatically assigned one so-called “primary topic” and one only. A “primary topic” has four levels of precision
<br/><br/>
The way OpenAlex assigns the primary topics is supposed by us to represent the topics covered by the laboratory

<h2>Use</h2>

The user is presented with the ROR affiliation tree of the University of Versailles Saint Quentin en Yvelines
<br/><br/>
But he can choose another institution and then it will be the ROR affiliation tree of this institution that will be presented to him
<br/><br/>
He has to choose one item from this tree, a range of years, and the search elements (ROR number, name, acronym, etc.). He is then presented with the number of OpenAlex articles corresponding to his request distributed along the first-level primary topics
<br/><br/>
He can display the second, third and fourth-level primary topics
<br/><br/>
If the number of articles is greater than a certain limit, a doughnut graph can be displayed.

<h2>Language</h2>

HTML and JavaScript
<br/><br/>
Any browser can run the code

<h2>Files</h2>

To allow the easiest possible installation, all the code (all functions) is in one single file, ror_affiliations_to_openalex_primary_topics.html

<h2>Dependencies</h2>

The tool is dependent on the ROR and OpenAlex APIs as they exist today (February 2025). The entry points : https://api.ror.org/organizations/ and https://api.openalex.org/works
<br/><br/>
It makes use of the Plotly visualization tool: https://plotly.com/

<h2>Operation, functions</h2>

The get_ror_affiliation_data_function() function (recursive) allows the construction of a ror_affiliations_tree_step_one object that contains the entire ROR tree of an institution (ror_origin_id)
<br/><br/>
From there, the function build_selection_from_node_function() (recursive) builds the ror selection presented to the user in the main form
<br/><br/>
Everything else is triggered by a click on the "launch" button of this form.
<br/><br/>
This click activates the launch_openalex_function() which in turn activates the get_node_function() which, from the ror_affiliations_tree_step_one object (the ror tree) builds the ror_affiliations_tree_step_two object (the ror tree reduced to the ror selected by the user)
<br/><br/>
Then harvest_ror_ids_from_node_function() grabs all the ROR identifiers contained in ror_affiliations_tree_step_two and places them in an array, ror_ids
<br/><br/>
Then launch_openalex_function() sends, depending on what the user ticked, the get_openalex_data_thru_affiliation_strings_function() or the get_openalex_data_thru_ror_ids_function() or both functions
<br/><br/>
These functions will fetch the data from OpenAlex. They behave in the same way: For each result found, they trigger the can_data_function() function which feeds two arrays (openalex_ids and openalex_sorting) and an object (openalex_data) intended to store the results
<br/><br/>
When the examination is finished, the launch_ending_function() is sent which puts openalex_sorting in alphabetical order by title, then sends display_openalex_data_function() which displays the results
<br/><br/>
The last functions (peek_a_boo_function_01(), peek_a_boo_function_02(), build_openalex_display_function(), breakup_function(), show_graph_function(), hide_graph_function()) manage the display of the graphs
<hr/>



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
<h2>Fonctionnement, fonctions</h2>
La fonction get_ror_affiliation_data_function() (récursive) permet la construction d’un objet ror_affiliations_tree_step_one qui contient toute l'arborescence ROR d’une institution de départ (ror_origin_id)
<br/><br/>
A partir de là, la fonction build_selection_from_node_function() (récursive) fabrique la partie ror du formulaire présenté à l’utilisateur
<br/><br/>
Tout le reste est déclenché par un click sur le bouton "lancer" de ce formulaire.
<br/><br/>
Ce click active la fonction launch_openalex_function() qui à son tour active la fonction get_node_function() (récursive) qui, à partir de ror_affiliations_tree_step_one (l'aborescence des ror) construit ror_affiliations_tree_step_two (l'aborescence des ror à partir du ror sélectionné par l’utilisateur)
<br/><br/>
Ensuite harvest_ror_ids_from_node_function() (récursive) attrape tous les identifiants ROR contenus dans ror_affiliations_tree_step_two et les places dans une array, ror_ids
<br/><br/>
Ensuite launch_openalex_function() envoie, selon ce qu'à tické l'utilisateur, 
la fonction get_openalex_data_thru_affiliation_strings_function() ou la fonction get_openalex_data_thru_ror_ids_function() 
ou les deux fonctions
<br/><br/>
Ces fonctions vont chercher les données dans OpenAlex. Elles se comportent de la même façon : A chaque résultat trouvé, elles déclenchent  la fonction can_data_function() qui nourrit deux array (openalex_ids et openalex_sorting) et un objet (openalex_data) destinés à stocker les résultats
<br/><br/>
Quand l’examen est terminé, envoi de la fonction launch_ending_function() qui met en ordre alphabétique de titre openalex_sorting, puis envoie 
display_openalex_data_function() qui effectue l'affichage des résultats
<br/><br/>
Les dernières fonctions (peek_a_boo_function_01(), peek_a_boo_function_02(), build_openalex_display_function(), breakup_function(), show_graph_function(), hide_graph_function()) gèrent l’affichage des graphes

# bibliometrics_openalex_ror-id-to-primary-topic
