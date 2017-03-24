---
title: "&lt;include&gt; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "include XML tag"
  - "<include> XML tag"
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# &lt;include&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Fait référence à un autre fichier qui décrit les types et membres dans votre code source.  
  
## Syntaxe  
  
```  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### Paramètres  
 `filename`  
 Obligatoire.  Nom du fichier contenant la documentation.  Le nom du fichier peut être précisé par un chemin.  Mettez `filename` entre guillemets doubles \(" "\).  
  
 `tagpath`  
 Obligatoire.  Chemin d'accès des balises dans `filename` qui permet d'accéder au `name` de la balise.  Mettez le chemin d'accès entre guillemets doubles \(" "\).  
  
 `name`  
 Obligatoire.  Spécificateur de nom dans la balise qui précède les commentaires.  `Name` aura un `id`.  
  
 `id`  
 Obligatoire.  ID de la balise qui précède les commentaires.  Mettez l'ID entre guillemets simples \(' '\).  
  
## Notes  
 Utilisez la balise `<include>` pour faire référence à des commentaires situés dans un autre fichier qui décrivent les types et membres dans votre code source.  Cette solution remplace celle consistant à placer des commentaires de documentation directement dans votre fichier de code source.  
  
 La balise `<include>` utilise la recommandation du W3C intitulée XML Path Language \(XPath\) Version 1.0.  Plus d'informations sur les moyens de personnaliser votre utilisation de `<include>` sont disponibles à la page http:\/\/www.w3.org\/TR\/xpath.  
  
## Exemple  
 Cet exemple utilise la balise `<include>` pour importer des commentaires de documentation membre d'un fichier nommé `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 Le format du `commentFile.xml` est le suivant :  
  
```  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## Voir aussi  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)