---
title: "Comment&#160;: restaurer des fuseaux horaires dans une ressource incorpor&#233;e | Microsoft Docs"
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
  - "fuseaux horaires (.NET Framework), désérialiser"
  - "fuseaux horaires (.NET Framework), restaurer"
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: restaurer des fuseaux horaires dans une ressource incorpor&#233;e
Cette rubrique décrit comment restaurer des fuseaux horaires qui ont été enregistrés dans un fichier de ressources.  Pour obtenir des informations et des instructions sur l'enregistrement de fuseaux horaires, consultez [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).  
  
### Pour désérialiser un objet TimeZoneInfo à partir d'une ressource incorporée  
  
1.  Si le fuseau horaire à récupérer n'est pas un fuseau horaire personnalisé, essayez de l'instancier en utilisant la méthode <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>.  
  
2.  Instanciez un objet <xref:System.Resources.ResourceManager> en passant le nom qualifié complet du fichier de ressources incorporées et une référence à l'assembly qui contient le fichier de ressources.  
  
     Si vous ne pouvez pas déterminer le nom qualifié complet du fichier de ressources incorporées, utilisez le [Ildasm.exe \(IL Disassembler\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour examiner le manifeste de l'assembly.  Une entrée `.mresource` identifie la ressource.  Dans l'exemple, le nom qualifié complet de la ressource est `SerializeTimeZoneData.SerializedTimeZones`.  
  
     Si le fichier de ressources est incorporé dans le même assembly qui contient le code d'instanciation du fuseau horaire, vous pouvez récupérer une référence en appelant la méthode `static` \(`Shared` dans Visual Basic\) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A>.  
  
3.  Si l'appel à la méthode <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> échoue ou si un fuseau horaire personnalisé doit être instancié, récupérez une chaîne qui contient le fuseau horaire sérialisé en appelant la méthode <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>.  
  
4.  Désérialisez les données de fuseau horaire en appelant la méthode <xref:System.TimeZoneInfo.FromSerializedString%2A>.  
  
## Exemple  
 L'exemple suivant désérialise un objet <xref:System.TimeZoneInfo> stocké dans un fichier de ressources .NET XML incorporé.  
  
 [!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
 [!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]  
  
 Ce code illustre la gestion des exceptions pour garantir la présence d'un objet <xref:System.TimeZoneInfo> requis par l'application.  Il essaie d'abord d'instancier un objet <xref:System.TimeZoneInfo> en le récupérant dans le Registre à l'aide de la méthode <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>.  Si le fuseau horaire ne peut pas être instancié, le code le récupère à partir du fichier de ressources incorporées.  
  
 Comme les données des fuseaux horaires personnalisés \(fuseaux horaires instanciés à l'aide de la méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>\) ne sont pas stockées dans le Registre, le code n'appelle pas <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> pour instancier le fuseau horaire de Palmer, en Antarctique.  À la place, il consulte immédiatement le fichier de ressources incorporées pour récupérer une chaîne qui contient les données du fuseau horaire avant d'appeler la méthode <xref:System.TimeZoneInfo.FromSerializedString%2A>.  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   qu'une référence à System.Windows.Forms.dll et System.Core.dll soit ajoutée au projet.  
  
-   que les espaces de noms suivants soient importés :  
  
     [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
     [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)   
 [Vue d'ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md)   
 [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)