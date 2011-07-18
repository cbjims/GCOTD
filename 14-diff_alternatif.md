Diff alternatif
===============

Vous êtes sans doute habitué à `git diff` qui affiche quelque chose comme ça : 

    .box-tree-node .box-tree-node-box {
    -    border : 1px solid red;
    +    border : 1px solid #888;
    +    overflow : hidden;
         margin-right : 10px;
         position : relative;
     }
    -.box-tree-node .box-tree-node-box .box-tree-node-align{
    +.box-tree-node .box-tree-node-box .box-tree-node-align {
         display : inline;
         position:absolute;
         right : 10px;
     }

Si vous avez configuré color.diff = auto, vous avez la même chose avec des couleurs : les lignes retirées en rouge, celles ajoutées en vert.

<pre>
.box-tree-node .box-tree-node-box {
<span style="color:red;">-    border : 1px solid red;</span>
<span style="color:green;">+    border : 1px solid #888;</span>
<span style="color:green;">+    overflow : hidden;</span>
     margin-right : 10px;
     position : relative;
 }
 <span style="color:red;">-.box-tree-node .box-tree-node-box .box-tree-node-align{</span>
<span style="color:green;"> +.box-tree-node .box-tree-node-box .box-tree-node-align {</span>
     display : inline;
     position:absolute;
     right : 10px;
 }
</pre>

Avec `git diff --color-words`, vous avez un diff plus compact, avec les différences synthétisées directement sur la ligne :

<pre>
.box-tree-node .box-tree-node-box {
    border : 1px solid  <span style="color:red;">red;</span> <span style="color:green;">#888;</span>
<span style="color:green;">    overflow : hidden;</span>
    margin-right : 10px;
    position : relative;
}
.box-tree-node .box-tree-node-box <span style="color:red;">.box-tree-node-align{</span><span style="color:green;">.box-tree-node-align {</span>
    display : inline;
    position:absolute;
    right : 10px;
}
</pre>


