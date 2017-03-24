---
title: "&lt;param&gt; (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "param"
  - "<param>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<param> (balise XML C#)"
  - "param (balise XML C#)"
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# &lt;param&gt; (Guide de programmation&#160;C#)
## Syntaxe  
  
```  
<param name="name">description</param>  
```  
  
#### Paramètres  
 `name`  
 Nom d'un paramètre de méthode.  Mettez le nom entre guillemets doubles \(" "\).  
  
 `description`  
 Description du paramètre.  
  
## Notes  
 La balise \<param\> doit être utilisée dans le commentaire pour une déclaration de méthode afin de décrire l'un des paramètres pour la méthode.  Pour documenter plusieurs paramètres, utilisez plusieurs balises \<param\>.  
  
 Le texte de la balise \<param\> est affiché dans IntelliSense, dans l'Explorateur d'objets et dans le rapport Web de commentaire de code.  
  
 Compilez avec [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 [!code-cs[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)