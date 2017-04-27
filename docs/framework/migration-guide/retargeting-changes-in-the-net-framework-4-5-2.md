---
title: "Modifications du reciblage dans le .NET Framework 4.5.2 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2be2a828-9052-4738-a965-d4a836cc6384
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 10af942724ce0207bc6e64f1ebabfdcd2d3488bd
ms.lasthandoff: 04/18/2017

---
# <a name="retargeting-changes-in-the-net-framework-452"></a>Reciblage des modifications dans le .NET Framework 4.5.2
Dans de rares cas, les modifications de reciblage peuvent affecter les applications recompilées pour cibler le .NET Framework 4.5.2. Sauf indication contraire dans les tableaux ci-après, ces modifications n'affectent pas les fichiers binaires qui ciblent une version antérieure du .NET Framework mais s'exécutent sous la version 4.5.2. Le .NET Framework 4.5.2 incluent des modifications de reciblage dans les zones suivantes :  
  
-   [Entity Framework](#EF)  
  
-   [Windows Forms](#WinForms)  
  
<a name="EF"></a>   
## <a name="entity-framework-retargeting-changes"></a>Modifications de reciblage Entity Framework  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Requêtes plus simples lors de l'utilisation d'opérations de limitation non triées|Les requêtes qui produisent des instructions `JOIN` et contiennent un appel à une opération de limitation sans préalablement utiliser <xref:System.Data.Objects.ObjectQuery%601.OrderBy%2A> produisent à présent un langage SQL plus simple. Après la mise à niveau vers [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ces requêtes produisent un langage SQL plus compliqué que les versions antérieures.|Cette fonctionnalité est désactivée par défaut. Si Entity Framework génère des instructions `JOIN` supplémentaires qui entraînent une dégradation des performances, vous pouvez activer cette fonctionnalité en ajoutant l'entrée suivante à la section `<appSettings>` du fichier de configuration de l'application (app.config) :<br /><br /> `<add key="EntityFramework_SimplifyLimitOperations" value="true" />`|Secondaire|  
  
<a name="WinForms"></a>   
## <a name="windows-forms-retargeting-changes"></a>Modifications de reciblage Windows Forms  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Récupération des données au format HTML depuis le Presse-papiers avec la méthode <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=fullName>|Pour les applications qui ciblent [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ou qui s’exécutent sur le .NET Framework 4.5.1 ou versions antérieures, <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=fullName> récupère les données au format HTML sous forme de chaîne ASCII. Ainsi, les caractères non-ASCII (caractères dont les codes ASCII sont supérieurs à 0x7F) sont représentés par deux caractères aléatoires. Par exemple, é (0xE9) est représenté par Ã© (0xC3 0xA9).<br /><br /> Pour les applications qui ciblent le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou version ultérieure et qui s'exécutent sur le .NET Framework 4.5.2, <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=fullName> récupère les données au format HTML sous la forme de données UTF-8, qui représentent correctement les caractères supérieurs à 0x7F.|Si vous avez implémenté une solution de contournement pour ce problème de codage des chaînes au format HTML (par exemple, en codant explicitement la chaîne HTML récupérée à partir du Presse-papiers en la transférant à la méthode <xref:System.Text.UTF8Encoding.GetString%2A?displayProperty=fullName>) et que vous reciblez votre application depuis la version 4 vers la version 4.5, cette solution devrait être supprimée.|Mineur|  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications du runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-2.md)   
 [Compatibilité des applications dans la version 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [Compatibilité des applications dans la version 4.5.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)
