---
title: "&lt;permission&gt; (Visual Basic) | Microsoft Docs"
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
  - "<permission> XML tag"
  - "permission XML tag"
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;permission&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie une autorisation requise pour le membre.  
  
## Syntaxe  
  
```  
<permission cref="member">description</permission>  
```  
  
#### Paramètres  
 `member`  
 Référence à un membre ou un champ qu'il est possible d'appeler depuis l'environnement de compilation actuel.  Le compilateur vérifie que l'élément de code donné existe et traduit `member` dans le nom d'élément canonique dans le fichier de sortie XML.  Mettez `member` entre guillemets \(" "\).  
  
 `description`  
 Description de l'accès au membre.  
  
## Notes  
 Utilisez la balise `<permission>` pour documenter l'accès d'un membre.  Utilisez la classe <xref:System.Security.PermissionSet> pour spécifier l'accès à un membre.  
  
 Compilez avec [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 Cet exemple utilise la balise `<permission>` pour décrire que le <xref:System.Security.Permissions.FileIOPermission> est requis par la méthode `ReadFile`.  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## Voir aussi  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)