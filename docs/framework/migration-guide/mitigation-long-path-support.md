---
title: "Atténuation : Prise en charge des chemins d’accès longs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3cbe2d77-6e2c-4665-a6c5-7000b9ad6890
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 138e96c3d45b79ccf30f6a3d39f0af26a48c0117
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-long-path-support"></a>Atténuation : Prise en charge des chemins d’accès longs
À partir des applications qui ciblent le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], les méthodes d’E/S du système de fichiers ne lèvent plus automatiquement une <xref:System.IO.PathTooLongException> si un chemin ou nom de fichier complet dépasse 260 (ou `MAX_PATH`) caractères. Au lieu de cela, les chemins d’accès longs de sont pris en charge jusqu'à 32 000 caractères.  
  
## <a name="impact"></a>Impact  
 Les applications recompilées pour cibler [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] et qui levaient précédemment une <xref:System.IO.PathTooLongException> automatiquement car un chemin dépassait 260 caractères lèvent maintenant une <xref:System.IO.PathTooLongException> uniquement dans les conditions suivantes :  
  
-   La longueur du chemin est supérieure à <xref:System.Int16.MaxValue?displayProperty=fullName> (32 767) caractères.  
  
-   Le système d’exploitation renvoie `COR_E_PATHTOOLONG` ou son équivalent.  
  
 L’ancien comportement pour les applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions antérieures faisait que le runtime levait automatiquement une <xref:System.IO.PathTooLongException> chaque fois qu’un chemin comportait plus de 260 caractères.  
  
## <a name="mitigation"></a>Atténuation  
 Pour les applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], vous pouvez annuler la prise en charge des longs chemins d’accès en ajoutant le code suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section de votre fichier app.config :  
  
```xml  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />   
</runtime>  
```  
  
 Pour les applications qui ciblent des versions antérieures de .NET Framework mais s’exécutent sur [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou version ultérieure, vous pouvez accepter la prise en charge des longs chemins d’accès en ajoutant le code suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier app.config :  
  
```xml  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)

