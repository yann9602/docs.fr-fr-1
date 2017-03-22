---
title: "Interopérabilité COM dans les Applications .NET Framework (Visual Basic) | Documents Microsoft"
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
- interoperability, COM and .NET framework objects
- COM interop
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 308ee8e495efa9368ef55d781f6b6dc314db51ac
ms.lasthandoff: 03/13/2017

---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>Interopérabilité COM dans les applications .NET Framework (Visual Basic)
Lorsque vous souhaitez utiliser les objets COM et .NET Framework dans la même application, vous devez résoudre les différences dans la façon dont les objets existent dans la mémoire. Un objet .NET Framework se trouve dans la mémoire managée, la mémoire contrôlée par le common language runtime et peut être déplacé par le runtime si nécessaire. Un objet COM se trouve dans la mémoire non managée et n’est pas prévu de passer à un autre emplacement de mémoire. [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]et [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] fournissent des outils pour contrôler l’interaction de ces composants managés et. Pour plus d’informations sur le code managé, consultez [Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482).  
  
 Outre l’utilisation des objets COM dans les applications .NET, vous pouvez également utiliser [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour développer des objets accessibles à partir de code non managé via COM.  
  
 Les liens de cette page fournissent des détails sur les interactions entre les objets COM et .NET Framework.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 Fournit des liens vers des rubriques traitant de l’interopérabilité COM dans Visual Basic, y compris COM objets ActiveX contrôles, les DLL Win32, les objets managés et l’héritage d’objets COM.  
  
 [Erreur de Wrapper COM Interop](https://docs.microsoft.com/cpp/misc/com-interop-wrapper-error)  
 Décrit les conséquences et les options si le système de projet ne peut pas créer un wrapper d’interopérabilité COM pour un composant particulier.  
  
 [Interopération avec du Code non managé](https://msdn.microsoft.com/library/sd10k43k)  
 Certains problèmes d’interaction entre du code managé et décrit brièvement et fournit des liens pour approfondir ce sujet.  
  
 [Wrappers COM](http://msdn.microsoft.com/library/e56c485b-6b67-4345-8e66-fd21835a6092)  
 Traite des wrappers RCW, qui permettent au code managé d’appeler les méthodes COM, et par COM, qui permettent aux clients COM d’appeler les méthodes d’objets .NET.  
  
 [Interopérabilité COM avancée](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 Fournit des liens vers des rubriques traitant de l’interopérabilité COM en ce qui concerne les wrappers, exceptions, l’héritage, threads, événements, les conversions et marshaling.  
  
 [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 Décrit l’outil que vous pouvez utiliser pour convertir les définitions de type trouvées dans une bibliothèque de types COM en définitions équivalentes dans un assembly du common language runtime.
