---
title: "&lt;list&gt; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "listheader XML tag"
  - "<item> XML tag"
  - "<list> XML tag"
  - "<listheader> XML tag"
  - "term XML tag"
  - "list XML tag"
  - "<description> XML tag"
  - "description XML tag"
  - "item XML tag"
  - "<term> XML tag"
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;list&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Définit une liste ou une table.  
  
## Syntaxe  
  
```  
<list type="type">  
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
 `type`  
 Type de la liste.  Doit être une "puce" pour une liste à puces, "numéro" pour une liste numérotée, ou "table" pour une table à deux colonnes.  
  
 `term`  
 Utilisé uniquement lorsque `type` est « table ». Terme à définir qui est défini dans la balise de description.  
  
 `description`  
 Lorsque `type` est « puce » ou « numéro », `description` est un élément dans la liste. Lorsque `type` est « table », `description` est la définition de `term`.  
  
## Notes  
 Le bloc `<listheader>` permet de définir le titre d'une table ou d'une liste de définitions.  Lorsque vous définissez une table, il suffit de fournir une entrée pour `term` dans le titre.  
  
 Chaque élément de la liste est spécifié dans un bloc `<item>`.  Lorsque vous créez une liste de définitions, vous devez spécifier à la fois `term` et `description`.  Cependant, pour une table, une liste à puces ou une liste numérotée, il vous suffit de fournir une entrée pour `description`.  
  
 Une liste ou une table peut comporter autant de blocs `<item>` que nécessaire.  
  
 Compilez avec [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 Cet exemple utilise la balise `<list>` pour définir une liste à puces dans la section Notes.  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## Voir aussi  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)