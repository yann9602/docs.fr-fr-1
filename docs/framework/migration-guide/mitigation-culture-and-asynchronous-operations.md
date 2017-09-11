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
# <a name="mitigation-culture-and-asynchronous-operations"></a><span data-ttu-id="9fbab-102">Atténuation : Culture et opérations asynchrones</span><span class="sxs-lookup"><span data-stu-id="9fbab-102">Mitigation: Culture and Asynchronous Operations</span></span>
<span data-ttu-id="9fbab-103">Pour les applications qui ciblent le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] et versions ultérieures, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sont stockées dans le <xref:System.Threading.ExecutionContext> d’un thread, qui circulent à travers des opérations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="9fbab-103">For apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] and later versions, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> are stored in a thread's <xref:System.Threading.ExecutionContext>, which flows across asynchronous operations.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="9fbab-104">Impact</span><span class="sxs-lookup"><span data-stu-id="9fbab-104">Impact</span></span>  
 <span data-ttu-id="9fbab-105">Conséquence de ce changement, les changements apportés à <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou à <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sont reflétées dans les tâches exécutées de façon asynchrone par la suite.</span><span class="sxs-lookup"><span data-stu-id="9fbab-105">As a result of this change, changes to the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> are reflected in tasks which are later run asynchronously.</span></span> <span data-ttu-id="9fbab-106">Ce comportement diffère des précédentes versions du .NET Framework, qui réinitialisaient <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> aux valeurs système par défaut dans toutes les tâches asynchrones.</span><span class="sxs-lookup"><span data-stu-id="9fbab-106">This differs from the behavior of previous .NET Framework versions, which would reset <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> to the system default  in all asynchronous tasks.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="9fbab-107">Atténuation</span><span class="sxs-lookup"><span data-stu-id="9fbab-107">Mitigation</span></span>  
 <span data-ttu-id="9fbab-108">Les applications affectées par ce changement peuvent contourner ce problème de deux manières :</span><span class="sxs-lookup"><span data-stu-id="9fbab-108">Apps affected by this change can work around it in either of two ways:</span></span>  
  
-   <span data-ttu-id="9fbab-109">En définissant explicitement la propriété <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> souhaitée comme première opération dans une tâche asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9fbab-109">By explicitly setting the desired <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> property as the first operation in an asynchronous task.</span></span>  
  
-   <span data-ttu-id="9fbab-110">En optant pour l’ancien comportement qui ne transmet pas <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> en ajoutant l’élément `AppContextSwitchOverrides` suivant au fichier de configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="9fbab-110">By opting into the old behavior of not flowing <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> by adding the following `AppContextSwitchOverrides` element to the application's configuration file:</span></span>  
  
    ```xml  
    <configuration>  
        <runtime>  
            <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
        </runtime>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="9fbab-111">En optant pour l’ancien comportement qui ne transmet pas <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> en définissant le commutateur de compatibilité suivant par programmation :</span><span class="sxs-lookup"><span data-stu-id="9fbab-111">By opting into the old behavior of not flowing <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> by setting the following compatibility switch programatically:</span></span>  
  
    ```csharp  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);  
    ```  
  
    ```vb  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9fbab-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fbab-112">See Also</span></span>  
 [<span data-ttu-id="9fbab-113">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="9fbab-113">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

