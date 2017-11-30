---
title: Enregistrement et restauration de fuseaux horaires
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
- restoring time zones
- deserialization [.NET Framework], time zones
- serialization [.NET Framework], time zones
- time zone objects [.NET Framework], restoring
- saving time zones
- time zone objects [.NET Framework], deserializing
- time zones [.NET Framework], saving
- time zones [.NET Framework], restoring
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d4e04de61ed5636d0102af694220dce06c256751
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="saving-and-restoring-time-zones"></a>Enregistrement et restauration de fuseaux horaires

La <xref:System.TimeZoneInfo> classe s’appuie sur le Registre pour récupérer des données de fuseau horaire prédéfinies. Toutefois, le Registre est une structure dynamique. En outre, les informations de fuseau horaire que le Registre contient sont utilisées par le système d’exploitation essentiellement pour traiter les conversions et le réglage de l’heure pour l’année actuelle. Cela a deux conséquences principales pour les applications qui s’appuient sur des données de fuseau horaire exactes :

* Un fuseau horaire qui est requis par une application ne peut pas être défini dans le Registre, ou peut avoir été renommé ou supprimé du Registre.

* Un fuseau horaire qui est défini dans le Registre peut ne disposent pas d’informations sur les règles d’ajustement spécifiques qui sont nécessaires pour les conversions de fuseau horaire historiques.

La <xref:System.TimeZoneInfo> classe résout ces limitations en prenant en charge la sérialisation (enregistrement) et la désérialisation (restauration) des données de fuseau horaire.

## <a name="time-zone-serialization-and-deserialization"></a>La désérialisation et la sérialisation de fuseau horaire

Enregistrement et restauration d’un fuseau horaire à sérialiser et désérialiser des données de fuseau horaire impliquent deux appels de méthode :

* Vous pouvez sérialiser une <xref:System.TimeZoneInfo> objet en appelant l’objet <xref:System.TimeZoneInfo.ToSerializedString%2A> (méthode). La méthode ne prend aucun paramètre et retourne une chaîne qui contient les informations de fuseau horaire.

* Vous pouvez désérialiser un <xref:System.TimeZoneInfo> objet à partir d’une chaîne sérialisée en passant cette chaîne à la `static` (`Shared` en Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> (méthode).

## <a name="serialization-and-deserialization-scenarios"></a>Scénarios de sérialisation et la désérialisation

La possibilité d’enregistrer (ou le sérialiser) un <xref:System.TimeZoneInfo> objet en une chaîne et de restauration (ou désérialiser) pour une utilisation ultérieure accroît l’utilité et la flexibilité de la <xref:System.TimeZoneInfo> classe. Cette section examine certains des situations dans lesquelles la sérialisation et la désérialisation sont très utiles.

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>Sérialiser et désérialiser des données de fuseau horaire dans une application

Lorsqu’il est nécessaire, un fuseau horaire sérialisé peut être restauré à partir d’une chaîne. Une application peut procéder ainsi si le fuseau horaire récupéré à partir du Registre ne peut pas convertir correctement une date et une heure dans une plage de dates. Par exemple, les données de fuseau horaire dans le Registre de Windows XP prend en charge une règle d’ajustement unique, tandis que les fuseaux horaires définis dans le Registre Windows Vista généralement fournissent des informations sur deux règles d’ajustement. Cela signifie que les conversions d’heures historiques peuvent être inexactes. Sérialisation et désérialisation de données de fuseau horaire peuvent gérer cette limitation.

Dans l’exemple suivant, une personnalisée <xref:System.TimeZoneInfo> classe qui a des règles d’ajustement est définie pour représenter Zone de l’heure à partir de 1883 à 1917, avant l’introduction de l’heure d’été aux États-Unis. Le fuseau horaire personnalisé est sérialisé dans une variable qui a une portée globale. La méthode de conversion de fuseau horaire, `ConvertUtcTime`, est passée pour convertir le temps de temps universel coordonné (UTC). Si la date et l’heure se produit en 1917 ou une version antérieure, le personnalisé fuseau horaire est restauré à partir d’une chaîne sérialisée et remplace le fuseau horaire récupéré à partir du Registre.

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>La gestion des exceptions de fuseau horaire

Étant donné que le Registre est une structure dynamique, son contenu est soumises à modification accidentelle ou intentionnelle. Cela signifie qu’un fuseau horaire qui doit être défini dans le Registre et qui est requis pour une application de s’exécuter avec succès peuvent être absent. Sans la prise en charge pour la sérialisation de fuseau horaire et la désérialisation, ne vous reste plus qu’à gérer résultant <xref:System.TimeZoneNotFoundException> en mettant fin à l’application. Toutefois, à l’aide de fuseau horaire sérialisation et la désérialisation, vous pouvez gérer inattendus <xref:System.TimeZoneNotFoundException> en restaurant le fuseau horaire requis à partir d’une chaîne sérialisée et l’application continue de s’exécuter.

L’exemple suivant crée et sérialise un fuseau horaire Standard Central personnalisé. Ensuite, il essaie de récupérer le fuseau horaire Standard Central à partir du Registre. Si l’opération de récupération lève soit une <xref:System.TimeZoneNotFoundException> ou <xref:System.InvalidTimeZoneException>, le Gestionnaire d’exceptions désérialise le fuseau horaire.

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>Le stockage d’une chaîne sérialisée et la restauration en cas de besoin

Les exemples précédents ont stocké des informations de fuseau horaire à une variable de chaîne et restaurées. Toutefois, la chaîne qui contient l’heure sérialisée des informations de zone peuvent être stockées dans un support de stockage, tel qu’un fichier externe, un fichier de ressources incorporé dans l’application ou le Registre. (Notez que les informations sur les fuseaux horaires personnalisés doivent être stockées en dehors des clés de fuseau horaire du système dans le Registre).

Stockage d’une chaîne de fuseau horaire sérialisé de cette manière sépare également la routine de création de fuseau horaire à partir de l’application elle-même. Par exemple, une routine de création de fuseau horaire peut exécuter et créer un fichier de données qui contient des informations de fuseau horaire historiques qu’une application peut utiliser. Le fichier de données peut ensuite être installé avec l’application et elle peut être ouverte et un ou plusieurs de ses zones de temps peuvent être désérialisé lorsque l’application en a besoin.

Pour obtenir un exemple qui utilise une ressource incorporée pour stocker les données de fuseau horaire sérialisées, consultez [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) et [Comment : restaurer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
