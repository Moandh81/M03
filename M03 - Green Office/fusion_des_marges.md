#  Qu’est-ce que la fusion des marges?

La fusion des marges est un mécanisme décrit dans la spécification CSS (CSS 2.1: Collapsing Margins). Il concerne les marges verticales (margin-top et margin-bottom) des éléments de type bloc.

C’est un mécanisme qui, pour deux blocs qui se suivent, «fusionne» la marge inférieure du premier et la marge supérieure du deuxième. C’est-à-dire qu’au lieu d’additionner les deux marges, le navigateur va conserver la plus grande des deux. Ainsi, dans l’exemple suivant l’écart entre les deux paragraphes ne sera pas de 50 pixels (20 + 30), mais de 30 pixels:

<p style="margin-bottom: 20px;">
  Premier paragraphe
</p>
<p style="margin-top: 30px;">
  Deuxième paragraphe
</p>


# Fusion des marges entre un élément et son parent

La fusion des marges ne se limite pas aux éléments frères (par exemple deux paragraphes qui se suivent), mais s’applique aussi aux éléments parents et enfants (par exemple un paragraphe dans un conteneur div).

<div style="background: #69f; margin: 10px;">
  <p style="background: #9f3; margin: 50px;">
    Un paragraphe (fond vert)
  </p>
</div>



Que constate-t-on? Les marges verticales du paragraphe, au lieu de créer un espace vide entre les bords du div et ceux du paragraphe, fusionnent avec les marges verticales du div. Le retrait au-dessus du div sera donc de 50 pixels, au lieu de 10 pixels. Ce comportement est normal, même s’il peut être surprenant.






# Exemple avec un texte qui fait obstacle à la fusion des marges


Notons que la fusion des marges ne se produit que pour la marge supérieure du premier enfant et la marge inférieure du dernier enfant d’un bloc. De plus, si le bloc contient du texte au début ou à la fin, la fusion des marges ne se produit pas. C’est ce que démontre l’exemple suivant:

<div style="background: skyblue; margin: 10px;">
  Ce div a un fond bleu ciel.
  <p style="background: #909; color:white; margin: 50px;">
    Un paragraphe (fond violet)
  </p>
  <p style="background: #909; color:white; margin: 50px;">
    Un deuxième paragraphe
  </p>
</div>







#Empêcher la fusion des marges entre parent et enfant


1. Avec du padding

La technique la plus simple pour éviter la fusion des marges entre un élément et son parent est d’utiliser du padding sur l’élément parent. 


<div style="background: skyblue; margin: 10px;
	padding: 1px 0;">
	<p style="background: #909; color:white; margin: 50px;">
		Un paragraphe (fond violet)
	</p>
</div>


2. Avec des bordures (propriété border)

<div style="background: skyblue; margin: 10px;
	border: 1px solid blue;">
	<p style="background: #909; color:white; margin: 50px;">
		Un paragraphe (fond violet)
	</p>
</div>



# 3. Avec un contexte de formatage (propriété overflow)


# 4. Avec les principales propriétés de positionnement
