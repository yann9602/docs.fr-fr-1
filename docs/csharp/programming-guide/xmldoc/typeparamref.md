---
title: "&lt;typeparamref&gt; (guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "typeparamref"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<typeparamref> (balise XML C#)"
  - "typeparamref (balise XML C#)"
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;typeparamref&gt; (guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## Syntaxe  
  
```  
<typeparamref name="name"/>  
```  
  
#### Paramètres  
 `name`  
 Nom du paramètre de type.  Mettez le nom entre guillemets doubles \(" "\).  
  
## Notes  
 Pour plus d'informations sur les paramètres de type dans les types et méthodes génériques, consultez [Génériques](../../../csharp/programming-guide/generics/index.md).  
  
 Employez cette balise pour permettre aux utilisateurs du fichier de documentation de mettre en forme le mot de façon distincte, par exemple en italiques.  
  
 Compilez avec [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 [!code-cs[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)