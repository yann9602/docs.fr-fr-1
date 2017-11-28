---
title: "Atténuation : rendu de la fenêtre WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 57d4cc56cc8d3a4dc3614043779eb09d7a8b8e25
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-wpf-window-rendering"></a>Atténuation : rendu de la fenêtre WPF
Dans le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] s'exécutant sur Windows 8 et versions ultérieures, la totalité de la fenêtre est restituée sans découpage lorsqu'elle s'étend au-delà d'un seul affichage dans un scénario à plusieurs écrans.  
  
## <a name="impact"></a>Impact  
 En général, le rendu de toute une fenêtre sur plusieurs écrans sans découpage est le comportement attendu. Cependant, sur Windows 7 et versions antérieures, les fenêtres WPF sont tronquées lorsqu'elles s'étendent au-delà d'un seul affichage, car le rendu d'une partie de la fenêtre sur le second écran a un impact significatif sur les performances.  
  
 L'impact du rendu des fenêtres WPF sur les écrans sur Windows 8 et versions ultérieures n'est pas précisément quantifiable, car il dépend d'un grand nombre de facteurs. Dans certains cas, il peut se produire un impact indésirable sur les performances, en particulier pour les utilisateurs qui exécutent des applications riches en graphisme et dont les fenêtres se chevauchent. Dans d'autres cas, vous pouvez simplement vouloir un comportement cohérent entre les versions du .NET Framework.  
  
## <a name="mitigation"></a>Atténuation  
 Vous pouvez désactiver cette modification et rétablir le comportement précédent de découpage d'une fenêtre WPF lorsqu'elle s'étend au-delà d'un affichage unique. Il existe deux façons d'effectuer cette opération :  
  
-   En ajoutant l'élément `<EnableMultiMonitorDisplayClipping>` à la section `<appSettings>` du fichier de configuration de votre application, vous pouvez activer ou désactiver ce comportement sur les applications qui s'exécutent sur Windows 8 ou versions ultérieures. Par exemple, la section de configuration suivante désactive le rendu sans découpage :  
  
    ```xml  
    <appSettings>  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
      </appSettings>  
    ```  
  
     Le paramètre de configuration `<EnableMultiMonitorDisplayClipping>` peut avoir l'une des deux valeurs suivantes :  
  
    -   `true`, pour activer le découpage des fenêtres selon les limites de l'écran pendant le rendu.  
  
    -   `false`, pour désactiver le découpage des fenêtres selon les limites de l'écran pendant le rendu.  
  
-   En définissant la propriété <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> avec la valeur `true` au démarrage de l'application.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications du runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
