---
title: "&lt;list&gt; (guide de programmation C#) | Microsoft Docs"
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
  - "list"
  - "<list>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<item> (balise XML C#)"
  - "<list> (balise XML C#)"
  - "<listheader> (balise XML C#)"
  - "item (balise XML C#)"
  - "list (balise XML C#)"
  - "listheader (balise XML C#)"
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;list&gt; (guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## Syntaxe  
  
```  
<list type="bullet" | "number" | "table">  
    <listheader>  
        <term>term</term>  
        <description>description</description>  
    </listheader>  
    <item>  
        <term>term</term>  
        <description>description</description>  
    </item>  
</list>  
```  
  
#### Paramètres  
 `term`  
 Terme à définir, qui est défini dans `description`.  
  
 `description`  
 Élément d'une liste à puces ou numérotée, ou définition d'un `term`.  
  
## Notes  
 Le bloc \<listheader\> permet de définir la ligne de titre d'un tableau ou d'une liste de définitions.  Lorsque vous définissez un tableau, il suffit de fournir une entrée pour term dans le titre.  
  
 Chaque élément de la liste est spécifié par un bloc \<item\>.  Lorsque vous créez une liste de définitions, vous devez spécifier à la fois `term` et `description`.  Cependant, pour un tableau, une liste à puces ou une liste numérotée, il vous suffit de fournir une entrée pour `description`.  
  
 Une liste ou un tableau peut comporter autant de blocs \<item\> que nécessaire.  
  
 Compilez avec [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 [!code-cs[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)