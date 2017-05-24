---
title: "Modification du runtime dans le .NET Framework 4.5.2 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94ac01ea-8b12-44d2-b12b-5220a5d14d87
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 247fbf574f13985fc941f252c0a6e7268194c079
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="runtime-changes-in-the-net-framework-452"></a>Modifications du runtime dans le .NET Framework 4.5.2
Dans de rares cas, les modifications du runtime peuvent affecter les applications existantes qui ciblent les versions antérieures du .NET Framework mais qui s'exécutent sur le runtime du .NET Framework 4.5.2. Il s'agit notamment des modifications dans les domaines suivants :  
  
-   [ASP.NET](#ASP_NET)  
  
-   [Entity Framework](#EF)  
  
<a name="ASP_NET"></a>   
## <a name="aspnet-runtime-changes"></a>Modifications du runtime ASP.NET  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|`enableViewStateMac` attribute of the [pages element](http://msdn.microsoft.com/en-us/4123bb66-3fe4-4d62-b70e-33758656b458)|ASP.NET ne permet plus aux développeurs de spécifier :<br /><br /> `<pages enableViewStateMac="false" />`<br /><br /> ou :<br /><br /> `<@Page EnableViewStateMac="false" %>`|Le code d'authentification de message (code MAC) de l'état d'affichage est à présent appliqué à toutes les demandes avec état d'affichage intégré. Seules les applications qui affectent explicitement à la propriété <xref:System.Web.UI.Page.EnableViewStateMac%2A> la valeur `false` sont affectées.<br /><br /> Pour plus d’informations, consultez [Résolution des erreurs de code d’authentification de message de l’état d’affichage](http://support.microsoft.com/kb/2915218).|Majeur|  
  
<a name="EF"></a>   
## <a name="entity-framework-runtime-changes"></a>Modifications du runtime Entity Framework  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Relations sur un QueryView|Entity Framework ne lève plus une exception <xref:System.StackOverflowException> quand une application exécute une requête qui implique un QueryView avec une propriété de navigation 0..1 qui tente d'inclure les entités associées dans le cadre de la requête, par exemple, en appelant `.Include(e=>e.RelatedNavProp)`.|Cette modification affecte uniquement le code qui utilise des QueryView avec des relations 1-0..1 pour exécuter des requêtes qui appellent `.Include`. Elle permet d'améliorer la fiabilité et doit être transparente pour presque toutes les applications. Toutefois, si elle entraîne un comportement inattendu, vous pouvez la désactiver en ajoutant l'entrée suivante à la section `<appSettings>` du fichier de configuration de l'application :<br /><br /> `<add key="EntityFramework_SimplifyUserSpecifiedViews"  value="false" />`|Limité|  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-5-2.md)   
 [Compatibilité des applications dans la version 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [Compatibilité des applications dans la version 4.5.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)
