---
title: "Activation du débogage JIT-attach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
caps.latest.revision: 17
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5ca6d1e6ec5c19f690ab862b13783b9db05ac2a9
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="enabling-jit-attach-debugging"></a>Activation du débogage JIT-attach
Débogage JIT-attach est l’expression utilisée pour décrire l’attachement d’un débogueur à un processus quand vous rencontrez des erreurs. Le débogage JIT-attach peut aussi être déclenché par des méthodes ou des fonctions spécifiques.  
  
 Le débogage JIT-attach est utilisé dans les conditions d’erreur suivantes :  
  
-   Exceptions non gérées (dans le code natif et managé)  
  
-   Méthode <xref:System.Environment.FailFast%2A?displayProperty=fullName> ou fonction [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) (famille Windows 7)  
  
-   Erreurs irrécupérables du runtime  
  
 Le débogage JIT-attach est également déclenché par des appels aux fonctions et méthodes suivantes :  
  
-   Méthode <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=fullName>.  
  
-   Méthode <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=fullName>.  
  
-   Fonction [DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) (Win32)  
  
 Avant le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], le .NET Framework fournissait des clés de Registre distinctes pour contrôler le comportement des débogueurs natifs et managés. À compter du [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], le contrôle est consolidé sous une clé de Registre unique : HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Les valeurs que vous pouvez définir pour cette clé déterminent si un débogueur est appelé et, dans l’affirmative, s’il est appelé avec une boîte de dialogue qui nécessite une interaction utilisateur. Pour plus d’informations sur la définition de cette clé de Registre, consultez [Configuring Automatic Debugging](http://go.microsoft.com/fwlink/?LinkId=181767) (Configuration du débogage automatique) dans MSDN Library.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage, traçage et profilage](../../../docs/framework/debug-trace-profile/index.md)   
 [Simplification du débogage d’une image](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)   
 [Activation du profilage](http://msdn.microsoft.com/en-us/3b669676-f0e0-4ebf-8674-68986dd2020d)

