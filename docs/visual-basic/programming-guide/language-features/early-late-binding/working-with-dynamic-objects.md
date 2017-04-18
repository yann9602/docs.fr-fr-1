---
title: "Utilisation d’objets dynamiques (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 366b563764baaa39849356a782ecee264b2ae94f
ms.lasthandoff: 03/13/2017

---
# <a name="working-with-dynamic-objects-visual-basic"></a>Utilisation d'objets dynamiques (Visual Basic)
Objets dynamiques fournissent une autre manière, autre que le `Object` type, à liaison tardive à un objet au moment de l’exécution. Un objet dynamique expose des membres tels que les propriétés et les méthodes au moment de l’exécution à l’aide des interfaces dynamiques définies dans le <xref:System.Dynamic>espace de noms.</xref:System.Dynamic> Vous pouvez utiliser les classes dans le <xref:System.Dynamic>espace de noms pour créer des objets qui fonctionnent avec des structures de données qui ne correspondent pas à un format ou le type statique.</xref:System.Dynamic> Vous pouvez également utiliser les objets dynamiques qui sont définies dans les langages dynamiques tels que IronPython et IronRuby. Pour obtenir des exemples qui montrent comment créer des objets dynamiques ou utiliser un objet dynamique défini dans un langage dynamique, consultez la page [procédure pas à pas : création et l’utilisation d’objets dynamiques](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, ou <xref:System.Dynamic.ExpandoObject>.</xref:System.Dynamic.ExpandoObject> </xref:System.Dynamic.DynamicObject>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Crée une liaison aux objets des langages dynamiques tels que IronPython et IronRuby et le dynamic language runtime à l’aide de la <xref:System.Dynamic.IDynamicMetaObjectProvider>interface.</xref:System.Dynamic.IDynamicMetaObjectProvider> Exemples de classes qui implémentent la `IDynamicMetaObjectProvider` interface sont les <xref:System.Dynamic.DynamicObject>et <xref:System.Dynamic.ExpandoObject>classes.</xref:System.Dynamic.ExpandoObject> </xref:System.Dynamic.DynamicObject>  
  
 Si un appel à liaison tardive est effectué vers un objet qui implémente le `IDynamicMetaObjectProvider` interface, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] lie à l’objet dynamique à l’aide de cette interface. Si un appel à liaison tardive est effectué vers un objet qui n’implémente pas le `IDynamicMetaObjectProvider` interface, ou si l’appel à la `IDynamicMetaObjectProvider` échoue, l’interface [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] lie à l’objet en utilisant les fonctionnalités de liaison tardive de la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] runtime.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Dynamic.DynamicObject></xref:System.Dynamic.DynamicObject>   
 <xref:System.Dynamic.ExpandoObject></xref:System.Dynamic.ExpandoObject>   
 [Procédure pas à pas : Création et utilisation d’objets dynamiques](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)   
 [Liaison anticipée et liaison tardive](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
