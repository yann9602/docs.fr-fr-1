---
title: "&lt;typeparam&gt; (guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "typeparam"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<typeparam> (balise XML C#)"
  - "typeparam (balise XML C#)"
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# &lt;typeparam&gt; (guide de programmation C#)
## Syntaxe  
  
```  
<typeparam name="name">description</typeparam>  
```  
  
#### Paramètres  
 `name`  
 Nom du paramètre de type.  Mettez le nom entre guillemets doubles \(" "\).  
  
 `description`  
 Description du paramètre de type.  
  
## Notes  
 La balise `<typeparam>` doit être utilisée dans le commentaire d'une déclaration de méthode ou de type générique pour décrire un paramètre de type.  Ajoutez une balise pour chaque paramètre de type du type ou de la méthode générique.  
  
 Pour plus d'informations, consultez [Génériques](../../../csharp/programming-guide/generics/index.md).  
  
 Le texte de la balise `<typeparam>` sera affiché dans IntelliSense, le rapport Web du commentaire de code [Object Browser Window](http://msdn.microsoft.com/fr-fr/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda).  
  
 Compilez avec [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 [!code-cs[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/csharp/typeparam_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)