---
title: "Att&#233;nuation&#160;: contr&#244;le de version de produit | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Att&#233;nuation&#160;: contr&#244;le de version de produit
Dans [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] et 4.6.1, le contrôle de version de produit a changé par rapport aux mises en production précédentes du .NET Framework \(.NET Framework 4, 4.5, 4.5.1 et 4.5.2\).  
  
## Modifications du contrôle de version de produit  
 Voici le détail des modifications :  
  
-   La valeur de l'entrée `Version` dans la clé `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` est désormais `4.6.`*xxxxx*. Dans le .NET Framework 4.5, 4.5.1 et 4.5.2, elle avait le format `4.5.`*xxxxx*.  
  
-   Le contrôle de version de fichier et de produit pour les fichiers .NET Framework est passé de `4.0.30319.x` à `4.6.X.0` par rapport au schéma de contrôle de version antérieur. Pour voir ces nouvelles valeurs, cliquez avec le bouton droit sur un fichier, puis affichez ses **Propriétés**.  
  
-   Les attributs <xref:System.Reflection.AssemblyFileVersionAttribute> et <xref:System.Reflection.AssemblyInformationalVersionAttribute> pour les assemblys managés possèdent des valeurs <xref:System.Version> sous la forme `4.6.X.0`.  
  
-   Dans [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] et 4.6.1, la propriété <xref:System.Environment.Version%2A?displayProperty=fullName> retourne la chaîne de version fixe `4.0.30319.42000`. Dans le .NET Framework 4, 4.5, 4.5.1 et 4.5.2, elle retournait les chaînes de version dans le format `4.0.30319.xxxxx` \(par exemple « 4.0.30319.18010 »\). Notez que nous ne recommandons pas que le code d'application prenne de nouvelles dépendances sur la propriété <xref:System.Environment.Version%2A?displayProperty=fullName>.  
  
### Gestion des modifications du contrôle de version de produit  
 En général, les applications doivent s'appuyer sur les techniques recommandées pour la détection d'éléments tels que la version de runtime du .NET Framework et le répertoire d'installation :  
  
-   Pour détecter la version du runtime du .NET Framework, consultez [Comment : déterminer les versions .NET Framework installées](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).  
  
-   Pour déterminer le chemin d'installation du .NET Framework, utilisez la valeur de l'entrée `InstallPath` dans la clé `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`.  
  
    > [!IMPORTANT]
    >  Le nom de la sous\-clé est `NET Framework Setup`, et non `.NET Framework Setup`.  
  
-   Pour déterminer le chemin d'accès du répertoire du Common Language Runtime du .NET Framework, appelez la méthode <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=fullName>.  
  
-   Pour obtenir la version du CLR, appelez la méthode <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=fullName>.   Pour .NET Framework 4 et ses mises en production intermédiaires \(.NET Framework 4.5, 4.5.1, 4.5.2, ainsi que pour [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] et 4.6.1, elle retourne la chaîne `v4.0.30319`.  
  
## Voir aussi  
 [Modifications du runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)