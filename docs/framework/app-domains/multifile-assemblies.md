---
title: Assemblys multifichiers
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bded4fae854d10a17ddd03b8855f6096e18ab87f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="multifile-assemblies"></a>Assemblys multifichiers
Vous pouvez créer des assemblys multifichiers à l’aide de compilateurs de ligne de commande ou [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] avec Visual C++. L’un des fichiers de l’assembly doit contenir le manifeste d’assembly. Un assembly qui démarre une application doit également contenir un point d’entrée, tel que la méthode Main ou WinMain.  
  
 Supposons, par exemple, que vous possédiez une application contenant deux modules de code, Client.cs et Stringer.cs. Stringer.cs crée l’espace de noms `myStringer` qui est référencé par le code contenu dans Client.cs. Client.cs contient la méthode `Main` qui est le point d’entrée de l’application. Dans cet exemple, vous compilez les deux modules de code, puis créez un troisième fichier qui contient le manifeste d’assembly, qui lance l’application. Le manifeste d’assembly référence les modules `Client` et `Stringer`.  
  
> [!NOTE]
>  Les assemblys multifichiers ne peuvent avoir qu’un seul point d’entrée, même si l’assembly a plusieurs modules de code.  
  
 Il est possible de créer un assembly multifichier pour plusieurs raisons :  
  
-   Pour combiner des modules écrits dans différents langages. Il s’agit de la raison la plus courante de créer un assembly multifichier.  
  
-   Pour optimiser le téléchargement d’une application en plaçant des types rarement utilisés dans un module qui n’est téléchargé que si nécessaire.  
  
    > [!NOTE]
    >  Si vous créez des applications destinées à être téléchargées à l’aide de la balise `<object>` avec Microsoft Internet Explorer, il est important de créer des assemblys multifichiers. Dans ce scénario, vous créez un fichier distinct de vos modules de code, qui contient uniquement le manifeste d’assembly. Internet Explorer télécharge d’abord le manifeste d’assembly, puis crée des threads de travail pour télécharger tout assembly ou module supplémentaire requis. Pendant le téléchargement du fichier contenant le manifeste d’assembly, Internet Explorer ne répond pas aux entrées d’utilisateur. La durée de non-réponse d’Internet Explorer est proportionnelle à la taille du fichier contenant le manifeste d’assembly.  
  
-   Pour combiner des modules de code écrits par plusieurs développeurs. Même si chaque développeur peut compiler chaque module de code dans un assembly, ceci peut forcer l’exposition publique de certains types qui ne sont pas exposés si tous les modules sont placés dans un assembly multifichier.  
  
 Une fois l’assembly créé, vous pouvez signer le fichier qui contient le manifeste d’assembly (donc, l’assembly) ou attribuer au fichier (et à l’assembly) un nom fort et le placer dans le Global Assembly Cache.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour générer un assembly multifichier](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Programmation à l’aide d’assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)
