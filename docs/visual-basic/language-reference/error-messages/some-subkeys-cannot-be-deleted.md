---
title: "Some subkeys cannot be deleted | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 14562137-af43-4972-84c1-a380a90f7d6c
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Some subkeys cannot be deleted
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une tentative a été effectuée pour supprimer une clé de Registre, mais l'opération a échoué car certaines sous\-clés ne peuvent pas être supprimées.  Cela est généralement dû à une absence d'autorisations.  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous que vous disposez des autorisations nécessaires pour supprimer les sous\-clés spécifiées.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy?displayProperty=fullName>   
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>   
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>   
 <xref:System.Security.Permissions.RegistryPermission>