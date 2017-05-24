---
title: "Atténuation : Sérialisation des caractères de contrôle avec DataContractJsonSerializer | Microsoft Docs"
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
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9460c8b6ca8db927af4064e3567eca34c1bf5c91
ms.openlocfilehash: be68f399587910e290fc3487b887ca566c2c9f97
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Atténuation : Sérialisation des caractères de contrôle avec DataContractJsonSerializer

À compter de .NET Framework 4.7, la manière dont les caractères de contrôle sont sérialisés avec le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a changé pour être conforme à ECMAScript V6 et V8. 
 
## <a name="impact"></a>Impact

Dans .NET Framework 4.6.2 et versions antérieures, le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ne sérialise pas certains caractères de contrôle spéciaux, comme `\b`, `\f` et `\t` d’une manière compatible avec les normes ECMAScript V6 et V8.

Pour les applications qui ciblent des versions de .NET Framework ultérieures à 4.7, la sérialisation de ces caractères de contrôle est compatible avec ECMAScript V6 et V8. Les API suivantes sont concernées :

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Atténuation

Pour les applications qui ciblent des versions de .NET Framework ultérieures à la 4.7, ce comportement est activé par défaut.

Si ce comportement n’est pas souhaitable, vous pouvez désactiver cette fonctionnalité en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config ou au fichier web.config :

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Voir aussi
[Reciblage des modifications dans le .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

