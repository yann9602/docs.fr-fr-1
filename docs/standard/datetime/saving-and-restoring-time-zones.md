---
title: "Enregistrement et restauration de fuseaux horaires | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "désérialisation (.NET Framework), fuseaux horaires"
  - "restauration de fuseaux horaires"
  - "enregistrement de fuseaux horaires"
  - "sérialisation (.NET Framework), fuseaux horaires"
  - "objet de fuseau horaire (.NET Framework), désérialiser"
  - "objet de fuseau horaire (.NET Framework), restaurer"
  - "objet de fuseau horaire (.NET Framework), enregistrer"
  - "objet de fuseau horaire (.NET Framework), sérialisation"
  - "fuseaux horaires (.NET Framework), restaurer"
  - "fuseaux horaires (.NET Framework), enregistrer"
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Enregistrement et restauration de fuseaux horaires
La classe <xref:System.TimeZoneInfo> dépend du Registre pour récupérer des données de fuseau horaire prédéfinies.  Toutefois, le Registre est une structure dynamique.  En outre, les informations de fuseau horaire présentes dans le Registre sont surtout utilisées par le système d'exploitation pour gérer les ajustements et les conversions horaires de l'année en cours.  Cela a deux conséquences majeures pour les applications qui requièrent des données de fuseau horaire exactes :  
  
-   Il se peut qu'un fuseau horaire requis par une application ne soit pas défini dans le Registre ou qu'il ait été renommé ou supprimé du Registre.  
  
-   Il se peut qu'un fuseau horaire défini dans le Registre manque d'informations sur les règles d'ajustement spécifiques nécessaires aux conversions de fuseau horaire historiques.  
  
 La classe <xref:System.TimeZoneInfo> surmonte ces limitations en prenant en charge la sérialisation \(enregistrement\) et la désérialisation \(restauration\) des données de fuseau horaire.  
  
## Sérialisation et désérialisation de fuseau horaire  
 L'enregistrement et la restauration d'un fuseau horaire en sérialisant et désérialisant des données de fuseau horaire supposent deux appels de méthode uniquement :  
  
-   Vous pouvez sérialiser un objet <xref:System.TimeZoneInfo> en appelant la méthode <xref:System.TimeZoneInfo.ToSerializedString%2A> de cet objet.  La méthode n'accepte aucun paramètre et retourne une chaîne qui contient des informations de fuseau horaire.  
  
-   Vous pouvez désérialiser un objet <xref:System.TimeZoneInfo> à partir d'une chaîne sérialisée en passant cette chaîne à la méthode `static` \(`Shared` dans Visual Basic\) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=fullName>.  
  
## Scénarios de sérialisation et de désérialisation  
 La capacité d'enregistrer \(ou de sérialiser\) un objet <xref:System.TimeZoneInfo> sur une chaîne et de le restaurer \(ou le désérialiser\) en vue d'une utilisation ultérieure accroît l'utilité et la souplesse de la classe <xref:System.TimeZoneInfo>.  Cette section examine quelques situations dans lesquelles la sérialisation et la désérialisation sont très utiles.  
  
### Sérialisation et désérialisation de données de fuseau horaire dans une application  
 Un fuseau horaire sérialisé peut être restauré à partir d'une chaîne, le cas échéant.  Une application peut effectuer cette restauration si le fuseau horaire récupéré du Registre ne peut pas convertir correctement une date et une heure dans une plage de dates donnée.  Par exemple, les données de fuseau horaire du Registre Windows XP prennent en charge une seule règle d'ajustement, tandis que les fuseaux horaires définis dans le Registre Windows Vista fournissent généralement des informations concernant deux règles d'ajustement.  Cela signifie que les conversions d'heures historiques peuvent être inexactes.  La sérialisation et la désérialisation des données de fuseau horaire peuvent gérer cette limitation.  
  
 Dans l'exemple suivant, une classe personnalisée <xref:System.TimeZoneInfo> qui n'a pas de règle d'ajustement est définie pour représenter le fuseau horaire standard des États\-Unis de 1883 à 1917, avant l'introduction de l'heure d'été aux États\-Unis.  Le fuseau horaire personnalisé est sérialisé dans une variable de portée globale.  La méthode de conversion de fuseau horaire, `ConvertUtcTime`, est passée pour convertir le temps universel coordonné \(UTC, Coordinated Universal Time\).  Si la date et l'heure se produisent en 1917 ou avant, fuseau horaire personnalisé de la côte est des États\-Unis est restauré à partir d'une chaîne sérialisée et remplace le fuseau horaire récupéré du Registre.  
  
 [!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
 [!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]  
  
### Gestion des exceptions de fuseau horaire  
 Comme le Registre est une structure dynamique, son contenu peut être modifié délibérément ou accidentellement.  Il se peut donc qu'un fuseau horaire nécessaire à l'exécution d'une application et qui devrait être défini dans le Registre soit absent.  Si la sérialisation et la désérialisation de fuseau horaire ne sont pas prises en charge, il ne vous reste plus qu'à gérer l'exception <xref:System.TimeZoneNotFoundException> résultante en mettant fin à l'application.  Toutefois, si vous faites appel à la sérialisation et à la désérialisation de fuseau horaire, vous pouvez gérer une exception <xref:System.TimeZoneNotFoundException> inattendue en restaurant le fuseau horaire requis à partir d'une chaîne sérialisée. L'application pourra alors poursuivre son exécution.  
  
 L'exemple suivant crée et sérialise un fuseau horaire personnalisé du Centre des États\-Unis.  Il essaie ensuite de récupérer le fuseau horaire du Centre à partir du Registre.  Si l'opération de récupération lève une exception <xref:System.TimeZoneNotFoundException> ou <xref:System.InvalidTimeZoneException>, le gestionnaire d'exceptions désérialise le fuseau horaire.  
  
 [!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
 [!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]  
  
### Stockage et restauration d'une chaîne sérialisée  
 Dans les exemples précédents, les informations de fuseau horaire ont été stockées dans une variable chaîne puis restaurées.  Toutefois, la chaîne qui contient des informations de fuseau horaire sérialisées peut être stockée sur un support de stockage, tel qu'un fichier externe, un fichier de ressources incorporé dans l'application ou le Registre. \(Les informations sur les fuseaux horaires personnalisés doivent être stockées à l'écart des clés relatives au fuseau horaire du système dans le Registre.\)  
  
 En stockant une chaîne de fuseau horaire sérialisée de cette manière, la routine de création de fuseau horaire est également séparée de l'application elle\-même.  Par exemple, une routine de création de fuseau horaire peut exécuter et créer un fichier de données qui contient des informations de fuseau horaire historiques exploitables par une application.  Le fichier de données peut ensuite être installé avec l'application puis être ouvert. Un ou plusieurs de ses fuseaux horaires peuvent être désérialisés dès que l'application en a besoin.  
  
 Pour obtenir un exemple qui utilise une ressource incorporée afin de stocker des données de fuseau horaire sérialisées, consultez [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) et [Comment : restaurer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)