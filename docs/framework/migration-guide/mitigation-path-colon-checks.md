---
title: "Atténuation : Vérifications des signes deux-points dans les chemins d’accès"
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
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a387e02c9d754db6af7fa2d2ba5f2ea6d96d4301
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-path-colon-checks"></a>Atténuation : Vérifications des signes deux-points dans les chemins d’accès
Plusieurs modifications ont été apportées pour prendre en charge les chemins d’accès non pris en charge précédemment (à la fois en termes de longueur et le format), à commencer par les applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]. En particulier, les vérifications de bonne syntaxe de séparateur de lecteur (le signe deux-points) ont été rendues plus correctes.  
  
## <a name="impact"></a>Impact  
 Ces modifications bloquent certains chemins d’URI que les méthodes <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> prenaient précédemment en charge.  
  
## <a name="mitigation"></a>Atténuation  
 Pour contourner le problème d’un chemin précédemment acceptable qui n’est plus pris en charge par les méthodes <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>, effectuez les étapes suivantes :  
  
-   Supprimez manuellement le schéma à partir d’une URL. Par exemple, supprimez `file://` à partir d’une URL.  
  
-   Passez l’URI à un constructeur <xref:System.Uri> et récupérez la valeur de la propriété <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>.  
  
-   Refusez la nouvelle normalisation de chemin d’accès en affectant à `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> la valeur `true`.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
