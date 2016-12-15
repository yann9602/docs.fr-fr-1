---
title: "&lt;permission&gt; (guide de programmation C#) | Microsoft Docs"
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
  - "permission"
  - "<permission>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<permission> (balise XML C#)"
  - "permission (balise XML C#)"
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;permission&gt; (guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## Syntaxe  
  
```  
<permission cref="member">description</permission>  
```  
  
#### Paramètres  
 cref \= "`member`"  
 Référence à un membre ou un champ qu'il est possible d'appeler depuis l'environnement de compilation actuel.  Le compilateur vérifie que l'élément de code donné existe et traduit `member` par le nom d'élément complet dans la sortie XML. *membre* doit être placé entre guillemets doubles \(" "\).  
  
 Pour plus d'informations sur la création d'une référence cref à un type générique, consultez [\<see\>](../../../csharp/programming-guide/xmldoc/see.md).  
  
 `description`  
 Description de l'accès au membre.  
  
## Notes  
 La balise \<permission\> permet de documenter l'accès d'un membre.  La classe <xref:System.Security.PermissionSet> vous permet de spécifier l'accès à un membre.  
  
 Compilez avec [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 [!code-cs[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)