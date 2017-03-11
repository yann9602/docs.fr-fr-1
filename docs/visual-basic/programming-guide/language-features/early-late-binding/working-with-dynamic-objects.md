---
title: "Working with Dynamic Objects (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "dynamic objects [Visual Basic]"
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Working with Dynamic Objects (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les objets Dynamic offrent un moyen différent, autre que le type `Object`, de créer une liaison tardive à un objet au moment de l'exécution.  Un objet dynamique expose des membres tels que les propriétés et les méthodes au moment de l'exécution à l'aide des interfaces dynamiques définies dans l'espace de noms <xref:System.Dynamic>.  Vous pouvez utiliser les classes de l'espace de noms <xref:System.Dynamic> pour créer des objets fonctionnant avec les structures de données qui ne correspondent pas à un type ou à un format statique.  Vous pouvez également utiliser les objets dynamiques définis dans les langages dynamiques tels qu'IronPython et IronRuby.  Pour des exemples indiquant comment créer des objets dynamiques ou utiliser un objet dynamique défini dans un langage dynamique, consultez [Procédure pas à pas : création et utilisation d'objets dynamiques](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject> ou <xref:System.Dynamic.ExpandoObject>.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] crée une liaison avec les objets DLR \(Dynamic Language Runtime\) et de langages dynamiques tels qu'IronPython and IronRuby à l'aide de l'interface <xref:System.Dynamic.IDynamicMetaObjectProvider>.  Les classes <xref:System.Dynamic.DynamicObject> et <xref:System.Dynamic.ExpandoObject> constituent des exemples de classes qui implémentent l'interface `IDynamicMetaObjectProvider`.  
  
 Si un appel à liaison tardive est effectué vers un objet qui implémente l'interface `IDynamicMetaObjectProvider`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] crée une liaison avec l'objet dynamique à l'aide de cette interface.  Si un appel à liaison tardive est effectué vers un objet qui n'implémente pas l'interface `IDynamicMetaObjectProvider`, ou si l'appel à l'interface `IDynamicMetaObjectProvider` échoue, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] crée une liaison avec l'objet à l'aide des fonctions de liaison tardive de l'exécution [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
## Voir aussi  
 <xref:System.Dynamic.DynamicObject>   
 <xref:System.Dynamic.ExpandoObject>   
 [Procédure pas à pas : création et utilisation d'objets dynamiques](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)   
 [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)