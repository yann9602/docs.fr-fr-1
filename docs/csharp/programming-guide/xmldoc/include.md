---
title: "&lt;include&gt; (guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "include"
  - "<include>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<include> (balise XML C#)"
  - "include (balise XML C#)"
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# &lt;include&gt; (guide de programmation C#)
## Syntaxe  
  
```  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### Paramètres  
 `filename`  
 Nom du fichier XML contenant la documentation.  Le nom du fichier peut être précisé par un chemin.  Mettez `filename` entre guillemets simples \(' '\).  
  
 `tagpath`  
 Chemin d'accès des balises dans `filename` qui permet d'accéder au `name` de la balise.  Mettez le chemin entre guillemets simples \(' '\).  
  
 `name`  
 Dans la balise, spécificateur de nom précédant les commentaires ; `name` est associé à un `id`.  
  
 `id`  
 ID de la balise qui précède les commentaires.  Placez l'ID entre guillemets doubles \(" "\).  
  
## Notes  
 La balise \<include\> permet de faire référence à des commentaires situés dans un autre fichier qui décrivent les types et membres dans votre code source.  Cette solution remplace celle consistant à placer des commentaires de documentation directement dans votre fichier de code source.  En mettant la documentation dans un fichier séparé, vous pouvez appliquer séparément le contrôle de code source à la documentation du code source.  Une personne peut avoir le fichier de code source extrait et une autre peut avoir le fichier de documentation extrait.  
  
 La balise \<include\> utilise la syntaxe XML XPath.  Pour en savoir plus sur les différentes façons de personnaliser votre utilisation de \<include\>, consultez la documentation XPath.  
  
## Exemple  
 Cet exemple fait appel à plusieurs fichiers.  Le premier, qui utilise \<include\>, est indiqué ci\-dessous :  
  
 [!code-cs[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 Le deuxième fichier, xml\_include\_tag.doc, contient les commentaires de documentation suivants :  
  
```  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## Sortie du programme  
 La sortie suivante est générée lorsque vous compilez les classes Test2 et Test avec la ligne de commande suivante : `/doc:DocFileName.xml.` Dans Visual Studio, vous spécifiez l'option de commentaires de document XML dans le volet Génération du Concepteur de projets.  Lorsque le compilateur C\# rencontre la balise \< inclue \>, il recherchera des commentaires sur la documentation dans xml\_include\_tag.doc au lieu du fichier source actif.  Le compilateur génère ensuite DocFileName.xml et c'est le fichier qui est consommé par les outils de documentation tels que [Sandcastle](http://go.microsoft.com/fwlink/?LinkId=124061) pour produire la documentation finale.  
  
```  
<?xml version="1.0"?>   
<doc>   
    <assembly>   
        <name>xml_include_tag</name>   
    </assembly>   
    <members>   
        <member name="T:Test">   
            <summary>   
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)