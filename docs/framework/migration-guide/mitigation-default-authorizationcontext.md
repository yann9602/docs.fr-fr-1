---
title: "Att&#233;nuation&#160;: AuthorizationContext par d&#233;faut | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6cfeee63-b148-429a-a7e6-6fe9b0cb7610
caps.latest.revision: 3
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 3
---
# Att&#233;nuation&#160;: AuthorizationContext par d&#233;faut
L'implémentation du <xref:System.IdentityModel.Policy.AuthorizationContext> retourné par un appel à la <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> avec un argument `null` `authorizationPolicies` a changé son implémentation dans le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].  
  
## Impact  
 Dans de rares cas, les applications WCF qui utilisent l'authentification personnalisée peuvent voir les différences de comportement.  
  
## Atténuation  
 Vous pouvez restaurer le comportement précédent de deux manières :  
  
-   Recompiler l'application pour cibler une version antérieure du .NET Framework autre que 4.6.  Pour les services hébergés dans IIS, utilisez l'élément `<httpRuntime targetFramework="x.x" />` pour cibler une version antérieure du .NET Framework.  
  
-   Ajoutez la ligne suivante à la section `<appSettings>` de votre fichier app.config :  
  
    ```  
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />  
    ```  
  
## Voir aussi  
 [Reciblage des modifications](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)