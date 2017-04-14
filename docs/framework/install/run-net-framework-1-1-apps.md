---
title: "Ex&#233;cution des applications&#160;.NET Framework&#160;1.1 sous Windows&#160;8,&#160;8.1 ou Windows&#160;10 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework 1.1, exécution sur Windows 8"
  - "Windows 8, exécution des applications .NET Framework 1.1"
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# Ex&#233;cution des applications&#160;.NET Framework&#160;1.1 sous Windows&#160;8,&#160;8.1 ou Windows&#160;10
Le .NET Framework 1.1 n'est pas pris en charge sur le [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] ou les systèmes d'exploitation Windows 10.  Dans certains cas, le. NET Framework 1.1 est identifié spécifiquement selon les exigences de l'exécution de l'application.  Dans ces cas\-là, vous devez contacter l'éditeur de logiciels indépendants \(ISV\) pour effectuer la mise à niveau de l'application afin qu'elle s'exécute sur [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] ou version ultérieure.  Pour plus d'informations, consultez [Migration à partir du .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).  
  
## Installation du .NET Framework 1.1 à partir d'un CD ou du Centre de téléchargement  
 Il n'est pas possible d'installer manuellement le .NET Framework 1.1 sur [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] ou Windows 10.  Elle n'est plus prise en charge.  Si vous essayez d'installer le package, le message d'erreur suivant s'affiche : « Le programme d'installation ne peut pas continuer, car cette version du .NET Framework est incompatible avec une version précédemment installée. ». Pour résoudre le problème, installez le [.NET Framework 3.5 SP1](http://www.microsoft.com/download/details.aspx?id=22).  Cette version inclut le .NET Framework 2.0 \(version qui suit le .NET Framework 1.1\), pris en charge sur [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)] et Windows 10.  Vous devez toujours essayer d'installer l'application d'abord afin de déterminer si elle sera mise à jour automatiquement vers une version ultérieure du .NET Framework.  Si ce n'est pas le cas, contactez votre éditeur de logiciels indépendant pour une mise à jour de l'application.  
  
## Voir aussi  
 [Migration à partir du .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)   
 [Installing the .NET Framework 3.5 on Windows 8 and later versions](../../../docs/framework/install/net-framework-3-5-on-windows-8-plus.md)