---
title: "Atténuation : Culture et opérations asynchrones | Microsoft Docs"
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
ms.assetid: d2cdb578-9923-47df-9ffd-5865333ac1a4
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c2dbf60cacf47be3c448b5683b771840ef85ddaf
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-culture-and-asynchronous-operations"></a>Atténuation : Culture et opérations asynchrones
Pour les applications qui ciblent le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] et versions ultérieures, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sont stockés dans le <xref:System.Threading.ExecutionContext> d’un thread, qui transite via des opérations asynchrones.  
  
## <a name="impact"></a>Impact  
 Conséquence de ce changement, les modifications apportées aux propriétés <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sont reflétées dans les tâches exécutées de façon asynchrone par la suite. Ce comportement diffère des précédentes versions de .NET Framework, qui réinitialiseraient <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> aux valeurs système par défaut dans toutes les tâches asynchrones.  
  
## <a name="mitigation"></a>Atténuation  
 Les applications affectées par ce changement peuvent contourner ce problème de deux manières :  
  
-   En définissant explicitement la propriété <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> souhaitée comme première opération dans une tâche asynchrone.  
  
-   En optant pour l’ancien comportement qui ne transmet pas <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> en ajoutant l’élément `AppContextSwitchOverrides` suivant au fichier de configuration de l’application :  
  
    ```xml  
  
    <configuration>  
        <runtime>  
            <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
        </runtime>  
    </configuration>  
  
    ```  
  
-   En optant pour l’ancien comportement qui ne transmet pas <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> en définissant le paramètre de compatibilité suivant par programme :  
  
    ```csharp  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);  
    ```  
  
    ```vb  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true)  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
