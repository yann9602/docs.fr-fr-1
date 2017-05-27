---
title: Guide de programmation (LINQ to XML) (C#) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 4b1ffd10-ab81-4a0d-a0ca-e9876478d924
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5e1e95d92123b2874aace0c36005a8a07a6203fc
ms.contentlocale: fr-fr
ms.lasthandoff: 05/24/2017

---
# <a name="programming-guide-linq-to-xml-c"></a>Guide de programmation (LINQ to XML) (C#)
Cette section fournit des informations conceptuelles et de procédure sur la programmation avec [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
## <a name="who-should-read-this-documentation"></a>À qui cette documentation est-elle destinée ?  
 Cette documentation est destinée aux développeurs qui connaissent déjà le langage C# et certains aspects de base du [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)].  
  
 L’objectif de cette documentation est de simplifier l’utilisation de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] pour tous les développeurs. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] facilite la programmation XML. Son utilisation n'est pas restreinte aux développeurs expérimentés.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] s’appuie essentiellement sur les classes génériques. Par conséquent, il est très important de comprendre l'utilisation des classes génériques. En outre, il est utile de connaître la notion de délégués déclarés en tant que types paramétrés. Si vous ne connaissez pas bien les classes génériques en C#, consultez [Classes génériques](../../../../csharp/programming-guide/generics/generic-classes.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Vue d’ensemble de la programmation LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)|Fournit une vue d'ensemble des classes [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] et des informations détaillées sur trois des classes les plus importantes : <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XDocument>.|  
|[Création d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)|Fournit des informations conceptuelles et basées sur les tâches concernant la création des arborescences XML. Vous pouvez créer des arborescences XML à l'aide de la construction fonctionnelle ou en analysant du texte XML à partir d'une chaîne ou d'un fichier. Vous pouvez également utiliser un objet <xref:System.Xml.XmlReader> pour remplir une arborescence XML.|  
|[Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)|Fournit des informations détaillées sur la création d’arborescences XML qui utilisent des espaces de noms.|  
|[Sérialisation d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)|Décrit plusieurs approches de la sérialisation d’une arborescence XML et fournit des conseils sur l’approche à utiliser.|  
|[Axes LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)|Énumère et décrit les méthodes d’axe [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], que vous devez comprendre pour pouvoir écrire des requêtes [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].|  
|[Interrogation d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)|Fournit des exemples courants d’interrogation d’arborescences XML.|  
|[Modification d’arborescences XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)|Comme le modèle DOM (Document Object Model), [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] vous permet de modifier directement une arborescence XML.|  
|[Programmation LINQ to XML avancée (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)|Fournit des informations sur les annotations, événements, transmission en continu et autres scénarios avancés.|  
|[Sécurité LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-security.md)|Décrit des problèmes de sécurité associés à LINQ to XML et fournit quelques conseils pour limiter les risques liés à la sécurité.|  
|[Exemples de documents XML (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)|Contient les exemples de documents XML utilisés par de nombreux exemples dans cette documentation.|  
  
## <a name="see-also"></a>Voir aussi  
 [Bien démarrer (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)   
 [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)
