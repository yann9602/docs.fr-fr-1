---
title: "Atténuation : disposition WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d3ba5ac792169cc076f9621025f35444281cec6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-wpf-layout"></a>Atténuation : disposition WPF
La disposition des contrôles WPF peut varier légèrement.  
  
## <a name="impact"></a>Impact  
 Résultat de cette modification :  
  
-   La largeur ou la hauteur d'éléments peut croître ou diminuer d'un pixel au plus.  
  
-   La position d'un objet peut se déplacer d'un pixel au plus.  
  
-   Les éléments centrés peuvent être décalés verticalement ou horizontalement d'un pixel au plus.  
  
 Par défaut, cette nouvelle disposition est activée uniquement pour les applications qui ciblent le .NET. Framework 4.6.  
  
## <a name="mitigation"></a>Atténuation  
 Dans la mesure où cette modification tend à éliminer le découpage droit ou inférieur des contrôles WPF dont le PPP est élevé, les applications qui ciblent les versions antérieures du .NET Framework, mais qui s'exécutent sur le .NET Framework 4.6, peuvent choisir ce nouveau comportement en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 Les applications qui ciblent le .NET Framework 4.6, mais veulent que les contrôles WPF soient rendus à l'aide de l'algorithme de disposition précédent peuvent y parvenir en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
