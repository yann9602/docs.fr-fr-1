---
title: "&lt;list&gt; (guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
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
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# &lt;list&gt; (guide de programmation C#)
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
 [!code-cs[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/csharp/list_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)