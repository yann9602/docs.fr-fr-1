---
title: "Reciblage des modifications dans le&#160;.NET Framework 4.5.1 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8087326d-77e9-4804-ba33-ff1bb1bec2b8
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Reciblage des modifications dans le&#160;.NET Framework 4.5.1
Dans de rares cas, les modifications de reciblage peuvent affecter les applications recompilées pour cibler le [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]. Elles n'affectent pas les fichiers binaires qui ciblent une version antérieure du .NET Framework mais s'exécutent sous la version 4.5.1. Le [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] inclut des modifications de reciblage dans les domaines suivants :  
  
-   [Principal](#Core)  
  
-   [ADO.NET](#ADO)  
  
-   [MSBuild](#MSBuild)  
  
 La colonne Portée des tableaux suivants indique l'importance de chaque modification :  
  
-   Majeur. Modification importante qui affecte un grand nombre d'applications ou qui nécessite de modifier significativement le code. Notez qu'aucune des modifications de reciblage ne correspond à cette catégorie.  
  
-   Mineur. Modification qui affecte un petit nombre d'applications ou qui nécessite peu de modifications du code.  
  
-   Limité. Modification qui affecte des applications dans des scénarios très spécifiques qui ne sont pas courants.  
  
-   Transparent. Modification qui n'a pas d'effet visible pour le développeur ou l'utilisateur de l'application. L'application n'a pas besoin d'être modifiée en raison de cette modification.  
  
<a name="Core"></a>   
## Principales modifications de reciblage  
  
|Fonctionnalité|Modification|Impact|Portée|  
|--------------------|------------------|------------|------------|  
|Attribut <xref:System.ObsoleteAttribute?displayProperty=fullName>|Quand vous créez une bibliothèque de métadonnées Windows \(fichier .winmd\), l’attribut <xref:System.ObsoleteAttribute> est exporté en tant que <xref:System.ObsoleteAttribute> et [Windows.Foundation.DeprecatedAttribute](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.deprecatedattribute.aspx).|La recompilation de code source existant qui utilise l'attribut <xref:System.ObsoleteAttribute> peut générer des avertissements quand ce code est consommé à partir de C\+\+\/CX ou JavaScript.<br /><br /> Nous déconseillons d’appliquer <xref:System.ObsoleteAttribute> et [Windows.Foundation.DeprecatedAttribute](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.deprecatedattribute.aspx) au code d’assemblys managés, car cela peut produire des avertissements de génération.<br /><br /> Pour plus d'informations, voir la rubrique de référence relative à <xref:System.ObsoleteAttribute>.|Bord|  
  
<a name="ADO"></a>   
## Modifications de reciblage ADO.NET  
  
|Fonctionnalité|Modification|Impact|Portée|  
|--------------------|------------------|------------|------------|  
|Classe <xref:System.Data.Common.DbParameter?displayProperty=fullName>|Les propriétés <xref:System.Data.Common.DbParameter.Precision%2A?displayProperty=fullName> et <xref:System.Data.Common.DbParameter.Scale%2A?displayProperty=fullName> sont implémentées en tant que propriétés virtuelles publiques. Elles remplacent les implémentations d'interface explicites correspondantes, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision%2A?displayProperty=fullName> et <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale%2A?displayProperty=fullName>.|La modification affecte uniquement les développeurs qui génèrent un fournisseur de base de données ADO.NET.|Bord|  
  
<a name="MSBuild"></a>   
## Modifications de reciblage MSBuild  
  
|Fonctionnalité|Modification|Impact|Portée|  
|--------------------|------------------|------------|------------|  
|Tâche `ResolveAssemblyReference`|La tâche émet un avertissement, MSB3270, qui indique qu'une référence ou l'une de ses dépendances ne correspond pas à l'architecture de l'application. Cette situation se produit, par exemple, si une application qui a été compilée avec l'option `anycpu` inclut une référence x86. Ainsi, l'application peut échouer au moment de l'exécution \(si l'application est déployée en tant que processus x64 dans notre exemple\).|Deux domaines sont impactés :<br /><br /> -   La recompilation génère des avertissements qui n'étaient pas apparus quand l'application avait été compilée sous une version antérieure de MSBuild. En revanche, étant donné que l'avertissement identifie une source potentielle d'échec du runtime, vous devez l'examiner et le traiter.<br />-   Si les avertissements sont considérés comme des erreurs, la compilation de l'application échouera.|Secondaire|  
  
## Voir aussi  
 [Modifications du runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)   
 [Compatibilité des applications dans la version 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [Compatibilité des applications dans la version 4.5.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)