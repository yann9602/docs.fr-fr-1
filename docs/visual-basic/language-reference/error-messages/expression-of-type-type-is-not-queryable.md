---
title: "Expression de type &lt;type&gt; n’est pas utilisable dans une requête"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords: BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f2b98bf48f0b3965929f9211c2944ff97754f23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a>Expression de type &lt;type&gt; n’est pas utilisable dans une requête
Expression de type \<type > ne peut pas être interrogée. Assurez-vous que vous ne manque pas une importation d’espace de noms de référence ou d’assembly pour le fournisseur LINQ.  
  
 Types pouvant être interrogés sont définis dans le <xref:System.Linq>, <xref:System.Data.Linq>, et <xref:System.Xml.Linq> espaces de noms. Vous devez importer un ou plusieurs de ces espaces de noms pour effectuer des requêtes LINQ.  
  
 Le <xref:System.Linq> espace de noms vous permet de requêtes sur des objets tels que des collections et tableaux à l’aide de LINQ.  
  
 Le <xref:System.Data.Linq> vous permet d’interroger des jeux de données ADO.NET et des bases de données SQL Server à l’aide de LINQ.  
  
 Le <xref:System.Xml.Linq> espace de noms vous permet d’interroger XML à l’aide de LINQ et à utiliser les fonctionnalités XML en Visual Basic.  
  
 **ID d’erreur :** BC36593  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Ajouter un `Import` instruction pour le <xref:System.Linq>, <xref:System.Data.Linq>, ou <xref:System.Xml.Linq> espace de noms à votre fichier de code. Vous pouvez également importer des espaces de noms pour votre projet à l’aide de la **références** page du Concepteur de projets (**mon projet**).  
  
2.  Vérifiez que le type que vous avez identifié comme source de votre requête est un type requêtable. Autrement dit, un type qui implémente <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq>  
 <xref:System.Data.Linq>  
 <xref:System.Xml.Linq>  
 [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Références et l’instruction Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Imports (instruction) (espace de noms et type .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Page Références, Concepteur de projet (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
