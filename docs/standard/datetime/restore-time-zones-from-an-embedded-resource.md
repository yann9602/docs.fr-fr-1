---
title: "Comment : restaurer des fuseaux horaires dans une ressource incorporée"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: efb133d972427a9619581d0670268cba9fbd3ee6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Comment : restaurer des fuseaux horaires dans une ressource incorporée

Cette rubrique explique comment restaurer des fuseaux horaires qui ont été enregistrées dans un fichier de ressources. Pour plus d’informations et des instructions sur l’enregistrement de fuseaux horaires, consultez [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Pour désérialiser un objet TimeZoneInfo à partir d’une ressource incorporée

1. Si le fuseau horaire à récupérer n’est pas un fuseau horaire personnalisé, essayez de l’instancier à l’aide de la <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> (méthode).

2. Instancier une <xref:System.Resources.ResourceManager> en passant le nom qualifié complet du fichier de ressources incorporées et une référence à l’assembly qui contient le fichier de ressources.

   Si vous ne peut pas déterminer le nom qualifié complet du fichier de ressources incorporé, utilisez la [Ildasm.exe (désassembleur IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour examiner le manifeste d’assembly. Un `.mresource` entrée identifie la ressource. Dans l’exemple, le nom qualifié complet de la ressource est `SerializeTimeZoneData.SerializedTimeZones`.

   Si le fichier de ressources est incorporé dans le même assembly qui contient le code de l’instanciation du fuseau horaire, vous pouvez récupérer une référence à celle-ci en appelant le `static` (`Shared` en Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> (méthode).

3. Si l’appel à la <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> méthode échoue, ou si un fuseau horaire personnalisé doit être instancié, récupérez une chaîne qui contient le fuseau horaire sérialisé en appelant le <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> (méthode).

4. Désérialisez les données de fuseau horaire en appelant le <xref:System.TimeZoneInfo.FromSerializedString%2A> (méthode).

## <a name="example"></a>Exemple

L’exemple suivant désérialise un <xref:System.TimeZoneInfo> objet stocké dans un fichier de ressources .NET XML incorporé.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Ce code illustre la gestion des exceptions pour vous assurer qu’un <xref:System.TimeZoneInfo> objet requis par l’application est présent. Il essaie d’instancier un <xref:System.TimeZoneInfo> récupérant dans le Registre à l’aide de l’objet le <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> (méthode). Si le fuseau horaire ne peut pas être instancié, le code extrait du fichier de ressources incorporées.

Étant donné que les données de fuseaux horaires personnalisés (fuseaux horaires instanciés à l’aide de la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> (méthode)) ne sont pas stockées dans le Registre, le code n’appelle pas la <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> pour instancier le fuseau horaire de Palmer, en Antarctique. Au lieu de cela, il consulte immédiatement le fichier de ressources incorporées pour récupérer une chaîne qui contient les données du fuseau horaire avant d’appeler le <xref:System.TimeZoneInfo.FromSerializedString%2A> (méthode).

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

* Une référence à System.Windows.Forms.dll et System.Core.dll à ajouter au projet.

* Que les espaces de noms suivants soient importés :

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
[vue d’ensemble du fuseau horaire](../../../docs/standard/datetime/time-zone-overview.md)
[Comment : enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
