---
title: "&lt;param&gt; (Visual Basic) | Microsoft Docs"
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
  - "param XML tag"
  - "<param> XML tag"
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;param&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Définit un nom et une description de paramètre.  
  
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
 La balise `<param>` doit être utilisée dans le commentaire pour une déclaration de méthode afin de décrire l'un des paramètres pour la méthode.  
  
 Le texte de la balise d' `<param>` apparaîtra dans les emplacements suivants :  
  
-   Les informations sur les paramètres Intellisense.  Pour plus d’informations, consultez [Utilisation de la fonctionnalité IntelliSense](/visual-studio/ide/using-intellisense).  
  
-   Explorateur d'objets.  Pour plus d’informations, consultez [Affichage de la structure du code](/visual-studio/ide/viewing-the-structure-of-code).  
  
 Compilez avec [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 Cet exemple utilise la balise `<param>` pour décrire le paramètre `id`.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## Voir aussi  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)