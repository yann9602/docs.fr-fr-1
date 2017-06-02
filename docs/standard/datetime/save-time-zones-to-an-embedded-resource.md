---
title: "Comment&#160;: enregistrer des fuseaux horaires dans une ressource incorpor&#233;e | Microsoft Docs"
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
  - "objet de fuseau horaire (.NET Framework), enregistrer"
  - "objet de fuseau horaire (.NET Framework), sérialisation"
  - "fuseaux horaires (.NET Framework), enregistrer"
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: enregistrer des fuseaux horaires dans une ressource incorpor&#233;e
Une application prenant en charge les fuseaux horaires requiert généralement la présence d'un fuseau horaire particulier.  Toutefois, comme la disponibilité d'objets <xref:System.TimeZoneInfo> individuels dépend d'informations stockées dans le Registre du système local, même les fuseaux horaires habituellement disponibles peuvent être absents.  De plus, les informations sur les fuseaux horaires personnalisés instanciés à l'aide de la méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> ne sont pas stockées avec d'autres informations de fuseau horaire dans le Registre.  Pour que ces fuseaux horaires soient disponibles lorsque vous en avez besoin, vous pouvez les enregistrer en les sérialisant puis les restaurer en les désérialisant.  
  
 En général, la sérialisation d'un objet <xref:System.TimeZoneInfo> se produit en dehors de l'application prenant en charge les fuseaux horaires.  Selon le magasin de données utilisé pour accueillir les objets <xref:System.TimeZoneInfo> sérialisés, les données de fuseau horaire peuvent être sérialisées dans le cadre d'une routine d'installation ou de configuration \(par exemple, lorsque les données sont stockées dans une clé du Registre relative à une application\) ou d'une routine d'utilitaire qui s'exécute avant la compilation de l'application finale \(par exemple, lorsque les données sérialisées sont stockées dans un fichier de ressources \(.resx\) .NET XML\).  
  
 Outre un fichier de ressources qui est compilé avec l'application, plusieurs autres magasins de données peuvent être utilisés pour contenir les informations de fuseau horaire,  et notamment :  
  
-   le Registre ;  à noter qu'une application doit utiliser les sous\-clés de sa propre clé d'application pour stocker des données de fuseau horaire personnalisées plutôt que les sous\-clés de HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\Time Zones.  
  
-   les fichiers de configuration ;  
  
-   d'autres fichiers système.  
  
### Pour enregistrer un fuseau horaire en le sérialisant dans un fichier .resx  
  
1.  Récupérez un fuseau horaire existant ou créez un fuseau horaire.  
  
     Pour récupérer un fuseau horaire existant, consultez [Comment : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis](../../../docs/standard/datetime/access-utc-and-local.md) et [Comment : instancier un objet TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).  
  
     Pour créer un fuseau horaire, appelez l'une des surcharges de la méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>.  Pour plus d'informations, consultez [Comment : créer des fuseaux horaires sans règles d'ajustement](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) et [Comment : créer des fuseaux horaires avec des règles d'ajustement](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).  
  
2.  Appelez la méthode <xref:System.TimeZoneInfo.ToSerializedString%2A> pour créer une chaîne qui contient les données du fuseau horaire.  
  
3.  Instanciez un objet <xref:System.IO.StreamWriter> en fournissant le nom et éventuellement le chemin d'accès du fichier .resx au constructeur de classe <xref:System.IO.StreamWriter>.  
  
4.  Instanciez un objet <xref:System.Resources.ResXResourceWriter> en passant l'objet <xref:System.IO.StreamWriter> au constructeur de classe <xref:System.Resources.ResXResourceWriter>.  
  
5.  Passez la chaîne sérialisée du fuseau horaire à la méthode <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=fullName>.  
  
6.  Appelez la méthode <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=fullName>.  
  
7.  Appelez la méthode <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=fullName>.  
  
8.  Fermez l'objet <xref:System.IO.StreamWriter> en appelant sa méthode <xref:System.IO.StreamWriter.Close%2A>.  
  
9. Ajoutez le fichier .resx généré au projet Visual Studio de l'application.  
  
10. Dans la fenêtre **Propriétés** de Visual Studio, assurez\-vous que la propriété **Build Action** du fichier .resx a la valeur **Ressource incorporée**.  
  
## Exemple  
 L'exemple suivant sérialise un objet <xref:System.TimeZoneInfo> qui représente l'heure du Centre des États\-Unis et un objet <xref:System.TimeZoneInfo> qui représente l'heure de la station de Palmer, en Antarctique, dans un fichier de ressources .NET XML nommé SerializedTimeZones.resx.  L'heure du Centre est généralement définie dans le Registre. La station de Palmer, en Antarctique, est un fuseau horaire personnalisé.  
  
 [!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
 [!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]  
  
 Cet exemple sérialise des objets <xref:System.TimeZoneInfo> pour qu'ils soient disponibles dans un fichier de ressources à la compilation.  
  
 Comme la méthode <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=fullName> ajoute des informations d'en\-tête complètes à un fichier de ressources .NET XML, il n'est pas possible de l'utiliser pour ajouter des ressources à un fichier existant.  L'exemple gère cette situation en recherchant le fichier SerializedTimeZones.resx. S'il existe, toutes ses ressources, à l'exception des deux fuseaux horaires sérialisés, sont stockées dans un objet <xref:System.Collections.Generic.Dictionary%602> générique.  Le fichier existant est ensuite supprimé et les ressources existantes sont ajoutées à un nouveau fichier SerializedTimeZones.resx.  Les données de fuseau horaire sérialisées sont également ajoutées à ce fichier.  
  
 Les champs clés \(ou **Nom**\) de ressources ne doivent pas contenir d'espaces incorporés.  La méthode <xref:System.String.Replace%28System.String%2CSystem.String%29> est appelée pour supprimer tous les espaces incorporés dans les identificateurs de fuseau horaire avant qu'ils ne soient assignés au fichier de ressources.  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   qu'une référence à System.Windows.Forms.dll et System.Core.dll soit ajoutée au projet.  
  
-   que les espaces de noms suivants soient importés :  
  
     [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
     [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)   
 [Vue d'ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md)   
 [Comment : restaurer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)