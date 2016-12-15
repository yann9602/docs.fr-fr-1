---
title: "COM Interoperability in .NET Framework Applications (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "interoperability, COM and .NET framework objects"
  - "COM interop"
  - "shared components"
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# COM Interoperability in .NET Framework Applications (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Avant d'utiliser des objets  COM et des objets .NET Framework dans la même application, vous devez résoudre les différences entre ces objets concernant la manière dont ils existent dans la mémoire.  Un objet .NET Framework se trouve dans la mémoire managée \(la mémoire contrôlée par le Common Language Runtime\) et peut être déplacé par le runtime si nécessaire.  Un objet COM se trouve dans la mémoire non managée et n'est pas censé se déplacer vers un autre emplacement dans la mémoire.  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] et le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] fournissent des outils pour contrôler l'interaction de ces composants managés et non managés.  Pour plus d'informations sur le code managé, consultez [Common Language Runtime](../Topic/Common%20Language%20Runtime%20\(CLR\).md).  
  
 Outre les objets COM dans les applications .NET, vous pouvez utiliser [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour développer des objets accessibles à partir du code non managé via COM.  
  
 Les liens dans cette page fournissent des détails sur les interactions entre les objets COM et les objets .NET Framework.  
  
## Rubriques connexes  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 Propose des liens vers des rubriques traitant de l'interopérabilité COM en Visual Basic, y compris les objets COM, les contrôles ActiveX, les DLL Win32, les objets managés et l'héritage d'objets COM.  
  
 [COM Interop Wrapper Error](/visual-cpp/misc/com-interop-wrapper-error)  
 Décrit les conséquences et les options si le système de projet ne peut pas créer un wrapper d'interopérabilité COM pour un composant particulier.  
  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)  
 Décrit brièvement certains problèmes d'interaction entre le code managé et le code non managé et propose des liens pour une étude plus approfondie.  
  
 [COM Wrappers](../Topic/COM%20Wrappers.md)  
 Présente les wrappers RCW \(Runtime Callable Wrapper\), qui permettent au code managé d'appeler les méthodes COM, ainsi que les wrappers CCW \(COM Callable Wrapper\), qui permettent aux clients COM d'appeler les méthodes d'objets .NET.  
  
 [Advanced COM Interoperability](http://msdn.microsoft.com/fr-fr/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 Propose des liens vers des rubriques traitant de l'interopérabilité COM par rapport aux wrappers, aux exceptions, à l'héritage, au threading, aux événements, aux conversions et au marshaling.  
  
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)  
 Présente l'outil que vous pouvez utiliser pour convertir les définitions de type trouvées dans une bibliothèque de types COM en définitions équivalentes dans un assembly Common Language Runtime.