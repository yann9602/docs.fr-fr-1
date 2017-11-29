---
title: "Atténuation : Sérialisation des caractères de contrôle avec DataContractJsonSerializer"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6da580d208736a64e2094f701fb4c1241a488322
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="ed815-102">Atténuation : Sérialisation des caractères de contrôle avec DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="ed815-102">Mitigation: Serialization of Control Characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="ed815-103">À compter du .NET Framework 4.7, la manière dont les caractères de contrôle sont sérialisés avec le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a changé pour être conforme à ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="ed815-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="ed815-104">Impact</span><span class="sxs-lookup"><span data-stu-id="ed815-104">Impact</span></span>

<span data-ttu-id="ed815-105">Dans le .NET Framework 4.6.2 et versions antérieures, le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ne sérialise pas certains caractères de contrôle spéciaux, comme `\b`, `\f` et `\t`, d’une manière compatible avec les normes ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="ed815-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="ed815-106">Pour les applications qui ciblent des versions de .NET Framework ultérieures à 4.7, la sérialisation de ces caractères de contrôle est compatible avec ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="ed815-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="ed815-107">Les API suivantes sont concernées :</span><span class="sxs-lookup"><span data-stu-id="ed815-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="ed815-108">Atténuation</span><span class="sxs-lookup"><span data-stu-id="ed815-108">Mitigation</span></span>

<span data-ttu-id="ed815-109">Pour les applications qui ciblent des versions de .NET Framework ultérieures à la 4.7, ce comportement est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="ed815-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="ed815-110">Si ce comportement n’est pas souhaitable, vous pouvez désactiver cette fonctionnalité en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config ou au fichier web.config :</span><span class="sxs-lookup"><span data-stu-id="ed815-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="ed815-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed815-111">See also</span></span>
[<span data-ttu-id="ed815-112">Reciblage des modifications dans le .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="ed815-112">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
