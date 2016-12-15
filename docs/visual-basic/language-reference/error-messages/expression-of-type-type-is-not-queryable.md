---
title: "Expression of type &lt;type&gt; is not queryable | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36593"
  - "vbc36593"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36593"
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Expression of type &lt;type&gt; is not queryable
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'expression de type '\<type\>' ne peut pas être interrogée.Vérifiez que vous n'omettez pas une référence d'assembly et\/ou une importation d'espace de noms pour le fournisseur LINQ.  
  
 Les types pouvant être interrogés sont définis dans les espaces de noms <xref:System.Linq>, <xref:System.Data.Linq> et <xref:System.Xml.Linq>.  Vous devez importer un ou plusieurs de ces espaces de noms pour exécuter des requêtes LINQ.  
  
 L'espace de noms <xref:System.Linq> vous permet d'interroger des objets tels que des collections et des tableaux en utilisant des requêtes LINQ.  
  
 L'espace de noms <xref:System.Data.Linq> vous permet d'interroger des groupes de données ADO.NET et des bases de données SQL Server en utilisant des requêtes LINQ.  
  
 L'espace de noms <xref:System.Xml.Linq> vous permet d'interroger le code XML en utilisant des requêtes LINQ et d'utiliser les fonctionnalités XML dans Visual Basic.  
  
 **ID d'erreur :** BC36593  
  
### Pour corriger cette erreur  
  
1.  Ajoutez une instruction `Import` pour l'espace de noms <xref:System.Linq>, <xref:System.Data.Linq> ou <xref:System.Xml.Linq> dans votre fichier de code.  Vous pouvez également importer des espaces de noms pour votre projet à l'aide de la page **Références** du Concepteur de projets \(**My Project**\).  
  
2.  Vérifiez que le type que vous avez identifié comme source de votre requête est un type pouvant être interrogé.  Autrement dit, un type qui implémente <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.  
  
## Voir aussi  
 <xref:System.Linq>   
 <xref:System.Data.Linq>   
 <xref:System.Xml.Linq>   
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Page Références, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)