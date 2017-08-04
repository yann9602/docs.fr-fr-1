---
title: "Atténuation : Culture et opérations asynchrones"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: debcae8281c832d2815e1b9896fbbcb725c8ffc3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-culture-and-asynchronous-operations"></a>Atténuation : Culture et opérations asynchrones
Pour les applications qui ciblent le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] et versions ultérieures, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sont stockées dans le <xref:System.Threading.ExecutionContext> d’un thread, qui circulent à travers des opérations asynchrones.  
  
## <a name="impact"></a>Impact  
 Conséquence de ce changement, les changements apportés à <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou à <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sont reflétées dans les tâches exécutées de façon asynchrone par la suite. Ce comportement diffère des précédentes versions du .NET Framework, qui réinitialisaient <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> aux valeurs système par défaut dans toutes les tâches asynchrones.  
  
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
  
-   En optant pour l’ancien comportement qui ne transmet pas <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> en définissant le commutateur de compatibilité suivant par programmation :  
  
    ```csharp  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);  
    ```  
  
    ```vb  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true)  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

