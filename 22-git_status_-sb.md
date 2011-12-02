git status pour les grands
==========================

Maintenant que vous utilisez `git` depuis un moment, la sortie bavarde de `git status` n'est plus très utile. `git status` peut fournir une version compacte si on lui passe l'option `-s` (`--short`) :

<pre>
 <span  style="color:green;">M</span> src/some/file.js
<span style="color:maroon;">M</span>  src/another/file.js
<span style="color:maroon;">??</span> Readme
</pre>

Avec `-b` (`--branch`), on ajoute les infos de branches, toujours utiles :

<pre>
## <span style="color:green;">master</span>...<span style="color:maroon;">origin/master</span> [ahead <span style="color:green;">1</span>]
 <span  style="color:green;">M</span> src/some/file.js
<span style="color:maroon;">M</span>  src/another/file.js
<span style="color:maroon;">??</span> Readme
</pre>

Pour les détails sur les symboles dans les deux premières colonnes : `man git status`.
